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

1. Read the issue context first — this establishes what behavior is actually being fixed, independent of any later framing.
2. Read the repro-evidence block second, noting the exact steps taken and the exact artifact/output shown. This is the ground truth every later check's evidence gets compared against.
3. Read the plan third — diagnosis, scope, approach, test plan, risks/unknowns — noting each section's content as you go.
4. Read the plan comment last, and read the thread highlights (or live thread) alongside it.

This order matters because diagnosis-grounded, test-decisive, and comment-faithful all require comparing something in the plan against something read earlier (the repro evidence, or the thread) — grading the plan before fully absorbing the repro evidence risks judging the diagnosis as "plausible" rather than "actually grounded."

## Evidence gathering

- **Diagnosis and grounding**: from the repro-evidence block, record the exact behavior shown (error message, missing output, or symptom). From the plan, record the stated cause verbatim.
- **Bounded scope**: from the plan, record the in-scope statement, the not-in-scope statement, and every file/area named anywhere in the plan (approach section included, since scope creep often shows up there even when the scope statement itself looks clean).
- **Executable by a stranger**: from the plan's approach section, record the first concrete step stated. If no concrete first step exists, record that absence directly rather than inferring one.
- **Test decisive**: from the plan, record the stated test steps and expected-after. From the repro-evidence block (read in step 2), record the original repro steps for comparison.
- **Unknowns honest**: from the plan, record every line in the risks/unknowns section verbatim. If the section is empty or missing, record that as its own fact.
- **Comment faithful**: from the plan comment, record its exact text. From the thread highlights/live thread, record any maintainer comment that offers guidance. From the repo-facts block, record the stated contribution/disclosure policy.

## Check execution

Run checks in this order: diagnosis-grounded, bounded-scope, executable-by-a-stranger, test-decisive, unknowns-honest, comment-faithful — the same order evidence was gathered in, so each check is graded immediately while its evidence is freshest.

When evidence for a check is genuinely absent from the package (not just thin, but not present at all — e.g., no risks/unknowns section exists), grade that check `?`, which the verdict rule treats as fail for required checks, same as an explicit F. Do not infer evidence that isn't stated to avoid a `?`.

A check may be graded without re-reading the full package only when its gathered evidence is fully self-contained — comment-faithful can be graded from the recorded comment text, thread highlights, and policy alone, without re-reading the plan's diagnosis or approach sections again.

## Verdict assembly

Apply the rubric's verdict rule: accept only if all six checks graded P; any F or `?` on a required check produces reject. For the output, quote the evidence line recorded for the first failing check (in check-execution order) as the "deciding check" — if multiple checks fail, only the first one encountered in execution order is quoted, to keep the output focused on one clear, actionable reason rather than listing every failure at once.
