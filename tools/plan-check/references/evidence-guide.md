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

Where it lives: in an eval bundle, the plan's stated cause (usually near the top, a "diagnosis" or "root cause" line), read against the repro-evidence block's steps and the artifact/output it shows. In live mode, the student's draft plan.md's diagnosis section, read against their own posted repro comment from the prior unit.

What good looks like: the stated cause, if true, would produce exactly the behavior the repro evidence shows — not a nearby but distinct mechanism, and not just the symptom reworded as a cause ("the test fails" is a symptom; "the fixture is indented" is a cause). A diagnosis that cites a specific line, function, or condition in the evidence is stronger than one that gestures at the general area.

## Bounded scope

Where it lives: the plan's explicit in-scope / not-in-scope statement, usually near the top alongside the diagnosis, plus whatever files or areas are named in the approach section.

What good looks like: scope is bounded to the smallest change that fixes the diagnosed cause — one file, or a small set of files all touched for the same stated reason. A drive-by rewrite looks like extra files touched with no stated connection to the diagnosis, or language like "while I'm here" or "also cleaned up."

## Executable by a stranger

Where it lives: the plan's approach/steps section, read against the files or areas it names elsewhere in the plan.

What good looks like: a stranger with no prior context could read the approach and know exactly what file to open and what to do first — a named function, a specific change ("dedent the markdown string," not "fix the formatting"). A plan that states only the goal, or assumes the reader already knows which file/function is involved without naming it, is not executable by a stranger.

## Test decisive

Where it lives: the plan's test-plan section, read directly against the repro evidence's own steps and artifact from the prior unit's repro comment.

What good looks like: the test plan names the exact same command/steps used in the original repro, plus a stated expected-after (what output or behavior should look like once the fix lands) — specific enough that running it gives an unambiguous yes/no on whether the fix worked. "Re-run the tests" without naming which test or what passing looks like now is not decisive.

## Unknowns honest

Where it lives: the plan's risks/unknowns section, read against the confidence level of the diagnosis and approach sections elsewhere in the plan.

What good looks like: a real unknown names something specific the author hasn't verified yet (e.g., "haven't checked whether other fixtures in this file have the same indentation issue"), not a generic hedge that could apply to any change. A plan with zero unknowns for a change touching code the author just encountered is a signal of false confidence, not thoroughness.

## Comment faithful

Where it lives: the plan comment, read against the issue thread's highlights (or the live thread) for any maintainer guidance already given, and against the repo-facts block's stated contribution policy, including any AI-use disclosure requirement.

What good looks like: the comment references the specific plan (not generic "working on a fix"), acknowledges and follows any guidance a maintainer already left in the thread (e.g., "as suggested above, I'll look at X"), states only that a plan exists and will be attempted — not a completion guarantee — and includes a disclosure statement if the repo's policy requires one.
