# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
| --- | --- | --- | --- |
| diagnosis-grounded | The plan's stated cause, read against what the repro-evidence block's steps and artifact actually show | Pass if the plan's stated cause explains the specific behavior the repro evidence demonstrates — not a plausible-sounding but different mechanism, and not a restatement of the symptom as if it were the cause. Fail if the stated cause isn't supported by, or actively contradicts, what the repro evidence shows, or if no cause is stated at all | required |
| bounded-scope | The plan's in-scope / not-in-scope statement and its named files or areas | Pass if the plan names one bounded change — a specific file, function, or small set of related files under one fix — and explicitly states what's out of scope. Fail if the plan's scope is open-ended ("clean up related issues while I'm in there"), touches unrelated areas with no stated reason tying them to the same cause, or states no boundary at all | required |
| executable-by-a-stranger | The plan's approach/steps section, read against the files or areas it names | Pass if someone who has never seen the issue could identify the specific subsystem/area and begin tracing from there, even if the exact file or function is pinned down as a stated next step (e.g., "exact functions to be named after tracing with debug logs, which I already have working") rather than named upfront — as long as the plan states enough specific context (the mechanism, the relevant subsystem, evidence already gathered) that the next step is unambiguous. Fail if the plan states only the desired outcome with no named subsystem or mechanism, or assumes context about the codebase that it never states anywhere in the plan. | required |
| test-decisive | The plan's test-plan section, read against the repro evidence's own steps and artifact from the prior unit | Pass if the test plan names a specific, observable before/after — reusing the actual repro steps and stating what output or behavior should change — such that someone could run it and get a yes/no answer. Fail if the test plan is vague ("test it works"), doesn't reference the original repro steps/evidence, or doesn't state what the expected-after looks like | required |
| unknowns-honest | The plan's risks/unknowns section, read against what the plan's diagnosis and approach claim elsewhere | Pass if the plan states genuine open questions or risks it hasn't resolved, OR explicitly identifies a specific, bounded cost/trade-off of the approach even if that cost is small or already well-understood (e.g., "one extra request per day, which is the constant's existing purpose"). Fail if the plan has no risks/unknowns section at all, or one that's boilerplate/generic ("risk: might not work") without naming anything specific to this change — including a specific, small, already-understood cost in that specificity bar. | required |
| comment-faithful | The plan comment, read against the issue thread's highlights (or live thread) and the repo-facts block's contribution policy | Pass if the comment is specific to this issue's plan (not boilerplate), acknowledges relevant maintainer signals already in the thread if any exist, promises only the stated plan (not a guaranteed timeline or fix), and includes any disclosure the repo's policy requires. Fail if the comment ignores existing thread guidance, is generic, promises more than the plan supports, or omits a required disclosure | required |

## Verdict rule

Accept (ready to post and build from) only if all six required checks pass. Any single required check failing holds the package. `unclear` on any check counts as a fail for that check.
