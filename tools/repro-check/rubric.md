# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Claim grounded in the issue | The claim comment read against the issue title, body, and relevant maintainer comments. | Pass if the claim clearly refers to the specific issue or behavior being investigated and states a concrete next step to investigate or reproduce it and report back. Fail if the claim is generic enough to apply to any issue, promises a fix or completion date before investigation, or claims reproduction work that has not yet been shown. | required |
| Environment matches target | The repro report's environment record read against the issue context and any relevant setup requirements in the repo-facts or repository documentation. | Pass if the report records the environment details needed to repeat the attempt and they match the environment targeted by the issue, or any meaningful differences are explicitly identified. Fail if a missing or conflicting environment detail could reasonably change the observed behavior. | required |
| Steps are rerunnable | The repro report's reproduction steps, including commands, inputs, setup state, and trigger action. | Pass if a stranger starting from the stated environment could follow the recorded actions in order and reach the attempted trigger without having to guess a material command, input, configuration, or starting state. Fail if a required action is omitted or replaced with an unexplained summary such as "set up the project" or "run the test." | required |
| Evidence matches the issue | The report's artifacts, such as command output, logs, test results, screenshots, or other captured behavior, read against the behavior or condition described by the issue. | Pass if the artifacts directly demonstrate the issue's described behavior or directly demonstrate that the described behavior did not occur during a valid reproduction attempt. Fail if the evidence only shows a nearby, unrelated, or differently configured behavior. | required |
| Outcome matches the evidence | The repro report's stated result read against its steps and artifacts. | Pass if the conclusion says only what the supplied evidence supports. A clearly evidenced cannot-reproduce result passes when the report records the attempted conditions and observed result. Fail if the report claims the issue was reproduced when the evidence shows a different behavior, or claims success/failure beyond what the artifacts establish. | required |
| Repository conventions followed | The claim and repro comments read against the repo-facts block, contribution documentation, issue templates, and any stated AI-use or disclosure policy. | Pass if the comments satisfy the repository's applicable contribution and communication requirements, including any required disclosure of AI assistance. If no relevant convention is stated, pass. Fail if a stated requirement that applies to these comments is violated or omitted. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->
Accept when every applicable required check passes. Reject when any applicable required check fails or is unclear because the evidence needed to verify it is missing. In claim-only live mode, checks that require a repro report are not yet applicable and do not affect the claim verdict.
