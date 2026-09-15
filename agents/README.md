Status: Current

# Agent types

One agent definition so far: `responder.md`. It describes two ROLES, not two agent types -
the same brief shape (verify state directly, cite everything, honest-stop on contradiction)
governs both, and what changes between them is the **dispatch mode**, which is the load-bearing
distinction the whole kit hangs on.

| Role | Dispatch mode | Can it reject the premise? |
|---|---|---|
| Evidence gatherer | A fork, or any dispatch that shares context with the session that formed the hypothesis | No - by construction, and that's fine, that's not its job |
| Premise adversary | A fresh-context agent, no shared history, handed the hypothesis explicitly as a claim under review | Yes - that is its ONLY job |

Never use an evidence-gathering dispatch where the brief needs premise-rejection to be a live
outcome. The dispatch mode enforces the distinction; a well-worded prompt to a fork does not,
because the fork still inherited the premise along with the rest of its context.
