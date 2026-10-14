# Rubric: is this pull request ready to submit?

<!--
THIS IS THE PART YOU WRITE (fourth week running; this is the rubric's
final form in the sandbox). Your frame in SKILL.md executes whatever
checks you define here, via your procedure.md. It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the diff read against the plan's scope, the test
     evidence read against the plan's test plan, the description read
     against the diff, the repo-facts block's template asks) or a
     location from your references/evidence-guide.md. "The PR" is not
     a source; "the diff's changed files read against the plan's
     stated boundary" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself
     (does the diff fall inside the plan plus its deviation notes? is
     the claimed evidence observable?), never the write-up's shape
     (how long the description is, how many commits there are).
     Structure-shaped checks are what make graders disagree with
     themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (submit) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. State the `unclear`
   treatment explicitly: the frame here is YOUR SKILL.md, so a rubric
   that stays silent is only covered if your frame's grading
   discipline says what happens (the contract's own default is that
   an unverifiable claim fails).

Cover what actually gets bad PRs submitted. The failure families the
lecture named ARE the harness's scoring categories, same names as the
eval README: silent drift (the diff silently does more or less than
the posted plan, or the description claims fidelity the diff
contradicts), not tested (the evidence proves nothing observable, or
the repo's own checks were never run), unreviewable (debris or
unrelated hunks bury the change), and standards wall (the repo's
stated template and disclosure asks are ignored). Your evidence
guide's four headings map onto these one to one (plan fidelity =
silent drift, test evidence = not tested, diff quality =
unreviewable, standards and comms = standards wall), and the category
floor is scored on exactly these names plus clear accept. A rubric
that ignores a category will fail the eval packages built around
that category. And remember the honest-outcome
rule, fourth week running: a PR that honestly discloses a shortfall
can be ready; a rubric that equates "less than everything" with
"hold" fails the set.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Implementation matches the plan | The committed branch diff read against the issue's requested outcome, the plan's stated scope and approach, and the plan's ## Deviations section. | Pass if every material change in the diff is covered by the plan or an explicitly recorded deviation, and the implementation delivers the planned issue outcome. A disclosed deviation may pass when the plan explains what changed and why. Fail if the diff silently adds unrelated work, omits a material planned outcome without disclosure, or contradicts the plan or issue. | required |
| Description matches the delivered change | The PR title and description read against the committed diff and the plan/deviation notes. | Pass if the title and description accurately describe what the committed diff actually does, including any disclosed shortfall or deviation that matters to reviewers. Fail if the description claims work the diff does not contain, hides material behavior present in the diff, or presents an incomplete implementation as complete. | required |
| Test evidence supports the claims | test_evidence.md or the eval package's test-evidence section read against the plan's test plan, Unit 2 reproduction behavior, and the repository's required checks. | Pass if the planned before/after behavior is demonstrated with observable commands and output, the repository's required checks were run, and their actual outcomes are reported. A failing or blocked check may still pass this rubric check when it is honestly shown, its cause is identified, and it does not invalidate the PR's claimed outcome. Fail if testing is missing, only asserted without observable output, skips a required verification without explanation, or the evidence does not establish the claimed change. | required |
| Diff is focused and reviewable | The committed diff and commit contents, including changed files and hunks. | Pass if the issue-related implementation is visible without unrelated edits or development debris. Fail if debug output, dead or commented-out code, accidental generated files, formatting churn, unrelated refactors, or drive-by changes materially obscure or expand the requested change. | required |
| Repository standards are satisfied | The PR title and description read against the repository's PR template, docs/CONTRIBUTING.md, stated policy, and relevant maintainer directions in the issue thread. | Pass if every applicable template section has meaningful content, the correct issue is linked as required, testing results are represented accurately, required AI-use disclosure is present, and applicable maintainer or contribution instructions are followed. Fail if an applicable stated requirement is omitted, falsely checked, left as boilerplate, or ignored. | required |

## Verdict rule

Accept only when every required check passes.

Reject when any required check fails or is unclear because the evidence needed to verify it is missing or conflicting.

Preferred checks, if any are added later, may inform the readable feedback but never change the final verdict.

An honestly disclosed limitation, deviation, or failing repository check does not automatically cause rejection; grade it according to the relevant check's pass condition and whether it makes the PR's claims untrue or the requested change unreviewable.
