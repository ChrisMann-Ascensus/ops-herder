Status: Current

# The Healing Loop

Companion to [the constitution](../constitution.md) (see also `constitution-guide.md`, how it
was derived). The constitution is what this practice must never do; the Healing Loop is the
metabolism - how the practice that
runs investigations repairs and hardens itself. Adapted from `agent-herder`'s Healing Loop,
which named the same mechanism for a build practice; this is the same loop pointed at
diagnosis instead of construction.

## The observation that started it

As an investigation practice matures, the failure surface migrates UP the stack: from "was the
cert actually expired" (a fact check), to "was the theory ever tested" (a premise problem), to
"did the correction reach everywhere the theory was restated" (a coordination problem), to
"do we even know what a claim's own instrument was" (an epistemics problem). The operators
barely miss individual facts; the misses live in what got assumed, what got left uncorrected,
and what got reported without its measurement caveat.

Two things sharpen this compared to a human on-call rotation:

1. **Every dispatched agent is a new hire on day one.** A subagent accumulates no experience
   across dispatches. Only what is WRITTEN persists - in the investigation's own document, in
   memory, in a runbook. Process here is not bureaucracy layered on top of the work; it IS the
   institution, because the workforce evaporates at the end of every session.
2. **A skeptical second opinion is cheap here in a way it never is on a human on-call
   rotation.** A genuinely independent, fresh-context review costs one dispatch. That flips the
   constraint from "who can we spare to double-check this" to "have we actually designed a
   check for this failure class" - so the system should optimize for gates that catch classes
   of wrong conclusion, not just this investigation's instance of one.

## The loop

Every failure, at every altitude (a fact, a premise, a citation, a correction, the report
itself), gets the same four-step treatment:

1. **Classify to the CLASS, not the instance.** "The onset date was wrong" is an instance.
   "A query window was mistaken for the system's actual retention, and nobody tested whether a
   wider window would change the conclusion" is the class. Naming a class means you would
   recognize its next occurrence in a completely different investigation.
2. **Install a mechanical guard at the cheapest layer that could have caught it.** A standing
   step in the ladder (premise attack, citation pass, withdrawal sweep) beats a reminder; a
   reminder beats vigilance. Prefer guards that fire automatically as part of the process shape
   over guards that require someone to remember to apply them.
3. **Give the guard binding authority.** An adversarial premise-attack that can be overruled by
   the session that formed the hypothesis is not a guard, it is theater. A REJECT on a
   hypothesis is binding until the owner rules otherwise, in writing.
4. **Write it into the institution.** `ops-doctrine.md`, `LESSONS.md`, the queue's own
   maintenance convention, the agent definition. The written system is the only system that
   survives the session ending.

## The preconditions (why the loop works)

- **Honest-failure framing.** A withdrawn hypothesis, a REJECT on a claim, an operator's own
  disclosed miss - all named SUCCESS outcomes - are what let an investigation surface its own
  wrong turns instead of hiding them. A blame-shaped practice hides exactly the signal healing
  requires.
- **Adversaries at every altitude**, not just at the end. Premise attack before elaboration;
  citation pass on the whole report; withdrawal sweep across every document; verdict review
  before it reaches the requester. Each catches a different failure class at the cheapest
  point that class is catchable.
- **Executable knowledge, where it can be.** A lesson that only lives in prose defends nothing
  once the session that learned it is gone. Where a lesson can become a step in the ladder or
  a line in a report template, it should.
- **One doctrine, independently re-derivable.** If two separate investigations, worked by
  different sessions, land on the same correction without coordinating, the doctrine is real.

## The honest edges

- **Nothing prunes by default.** A gate that only ever adds ceremony without ever catching
  anything is a pruning candidate, reviewed with the same deliberateness it was installed with.
  A young practice adopting this should watch this edge hardest: start with the right-sized
  subset (`ADOPTION.md`), let real investigations install the rest.
- **The loop is human-supervised, and that is a design choice, not a gap.** "This doesn't smell
  right, stop" is a human immune response no gate is watching for; the arbiter above every gate
  is the owner.
- **Rules bind only where they are structural.** A prose rule binds an agent that reads it; a
  dispatch-mode distinction (adversary vs. elaborating fork) binds regardless of who reads the
  prose. Where a rule can be made structural rather than remembered, it should be.
