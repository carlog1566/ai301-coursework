# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/13

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
{
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/13",
    "checks": [
      {"name": "Maintainer activity", "grade": "pass", "evidence": "Newest main commit 2f4e82f by human Aburke225 on 2026-09-16, 5 days before capture (within 90 days)."},
      {"name": "Repository activity", "grade": "pass", "evidence": "isArchived: false, pushedAt 2026-09-16 (within 180 days)."},
      {"name": "Bounded newcomer scope", "grade": "pass", "evidence": "One outcome - add a single @pytest.mark.integration test - with the blocker diagnosed: \"ReviewGenerator builds its own OpenAI client, so the test needs a way to pass in a fixed response.\""},
      {"name": "Issue availability", "grade": "pass", "evidence": "assignees: []; no comments; only timeline cross-reference is a closed ISSUE (fixture issue), not a PR; repo has zero PRs."},
      {"name": "Contribution policy", "grade": "pass", "evidence": "No AI-contribution ban in docs/CONTRIBUTING.md and no dedicated AI policy file."},
      {"name": "First-issue signal", "grade": "fail", "evidence": "Labels are enhancement, devops, rag, tests, tier-2 - no beginner label and no maintainer comment calling it newcomer-friendly."}
    ],
    "verdict": "accept"
}
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

First full run:

- `agreement: 17/20 scored items (bar: 18/20: below the bar)`

After revising my Bounded newcomer scope check, my second full run was:

- `agreement: 20/20 scored items (bar: 18/20: PASS)`

Final full run used for eval-run.txt:

- `agreement: 19/20 scored items (bar: 18/20: PASS)`

The last run only missed issue-20, and I still passed the required 18/20 bar and got at least one correct result in every category.

**Issue analysis**

I chose issue-15 for this part.

From my first run:

- `issue-15 reject accept NO graded accept`

My rubric accepted the issue, while the gold label rejected it.

The main problem was with my Bounded newcomer scope check. My original version mostly looked at whether the issue had one clear goal, so issue-15 still looked manageable at first. What I was missing was the fact that it had a long history of unresolved discussion and previous attempts that did not lead to a clear solution.

I changed the check so that issues with a long-running unresolved design discussion and repeated abandoned attempts can fail the scope check. After that change, my rubric rejected issue-15.

From the final run:

- `issue-15 reject reject yes`

**Check rationale**

The check I revised was:

- Bounded newcomer scope | The issue title, body, labels, linked PR state, and comment thread. | Pass if the issue defines one specific bug, feature, documentation goal, or desired outcome with enough concrete direction to begin implementation. The task may involve multiple related files, several steps, multiple diagnosed causes, or several suggested implementation approaches as long as they all serve one bounded outcome. Fail if the issue is explicitly an umbrella/mega/tracking issue, is only a usage/support question, provides no concrete expected behavior or specification, or shows a long-running unresolved design discussion with repeated abandoned implementation attempts and no settled direction. Do not fail an issue solely because it spans multiple files or lists multiple possible solutions. | required

I changed this check because my first version was a little too strict in some places and too loose in others. I did not want an issue to automatically fail just because it touched multiple files or had several steps if everything was still working toward one clear goal.

At the same time, I wanted the rubric to catch issues that look small at first but actually have a lot of unresolved design work behind them. Adding the part about repeated abandoned attempts helped separate those cases better.

**Trade-offs**

The downside of this check is that it can still accept something that is technically difficult as long as the task looks clearly defined.

I was okay with that because my first version was rejecting valid issues like issue-01 and issue-19 just because they involved multiple files, steps, or possible approaches.

That trade-off showed up again in my final run with issue-20. My rubric accepted it while the gold label rejected it. I decided not to make the rule much stricter just for that one case because the rubric still got 19/20 overall, and making it stricter could cause it to reject other issues that are still reasonable first contributions.

From the final run: 
- `issue-20  reject  accept   NO     graded accept`

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

1. The issue's fit to your interests and to the time available.
- I chose Issue #13 because I want to get more experience with RAG and LLM applications. The issue involves testing the full RAG pipeline with a mock LLM, so I would get to understand more of how the retrieval and generation parts connect together. It is also a Tier-2 issue with an estimated 4–6 hour workload, which feels manageable for the amount of time I have.

2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
- The rubric correctly picked up that the repository is active, the issue has a clear goal, nobody is currently assigned to it, and there is no active pull request already working on it. It also noticed that the issue does not have a good first issue label. What the rubric could not really judge was which issue interested me the most. Issue #69 ranked higher because it was smaller and had the beginner label, but I chose #13 because it gives me more experience with RAG and LLMs, which is something I specifically want to learn more about.

3. The anticipated difficulty in claiming it.
- I do not think claiming the issue itself should be too difficult because there is no assignee, no one has commented that they are working on it, and there is no active pull request for it. The harder part will probably be understanding the existing RAG pipeline well enough to write the integration test correctly, especially since the issue is not specifically labeled as a beginner issue.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
