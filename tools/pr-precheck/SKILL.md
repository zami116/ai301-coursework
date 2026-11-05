---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

Answer exactly one question about exactly one PR package per run: is this ready to submit? A PR package is a candidate pull request (title, description, commits, diff, test evidence) read against the plan it claims to implement and the issue that plan belongs to. Never grade anything else: not the issue's quality, not the plan's quality, not the code's style beyond what the rubric names. Never grade more than one package per run. Never answer from gut feel; execute the components named under "Component reads".

## Inputs and modes

Run in exactly one of two modes. Pick live mode when the person gives you a PR, a branch, or a draft to check. Pick eval mode when the input is a package bundle (a block starting "Eval package:").

**Live mode.** Gather these inputs and name any that are missing before grading:
- The plan: plan.md, including its deviation notes. A house-chain student reads the house plan instead.
- The diff: everything the branch changes relative to the default branch. Produce it with `git diff main...HEAD` (three dots) run from the working copy, and read the commit list with `git log main..HEAD --oneline`.
- The draft PR title and description.
- The test evidence: the before/after output of the reproduction steps and the outcome of the repo's own checks, as pasted in the description or captured in the working copy. A house-chain student reads the house repro pack instead.
- The issue, read from the real repo: the issue thread, the repo's PR template, CONTRIBUTING.md, and any stated AI or contribution policy.

**Eval mode.** The bundle is the whole world. Fetch nothing, read nothing outside the bundle, and do not read scope.md or voice-guide.md. Grade a complete package: run every check in rubric.md and apply the full verdict rule.

## The scope seam (live mode only)

In live mode, read scope.md before anything else, before reading any input. Take the repo named on its `Repo:` line as the only repo you may grade work in. If that line still holds a placeholder (anything like `<ORG>/<PATH-REVIEW-REPO>`), stop without grading and tell the person to fill the `Repo:` line in scope.md with their section's Path Review repo. Never guess a scope and never fill the line yourself. If the PR or branch is not in the scoped repo, refuse to grade it and say why. Apply any house rules scope.md states. In eval mode, ignore scope.md entirely.

## The voice seam (live mode only)

In live mode, after reading the inputs, read voice-guide.md and hold the draft PR title and description against each rule in it. Report every rule the draft breaks in the readable summary, quoting the offending line and the rule it breaks. If voice-guide.md has no rules in it, say that you checked no voice rules; do not report a clean pass. The voice guide never changes the verdict on its own, because the verdict comes only from rubric.md's checks. In eval mode, ignore voice-guide.md entirely.

## Component reads

Read these four components from the tool directory before grading, and grade through them:
- rubric.md defines the checks and the verdict rule. It decides what to grade and what passes.
- references/evidence-guide.md maps where each evidence family lives in a PR package and what good looks like. Use it to locate every piece of evidence a check names.
- procedure.md is executed as written, step by step, in its stated order. It decides how to grade.

If the procedure is silent on a step you need, report the gap in your summary and do not improvise a step around it. If rubric.md has no checks table row with content, or procedure.md has no content beyond its template, refuse to grade, say which file is empty, and emit no verdict. Comments inside the templates are guides, not content. Never invent checks at runtime.

## Verdict and output

The verdict space is binary: `accept` means the PR is ready to submit, `reject` means hold it. There is no third verdict, no "accept with reservations", and no score; put reservations in a check's evidence line. Write a readable per-check summary first (and in live mode the voice report and any procedure gaps), then end the reply with the fenced JSON block below: valid, containing every rubric check once, and last, with nothing after it.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

Follow these standing rules on every run:
- Evidence first. Name the fact or quote that decided each check before you grade it. "Looks fine" is not evidence.
- Grade the thing, not the polish. Read the artifact itself (the diff, the output, the claim) against the plan, the issue, and the stated standards. A terse complete PR can be ready; a polished confident one can hide drift.
- The rubric decides, not the run. If a check passes by its stated condition but feels wrong, it still passes. Do not tighten or loosen a pass condition mid-run.
- The procedure decides how, not the run. Follow procedure.md as written and report its gaps.
- Unclear defaults to fail. Grade `unclear` when the package does not let you verify a claim. Treat `unclear` as the rubric's verdict rule directs; where that rule is silent, an unverifiable claim is a failing one.
- An honestly disclosed shortfall is not a failure. Do not hold a PR merely because it does less than the whole plan, if the plan's deviation notes and the description say so.