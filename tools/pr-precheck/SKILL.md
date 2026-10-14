---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

<!--
THIS IS THE PART YOU WRITE, and it is the last one: the frame itself.
Weeks 1 through 3 handed you a working SKILL.md and you filled the
files behind it; this week the frame ships as headings, and you write
what it says. The frontmatter above and the section headings below are
fixed (CONTRACT.md's layout rule); the instructions under each heading
are yours. Write instructions to the tool, in the imperative, the way
weeks 1-3's frames spoke to you: what to read, in what order, what to
refuse, what to emit. Your executor in the rotation is the test: a
frame gap they hit (cannot tell what the tool reads, or how a verdict
gets assembled) is a missing sentence here.

One section is not yours: the JSON schema in "Verdict and output" is
reproduced from CONTRACT.md verbatim and may not be altered. Your
words decide everything around it.
-->

## The question

Decide whether one pull request package is ready to submit.

Treat the PR package as the implementation diff, the plan it claims to follow, its test evidence, its PR title and description, and the issue that motivated the work.

Grade whether the submitted change matches the plan and issue, is supported by test evidence, is reviewable, follows repository requirements, and is described accurately.

Do not redesign the implementation, grade unrelated work, or substitute a different solution for the one being submitted.

## Inputs and modes

Run in exactly one of two modes: live mode or eval mode.

### Live mode

Read the student's actual PR package.

Read:

1) plan.md, including its ## Deviations section.
2) The committed branch diff relative to main by running:
3) git diff main...HEAD
4) The draft PR title and description from the file named by the command, normally pr_draft.md.
5) The test evidence from the file named by the command, normally test_evidence.md.
6) The issue URL named in the command, including the issue body and relevant thread comments.
7) The repository's .github/PULL_REQUEST_TEMPLATE.md.
8) docs/CONTRIBUTING.md and any repository policy it directly references.

Treat git diff main...HEAD as the authoritative implementation diff. Do not treat uncommitted working-tree changes as part of the PR.

Use the issue to determine the requested outcome and use the plan to determine the intended implementation scope.

If the student is using a house chain, read the supplied house issue, reproduction package, plan, branch, test evidence, and PR draft instead of the student's earlier Unit 2 and Unit 3 artifacts.

### Eval mode

Treat the supplied practice package as the entire available world.

Read only the issue or thread context, plan, diff, PR title and description, test evidence, commits, and repo-facts or policies contained in that package.

Do not fetch GitHub, inspect a local repository, or use outside facts.

Run every rubric check and apply the full verdict rule.

## The scope seam (live mode only)

Read `scope.md` before grading any live package.

Confirm that the issue belongs to the repository named on the Repo: line and apply any house rules stated in `scope.md`.

If the Repo: line still contains a placeholder, stop without grading and tell the student to fill in the repository.

If the issue or PR belongs to a repository outside the stated scope, refuse to grade it.

Do not guess or broaden the scope.

Eval mode ignores `scope.md`.

## The voice seam (live mode only)

Read `voice-guide.md` before grading the student's outgoing PR text.

Apply the voice rules to the PR title and PR description.

If the title or description breaks a voice-guide rule, report the specific rule and the text that breaks it in the readable feedback.

A voice-guide violation does not change the final verdict by itself unless the same problem also fails a check in `rubric.md`.

Eval mode ignores `voice-guide.md`.

## Component reads

Read `rubric.md` to determine the checks, evidence each check uses, pass conditions, check weights, and final verdict rule.

Read `references/evidence-guide.md` to determine where each type of evidence lives and what good evidence looks like.

Execute `procedure.md` exactly as written to determine the order in which evidence is read, gathered, compared, and graded.

Do not silently invent a missing procedure step. If `procedure.md` does not explain how to gather or compare evidence needed by a rubric check, report that as a procedure gap.

If `rubric.md` has no substantive checks, stop without grading and explain that the rubric is incomplete.

If `procedure.md` has no substantive grading procedure, stop without grading and explain that the procedure is incomplete.

## Verdict and output

Use exactly two final verdicts:

- accept: the PR package is ready to submit under the rubric.
- reject: the PR package should be held because one or more required checks fail or remain unresolved under the rubric.

Give a readable summary of every rubric check before the machine-readable result.

End the reply with the following fenced JSON block.

The JSON must be valid, must be the final content in the response, and nothing may appear after it.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

Grade from evidence first.

For every check, identify the concrete fact, changed file, diff hunk, command result, test output, quote, or policy that determined the grade.

Grade the actual PR package rather than how polished its writing is. A short PR may pass if the implementation and evidence are complete. A polished description must not hide missing work, unsupported claims, silent drift, or unrelated changes.

Apply `rubric.md` exactly as written. Do not change a check's meaning during a grading run because a package feels like it should pass or fail.

Follow `procedure.md` exactly when deciding what to read and how to compare evidence.

When required evidence is missing, conflicting, or insufficient to decide a check, grade that check unclear.

If the rubric's verdict rule does not explicitly say otherwise, treat an unclear required check the same as a failed required check.

Do not automatically reject a PR only because a test, check, or planned item failed. If the shortfall is honestly disclosed, use the rubric's stated pass condition to decide whether it invalidates the PR's claims or readiness.

Do not excuse silent differences between the plan, diff, evidence, and PR description. A material deviation must be documented where the rubric expects it.
