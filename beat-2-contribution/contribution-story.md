# Contribution: Music : Add a boom bap drum pattern

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Zamijah Shakeur-Tompkins
**GitHub Username:** zami116
**Issue:** https://github.com/Babali42/DrumBeatRepo/issues/537
**Pull Request:** [GitHub PR link, once opened]

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 9: Turned issue-select into issue-scout and tested it on real repos**

I built issue-scout from my unit 5 skill by adding a fit profile and a search strategy with four gh queries and ranking filters. My first scan rejected all five candidates on Maintainer alive, and I planned to widen my 14-day window, but regrading #75 showed the real cause: the scout's comment listing was cut off at 15 comments and hid two collaborator replies. A later grade also called a claim "within 6 months" when it was about 15 months old, so I now read every evidence line before touching the rubric, which I left unchanged. My queries were pinned to the Path Review repo, so I took candidates from the Issue Selection site and graded them, and the scout accepted DrumBeatRepo #537, which I claimed.

**Unit 10: Installed the voice guard and patched my scout's scope check**

I added Upstream rules for claims, questions and pings to my voice guide, written from what happened on #537, and installed the guard hook. My first wiring test failed: `gh issue comment --help` ran instead of being stopped, and the guard log had no hook lines. The hook only watched Bash, but Claude Code on Windows can run commands through a PowerShell tool, so I widened the matcher in settings.json and the check in check_voice.py (with Claude Code's help, and I diffed it against the course copy). The same test now stops with "no body the guard can read," and I run the manual check on drafts I post from the browser. I also wrote CLAUDE.local.md for the DrumBeatRepo clone.

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I started with my scout on the Path Review repo: four queries returned 51 open issues, 35 survived my filters, and all five top candidates were rejected on Maintainer alive. When I regraded #75, I found the scout's comment listing had been cut off at 15 comments and hid two collaborator replies, so those rejects were unreliable. Because my queries were pinned to one classroom repo, I took candidates from the Issue Selection site instead and graded nine issues across Altinn, MaterialX, WebDevTools, dialogporten and DrumBeatRepo. Three were accepted: Altinn #12123 and DrumBeatRepo #537 and #270. I rejected #12123 for my own reasons: Altinn Studio's README lists Docker Desktop as a prerequisite and I don't have Docker, which my rubric can't see. #270 is a standing contribution guide that isn't meant to be closed, so it wasn't a single task.

I chose #537 (add a boom bap beat to DrumBeatRepo). The scout accepted it on 2026-11-03 with a moderate difficulty note: one beat file plus a metadata entry, no Docker, and it runs in a Codespace. The closed PR #557 showed me what was missing (the beat file, not just the metadata), and Babali42 answered my claim within hours with a step-by-step workflow. After I claimed, a regrade rejected it, but only on Unclaimed, because the scout counted my own claim comment as a live claim; I chose it anyway and I can explain why. It's a weak fit for my profile (the scout called it "not Python, testing or backend work"), but it is a bounded, reproducible task with a responsive maintainer. I hope to learn how a maintainer wants a contribution shaped and his DAW-to-JSON workflow for beats. Music design and production is one of my many interests, and this issue will allow me to experience the work that goes behind some music applications for when I start creating my own. Claim comment: [https://github.com/Babali42/DrumBeatRepo/issues/537#issuecomment-6619304869](https://github.com/Babali42/DrumBeatRepo/issues/537#issuecomment-6619304869) (posted 11/3/2026).

My honest read of the scout: it held up on maintainer, repo and scope evidence, but it fell short three times on real repos. It truncated comments, it misdated a claim by about 15 months, and it can't tell my own claim from a stranger's. It also never checks setup cost like Docker, so I now read each evidence line and check setup by hand before choosing.

**Toolkit**

- Tool: issue-scout, with my four-query strategy and my rubric, plus manual pre-screening of candidates
- What it produced: a scan of Path Review (51 found, 35 after filters), graded read-outs for nine site picks, and an accept on #537 with a "moderate" note after my scope patch
- Difficulties: truncated comment lists, a date misread on #12000, queries pinned to one repo, no check for setup cost (Docker), and #537 rejected on regrade because it counted my own claim
- What changed: I replaced my Scope fits you check with the staff scope-feasible row and added the difficulty note, logged in scan-notes.md. I left Unclaimed as is.

---

## Understanding the Issue

**Problem Description**

[In your own words, what is broken or missing?]

**Expected Behavior**

[What should happen?]

**Current Behavior**

[What actually happens?]

**Affected Components**

[Which parts of the codebase are involved?]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Reproduction Process

**Environment Setup**

Windows 11, Edge 157. I ran the app in a GitHub Codespace on my fork (zami116/DrumBeatRepo), branch main, commit e1da92a, Node v24.22.1. I forked Babali42/DrumBeatRepo, synced main, then used Code, Codespaces, Create codespace on main. The dev server started on its own and forwarded port 4200. Challenges: the Ports tab was empty at first and I thought I needed to start the server myself, but it came up on its own once the build finished.

**Steps to Reproduce**

1. Fork Babali42/DrumBeatRepo, sync main, and create a Codespace on main.
2. Open the forwarded app on port 4200.
3. Choose "Hip-Hop" in the genre dropdown and open the beat dropdown.
4. Observed: the list shows only "Hip-Hop: double kick offset", "Trap" and "Jul type beat". There is no Boom Bap.

**Reproduction Evidence**

- **Commit showing reproduction:** none
- **Screenshots/logs:** `ls frontend/src/assets/beats/hip-hop` at e1da92a: hiphop.json, jul.json, trap.json. `git ls-files | grep -i boom`: no output. `grep -c -i boom frontend/src/assets/beats/beats-metadata.json`: 0.
- **My findings:** Boom Bap is missing, as the issue says. It needs both a beat file in hip-hop/ and an entry in beats-metadata.json, which matches Babali42's note on #557 that a metadata entry alone would not work. Upstream main is 3 commits ahead (a jazz beat) and still has no Boom Bap. Reproduction is done and I'm starting on his workflow: listen to the existing samples, then sketch the pattern in LMMS.

**Toolkit**

- Tool: repro-check, run on my claim draft and my repro report
- What it produced: a reject at first, on behavior-matches only, because my screenshots were linked by local file paths a stranger can't open. After I replaced them with command output it accepted, with all five checks passing, and it verified my commit and the hip-hop folder against the live repo.
- Difficulties: its suggested fix assumed I would post the report on the issue, but my assignment says the PR carries the proof.
- What changed: screenshots became ls and grep output, I wrote full paths, and I added a line tying the report to the maintainer's workflow.

---

## Solution Approach

**Analysis**

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
