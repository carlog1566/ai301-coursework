# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

carlog1566

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/13#issuecomment-6028879086

I reproduced the current limitation and put together a plan for the change.

The main issue is that `ReviewGenerator` currently creates its own OpenAI client in the constructor, so the integration test does not have a direct way to provide a deterministic mock LLM response.

My plan is to:

- Add an optional client parameter to `ReviewGenerator` while keeping the current client creation as the default behavior.
- Add `tests/integration/test_rag_pipeline.py` and mark it with `@pytest.mark.integration`.
- Reuse `tests/fixtures/sample_profiles/basic_profile.json`.
- Exercise the real retrieval → generation → parsing path.
- Use a fixed fake LLM response and assert that the fake client's `create()` method is called.
- Run `pytest tests/integration -v -m integration` with `OPENAI_API_KEY` unset to verify the integration test passes without a real LLM request.
- Run `make test-unit` afterward to confirm the existing unit tests still pass.

I’m keeping retrieval behavior changes, prompt changes, unrelated refactors, and provider changes out of scope. One thing I still need to confirm during implementation is the correct existing entry point for exercising retrieval, generation, and parsing together without bypassing the retrieval layer.

---

## Your branch

**Branch**

`test/13-rag-integration-test`

**Evidence**

**Before**

During my Unit 2 reproduction, I checked the existing integration-test directory:

```bash
find tests/integration -maxdepth 2 -type f -print
```

Output:

```text
tests/integration/__init__.py
```

I also checked where the OpenAI client was created:

```bash
grep -n "openai.OpenAI" rag/generator/review_generator.py
```

Output:

```text
35:        self.client = openai.OpenAI(api_key=config.api_key, base_url=config.base_url)
```

This showed that there was no RAG integration test and that `ReviewGenerator` always created its OpenAI client internally.

**After**

After implementing the change, I checked the integration-test directory again:

```bash
find tests/integration -maxdepth 1 -type f -print
```

Output:

```text
tests/integration/test_rag_pipeline.py
tests/integration/__init__.py
```

I then checked the updated `ReviewGenerator` constructor:

```bash
grep -n "def __init__" rag/generator/review_generator.py | head
```

Output:

```text
29:    def __init__(self, config: ReviewConfig, client: Any | None = None):
```

I also checked the OpenAI client creation path:

```bash
grep -n "openai.OpenAI" rag/generator/review_generator.py
```

Output:

```text
40:            else openai.OpenAI(api_key=config.api_key, base_url=config.base_url)
```

This shows that the constructor now accepts an optional injected client while keeping the original OpenAI client creation as the default behavior.

I then ran the marked integration test:

```bash
pytest tests/integration -v -m integration
```

Output:

```text
collected 1 item

tests/integration/test_rag_pipeline.py::test_rag_pipeline_with_fixed_llm_response PASSED [100%]

1 passed, 1 warning
```

I also ran the integration directory using the same style as CI:

```bash
pytest tests/integration -v --tb=short
```

Output:

```text
collected 1 item

tests/integration/test_rag_pipeline.py::test_rag_pipeline_with_fixed_llm_response PASSED [100%]

1 passed, 1 warning
```

Finally, I ran the existing unit suite:

```bash
make test-unit
```

Output:

```text
375 passed, 53 xfailed, 2 warnings in 8.99s
```

The new integration test now exercises the real retrieval path through `VectorStore`, `KeywordSearcher`, and `HybridRetriever`, passes those retrieved chunks into `ReviewGenerator`, uses the injected fake LLM client, and verifies that the fixed response is parsed successfully.

## Eval iterations

**Run history**

My full eval run got:

> `agreement: 19/20 scored items  (bar: 18/20: PASS)`

This was the full run that produced my submitted `eval-run.txt`. The only disagreement was `pkg-20`; all other 19 scored packages matched their gold labels.

**Package analysis**

I chose `pkg-20`.

From my eval run:

> `pkg-20  thread-convention  reject  accept  NO     graded accept`

The gold label for `pkg-20` was **reject**, while my rubric decided **accept**.

My rubric's communication check focused on whether the draft comment was specific to the issue, accurately represented the proposed approach and test plan, did not contradict relevant maintainer guidance, and followed the repository's stated contribution requirements. Under those conditions, the grader found enough evidence to accept the package.

The gold label shows that there was still a thread or convention problem that my check did not catch. This means my rule could recognize obvious contradictions or missing repository requirements, but it was not strict enough to detect every thread-specific problem.

**Check rationale**

The check I used for this area was:

> `Comment follows thread and repo conventions | The draft plan comment read against the issue thread, repo-facts block or live contribution docs, and applicable repository policies. | Pass if the comment is specific to this issue, accurately summarizes the planned approach and test strategy, does not contradict relevant maintainer guidance, and follows any applicable contribution or AI-disclosure requirements. If no special requirement exists, pass. | required`

I wrote this check this way because the plan itself can be technically strong while the comment posted upstream can still be inappropriate for the issue or repository. I wanted the grader to compare the comment with the actual thread and contribution rules rather than judging it only as standalone writing.

I also chose not to require one specific comment format because the repository did not require one. The check instead focuses on whether the comment is accurate, issue-specific, consistent with maintainer guidance, and compliant with stated repository requirements.

**Trade-offs**

The trade-off of this check is that it is good at catching explicit thread or repository conflicts but can miss a more subtle thread-convention problem when the comment still appears issue-specific and consistent with the general repository rules.

`pkg-20` showed that limitation:

> `pkg-20  thread-convention  reject  accept  NO     graded accept`

My rubric accepted it while the gold label rejected it. I kept the check as written because the same rule correctly rejected the other `thread-convention` package, `pkg-04`, and the full eval still matched 19 of 20 scored packages and passed the required threshold. Tightening the check only to force `pkg-20` to reject could also risk rejecting valid plan comments that do not follow an unnecessary fixed format.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
