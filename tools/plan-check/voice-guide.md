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

I'm a CS student working through this issue as part of a course assignment, making my first real open-source contribution. I'm here to investigate and report back honestly — not to promise a fix, a timeline, or a merge. Readers should expect a specific, evidenced account of what I found, including if I couldn't reproduce something.

## Rules I write by

### Rule: Promise investigation, not outcomes

I can commit to looking into something. I cannot commit to fixing it, how long it'll take, or that my fix will be accepted — those depend on things I don't control yet (what I find, maintainer review, scope creep).

- Wrong: "I will fix it within 2 days guaranteed."
- Right: "I'd like to investigate this. I'll report back what I find."

### Rule: Say something only this issue could prompt

If a comment could be pasted onto any issue in any repo unchanged, it says nothing. Every comment should reference something specific — the exact symptom, a line from the thread, a file I looked at.

- Wrong: "Great project, I love using this every day! This issue looks like a good one for me."
- Right: "I can reproduce the missing Content-Type header on 3.2.4 with exactly one custom header (repro below)."

### Rule: Match my claim to my evidence, not my hope

If I reproduced it, I say so and point to the exact output that shows it. If I couldn't, I say that plainly and show what I actually tried — a real cannot-reproduce is useful; a confident guess dressed as a result is not.

- Wrong: "Yep, this is definitely broken, I can see why."
- Right: "I could not reproduce this on Linux + zsh with the report's exact steps; here's what differed from the original environment."

### Rule: Don't ask for exclusivity I haven't earned

Asking a maintainer to "reserve" or "assign" an issue to me before I've shown any real work on it asks for trust up front instead of earning it.

- Wrong: "Kindly assign it to me and keep this issue reserved for me."
- Right: "I'd like to take this on — here's what I've found so far investigating it."

### Rule: Disclose AI assistance when the repo asks for it

If a repo's contribution policy requires stating AI tool use, that goes in the comment plainly, not left out because the rest of the comment already sounds like me.

- Wrong: (silently omitting it because "the writing sounds human enough")
- Right: "I used Claude to help draft this report; the investigation and conclusions are my own."

## Things I never post

- A guaranteed fix or a completion date
- Flattery or filler that isn't about the actual issue ("great project!", "love this repo!")
- A request to be assigned or have the issue "reserved" before I've shown real investigation
- A claim of reproduction without showing the exact output that demonstrates it
- An omitted AI-disclosure statement when the repo's policy requires one
