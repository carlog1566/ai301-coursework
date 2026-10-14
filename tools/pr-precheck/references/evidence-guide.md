# Evidence guide: where evidence lives in a PR package

<!--
THIS IS THE PART YOU WRITE (third week running: the map stays in your
hands). Your tool uses this guide as its map: for every kind of
evidence a rubric check names, this file says WHERE to find it in a PR
package and WHAT GOOD LOOKS LIKE when you do.

The four families below are the harness's failure categories under
the names the eval README uses: plan fidelity = silent-drift, test
evidence = not-tested, diff quality = unreviewable, standards and
comms = standards-wall. A package that fails none of them is a
clear-accept. Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the plan-context block's scope pair and test
  plan, the candidate PR's diff, commits, description, or
  test-evidence section, the repo-facts block's template asks and
  stated policy). In live mode (where in your working copy and on
  GitHub: your plan.md and its deviation notes, your branch's diff,
  your draft title and description, your captured test output, the
  repo's PR template and CONTRIBUTING.md).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("every changed file falls inside the
  plan's stated boundary or a deviation note") over adjectives ("the
  diff is clean").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts three ways: your
procedure says WHEN to gather each family, this guide says WHERE, and
your SKILL.md says the tool reads both. Write the map you wish your
executor had.
-->

## Plan fidelity (harness category: silent-drift)

### Where it lives:

In eval mode, look at the package's plan-context block, especially the stated scope, planned files or behavior, test plan, and any deviation notes. Compare those against the candidate PR's unified diff, commit list, and description.

In live mode, read plan.md, including its ## Deviations section, and compare it with the committed branch diff from:

```bash
git diff main...HEAD
```

Also compare the PR title and description in pr_draft.md with the actual diff.

### What good looks like:

Every material change in the diff should be covered by the original plan or by an explicit deviation that explains what changed and why. Planned work that was not completed should also be disclosed rather than silently omitted.

The PR description should describe what the diff actually delivers. Silent drift includes both adding work outside the plan without recording it and leaving out planned work while still presenting the PR as complete.

## Test evidence (harness category: not-tested)

### Where it lives:

In eval mode, look at the package's test-evidence section and compare its before and after results with the plan-context block's test plan and reproduction steps. Also check any repository-required test commands and their supplied results.

In live mode, look at test_evidence.md, the test plan in plan.md, the Unit 2 reproduction evidence when it is reused as the before state, and the repository's required checks from the PR template or docs/CONTRIBUTING.md.

### What good looks like:

The evidence includes the actual commands and observable output for the original behavior and the behavior after the change. The after result should demonstrate the outcome the plan said would change rather than simply saying that tests passed.

Repository-required checks should have their real outcomes shown. A failed or blocked command can still be useful evidence when it is reported honestly with its reason instead of being hidden.

## Diff quality (harness category: unreviewable)

### Where it lives:

In eval mode, inspect the candidate PR's unified diff, changed-files information, and commit list.

In live mode, inspect:

```bash
git diff main...HEAD 
```

and, when useful:

```bash
git diff main...HEAD --stat
```

### What good looks like:

The diff contains only changes needed for the issue or changes that are explicitly justified by the plan's deviations. A reviewer should be able to identify the actual fix without separating it from unrelated work.

Warning signs include debug statements, dead or commented-out code, generated files, accidental dependency or configuration changes, large formatting-only changes, temporary files, and unrelated refactors or cleanup.

## Standards and comms (harness category: standards-wall)

### Where it lives:

In eval mode, look at the repo-facts block for the repository's PR template requirements, contributing instructions, stated policies, AI-use disclosure requirements, and relevant maintainer directions. Compare those requirements with the candidate PR title and description.

In live mode, read .github/PULL_REQUEST_TEMPLATE.md, docs/CONTRIBUTING.md, relevant issue-thread comments, and any policy files those sources reference. Compare them with the title and description in pr_draft.md.

If a claim depends on how a repository command or CI check actually runs, inspect the relevant Makefile, pyproject.toml, or .github/workflows/ file rather than assuming how it works.

### What good looks like:

Every applicable PR-template section is filled with real information rather than being left as boilerplate. The PR references the correct issue, reports testing accurately, follows explicit maintainer directions, and includes any required disclosure.

For this course, the PR should include an AI-use disclosure in Notes for Reviewers. Testing boxes or other completion claims should only be checked when the available evidence supports them.

Whether the PR description accurately represents the diff belongs under Plan fidelity above; this section focuses on whether the PR follows the repository's stated communication and submission requirements.
