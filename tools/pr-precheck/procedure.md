# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

1. In live mode, read scope.md first and confirm that the issue belongs to the configured Path Review repository.
2. In live mode, read voice-guide.md so the PR title and description can be checked against the student's communication rules.
3. Read the issue before evaluating the PR. Record the requested outcome, relevant maintainer guidance, and any explicit requirements or constraints.
4. Read plan.md, including its ## Deviations section. Record the diagnosis, intended scope, planned files and behavior, planned testing, and every disclosed deviation.
5. Read the complete committed diff. In live mode, use git diff main...HEAD. In eval mode, use only the diff supplied in the package.
6. Read the test evidence next. Record the before behavior, after behavior, repository checks that were run, and their actual results.
7. Read the PR title and description after understanding the implementation and evidence. This prevents the PR description from defining what the implementation is assumed to do.
8. Read the repository PR template, docs/CONTRIBUTING.md, relevant policy files, and applicable issue-thread directions before grading repository-standard checks.
9. Do not grade a check until all evidence named by that check has been read.

## Evidence gathering

1. For plan fidelity, list every material file and behavior changed by the diff. Pair each one with the plan section or ## Deviations entry that authorizes it.
2. Also record any planned material outcome that does not appear in the diff. Note whether the omission is disclosed.
3. For PR-description accuracy, extract each concrete implementation, testing, or completion claim from the title and description and compare it with the diff and test evidence.
4. For test evidence, identify the Unit 2 reproduction behavior or other before condition, the after condition, and every repository check required by the PR template or contribution guide. Record the actual command and result rather than a summary such as "tests passed."
5. For reviewability, inspect the diff for unrelated files, generated artifacts, debug statements, commented-out code, formatting churn, temporary helpers, accidental configuration changes, or unrelated refactors.
6. For repository standards, record every applicable requirement from the PR template, docs/CONTRIBUTING.md, issue thread, and any policy referenced by those files. Include required issue linking, testing checkboxes, AI-use disclosure, branch or title rules when applicable, and required template sections.
7. In live mode, if a claim depends on how CI or repository checks run, inspect the relevant Makefile, pyproject.toml, or .github/workflows/ configuration instead of inferring it from one source.
8. If required evidence is missing or conflicts, record the conflict rather than filling the gap from general knowledge.

## Check execution

1. Grade Implementation matches the plan by comparing every material diff change with the plan and ## Deviations. Fail silent additions, silent omissions, or contradictions. Do not fail a disclosed deviation solely because it differs from the original plan.
2. Grade Description matches the delivered change by comparing each important PR claim against the committed diff and test evidence. Fail claims that overstate, omit, or misrepresent the delivered change.
3. Grade Test evidence supports the claims by comparing the plan's verification strategy, before/after evidence, repository-required checks, and the PR's testing claims. A failing or blocked check may still pass this rubric check when it is shown honestly, its reason is stated, and it does not invalidate the claimed outcome.
4. Grade Diff is focused and reviewable by looking only for material reviewability problems. Do not fail harmless formatting produced by the repository's own formatter when it is limited to changed code, but fail unrelated churn or development debris.
5. Grade Repository standards are satisfied by comparing the PR draft against every applicable requirement gathered from the template, contribution guide, issue thread, and policy files.
6. For each check, record one concrete fact, output, changed file, or quote that determined the grade.
7. If a required check cannot be decided because evidence is absent or conflicting, grade it unclear. Do not silently assume the missing fact.
8. Do not let one check substitute for another. A technically correct implementation can still fail repository standards, and a polished description cannot compensate for an untested or drifting diff.

## Verdict assembly

1. Collect the grade for every required check.
2. Treat an unclear required check as a failure.
3. Return accept only when every required check passes.
4. Return reject when any required check fails or is unclear.
5. Do not reject automatically because a repository command failed if the rubric check allows an honestly disclosed limitation and the failure does not invalidate the PR's claimed outcome.
6. In the readable summary, identify each check, its grade, and the concrete evidence that decided it.
7. In live mode, separately report voice-guide violations when present, even if they do not independently change the verdict.
8. End with the exact JSON shape required by SKILL.md.
9. Emit nothing after the final JSON block.
