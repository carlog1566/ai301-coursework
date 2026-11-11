# Contribution: Freightliner Trucks (AU) Spider

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Carlo Gabarda
**GitHub Username:** carlog1566
**Issue:** https://github.com/alltheplaces/alltheplaces/issues/8514
**Pull Request:** Not opened yet

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Built and tested an issue-scout for open-source issue selection**

I updated my issue-scout to search for beginner-friendly Python issues using my fit profile, search strategy, and rubric. During my first scan, the scout evaluated five issues, accepting four and rejecting one because the task was too broad. Although the scout correctly evaluated the issues, some of the accepted results were not closely related to my preferred Python and backend development work. I kept my rubric unchanged and used the CodePath Issue Selection site to find three more relevant issues, which the scout accepted.

**Unit 6: Installing My Voice Guard and Setting Up Repository Memory**

I updated my voice guide with rules for claims, questions, and follow-up messages, then installed the voice guard in Claude Code. During testing, the guard successfully blocked a GitHub command without a comment body, and it passed my Freightliner claim message before I posted it. I also updated my issue-scout rubric and used Claude Code to inspect the relevant All the Places spiders so I could document the project's conventions in CLAUDE.local.md. The voice guard worked as expected, and the repository inspection helped me understand where to start without modifying any code yet.

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I used my issue-scout to search for beginner-friendly open-source issues that matched my experience with Python, APIs, and backend development. My initial scan evaluated five issues, accepting four and rejecting one because its scope was too broad. I then used the CodePath Issue Selection site to find three additional issues in the All the Places repository. My scout accepted all three, and I decided to work on Freightliner Trucks #8514 because it involved creating a Python scraper using a JSON API. This fits my experience working with APIs and data processing while giving me an opportunity to learn more about web scraping with Scrapy.

Another reason I chose this issue was that it had a clear goal and a relatively small scope. The repository was active, the issue was labeled `good first issue`, and no one had claimed it when I checked. One limitation of my initial scout was that some accepted issues were unrelated to my preferred development work. I also updated my scope check to `scope-feasible` so issues with reasonable uncertainty would not automatically be rejected. After updating the rubric, Freightliner still received an `accept` verdict.

**Claim comment:** https://github.com/alltheplaces/alltheplaces/issues/8514#issuecomment-6792094412

**Toolkit**

- **Tool:** issue-scout. I used my search strategy and rubric to evaluate GitHub issues, then directly graded three issues from the CodePath Issue Selection site.
- **What it produced:** The initial scan evaluated five issues, accepting four and rejecting one. The scout also accepted Freightliner #8514, including after I updated its scope check.
- **Difficulties:** Some accepted issues did not closely match my preferred Python and backend development work.
- **What changed:** I prioritized issues that matched my fit profile and replaced the original scope check with `scope-feasible`, adding difficulty ratings to help compare accepted issues.

---

## Understanding the Issue

**Problem Description**

[In your own words, what is broken or missing?]

**Expected Behavior**

[What should happen?]

**Current Behavior**

[What actually happens?]

**Affected Components**

[Which parts of the codebase are involved?]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Reproduction Process

**Environment Setup**

[What a stranger would need to stand this up: your operating system,
the relevant versions (language, runtime, package manager, the project
itself), and how you set the project up. Then the challenges you faced
and how you solved them, or that none came up.]

**Steps to Reproduce**

1. [Step 1]
2. [Step 2]
3. [Observed result]

**Reproduction Evidence**

- **Commit showing reproduction:** [link to commit in your fork]
- **Screenshots/logs:** [if applicable]
- **My findings:** [what you discovered during reproduction; an
  honest, evidenced cannot-reproduce that led you to re-pick or ask
  the maintainer belongs here and costs you nothing]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Solution Approach

**Analysis**

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
