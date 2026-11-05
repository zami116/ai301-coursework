# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

1. Read the plan first: its in-scope and not-in-scope statements, its files list, its test plan, and its deviation notes. Write down the boundary as a list of files and changes, and the test plan's command and expected-after. This is the yardstick every side-by-side check reads against, so read it before seeing any diff.
2. Read the issue context and the repo-facts block (live: the issue thread, the PR template, CONTRIBUTING.md). Write down every template section the repo names, any explicit AI-disclosure requirement, and any explicit maintainer direction.
3. Read the diff and the commit list. Write down every changed file, and flag each hunk as inside the plan, covered by a deviation note, or neither; list any debris.
4. Read the test evidence. Write down which command was run before and after, the observed output, and the outcome of the repo's own checks.
5. Read the description last, claim by claim. Reading it last stops its framing from shaping how the diff and evidence are read.

## Evidence gathering

- **diff-matches-plan:** pair every changed file in the diff with the plan's boundary list from step 1. Record each file as in-plan, noted-deviation, or unplanned. Then pair each planned change with the diff and record it as present, noted-deviation or disclosed-in-description, or missing.
- **description-matches-diff:** list every claim in the description about what the change does, fixes, or covers (including any statement that it follows the plan). Record each as true of the diff, false, or unverifiable.
- **test-evidence-decisive:** record the reproduction command and output shown for before and for after, the expected-after stated, and the repo's own checks' outcome. Compare the command to the plan's test plan and the reproduction steps; record whether the evidence is equivalent coverage of the changed behavior. Record any stated reason a check could not run.
- **diff-reviewable:** scan the diff for debug leftovers, commented-out or dead code, whitespace or formatting hunks on untouched lines, and edits to files unrelated to the plan. Record each tell with its file, or record that none exist.
- **standards-honored:** for each template section the repo names, record the description's content under it (real, empty, or placeholder). Record whether the policy requires disclosure and whether the description contains it. Record the maintainer direction and whether the description engages it.

## Check execution

Run the checks in rubric order: diff-matches-plan, description-matches-diff, test-evidence-decisive, diff-reviewable, standards-honored. Grade each from its gathered record, quoting the deciding fact before assigning pass, fail, or `unclear`. When evidence a check needs is genuinely absent (for example, no test-evidence section exists at all), grade that check `unclear`; do not infer evidence that is not stated. An absent deviation-notes section is not absent evidence: it means the plan recorded no deviations, so any mismatch is unrecorded. Apply each pass condition as written, including its carve-outs for honestly disclosed shortfalls. A check may be graded from its recorded facts without re-reading the whole package; re-read only when a recorded fact is ambiguous. Do not change a grade because another check failed.

## Verdict assembly

Apply the rubric's verdict rule: accept only if all five checks graded pass; any fail or `unclear` produces reject, because `unclear` counts as fail. When more than one check failed, name the first failing check in rubric order as the deciding check and quote its evidence line in the summary. In the JSON block, include every check with its own one-line evidence, and set the verdict to match. Emit the JSON block last.
