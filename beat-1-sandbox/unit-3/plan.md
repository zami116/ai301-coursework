# Plan: dedent the heading-hierarchy test fixture (#71)

## Diagnosis

The `markdown` fixture string in `test_extract_heading_hierarchy`
(`tests/unit/test_readme_parser.py`) is indented 8 spaces, inherited from
the enclosing method body. Markdown treats 4+ spaces of indentation as a
code block, so `_extract_heading_hierarchy` correctly finds no headings
in it. This is confirmed in the Unit 6 reproduction (commit `99673c7`):
the test fails exactly as its `xfail(strict=True, reason="issue #71
(manifest H-04): heading hierarchy fixture is indented, so it has no
headings")` marker states, and the fixture source shows the literal
8-space indentation on every line (e.g. `        # Main Title`). The
parser's behavior is correct; the test fixture is the bug.

## Scope

**In scope:** dedent the `markdown` string literal in
`test_extract_heading_hierarchy` so its lines start at column 0 (or at
whatever indentation the headings themselves require to be recognized,
with no leading indentation beyond that), and remove the
`@pytest.mark.xfail` marker on that test, per the contributing guide's
note that dropping the marker is part of fixing a seeded bug.

**Not in scope:** `_extract_heading_hierarchy`'s own logic, which is
already correct and untouched. The separate `test_parse_standard_readme`
xfail (issue #70, manifest H-03) is a different seeded bug in a
different test and is not touched by this change.

## Files

- `tests/unit/test_readme_parser.py` — the `test_extract_heading_hierarchy`
  method only: the `markdown` fixture string and its `@pytest.mark.xfail`
  decorator.

## Approach

1. Open `tests/unit/test_readme_parser.py` and locate
   `test_extract_heading_hierarchy`.
2. Remove the `@pytest.mark.xfail(strict=True, reason="issue #71 ...")`
   decorator immediately above the method.
3. Rewrite the `markdown` string literal so none of its lines carry the
   inherited 8-space method-body indentation — either by dedenting the
   literal directly or by applying `textwrap.dedent(...)` to it, matching
   whichever style the rest of the file's non-xfailed fixtures already
   use (`test_parse_readme_with_code_blocks` and similar methods have
   working, non-indented-as-code fixtures worth matching for consistency).
4. Run the single test
   (`pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v`)
   and confirm it passes with no `xfail`/`XPASS` markers at all.
5. Run the full file (`pytest tests/unit/test_readme_parser.py -v`) to
   confirm no regressions in the other 14 tests.

## Test plan

Re-run the exact Unit 6 repro command:

```bash
pytest tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy -v -rx
```

**Before (Unit 6 evidence, commit `99673c7`):**

```bash
XFAIL tests/unit/test_readme_parser.py::TestReadmeParser::test_extract_heading_hierarchy - issue #71 (manifest H-04): heading hierarchy fixture is indented, so it has no headings
1 xfailed in 0.20s
```

**Expected after:** the same command reports `1 passed`, with no
`xfail`/`XPASS` line at all (the marker will be removed, so there's
nothing left to report as expected-or-unexpected).

Additionally, `pytest tests/unit/test_readme_parser.py -v` should move
from `13 passed, 2 xfailed` (the Unit 6 baseline) to `14 passed, 1
xfailed` (only the unrelated issue #70/H-03 marker remaining).

## Risks and unknowns

- I haven't yet confirmed that dedenting alone satisfies every assertion
  in the test (that levels 1, 2, and 3 are all captured) — only that the
  code-block theory explains why zero headings are currently found. It's
  possible the dedented fixture still needs a structural tweak beyond
  whitespace to produce all three heading levels; I'll find out when I
  run step 4.
- I have not checked whether `test_parse_standard_readme` (the separate
  issue #70/H-03 xfail) shares this same indentation root cause. I'm
  treating it as a distinct issue rather than folding it in here, since
  Unit 6's reproduction only covered #71.

## Deviations

While removing #71’s xfail marker, I initially deleted the wrong decorator — #70’s marker (a separate, out-of-scope seeded bug) came off instead of #71’s. I caught this because test_parse_standard_readme started failing outright instead of showing its expected XFAIL, restored #70’s original decorator, then correctly removed #71’s. Final result matches the plan’s prediction exactly: 14 passed, 1 xfailed.
