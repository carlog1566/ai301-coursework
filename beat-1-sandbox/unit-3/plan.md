# Plan for Issue #13

## Diagnosis

The reproduction from Unit 2 showed two important parts of the current state:

```text
tests/integration/__init__.py
```

This confirms that there is currently no full RAG integration test under `tests/integration/`.

The reproduction also showed that `ReviewGenerator` creates its own OpenAI client inside its constructor:

```python
self.client = openai.OpenAI(api_key=config.api_key, base_url=config.base_url)
```

and later calls:

```python
response = self.client.chat.completions.create(...)
```

Because the client is created internally, there is no direct constructor-level injection point for an integration test to provide a fixed mock LLM response.

The issue therefore needs two related changes: make the generator testable with a controlled client, and add a marked integration test that exercises retrieval, generation, and parsing using that controlled LLM behavior.

## Scope

### In scope

- Add a way for `ReviewGenerator` to use an injected OpenAI-compatible client while keeping the current behavior as the default.
- Add `tests/integration/test_rag_pipeline.py`.
- Mark the new test with `@pytest.mark.integration` so it is included by the repository's integration-test command.
- Use the existing `tests/fixtures/sample_profiles/basic_profile.json` fixture.
- Use a fixed mock LLM response so the integration test does not depend on a live external API.
- Exercise retrieval, generation, and parsing through the real pipeline path.
- Keep existing production behavior unchanged when no mock client is supplied.

### Out of scope

- Changing the retrieval algorithm itself.
- Changing prompt templates unless a minimal adjustment is required for the test.
- Adding a new LLM provider.
- Refactoring unrelated RAG code.
- Changing application UI or API behavior.
- Making broad changes to OpenAI/OpenRouter configuration.

## Files to touch

### `rag/generator/review_generator.py`

Update `ReviewGenerator` so a caller can optionally provide an OpenAI-compatible client.

If no client is provided, `ReviewGenerator` should continue creating its own `openai.OpenAI` client from `ReviewConfig`.

### `tests/integration/test_rag_pipeline.py`

Add an integration test marked with:

```python
@pytest.mark.integration
```

The test will exercise the RAG path using `tests/fixtures/sample_profiles/basic_profile.json` and a deterministic fake LLM client.

## Approach

1. Update `ReviewGenerator.__init__` to accept an optional client parameter.

2. Preserve the current behavior when no client is supplied. Conceptually:

```python
self.client = client or openai.OpenAI(
    api_key=config.api_key,
    base_url=config.base_url,
)
```

The exact type annotation will depend on the OpenAI client type already used by the project.

3. Add `tests/integration/test_rag_pipeline.py`.

4. Mark the test with:

```python
@pytest.mark.integration
```

5. Reuse `tests/fixtures/sample_profiles/basic_profile.json` as the profile input.

6. Run the real retrieval path used by the RAG pipeline so the test covers retrieval rather than supplying already-retrieved chunks directly.

7. Provide a small fake OpenAI-compatible client that implements:

```text
client.chat.completions.create(...)
```

and returns a fixed response in the shape expected by:

```python
response.choices[0].message.content
```

8. Have the fake client record whether `create()` was called so the test can assert that generation actually used the fake client.

9. Pass the fake client into `ReviewGenerator`.

10. Assert that:
   - retrieval produces context used by the pipeline,
   - the fake client's `create()` method is called,
   - the fixed response is parsed into the expected `FeedbackSection`,
   - no real OpenAI/OpenRouter credentials are needed.

## Test plan

### Before the change

The Unit 2 reproduction showed:

```bash
find tests/integration -maxdepth 2 -type f -print
```

Output:

```text
tests/integration/__init__.py
```

It also showed:

```bash
grep -n "openai.OpenAI" rag/generator/review_generator.py
```

Output:

```text
35:        self.client = openai.OpenAI(api_key=config.api_key, base_url=config.base_url)
```

This is the baseline: there is no RAG integration test, and `ReviewGenerator` constructs its own client internally.

### After the change

First confirm the integration test exists:

```bash
find tests/integration -maxdepth 2 -type f -print
```

Expected output includes:

```text
tests/integration/__init__.py
tests/integration/test_rag_pipeline.py
```

Then run the repository's integration-test command:

```bash
pytest tests/integration -v -m integration
```

Expected result:

```text
1 passed
```

with the new RAG integration test selected rather than deselected.

To verify the test does not depend on a real LLM credential, run it with the OpenAI key removed:

```bash
env -u OPENAI_API_KEY pytest tests/integration -v -m integration
```

Expected result:

```text
1 passed
```

The test will also assert that the fake client's `create()` method was called, which confirms that generation used the injected fake instead of making a real LLM request.

Finally, run the existing unit tests:

```bash
make test-unit
```

Expected result: the existing unit tests continue to pass, confirming that adding optional client injection did not break the default production path.

## Risks and unknowns

- I still need to confirm the exact OpenAI response-object shape required by `response.choices[0].message.content`.
- I need to check whether the repository already contains a reusable fake OpenAI client or mock helper before creating a new one.
- I need to inspect the current RAG orchestration to identify the correct entry point that runs retrieval, generation, and parsing together without bypassing retrieval.
- I will keep the client-injection change minimal so normal production construction of `ReviewGenerator` remains unchanged.

## Deviations

The implementation stayed mostly consistent with the original plan. After inspecting the repository, I confirmed that there was no single existing entry point that ran retrieval and generation together. Because of that, the integration test wires the existing `VectorStore`, `KeywordSearcher`, `HybridRetriever`, and `ReviewGenerator` components together directly rather than adding a new production orchestration layer.

I also used a temporary ChromaDB store with deterministic embeddings so the test can run the real retrieval path without requiring an external embedding service. The fixed fake LLM client is injected into `ReviewGenerator`, and the test verifies that its `create()` method is called and that retrieved content reaches the generation prompt.

No other changes from the planned scope were necessary.