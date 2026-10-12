# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

zami116

**Plan comment**

[https://github.com/codepath/pathreview-ai301-fa26-howard/issues/71#issuecomment-6115885574](https://github.com/codepath/pathreview-ai301-fa26-howard/issues/71#issuecomment-6115885574)

Plan: the fixture in `test_extract_heading_hierarchy` is indented 8 spaces (inherited from the method body), which Markdown treats as a code block — that's why `_extract_heading_hierarchy` finds no headings, confirmed in my reproduction above. I'll dedent the fixture string and drop the `@pytest.mark.xfail` marker (manifest H-04), per the contributing guide's note that removing the marker is part of fixing a seeded bug. Test plan is re-running the same pytest command from my reproduction comment and confirming it moves from `xfail` to a clean pass, plus the full file's suite staying green.

One open question I haven't resolved yet: whether the dedented fixture needs any structural change beyond whitespace to satisfy all three assertion levels (1, 2, 3) — I'll find out once I run it and will say so here if it does.

I used Claude to help with research and drafting along the way; the plan and the change will be my own work that I understand and can explain.

---

## Your branch

**Branch**

fix/71-dedent-heading-fixture

**Evidence**

Before (Unit 2 reproduction, commit `99673c7`):
$ pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v -rx
...
XFAIL tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy - issue #71 (manifest H-04): heading hierarchy fixture is indented, so it has no headings
1 xfailed in 0.20s


Full-file baseline (before):

$ pytest tests/unit/test_readme_parser.py -v
...
13 passed, 2 xfailed in 0.33s


After (fix built on this branch):

$ pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v
...
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED [100%]
1 passed in 0.15s


Full-file result (after):

$ pytest tests/unit/test_readme_parser.py -v
...
tests/unit/test_readme_parser.py::TestReadmeParser::test_parse_standard_readme XFAIL (issue #70 (manifest H-03): README parser fixture is i...) [ 6%]
...
tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy PASSED [ 66%]
...
14 passed, 1 xfailed in 0.30s


`test_parse_standard_readme`'s separate #70/H-03 xfail marker is untouched and still correctly reports `XFAIL`, confirming the fix stayed within its stated scope.

---

## Eval iterations

**Run history**

Run 1: 18/20 (bar met) — Run 2 (--only, revised `unknowns-honest` and `executable-by-a-stranger`): 4/4 agreed, canaries held — Run 3 (full confirming run): 20/20 (bar met, PASS — this is the run committed to `eval-run.txt`)

**Package analysis**

pkg-14: my rubric's verdict was reject on the first full run (failed `executable-by-a-stranger`); gold label is accept. The plan states that "exact functions to be pinned in the PR after tracing the query issuance with debug logs, which I have working" — my original check's fail condition treated any plan that didn't name an exact function upfront as assuming unstated context. But this plan actually states specific, traced context (the mechanism, the subsystem, evidence already gathered via `zellij --debug`) and is honestly deferring only the final function names to a stated next step, not failing to think it through. I revised the check to allow a plan to identify the subsystem/mechanism precisely and defer exact naming to a stated, evidenced next step, which flipped this package to accept while still failing a plan that names no subsystem or mechanism at all.

**Check rationale**

`unknowns-honest`, as currently written in `rubric.md`:

> Pass if the plan states genuine open questions or risks it hasn't resolved, OR explicitly identifies a specific, bounded cost/trade-off of the approach even if that cost is small or already well-understood (e.g., "one extra request per day, which is the constant's existing purpose"). Fail if the plan has no risks/unknowns section at all, or one that's boilerplate/generic ("risk: might not work") without naming anything specific to this change — including a specific, small, already-understood cost in that specificity bar.

My first draft only accepted a plan if it named an unresolved question — which incorrectly failed pkg-05, a plan whose diagnosis was precise enough that its only real "risk" was a small, already-understood cost (one extra network request per day), not an open question. I revised the check to accept either an open unknown or a specifically-named small cost, rather than requiring the plan to manufacture uncertainty it genuinely didn't have.

**Trade-offs**

Accepting a specifically-named small cost as satisfying this check means a plan with genuine uncertainty and a plan with a trivial, fully-understood cost both pass the same way — the verdict doesn't distinguish "nothing left to worry about" from "here's a real open question I haven't resolved." I accept this: the alternative (requiring every plan to state an unresolved question) would have penalized well-grounded, low-risk plans for not inventing doubt, which is a worse failure mode than slightly blurring two different kinds of honesty. I re-ran pkg-06 (scope-creep) and pkg-10 (unbuildable) as canaries after this change to confirm it didn't loosen anything in checks this revision didn't target, and both still correctly rejected.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.


Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
