# Unit 4 — Test and Submit

Path: `beat-1-sandbox/unit-4/pull-request.md`

Record of the pull request you opened against the Path Review repo, and of the evaluation
runs that produced `eval-run.txt`. This file is graded at the path above; a copy kept
anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-howard/pull/82

**Branch**

fix/71-dedent-heading-fixture

## Eval iterations

**Run history**

Run 1: 20/20 (bar met). Run 2: all 20 packages errored (`claude exited 1`) because Claude Code was logged into the wrong account, so nothing was scored. Run 3: 20/20 (bar met, PASS), the run committed to `eval-run.txt`.

**Check rationale**

`standards-honored`, as it reads in the `rubric.md` I uploaded to `tools/pr-precheck/`:

> Pass if every section the repo's PR template states is filled with real content specific to this change, any explicit maintainer direction in the thread is followed or the description says why not, and the description contains the AI-use disclosure whenever the repo's stated policy explicitly requires a disclosure. Fail if a stated template section is left empty, left as placeholder text, or ignored, if the policy explicitly requires disclosure and the description omits it, or if explicit maintainer direction is ignored. A policy that only expresses a tone or authorship preference, without requiring a disclosure statement, is not tested here

I never revised this check after the first run, because it agreed on both standards-wall packages from the start. It reads this way for three reasons. The assignment says the standards-wall category cannot be made up for elsewhere, so the repo's template and disclosure asks needed their own required check. It tests only what the text can prove: a template section is filled or it isn't, and a required disclosure is present or it isn't. The last sentence carries over a unit 6 lesson, where a check that tried to judge authorship from comment text produced a false reject on a "write in your own words" policy. The live run also caught a real problem in my own PR draft, which still had unfilled placeholders in the template, so I fixed it before opening PR #82.

**Trade-offs**

I never revised the tool after the first run, so nothing changed and here is how I know: the first full run and the saved full run both agreed on all 20, with every category at 100% (clear-accept 7/7, not-tested 4/4, silent-drift 4/4, standards-wall 2/2, unreviewable 3/3), and a later `--only pkg-20` re-run agreed again. What `standards-honored` gives up is policies that only state a preference. A repo that asks for comments in your own words without requiring a disclosure statement is not tested, so my rubric would let through a PR that ignores that kind of ask.

**Package analysis**

pkg-20 (ghostty-org/ghostty#13604, category standards-wall): my rubric decided reject and the gold label is reject, so they agree. The saved run shows only the verdict. The per-check detail below comes from a later `--only pkg-20` re-run on the same unchanged tool, where two checks failed. The check that matches this package's category is `standards-honored`. The bundle's policy line reads: "All AI usage in any form must be disclosed, stating the tool used and the extent of the assistance". The candidate description contains no AI-use disclosure at all. My check's condition is "the description contains the AI-use disclosure whenever the repo's stated policy explicitly requires a disclosure", so a required disclosure that the description omits is a fail. The re-run's evidence line was: "AI_POLICY.md requires disclosure of any AI usage (tool and extent); the description contains no AI-use disclosure."

The re-run also failed `description-matches-diff`, which was the first failing check in rubric order. The description says "a second case covers the single-theme scheme flip", but the added second test is "changeConditionalState still ignores unrelated keys" (.fullscreen). The flip is covered by the rewritten existing test. My rubric read this as a claim the diff does not contain. The other three checks passed: the diff stays inside the plan's scope (`src/config/Config.zig` and its test block), the repro is shown before (`?997;2n`) and after (`?997;1n`), and the diff has no debris. This is the package where the polish hides the problem: a tidy, evidence-backed description still gets held because the repo's disclosure rule is not met.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/pr-precheck/`.
