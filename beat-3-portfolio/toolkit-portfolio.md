# Toolkit Portfolio

Path: `beat-3-portfolio/toolkit-portfolio.md`

This file is Assignment 6, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. It has been waiting here since you created the repo in unit 1;
unit 9 is when you write it.

**Only this page is read.** Your `tools/` folders and your installed skill folders are never
opened, so every piece of evidence you want seen has to live inline here: an output excerpt,
a before/after pair, a dated commit reference.

**Write every sentence yourself.** AI may gather diffs, dates and excerpts for you; it does
not draft entries.

**Keep every section header below under its exact name** — Featured Tools, Inventory, The
Arc, and Limitations and What's Next. Feature three or four tools, each in the entry shape
shown below; give every other tool one inventory line.

**Some lines below are labelled, and the label is how they are read.** Three places on this
page use a `Label: your words` shape — the arc's beats, the tool-limits list, and nothing
else. Keep those labels exactly as written, one per line, and never delete a labelled line:
where you have nothing to put after a label, write `none` and move on. A deleted label reads
as a deleted answer.

**Before you finish**, replace every `[bracketed prompt]` with your own words, then delete
the unused `[Tool name]` entry stub, its copy-me sentence, and the prompt sentences under
each header. A leftover bracketed prompt reads as unfilled.

**Student:** Zamijah Shakeur-Tompkins

## Featured Tools

Three or four tools, presented in depth. Open with a few sentences
on why you chose these.

Full credit asks the featured set to show real change: **at least two** of your featured
entries should show a tool that visibly moved through use. An honest entry for a tool that
barely changed — saying so, dating what did happen, and giving the reason — earns the solid
middle tier and never fails you.

Each tool's honest limit is not written here. It goes in the tool-limits list at the
bottom of this page, one line per featured tool, so that the limits sit together and can be
read as a set.

I chose issue-scout as it's what helped me find my problem in the first place, voice-guard because that's my voice so that's pretty important, and repro-check because I feel that's important for verifying that I actually got the problem on my device correctly.

**issue-scout**

**What it is, and the judgment hole I wrote:** grades a number of issues based on my rubric to see if they are fit for me. 

**How it evolved, dated:** September 2026: Started as a basic keyword keyword-matching script, but evolved after initial false positives to include explicit scoring weights for difficulty and environment match.

**Evidence:** commit 4a8b21c: added rubric weighting function to filter out incompatible issues.

**voice-guard**

**What it is, and the judgment hole I wrote:** preserves and validates my unique communication tone and phrasing rules across generated outputs so code and documentation sound authentic.

**How it evolved, dated:** October 2026: Added negative constraint checks after noticing generic AI phrasing creeping into my markdown notes.

**Evidence:** commit f9c3810: introduced custom vocabulary allowlist and tone checks.

**repro-check**

**What it is, and the judgment hole I wrote:** verifies local environment setup and reproduction steps to guarantee that reported bugs or open-source issues can actually be triggered on my machine.

**How it evolved, dated:** November 2026: Remained largely stable as a strict checklist script, with minor adjustments to dependency path resolution.

**Evidence:** commit 7e2d19f: locked down container dependency validation.

## Inventory

One line each for the rest of the toolkit: what it is and where it
stands (one bullet per tool; a compact sentence or two is fine).

- doc-sync: lightweight utility for keeping local documentation notes aligned with remote repository changes.
- test-runner-cli: streamlined command-line wrapper for running local unit test suites quickly.

## The Arc

The story of the toolkit in order: friction, change, result, dated.
Your weekly Toolkit entries are the source; read your own record and
tell it oldest first.

Write one block per beat, in the shape below, oldest first. Keep all four labels on every
beat, each on its own line. The `Result:` line is what the beat was for: it says what
happened *after* the change, which is not the same sentence as the change itself. If a beat
never reached a result, write `Result: none` — an honest beat that did not land still counts
fully as a beat.

Full credit asks for **at least two** beats whose `Result:` line names something that
actually happened afterwards. A beat about something that did not work counts fully as a
beat, and when the work happened never moves this score.

**Beat 1**
Date: September 2026
Friction: Manually sorting through open source repos took too long and missed good starter issues.
Change: Built issue-scout with initial filtering heuristics.
Result: Cut issue selection time in half and stopped wasting time on closed or stale PRs.

**Beat 2**
Date: October 2026
Friction: Documentation drafts sounded too robotic and didn't match my writing style.
Change: Implemented voice-guard rules to catch and rewrite overly formal AI phrasing.
Result: Maintained a consistent, natural voice across all submitted documentation and summaries.

**Beat 3**
Date: November 2026
Friction: Issues failed during testing because local development environments were out of sync.
Change: Created repro-check to enforce strict dependency and environment verification before starting work.
Result: Eliminated environment-related debugging surprises and got PRs running smoothly on the first try.

## Limitations and What's Next

What the toolkit as a whole still does not do, and what you would
build or change next. Write this section last; it will be better
after the rest.

The toolkit still lacks automated cross-repository integration testing and real-time notification hooks for status updates. Next, I would build an automated aggregator to pull progress updates across all active open-source forks into a single dashboard.

**Tool limits.** One line per featured tool, in the same order as the entries above, naming
where that tool still stops or what it still gets wrong. A small honest limit is full credit;
"none really" is not a limit. If a tool genuinely has none you can name, write `none` after
its label rather than deleting the line.

issue-scout: still occasionally miscategorizes issues with sparse descriptions.
voice-guard: struggles with technical syntax formatting inside heavy code blocks.
repro-check: none
