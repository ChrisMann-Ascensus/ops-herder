Status: Current

# INVEST and its provenance - two documents, never one

The investigation ladder's last gate is "verdict + disposition, reported to the requester."
This is what that gate actually produces: **two artifacts, not one**, with different jobs and
different readers. Collapsing them into a single document costs you whichever job the surviving
document does worse.

## Naming: INVEST, not "RCA"

The polished output artifact is called **INVEST**. Not "RCA" - that is a different practice's
own label, carrying that practice's connotations (a leadership-facing bar, a particular
organizational weight) this doctrine has no business forcing onto whoever adopts it next.
INVEST is deliberately practice-agnostic, chosen the same day this doctrine's own author caught
themselves defaulting to "RCA" out of habit and corrected it directly - worth naming as its own
small scar (see below), not smoothed over.

## The two artifacts

**INVEST.** The polished conclusion: executive summary, impact, root cause with its citation,
what was ruled out with its citation, disposition. Written for the person who needs the answer,
not the archaeology - a platform team accepting a handoff, an owner deciding priority, a
requester who filed the original ticket. Short enough to read in one sitting. Trimmed on
purpose: a dead end that added nothing belongs in the other document, not this one.

**The Provenance.** The full working record: every pass, every number, every dead end, every
correction, in the order things actually happened. Deliberately not trimmed. Redundant with
INVEST, and with itself, on purpose - the same fact stated in two places is a feature here, not
a defect, because the document's job is to survive being picked up cold, by a skeptical
reviewer, a platform-team engineer checking a specific claim, or this same practice months later
with no memory of the session that wrote it. If something got checked and killed, checked and
confirmed, or checked and left honestly unresolved, it is in here - "drop nothing on the floor"
is the whole design goal.

**Why two, not one, and not zero:** INVEST alone cannot satisfy Law 3 (citation and instrument)
or Law 9 (verification honesty) durably - it has room to *state* a citation but not to preserve
the full trail a citation claim rests on, including the parts that were wrong before they were
right. A Provenance alone fails its actual reader - nobody accepting a handoff wants to read the
dead ends before the answer. Neither document can do the other's job without degrading its own.

## Structure on disk

One folder per investigation that clears the "full ladder" bar (see
`the-investigation-ladder.md` on right-sizing - a single-fact check does not need either
document):

```
<date>-<short-title>/
    invest.md
    provenance.md
```

Cross-link both directions: INVEST's citation section points to `provenance.md` for the full
trail; the Provenance's own header names the INVEST it is a companion to. Neither survives being
read in isolation as well as the pair does.

## What goes in the Provenance, concretely

Everything the citation pass and the withdrawal sweep produced, not summarized further:

- Every hypothesis, including the ones withdrawn - kept in place with their withdrawal reason,
  never scrubbed, same as the constitution's own Law 8 requires of the working record generally.
- Every ruled-out theory with its citation, at the same rigor as confirmed findings.
- Every number, with its instrument (Law 3) - the query, the window, the retention limit.
- A record of the practice's own mistakes made *during* the investigation, if any, and how they
  were caught - this is not embarrassing detail to omit, it is evidence the ladder's own gates
  are actually catching things, which is the entire point of running them.
- Full text of any adversarial dispatch's reasoning, not a paraphrase of its conclusion alone -
  a verdict-only summary of a SAAR pass loses exactly the part someone might need to check later.

## The scar this document exists to fix

*2026-09-16, the same TLS-reset investigation `LESSONS.md` #2-#7 already cite.* A closed,
already-handed-off report got a second look the next day, purely as an adversarial premise-attack
exercise on a *closed* finding (not a new incident - the practice re-attacking its own settled
work). That second look reproduced the failure in a new environment, ran a real experiment that
killed a specific alternative theory, and - critically - **caught a wrong intermediate result
(a data-analysis indexing bug that had produced a false "0 failures" conclusion) only because a
teammate looked at raw output and asked "are you confident?"** That catch survived because the
raw numbers were still sitting in the working record; if the only surviving artifact had been a
polished conclusion with the wrong number already smoothed into prose, there would have been
nothing to check the claim against. The provenance log written for that investigation was built
*after* this had already happened once informally - this document exists so the next practice
gets the artifact on day one instead of after its own near-miss.

A second, smaller scar in the same investigation, caught in real time while drafting *this very
document*: the polished artifact was first named "the Verdict," reasonable enough on its own,
then reconsidered mid-draft by the practice owner directly in favor of a cleaner,
purpose-built name with zero baggage from any other practice - **INVEST**. Worth naming
honestly rather than presenting the final name as if it arrived fully formed, since that is
exactly the kind of smoothing-over this whole document argues against doing to a working record.

**Ruling, by the practice owner, same day: INVEST is the name going forward, and the first
instance is deliberately NOT renamed.** `junk-drawer/rcas/09-15-recaptcha-tls-resets/rca.md`
keeps its original name permanently, on purpose - not a pending cleanup, a standing decision.
Two reasons, stated directly by the owner: provenance (this document's whole argument is
"don't scrub the record of how a decision was reached" - retroactively renaming the first
instance would do exactly that to the naming decision itself), and because "RCA" at Ascensus is
not merely a casual industry term there - it names a real, formally-weighted document type in
that shop, distinct from this doctrine's own practice-agnostic INVEST. The first artifact
correctly wearing that name is itself part of the record of why a neutral replacement was
needed. Every INVEST after it uses the new name; the one that came before the name existed
keeps the name it actually had.
