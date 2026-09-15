# Ops Herder

Status: Current

**The prior art a troubleshooting / incident-response practice needs on day one, so it does
not pay the founding tax twice.**

Sibling to [`agent-herder`](../agent-herder), same author, same MIT license, deliberately a
**separate repo, not a shared module**. Clone it, submodule it, or drop it in wholesale.

## Why this is not just agent-herder with different words

`agent-herder` is a **build** doctrine: design → spec → plan → implement → review → CI. Its
unit of work is a diff, its failure classes are things like "the reviewer found the law, not
the author" and "obligations dropped between rungs."

This is an **investigation** doctrine: intake → hypothesis → attack the hypothesis → gather
evidence → cite it → report a verdict → disposition. Its unit of work is a *claim about a
system that already exists and that you did not build*, its failure classes are things like
"the premise was never tested, only elaborated" and "a withdrawn theory kept living somewhere
else in the same document."

Those are different skills. A build reviewer asks "does this diff do what the spec says." An
investigation reviewer asks "is the thing you believe actually true, and would you have caught
it if it weren't." Trying to run both out of one doctrine either buries the investigation
rules under build-specific ceremony (TDD, PR ladders, a `car` agent that commits to a branch)
that an incident response has no use for, or waters down the build rules to fit both. Separate
repos keep each doctrine legible to the role that actually uses it.

## The problem this exists to kill

Same shape as `agent-herder`'s: **rules travel, exemplars do not, and a rule without a scar
is a Chesterton's fence.** An investigation practice that only writes down "cite your
sources" without the story of the theory that shipped without one will prune that rule the
first time citing sources feels slow.

> **The founding incidents.** A New Relic housekeeping audit (2026-09-01/02) ran its design,
> spec, and plan review as **self-review** - one session writing the document and reviewing
> it, labeled "review" but never adversarial. A genuinely independent, fresh-context dispatch
> against the same three documents found 3, 4, and 3 Majors respectively that the
> self-review had missed, including one finding that was **factually wrong on
> re-verification** and a defect class (missing disposition rows) that recurred in a section
> a fix round never re-swept. Two weeks later, a production TLS-reset investigation
> (2026-09-15) let a hypothesis - "an estate-wide synchronized onset on 2026-09-04" - stand
> unattacked while two forks spent roughly two of three agent-hours elaborating it. A fresh
> adversarial dispatch broke it on its first query: log retention reached three weeks further
> back than the window used, and the "estate-wide" step was two apps carrying 84 percent of
> the volume while the rest of the estate showed nothing. The same investigation's own
> withdrawal of that hypothesis then sat contradicted, uncorrected, 120 lines later in the
> same document, because striking a theory in one place does not strike it everywhere it was
> restated.

That is the class: **a hypothesis elaborated instead of attacked, and a correction that does
not propagate.** Its cheapest fix is prior art someone already paid for, written down before
the next investigation needs it.

## What is in here

| Directory | What it is |
|---|---|
| `constitution.md` | **Ratified 2026-09-15.** Ten laws, each traced to a real scar or an independently-found gap. Read this first - it is the one document in here derived for this specific practice, not general-purpose doctrine. |
| `process/` | The operating rules - the investigation ladder, the doctrine, the healing loop, the constitution guide. **Rules.** |
| `agents/` | The `responder` agent type: the evidence-gathering role and the premise-adversary role, and why they must never be the same dispatch. |
| `LESSONS.md` | Every lesson, with the scar that earned it. Read this before adopting anything. |
| `ADOPTION.md` | **Start here.** The staged path, and what NOT to install yet. |

No `templates/`, `hooks/`, or `scripts/` yet, on purpose - see `ADOPTION.md`. This kit does
not build artifacts for rungs it has not run, and this practice has not yet run a rung that
needs a worked exemplar, a session-start hook, or a durable verdict-landing script.
`agent-herder/scripts/Land-Verdict.ps1` is the pattern to adapt when that day comes; it is
wired to a checkpoint tool this environment does not have, so it needs real adaptation, not a
copy-paste.

## What this is not

- **Not a framework.** Documents and one agent definition. Nothing here executes anything.
- **Not a replacement for judgment.** A REJECT on a hypothesis is a success outcome, and the
  owner is always the final arbiter, same as `agent-herder`.
- **Not finished.** Rungs this practice has not yet run are marked honestly in `ADOPTION.md`.
  Building an artifact for a rung nobody has run yet is inventing prior art you do not have -
  the same failure this repo exists to prevent, one rung over.

## Provenance and honesty

Every scar in `LESSONS.md` happened in this practice, on these two dates, in this Team Gold
DevOps troubleshooting work - not ported from someone else's postmortem. Where a lesson is
untested outside its origin, it says so.
