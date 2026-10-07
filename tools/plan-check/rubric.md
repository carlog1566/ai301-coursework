# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis follows the evidence | The plan's diagnosis read against the issue context and the quoted Unit 2 reproduction evidence. | Pass if the stated cause or limitation explains the behavior actually demonstrated by the reproduction evidence and does not contradict it. Fail if the diagnosis assumes a different problem, claims a root cause that the evidence does not support, or ignores evidence that materially changes the diagnosis. | required |
| Scope is bounded | The plan's in-scope and out-of-scope statements, named files or areas, and proposed changes read against the issue's requested outcome. | Pass if the plan limits itself to one change needed to address the issue and names what will not be changed. Fail if it adds unrelated cleanup, redesigns adjacent systems without need, or expands beyond what is necessary to satisfy the issue. | required |
| Approach addresses the cause | The planned changes and files read against the plan's diagnosis and the reproduction evidence. | Pass if the proposed implementation changes the part of the system responsible for the demonstrated limitation rather than only working around a visible symptom. Fail if the plan leaves the identified cause unchanged or proposes work unrelated to the reproduced condition. | required |
| Plan is executable | The plan's named files, implementation approach, order of work, and relevant repository context. | Pass if another contributor could begin implementing the plan without needing the author to explain a missing material decision, file, interface, or sequence. Unknown implementation details may remain if they are clearly identified and do not block the first implementation step. | required |
| Test plan proves the outcome | The plan's test steps and expected results read against the Unit 2 reproduction steps and evidence. | Pass if the test plan re-checks the reproduced condition through the real changed code and states an observable before/after result that would demonstrate whether the issue was addressed. Fail if it only says to run tests, relies only on unrelated existing tests, or has no observable success condition. | required |
| Unknowns are stated honestly | The plan's risks, unknowns, assumptions, and any Deviations section. | Pass if unresolved questions or assumptions that could affect implementation are identified as unknown rather than stated as confirmed facts. Pass if there are no meaningful unknowns and the supplied evidence supports that confidence. Fail if an unsupported assumption is presented as settled or a known risk is hidden. | required |
| Comment follows thread and repo conventions | The draft plan comment read against the issue thread, repo-facts block or live contribution docs, and applicable repository policies. | Pass if the comment is specific to this issue, accurately summarizes the planned approach and test strategy, does not contradict relevant maintainer guidance, and follows any applicable contribution or AI-disclosure requirements. If no special requirement exists, pass. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept only if every required check passes. Reject if any required check fails or is unclear. Preferred checks, if any are added later, never change the verdict.