# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

- Where it lives: In eval mode, compare the candidate plan's diagnosis with the issue context and repro-evidence block. In live mode, compare plan.md with the GitHub issue and the student's posted Unit 2 reproduction comment.

- What good looks like: The diagnosis explains the condition that the reproduction evidence actually demonstrates. Claims about the cause point to specific observed behavior or code evidence, and the plan does not turn an unsupported possibility into a confirmed root cause.

## Scope

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. --> 

- Where it lives: Look at the plan's in-scope and out-of-scope statements, named files or components, and the issue's requested outcome. In live mode, also check relevant maintainer guidance in the issue thread.

- What good looks like: The proposed changes are limited to what is needed for the issue's outcome. Multiple related files may be changed, but unrelated cleanup, broad redesigns, and drive-by refactors stay out of scope unless they are required by the demonstrated cause.

## Executability

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

- Where it lives: Look at the candidate plan's files-to-touch section, implementation approach, ordering of work, and named interfaces or functions. In live mode, compare those names with the current repository where needed.

- What good looks like: Another contributor can identify where to start and what change to make without asking the author to decide a missing material part of the design. Remaining unknowns are acceptable when they are named and do not prevent the first implementation steps.

## Test plan

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

- Where it lives: Compare the plan's test plan with the Unit 2 reproduction commands, inputs, artifacts, and result. In live mode, the posted reproduction comment is the source of the before state.

- What good looks like: The test plan exercises the real changed path and states what will be different after the change. It includes an observable success condition rather than only saying that tests will be run.

## Honesty

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

- Where it lives: Look at the diagnosis, risks, unknowns, assumptions, and ## Deviations section of the plan. Compare claims of certainty with the issue and reproduction evidence.

- What good looks like: Supported facts are stated as facts, while unresolved implementation questions or assumptions are identified as such. If implementation later differs from the posted plan, the deviation states what changed and why rather than hiding the difference.

## Comms

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->

- Where it lives: In eval mode, compare the draft plan comment with the issue/thread highlights and repo-facts block. In live mode, compare comment.md with the current GitHub issue thread, repository contribution documentation, and applicable policy files.

- What good looks like: The comment describes this contributor's own diagnosis, bounded approach, and verification plan rather than generic boilerplate or another person's plan. It respects relevant maintainer guidance and any stated contribution, formatting, or AI-disclosure requirements.
