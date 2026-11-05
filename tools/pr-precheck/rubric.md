# Rubric: is this pull request ready to submit?

<!--
THIS IS THE PART YOU WRITE (fourth week running; this is the rubric's
final form in the sandbox). Your frame in SKILL.md executes whatever
checks you define here, via your procedure.md. It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the diff read against the plan's scope, the test
     evidence read against the plan's test plan, the description read
     against the diff, the repo-facts block's template asks) or a
     location from your references/evidence-guide.md. "The PR" is not
     a source; "the diff's changed files read against the plan's
     stated boundary" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself
     (does the diff fall inside the plan plus its deviation notes? is
     the claimed evidence observable?), never the write-up's shape
     (how long the description is, how many commits there are).
     Structure-shaped checks are what make graders disagree with
     themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (submit) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. State the `unclear`
   treatment explicitly: the frame here is YOUR SKILL.md, so a rubric
   that stays silent is only covered if your frame's grading
   discipline says what happens (the contract's own default is that
   an unverifiable claim fails).

Cover what actually gets bad PRs submitted. The failure families the
lecture named ARE the harness's scoring categories, same names as the
eval README: silent drift (the diff silently does more or less than
the posted plan, or the description claims fidelity the diff
contradicts), not tested (the evidence proves nothing observable, or
the repo's own checks were never run), unreviewable (debris or
unrelated hunks bury the change), and standards wall (the repo's
stated template and disclosure asks are ignored). Your evidence
guide's four headings map onto these one to one (plan fidelity =
silent drift, test evidence = not tested, diff quality =
unreviewable, standards and comms = standards wall), and the category
floor is scored on exactly these names plus clear accept. A rubric
that ignores a category will fail the eval packages built around
that category. And remember the honest-outcome
rule, fourth week running: a PR that honestly discloses a shortfall
can be ready; a rubric that equates "less than everything" with
"hold" fails the set.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
| --- | --- | --- | --- |
| diff-matches-plan | The diff's changed files and hunks, read against the plan's in-scope and not-in-scope statements and the plan's deviation notes | Pass if every changed file and hunk is inside the plan's stated scope or covered by a deviation note, AND every planned change that is missing from the diff is accounted for by a deviation note or an explicit disclosure in the description. Fail if the diff changes something the plan puts out of scope or never mentions with no deviation note, or leaves out a planned change with no note or disclosure | required |
| description-matches-diff | The description's claims about what the change does, read against the diff's actual contents | Pass if every claim the description makes about what the change does or covers is true of the diff, and the description does not promise anything the diff lacks. A description that honestly discloses a limitation, a deferred edge, or a deviation passes on this check. Fail if the description claims a change, a fix, a file, or a coverage the diff does not contain, or claims the work followed the plan when the diff contradicts that | required |
| test-evidence-decisive | The description's test-evidence section (or the bundle's test-evidence section), read against the plan's test plan and the reproduction steps, plus the outcome shown for the repo's own checks | Pass if the evidence shows the reproduction steps run before and after the change with the observed output (or states the behavior that changed and the expected-after), AND shows the outcome of the repo's own checks or suite as an observable result (pass count, a named passing command, or output). Evidence that covers the changed behavior by an equivalent command or output counts. Fail if the evidence is only an assertion ("tests pass", "works for me"), shows no before or no after, or shows no outcome from the repo's own checks and does not explain why they could not be run. A shortfall in evidence that the description states honestly (with the reason) passes | required |
| diff-reviewable | The unified diff and the commit list | Pass if the diff contains no debug leftovers (stray prints, debug flags), no commented-out or dead code, no unrelated formatting churn, and no drive-by edits to files or lines unrelated to the plan's change, so a reviewer sees the fix without sorting past noise. Fail if any such debris or unrelated hunk is present, or the change is buried in churn | required |
| standards-honored | The repo-facts block's stated PR template sections, contribution instructions, and policy (live: the repo's PR template, CONTRIBUTING.md, and policy), read against the description, plus any explicit maintainer direction in the issue thread | Pass if every section the repo's PR template states is filled with real content specific to this change, any explicit maintainer direction in the thread is followed or the description says why not, and the description contains the AI-use disclosure whenever the repo's stated policy explicitly requires a disclosure. Fail if a stated template section is left empty, left as placeholder text, or ignored, if the policy explicitly requires disclosure and the description omits it, or if explicit maintainer direction is ignored. A policy that only expresses a tone or authorship preference, without requiring a disclosure statement, is not tested here | required |

## Verdict rule

Accept (ready to submit) only if all five required checks pass. A single required check graded fail or `unclear` holds the PR (reject). Preferred checks, if any are ever added, never change the verdict.
