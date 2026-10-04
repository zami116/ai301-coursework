# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

zami116

---

## Posted upstream

**Claim comment**

[https://github.com/codepath/pathreview-ai301-fa26-howard/issues/71#issuecomment-5975000745](https://github.com/codepath/pathreview-ai301-fa26-howard/issues/71#issuecomment-5975000745)

**Reproduction comment**

[Link to the comment where you posted your reproduction. It must record the environment
(OS, relevant versions, code state), steps a stranger could follow, and what you observed.
**Then paste the text of that comment underneath the link** — the pasted text is what this
field is graded on, so copy across what you actually posted.]

## Eval iterations

## Eval iterations

**Run history**

Run 1: 14/20 (below bar) — Run 2: 20/20 (bar met, PASS — this is the run committed to `eval-run.txt`)

**Package analysis**

pkg-19: my rubric's verdict was reject (failed `claim-specific`); gold label is also reject. The package's claim comment reads, in part: "Hello sir! Great project, I love Vue and use it every day... Kindly assign it to me, I will fix it within 2 days guaranteed... keep this issue reserved for me." My `claim-specific` check requires the claim comment to name something specific to the issue and limit its promise to investigation only — this comment does neither: it contains no reference to the issue's actual symptom or number, it guarantees a fix and a 2-day timeline (not just investigation), and it demands exclusive assignment before showing any real work. The repro report itself is actually solid (specific environment, a concrete re-created playground, a clearly shown artifact), which is exactly why this package is a good test of the check: a package can fail entirely on the comms half even when the technical reproduction is fine, which matches the lecture's framing that the words meeting the repo's expectations is its own proof family, separate from the technical evidence.

**Check rationale**

`claim-specific`, as currently written in `rubric.md`:

> Pass if BOTH: (a) the repro report's stated outcome (reproduced / could not reproduce) cites the specific evidence that decided it, rather than a generic assertion; AND (b) the claim comment names something specific to this issue (its number, title phrase, or exact symptom) and limits its promise to investigation only — never a guaranteed fix, a completion date, or a demand for exclusive assignment. Fail if either half fails: a vague/unsupported outcome claim, OR a claim comment that is generic boilerplate (could be pasted onto any issue in any repo unchanged) or promises more than investigation.

This check originally only covered half of this (the repro report's outcome claim). I merged the claim-comment requirement in after pkg-19 showed a real package where the comment itself was the only thing wrong — generic flattery, a guaranteed-fix promise, and a demand for exclusive assignment — and none of my other four checks were positioned to catch comment tone or promises at all. Rather than add a sixth check, I folded it into `claim-specific` since both halves are really testing the same thing: does the claim (about outcome, or about intent to work on it) match what the evidence actually supports, rather than what the author hopes or wants.

**Trade-offs**

Merging the two halves into one check means a package that fails on comment tone and a package that fails on a vague outcome claim both just show up as "failed: claim-specific" — the verdict alone doesn't say which half broke, only a human reading the evidence would know. I accept this: the alternative (a sixth check) would have meant deciding which of five+ checks a comment-tone problem belongs under, when the real issue is that both halves are instances of the same failure mode (claiming more than the evidence shows). I re-ran pkg-07, pkg-09, and pkg-11 as canaries after this merge to confirm it didn't regress any already-passing package with a measured, investigation-only comment, and all three still passed.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
