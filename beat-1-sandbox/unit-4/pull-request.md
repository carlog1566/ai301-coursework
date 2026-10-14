# Unit 4 — Test and Submit

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/203

**Branch**

`test/13-rag-integration-test`

## Eval iterations

**Run history**

I completed one full evaluation run.

> `agreement: 19/20 scored items`

The category results from that run were:

> `categories: clear-accept 6/7  not-tested 4/4  silent-drift 4/4  standards-wall 2/2  unreviewable 3/3`

This was the only full run I completed, and it is the run saved in my submitted `eval-run.txt`.

**Package analysis**

I chose `pkg-02`.

The result from my evaluation was:

> `pkg-02  clear-accept    accept  reject   NO     failed: Repository standards are satisfied`

My rubric decided **reject**, while the gold label was **accept**.

My rubric rejected this package because it failed my `Repository standards are satisfied` check. That check requires the PR to satisfy every applicable repository template, contribution-policy, testing, disclosure, and maintainer requirement. Based on the evidence available in the package, the grader interpreted one of those repository requirements as not being fully satisfied and therefore rejected the package.

This was the only package my rubric disagreed with. The result showed that my repository-standards check can be stricter than necessary for some otherwise acceptable PRs. However, that same strictness allowed the rubric to correctly reject both `standards-wall` packages, so I kept the check rather than loosening it only to make `pkg-02` match.

**Check rationale**

One check from my final `rubric.md` is:

> `Repository standards are satisfied | The PR title and description read against the repository's PR template, docs/CONTRIBUTING.md, stated policy, and relevant maintainer directions in the issue thread. | Pass if every applicable template section has meaningful content, the correct issue is linked as required, testing results are represented accurately, required AI-use disclosure is present, and applicable maintainer or contribution instructions are followed. Fail if an applicable stated requirement is omitted, falsely checked, left as boilerplate, or ignored. | required`

I made this check required because a PR can have a correct implementation and still not be ready to submit if it ignores the repository's stated contribution requirements. The Unit 4 eval also includes the `standards-wall` category, so I wanted the skill to compare the PR against the repository's actual PR template, contribution guide, policies, and relevant maintainer instructions rather than only checking the code.

I chose to make the rule evidence-based instead of requiring one specific PR format. This allows the check to adapt to the requirements stated by the repository while still catching missing issue references, inaccurate testing claims, missing disclosures, boilerplate sections, or ignored maintainer instructions.

**Trade-offs**

The main trade-off of `Repository standards are satisfied` is that it can be stricter than necessary for an otherwise acceptable PR.

This happened with:

> `pkg-02  clear-accept    accept  reject   NO     failed: Repository standards are satisfied`

The gold label accepted `pkg-02`, while my rubric rejected it. I accepted that trade-off because my full run still reached:

> `agreement: 19/20 scored items`

and the standards-wall category still achieved:

> `standards-wall 2/2`

I did not loosen the check after the run because doing so only to make `pkg-02` pass could weaken the rubric's ability to catch PRs that actually ignore explicit repository requirements. Since the rubric already exceeded the required agreement threshold and matched every failure category at least once, I kept the stricter version.