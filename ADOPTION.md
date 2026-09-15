# Adoption - the staged path

Status: Current

**Do not install all of this at once.** Same warning as `agent-herder`: an immune system that
only adds gates goes autoimmune - ritual, time cost, friction without catches. Adopt by
trigger, and let a real investigation earn the next stage.

The rule underneath all of it: **install a step just before the investigation that needs it,
never for a rung you have not yet run.**

---

## Stage 0 - day one, before any investigation

**Trigger: you have a queue.**

| Take | Why now |
|---|---|
| `process/the-investigation-ladder.md` | The gate sequence. Everything else references it. |
| `process/ops-doctrine.md` | Claims-carry-instrument, cite-your-sources, sweep-on-withdrawal, attack-the-hypothesis-first. These shape how every dispatch behaves from the first investigation. |
| `process/the-healing-loop.md` | How the practice repairs itself. Read once. |
| `process/constitution-guide.md` | **How to write your own.** Do not copy someone else's laws. |
| `LESSONS.md` | Read it. Adopt nothing from it as ceremony - it exists to make the doctrine's rules feel earned rather than arbitrary. |

**Cost:** an afternoon of reading, and a queue with a rung ordering that fits your actual
priority order of work.

**Do NOT take yet:** a formal report template, a verdict-landing script, a session-start hook.
None of them have anything to hold yet.

---

## Stage 1 - the first investigation that produces a hypothesis with a blast radius

**Trigger: you are about to claim a root cause, a scope, or a severity - not just a single
fact check.**

| Take | Why |
|---|---|
| `agents/responder.md`, evidence-gatherer role | Every claim carries its instrument; ruled-out theories get the same citation rigor as confirmed ones. |
| The premise-attack step of the ladder | Named out loud as a required step, before any elaborating dispatch goes out. |

**The one habit that matters most at this stage:** name the load-bearing premise out loud the
moment it forms, and ask "what would have to be true for this to be wrong, and is that cheap
to test." If it is cheap, test it before dispatching anything that assumes it.

---

## Stage 2 - the first genuinely independent adversarial dispatch

**Trigger: a hypothesis is about to be reported to someone outside this session as if it were
settled.**

| Take | Why |
|---|---|
| `agents/responder.md`, premise-adversary role | Fresh context, no shared history with the session that formed the hypothesis, told explicitly that APPROVE is available. |
| `agents/README.md`'s dispatch-mode table | The distinction that makes the adversary role actually adversarial - it is the dispatch mode, not the prompt wording. |

**Do not skip this because the hypothesis "feels" solid.** The scar this stage exists to
prevent (`LESSONS.md` #1 and #2) both happened to careful, competent work that simply never
got a genuinely independent second look before being reported as a conclusion.

---

## Stage 3 - the first time a hypothesis dies mid-investigation

**Trigger: a theory gets withdrawn or materially corrected while the document is still live.**

| Take | Why |
|---|---|
| The withdrawal-sweep step of the ladder | Formalizes what should already be habit by now: grep every place the theory was restated, in this document and any paired one, the moment it dies. |

---

## Stage 4 - the first verdict worth preserving past this session

**Trigger: an investigation's conclusion needs to survive beyond the chat transcript it was
reached in - handed to another operator, cited in a runbook, referenced in a postmortem.**

**Not built yet, and deliberately not copied wholesale from `agent-herder`.**
`agent-herder/scripts/Land-Verdict.ps1` and `Verify-Verdict.ps1` solve exactly this problem for
a build practice - extract a dispatched agent's verdict verbatim rather than hand-transcribing
it, and hash it so tampering is checkable rather than asserted - but they are wired to a
checkpoint tool (`Entire.io`) this environment does not have. When this stage is actually
triggered, adapt the pattern against what this environment actually offers: the Claude Code
session transcript under `~/.claude/projects/<project>/<session>.jsonl`, and a background
dispatch's own output file under the session's task directory. Building this before an
investigation has actually needed it would be inventing prior art nobody has used yet - the
exact failure class this kit exists to prevent, one rung over.

---

## What to install NEVER by default

- **A gate for a failure class this practice has not experienced.** Every step in the ladder
  was installed by something going wrong, on a real date, in this practice. Import the ones
  whose failure you can see coming here; leave the rest until they bite.
- **A verdict-landing script before the first verdict that needs landing.**
- **A second adversarial pass before the first one has ever rejected anything.**

## The counter-organ: count the catches

Whatever you install, count what it catches. A step that has caught nothing in a month of
real investigations is a pruning candidate, and retiring it should be as deliberate as
installing it was.
