I was able to confirm the current limitation described in this issue before making any implementation changes.

### Environment

- macOS
- Commit: `2f4e82f52efbcfcc57d65b3fa5348672163ca088`
- Python: `3.14.6`
- Node: `v24.18.0`
- npm: `12.0.2`
- Docker: `29.8.1`
- Docker Compose: `v5.5.1`
- Branch: `main`
- Working tree: clean

I set up the project successfully using the repository setup instructions before checking the current RAG integration-test path.

### Steps

From the repository root, I first checked the current integration-test directory:

```bash
find tests/integration -maxdepth 2 -type f -print
```

Output:

```text
tests/integration/__init__.py
```

I then checked where the OpenAI client is created:

```bash
grep -n "openai.OpenAI" rag/generator/review_generator.py
```

Output:

```text
35:        self.client = openai.OpenAI(api_key=config.api_key, base_url=config.base_url)
```

I also checked where that client is used to generate a response:

```bash
grep -n "self.client.chat.completions.create" rag/generator/review_generator.py
```

Output:

```text
63:        response = self.client.chat.completions.create(
```

Finally, I inspected the surrounding implementation in `ReviewGenerator`. Its constructor currently only accepts a `ReviewConfig` and creates the OpenAI client internally:

```python
def __init__(self, config: ReviewConfig):
    self.config = config
    self.client = openai.OpenAI(api_key=config.api_key, base_url=config.base_url)
```

`generate_section()` then uses that internally created client:

```python
response = self.client.chat.completions.create(...)
```

### Result

The current code matches the limitation described in the issue. There is currently no full RAG integration test under `tests/integration/`, and `ReviewGenerator` creates its OpenAI client internally instead of accepting a client that a test could control.

Because of that, there is no direct injection point for an integration test to provide a fixed mock LLM client or response through the current `ReviewGenerator` constructor. This is the state I observed before making any implementation changes.