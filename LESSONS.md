# Lessons, each with the scar that earned it

Status: Current

Every rule here was paid for, in this Team Gold DevOps troubleshooting practice, not ported
from someone else's postmortem. A rule without its scar is a Chesterton's fence awaiting
pruning - if you cannot imagine a scar happening to you, that rule is a pruning candidate
rather than a commandment.

---

## 1. Self-review under a review label is not adversarial review

A session that writes a document and then reviews its own document, however honestly it
labels the pass as "review," produces confirmation of what it already believed - not because
it is dishonest, but because it cannot see the premise it built the document on.

*Scar: 2026-09-01/02, a New Relic housekeeping audit. Design, spec, and plan documents were
each self-reviewed by the authoring session, "given this is a two-person project." A
genuinely independent, fresh-context dispatch against the same three documents - no shared
context with the author - returned REJECT on all three: 3, 4, and 3 Majors respectively that
self-review had missed. One finding was a cited "exact duplicate" alert-policy pair that, on
live re-verification, turned out to be two differently-named policies - a factually wrong
finding the self-review had accepted at face value. A defect class (findings recorded with no
disposition-table row) recurred in a section a fix round never re-swept.*

**Corollary: the delta re-review needs the same scrutiny as the original.** The fix for one
Major (removing a false duplicate-policy claim) accidentally reintroduced the exact defect
class of another Major (an orphaned finding with no disposition row) by deleting the row
entirely instead of correcting it. A fix creates its own new surface; a delta pass that skips
adversarial scrutiny on the fix itself will miss that.

## 2. Attack the hypothesis before elaborating it

Once a hypothesis forms, the next move tests the hypothesis, not its consequences. A fork
inherits the premise along with the context and is structurally unable to reject the
assumption that framed its own task.

*Scar: 2026-09-15, a production TLS-reset investigation. The hypothesis "an estate-wide
synchronized onset on 2026-09-04" formed early. Two forks were dispatched to hunt what changed
on 09-04 (deploy history, mesh/egress configuration) - both did careful, competent work, and
both presupposed the onset was real. Zero effort went to testing whether the onset was real.
When a fresh adversarial dispatch finally ran, it broke the premise on its first query: log
retention reached three weeks further back than the window used, and the "estate-wide" step
was two apps carrying 84 percent of the volume while the rest of the estate showed no step at
all. Roughly two of three agent-hours had gone into elaborating something false.*

## 3. Claims carry their instrument, or they are not claims

A number without its window, retention, aggregation, and dedup rule is not yet a claim - it is
the shape of whatever query produced it.

*Scar: the same 2026-09-15 investigation produced five separate wrong conclusions from
reporting measurement artifacts as system properties in a single pass: a "20/day baseline"
that was an artifact of where the query window started (the true peak, once retention was
checked, was 60x higher on an earlier date); "8 app families" that became "30-plus" once the
query stopped scoping to one team's log space; an app's apparent error onset that was
plausibly a logging-visibility artifact of its own deploy rather than a new failure; raw
counts that needed halving because the pipeline double-logs each failure; and a scope claim
that had to be widened twice before it stopped changing.*

## 4. Sweep on withdrawal - withdrawing a theory in one place does not strike it everywhere

A theory rarely lives in only one place. It gets restated as a "leading hypothesis," folded
into a "next step," said out loud in chat after the point it should have died.

*Scar: the same investigation's "shared egress / proxy / SASE" hypothesis was tested and
explicitly marked WITHDRAWN, with its reason, in one block of the working document. A
"Leading hypothesis" section 120 lines later, in the same document, kept presenting that
identical, already-withdrawn theory as the live lead - never touched when the withdrawal
happened, and repeated out loud in chat afterward. Caught only when a full re-audit was
applied retroactively - which should not have been necessary to catch a direct
self-contradiction sitting in one file.*

## 5. Verify at the primary source, not a convenience field that looks like the answer

A field that is cheap to read is not the same as the field that is actually authoritative.

*Scar: an early pass in the same investigation read a Kubernetes pod's
`kubectl.kubernetes.io/restartedAt` annotation as the pod's start time and concluded "no
application change explains it, pods last restarted 2026-08-02." That was wrong: the
annotation is a stale pod-template value carried forward from an unrelated prior rollout.
`creationTimestamp` and the Deployment's `Progressing.lastUpdateTime` showed the actual pods
were created 2026-09-09, and an Octopus release record showed a deploy at 2026-09-09 20:12 UTC
- about 4 hours 45 minutes before that app's own local error onset. The wrong conclusion stood
until someone checked the primary source instead of the convenience field.*

## 6. Widen scope before concluding

The person who reported a problem noticed it from inside their own scope; a report that only
widens as far as the original complaint will understate breadth every time.

*Scar: the 2026-09-15 investigation started as "SSL errors in one app's logs, in one Kibana
space" and was reported at first as affecting roughly 8 app families. Widening the query to
every space in the same cluster found 30-plus affected families and a materially earlier true
onset. The first, narrower report was not dishonest - it was simply never widened before being
treated as a conclusion.*

## 7. Cite your sources, confirmed and disproven alike

A theory offered without evidence is a guess dressed as a finding - true of a confirmed
theory and, less obviously, just as true of one that was checked and ruled out.

*Applied directly in the 2026-09-15 investigation's write-up: "not a certificate problem" was
backed by "zero certificate-validation errors in 30 days, every hit the same TLS-reset chain
with no expiry, name-mismatch, or chain error" - the same citation discipline the confirmed
findings (a named stack trace, a named request path, a per-day failure count) already carried.
A "ruled out" section without that same rigor would have been the easiest place to cut the
corner, precisely because a negative result feels like it needs less proof than a positive
one.*

## 8. INVEST and its provenance are different documents with different jobs

A polished conclusion and a full working record cannot be the same document without one of them
losing its job. The polished one needs to be short enough that a handoff reads it; the working
record needs to keep every number, every dead end, and every correction, precisely because it
will get checked later against a claim someone doubts.

*Scar: 2026-09-16, a second look at an already-closed, already-handed-off TLS-reset report -
attacking its own settled premise, not investigating a new incident. That second look caught a
wrong intermediate result (a data-analysis indexing bug that had produced a false "0 failures"
conclusion) only because a teammate looked at the raw numbers still sitting in the working
record and asked "are you confident?" If the only surviving artifact had been the polished
conclusion, with that number already smoothed into prose, there would have been nothing left to
check the claim against. See `process/invest-and-provenance.md`.*

**Corollary, same investigation, caught in real time:** the polished artifact was first named
after this practice's own borrowed term, "RCA" - a different practice's label, with that
practice's connotations, no business being forced on whoever adopts this doctrine next. Renamed
to **INVEST**, a practice-agnostic name built for this doctrine specifically, after the
practice owner caught the habit mid-draft. Worth recording as its own lesson: **a borrowed name
is itself a Chesterton's fence** - it will not visibly break anything, right up until someone
else tries to adopt the doctrine and inherits vocabulary that was never theirs to inherit.

## 9. A rung-sorted queue beats a first-in-first-out queue for triage

Incoming work sorted by a small number of standing priority rungs, with the highest live rung
worked next, surfaces what actually matters faster than working items in arrival order -
because arrival order has no relationship to blast radius, deadline, or who is blocked on the
answer.

*Applied as a standing convention rather than a single scar: a real-time working queue,
maintained under the same rung ordering every day, with completed items checked off and moved
into a "recently done" section in the same edit that closes them - never left sitting inside a
live rung looking unfinished.*
