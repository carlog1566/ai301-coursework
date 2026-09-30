# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->
Where it lives:
In eval mode, look at the issue context, repo-facts block, and the environment section of the repro report. In live mode, compare the draft repro report with the issue thread and the repository's setup or contribution documentation.

What good looks like:
The report names the environment details that could affect reproduction, such as operating system, runtime or language version, dependency state, application version or commit, and relevant configuration. Those details should match what the issue targets, or the report should clearly call out any difference that could affect the result.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->
Where it lives:
Look at the repro report's ordered commands and actions, along with any setup state, inputs, fixtures, URLs, files, or configuration it says were used.

What good looks like:
A stranger using the stated environment can repeat the attempt from the recorded starting state through the action that triggers the behavior. Material commands, inputs, configuration values, or transitions are written explicitly rather than hidden behind phrases such as "set everything up" or "run it normally."

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->
Where it lives:
Look at artifacts included or quoted in the repro report, such as terminal output, test results, stack traces, logs, screenshots, HTTP responses, or other captured results. Read them against the behavior described in the issue context.

What good looks like:
The evidence shows the same behavior, failure, or condition the issue describes, not merely a related error or a result from a different configuration. A cannot-reproduce attempt is also valid evidence when the artifact clearly shows the expected trigger was exercised without producing the reported behavior.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->
Where it lives:
Compare the repro report's conclusion and wording with the environment, steps, and artifacts it provides.

What good looks like:
The report states exactly what the evidence supports. If reproduction succeeds, the artifact demonstrates the target behavior. If it does not reproduce, the report says so and records what happened instead. Uncertainty or environmental differences are named rather than hidden, and the report does not turn an inference into an observed fact.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->
Where it lives:
In eval mode, compare the claim comment and repro report with the issue context and repo-facts block, including contribution or AI-use policies. In live mode, also check the current issue thread, repository contribution documentation, and the student's draft comments.

What good looks like:
The claim is specific to the issue, says what the contributor plans to investigate next, and does not promise a fix or deadline before reproduction. The repro comment communicates the actual result and supporting evidence in the contributor's own words. Any repository-required template, attribution, or AI-use disclosure that applies to the comments is followed.