# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

1. In live mode, read scope.md first and confirm that the issue belongs to the scoped Path Review repository. Read voice-guide.md for the student's communication rules.
2. Read the issue context before reading the candidate plan. Record the requested outcome, relevant files, maintainer guidance, and any explicit constraints.
3. Read the Unit 2 reproduction evidence next. Record the environment, exact reproduced condition, commands or artifacts that demonstrated it, and the conclusion the evidence supports.
4. Read the candidate plan.md. Record its diagnosis, in-scope and out-of-scope statements, files to change, implementation approach, test plan, risks or unknowns, and Deviations section if it has been filled.
5. Read the draft plan comment last. Compare what it tells maintainers with the full plan, issue thread, and repository conventions.
6. Do not grade a check until the issue, reproduction evidence, and relevant part of the plan have been read. This order prevents the plan's explanation from replacing the evidence it is supposed to follow.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

1. For diagnosis evidence, pair each cause or limitation stated in the plan with the specific reproduction artifact or quoted observation that supports it.
2. For scope evidence, record the issue's requested outcome, the plan's in-scope and out-of-scope statements, and every file or subsystem the plan proposes changing.
3. For approach evidence, record what code or interface the plan intends to change and compare it with the location implicated by the reproduction evidence.
4. For executability, record the named files, interfaces, sequence of changes, and any implementation choice that would have to be decided before a contributor could begin.
5. For testing, record the Unit 2 reproduction trigger and observed result, then record the plan's post-change command or action and its expected observable result.
6. For honesty, record each risk, unknown, assumption, and deviation. Note any statement presented as certain that the available evidence does not establish.
7. For communications, compare the draft comment with the live issue thread or eval thread highlights and the repo-facts or contribution documentation. Record any requirement that applies to the comment.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Grade Diagnosis follows the evidence first using only the diagnosis and the reproduction/issue evidence gathered for it.
2. Grade Scope is bounded by comparing the proposed work with the issue's requested outcome. Do not fail merely because more than one related file must change.
3. Grade Approach addresses the cause by checking that the proposed edits act on the part of the system identified by the supported diagnosis.
4. Grade Plan is executable by asking whether another contributor can take the first implementation steps without needing a material missing decision from the author.
5. Grade Test plan proves the outcome by comparing the planned verification directly with the Unit 2 reproduction. The test must produce an observable result that distinguishes success from the original state.
6. Grade Unknowns are stated honestly by comparing certainty in the plan with what the evidence actually establishes.
7. Grade Comment follows thread and repo conventions last because it depends on the finished understanding of the plan and issue.
8. If evidence required by a pass condition is genuinely absent or conflicting, grade that check unclear. Do not infer missing evidence or fill it in from general knowledge.
9. Record one concrete fact or quote that determined every check grade.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

1. Collect the grade for every required check.
2. Treat unclear the same as a failed required check.
3. Return accept only when every required check is pass.
4. Return reject when at least one required check is fail or unclear.
5. In the readable summary, identify every failing or unclear check and the evidence that caused it.
6. In the final fenced JSON block, include every check, its grade, one concise evidence statement, and the final binary verdict.
7. Emit nothing after the final JSON block.