# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->
I'm a computer science student who is still getting experience contributing to larger codebases and open-source projects. When I comment on an issue, I'm usually trying to understand and reproduce the problem before making any changes. I want my comments to be clear about what I actually did, what I found, and what I still need to figure out.

## Rules I write by

<!-- 3-5 rules, drafted from the lecture's slide-12 moment. Each rule
needs a wrong/right pair from your own hand: one line you might
actually have written that breaks the rule, and the line you would
post instead. The pair is what makes a rule executable; a rule without
one is a wish.

Format each rule like this:

### Rule: <short name>

<The rule, one or two sentences.>

- Wrong: "<a line that breaks it>"
- Right: "<the line to post instead>"
-->
### Rule: Don't say I did something before I actually did it

I should only say that I reproduced, tested, or confirmed something if I actually did it and have evidence for it. If I am still planning to investigate something, I should make that clear.

- Wrong: "I reproduced the issue and I'll work on fixing it."
- Right: "I'd like to look into this issue. I'll try to reproduce the behavior first and report back with what I find."

### Rule: Don't promise a fix or deadline

When claiming an issue, I should only commit to investigating and reporting back. I do not know what the problem will require until I reproduce and understand it.

- Wrong: "I'll have a fix for this by the end of the week."
- Right: "I'll investigate the issue and post my reproduction steps and results once I have them."

### Rule: Be specific about what I actually tested

Instead of saying that I "looked into" something, I should mention the actual command, behavior, error, or part of the project I tested when that information is available.

- Wrong: "I tested the issue and ran into the same problem."
- Right: "I ran the integration test with the mock response and saw the same error described in the issue."

### Rule: Be honest when something does not work

I should not force a conclusion just because I expected a certain result. If I cannot reproduce something or get a different result, I should say exactly that and mention anything about my setup that could explain the difference.

- Wrong: "The bug is confirmed even though I couldn't get the exact same error."
- Right: "I wasn't able to reproduce the reported error. In my environment I got a different result, so I'm going to include my setup and output in case that difference matters."

### Rule: Keep comments natural and focused

I want my comments to sound like something I would actually say to another developer. I should avoid unnecessary formal wording and focus on the information that is useful for understanding the issue.

- Wrong: "After conducting a comprehensive investigation of the aforementioned behavior, I have determined that further analysis is necessary."
- Right: "I tested the behavior locally, but I still need to trace where the response is being created before I can say what's causing it."

## Things I never post

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->
- A promise that I will definitely fix an issue.
- A deadline that I do not know I can meet.
- A claim that I reproduced something without evidence.
- A guess presented as if it were confirmed.
- "Same as above" instead of posting my own reproduction steps and evidence.
- Overly formal or vague wording that hides what I actually did.
- A confident root-cause claim before I have traced and verified it.