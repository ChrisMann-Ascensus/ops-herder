Status: Current

# The investigation ladder - the gate sequence, and what each gate exists to catch

Each gate attacks a **different failure class** at the cheapest point that class is
catchable. Sending one gate's brief to another gate produces a spelling check.

```
intake, sorted by rung
    → hypothesis forms
    → PREMISE ATTACK (fresh adversarial dispatch - before any elaboration)
    → evidence gathering (parallel legwork, only after the premise survives)
    → citation pass (confirmed AND ruled-out, each with its instrument)
    → withdrawal sweep (if anything died, grep every document that cited it)
    → verdict + disposition, reported to the requester
    → closeout
```

**Right-size first.** A single-symptom, single-system question ("is this cert expired") takes
one responder and a citation, not the full ladder. The full ladder is for anything that
produces a hypothesis with a blast radius - a claimed root cause, a claimed scope, a claimed
severity - because those are exactly the claims that get repeated to other people afterward.

## The gates, and their distinct failure classes

| Gate | Attacks | The class it catches | Scar |
|---|---|---|---|
| **Premise attack** | the HYPOTHESIS ITSELF, before anyone elaborates it | A theory assumed true because it was only ever built on top of, never tested against | TLS reset: "estate-wide 09-04 onset" stood unattacked while two forks spent two of three agent-hours elaborating it |
| **Evidence gathering** | the SYSTEM, once the premise survives | Legwork that never happens because everyone assumed someone else checked | (expected, unremarkable when it runs after the premise attack) |
| **Citation pass** | EVERY CLAIM in the report, confirmed or ruled out | A claim standing on a window, a retention limit, an aggregation, or a dedup rule that isn't stated alongside it | TLS reset: a "20/day baseline" was an artifact of where the query window started; retention actually reached three weeks further back and the true daily peak was 60x higher |
| **Withdrawal sweep** | the WHOLE DOCUMENT SET, not just the paragraph being corrected | A withdrawn theory recycled elsewhere as if still live | TLS reset: the withdrawn "shared egress/SASE" hypothesis was restated as a live "leading hypothesis" 120 lines later in the same file |
| **Verdict + disposition** | the REPORT going to the requester | Reporting a measurement artifact as a system property; declaring scope/severity before the net was widened | TLS reset: "8 app families" became "30+" once the query stopped scoping to one Kibana space |

## Premise attack is the headline gate, and it goes first

**A fork inherits the premise along with the context.** Forks are excellent for parallel
legwork and constitutionally incapable of rejecting the assumption that framed their own
task - the same fact `agent-herder`'s design review states about unquestioned premises
applies here with more force, because an investigation's premise usually forms mid-session,
informally, and nobody names it as a claim under review.

Only a **fresh-context agent, handed the conclusion explicitly as a claim to attack**, can
reject the premise. That is a difference in dispatch mode, not prompt wording:

- **Elaborating dispatch (fork or otherwise):** "given that X happened on date D, find out
  what changed on D." This dispatch cannot produce "X did not happen" as an output, because
  its brief assumes X.
- **Adversarial dispatch:** "here is the claim that X happened on date D, with its supporting
  numbers. Attack it. An APPROVE - the claim holds - is an available, genuine outcome."

**Sequencing: adversary first, elaborating forks second.** This is the reverse of what feels
natural, because elaboration feels like progress and premise-testing feels like delay.

## The citation pass covers ruled-out theories as rigorously as confirmed ones

A "ruled out" section is not optional garnish. "Not a certificate problem" is not a citation.
"Zero certificate-validation errors in 30 days: no expiry, no name mismatch, no chain errors -
every hit is the same chain, TLS handshake reset, not a bad cert" is. The discipline is
identical for a confirmed finding and a disproven one; skipping it on the disproven half is
the easier place to cut the corner, which is exactly why it needs saying.

## The withdrawal sweep is a distinct step, not a side effect of the citation pass

Withdrawing a hypothesis is a point-in-time edit unless something sweeps for its dependents.
A theory rarely lives in only one place - it gets restated as a "leading hypothesis," folded
into a "next step," said out loud in chat after the point it should have died. The moment a
theory is withdrawn:

- `grep` the current document for its name or key terms - an app, a mechanism, a date - to
  find every place it was asserted, not just the block being corrected.
- Check every other document that cites the same investigation. A queue entry and its paired
  memory or runbook are separate documents that drift out of sync with each other, not just
  within one file.
- If the theory was said out loud after it should have been withdrawn, say so plainly when
  corrected - don't just quietly fix the file.

## Where the human belongs

Same answer as `agent-herder`: the loop is human-supervised by design, not by gap. "Stop the
investigation, this doesn't smell right" is an immune response no gate is watching for, and
the arbiter above every gate is the owner. Adversarial review is blind to unquestioned
premises for the same reason a reviewer is blind to them in a design - it rejects what is on
the page and cannot reject the assumption that put it there. That is why the premise-attack
gate exists as a **separate, earlier** step rather than being folded into "review" generally.
