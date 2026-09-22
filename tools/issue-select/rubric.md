# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer activity | The last 5 default-branch commits and maintainer first-response sample in the repo-facts block, plus Owner/Member/Collaborator comments in the issue thread. | Pass if there is evidence of recent human maintainer activity: at least one non-bot default-branch commit within 90 days of the capture date, a maintainer first response within 30 days in the response sample, or an Owner/Member/Collaborator comment on this issue within 90 days. Bot-authored commits by themselves do not count as maintainer activity. | required |
| Repository activity | The archived, last push to any branch, and latest release fields in the repo-facts block. | Pass if the repository is not archived and either its last push was within 180 days of the capture date or its latest release was within 365 days. A repository does not need a recent release if it still has recent development activity. | required |
| Bounded newcomer scope | The issue title, body, labels, linked PR state, and comment thread. | Pass if the issue defines one specific bug, feature, documentation goal, or desired outcome with enough concrete direction to begin implementation. The task may involve multiple related files, several steps, multiple diagnosed causes, or several suggested implementation approaches as long as they all serve one bounded outcome. Fail if the issue is explicitly an umbrella/mega/tracking issue, is only a usage/support question, provides no concrete expected behavior or specification, or shows a long-running unresolved design discussion with repeated abandoned implementation attempts and no settled direction. Do not fail an issue solely because it spans multiple files or lists multiple possible solutions. | required |
| Issue availability | The issue's assignees, linked PRs, and claim statements in the comment thread. | Pass if the issue has no current assignee, no open linked or mentioned PR implementing the issue, and no recent unresolved claim from another contributor saying they are actively working on it. A closed unmerged PR or a comment clearly showing that the contributor stopped working on it does not count as an active claim. | required |
| Contribution policy | The contribution policy field in the repo-facts block, including CONTRIBUTING.md, dedicated AI policy files, and any relevant contributor requirements summarized there. | Pass unless the repository explicitly prohibits AI-generated or AI-assisted contributions. Disclosure, testing, personal-understanding, or human-review requirements pass because they are conditions that can be followed. If no AI policy is stated, pass. | required |
| First-issue signal | The issue labels, issue body, and maintainer comments in the thread. | Pass if the issue has a good first issue or equivalent beginner label, or a maintainer explicitly describes the task as appropriate for a new contributor. Otherwise grade this check fail or unclear; because it is preferred, it does not reject the issue. | preferred |

## Verdict rule

Accept an issue only if every required check passes. Reject the issue if any required check fails. Treat unclear on a required check as a failure because the evidence is not strong enough to verify that the issue is a safe first contribution. Preferred checks never change an accept or reject verdict; they are used only to rank issues that already passed every required check.
