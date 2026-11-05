# Evidence guide: where evidence lives in a PR package

<!--
THIS IS THE PART YOU WRITE (third week running: the map stays in your
hands). Your tool uses this guide as its map: for every kind of
evidence a rubric check names, this file says WHERE to find it in a PR
package and WHAT GOOD LOOKS LIKE when you do.

The four families below are the harness's failure categories under
the names the eval README uses: plan fidelity = silent-drift, test
evidence = not-tested, diff quality = unreviewable, standards and
comms = standards-wall. A package that fails none of them is a
clear-accept. Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the plan-context block's scope pair and test
  plan, the candidate PR's diff, commits, description, or
  test-evidence section, the repo-facts block's template asks and
  stated policy). In live mode (where in your working copy and on
  GitHub: your plan.md and its deviation notes, your branch's diff,
  your draft title and description, your captured test output, the
  repo's PR template and CONTRIBUTING.md).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("every changed file falls inside the
  plan's stated boundary or a deviation note") over adjectives ("the
  diff is clean").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts three ways: your
procedure says WHEN to gather each family, this guide says WHERE, and
your SKILL.md says the tool reads both. Write the map you wish your
executor had.
-->

## Plan fidelity (harness category: silent-drift)

Where it lives: In an eval bundle, the plan-context block holds the plan's scope pair (in scope / not in scope) and any deviation notes; the candidate PR's diff section lists the changed files and hunks; the candidate PR's description holds the fidelity claims. In live mode, the plan is plan.md with its deviation notes, the diff is `git diff main...HEAD` from the working copy, and the claims are in the draft PR description.

What good looks like: Every changed file falls inside the plan's stated scope or is covered by a deviation note, and every planned change missing from the diff is covered by a deviation note or stated in the description. Silent drift has two directions: the diff does more than the plan (an unplanned file, an extra fix) or less (a planned change absent) with no note. A description that claims more or less than the diff delivers, or says "implements the plan" when the diff contradicts it, is silent drift too. An honest deviation or disclosed shortfall re-ties the mismatch and passes.

## Test evidence (harness category: not-tested)

Where it lives: In an eval bundle, the candidate PR's test-evidence section, read against the plan-context block's test plan and the reproduction steps. In live mode, the evidence section of the draft description and any captured terminal output, read against plan.md's test plan and the reproduction comment's steps.

What good looks like: The reproduction steps are shown run before and after, with the actual output, and the expected-after is stated. The outcome of the repo's own checks or suite is visible (a pass count or a named passing command), not just claimed. "Tests pass" with no output, a missing before or after, or checks never run (with no stated reason) is not decisive. An honestly stated limit, such as a check that could not run locally and why, is acceptable evidence of an honest PR.

## Diff quality (harness category: unreviewable)

Where it lives: The unified diff and the commit list (in an eval bundle, the candidate PR's diff and commits sections; in live mode, `git diff main...HEAD` and `git log main..HEAD --oneline`).

What good looks like: The fix is visible and nothing unrelated rides along. The tells of debris are debug leftovers (stray prints, debug flags), commented-out blocks, dead code, formatting churn (whitespace or reflow on lines the fix does not touch), and drive-by edits to unrelated files or lines. A small focused diff with no noise passes; a diff where the fix is buried does not.

## Standards and comms (harness category: standards-wall)

Where it lives: In an eval bundle, the repo-facts block states the PR template's sections, the contributing instructions, and the stated policy (including AI-use disclosure), and the thread highlights show maintainer direction. In live mode, read the repo's PR template file, CONTRIBUTING.md, and the issue thread, then read the draft description against them.

What good looks like: Each section the template names is filled with content specific to this change (not blank, "N/A" with no reason, or generic filler that fits any PR). The AI-use disclosure is present when the policy explicitly requires one. Explicit maintainer direction in the thread is followed or answered. Whether the description's claims match the diff is plan fidelity above, not this family. Tone or authorship preferences that name no required statement are not testable from the text and are not graded here.
