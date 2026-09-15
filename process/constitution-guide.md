Status: Current

# Writing your constitution - a guide, deliberately not a template

**Do not copy someone else's laws.** This is the one artifact in this repo you must write
yourself, and the reason is mechanical rather than sentimental: **copied laws are ceremony;
derived laws bind.**

A law works when an operator can hit it while investigating and know it forbids the thing
they were about to do - report a theory as fact, carry a withdrawn claim forward, skip the
ruled-out section because the confirmed findings feel sufficient. That only happens if the
law names something *your* practice must never do. Someone else's laws will be about someone
else's incidents, and yours will fail silently.

## The shape

- **Few.** Under ten. A law nobody can recall is not a constraint.
- **Ordered.** Earlier laws outrank later ones when they conflict, and they *will* conflict -
  say which wins before you need to know.
- **Each one a prohibition you can point at a real defect with.** If you cannot imagine the
  bug a law forbids, it is a preference, not a law.
- **Ratified before it is needed**, by whoever owns the practice. Amendments go through them.

## How to derive them

Ask what this practice would be **worse than useless** for doing. Not "what should it do
well" - what would make a requester right to stop trusting a report entirely?

Some starting questions, deliberately generic:

- What is the worst *confident falsehood* this practice could hand a requester? (Almost every
  investigation practice's first law is some form of "never assert a root cause, scope, or
  severity without the citation that supports it," because a confident wrong diagnosis is
  worse than "still investigating.")
- Who **outranks** the finding? What happens when the owner overrides a verdict?
- What must never be **silently** carried forward after it is withdrawn?
- What must the practice be honest about **regarding its own measurements** - a query window,
  a retention limit, a sample versus a census?
- Where is the **single source of truth** for an in-progress investigation, and what is
  forbidden from keeping a second, driftable copy of it?
- Who is the **requester** you report to, and what would make your report unusable to them -
  jargon, vagueness, an unstated caveat they'd only discover by acting on it?
- How does this practice **learn** - what happens to a wrong conclusion after it is caught?

Write the answers as prohibitions, order them by which you would sacrifice last, and stop.

## What makes a law load-bearing rather than decorative

The test: **can it produce a REJECT?** A law that has never rejected anything is either
perfectly obeyed or unenforceable, and you cannot tell which from the inside.

So each law should be checkable at a gate. In practice that means every verdict or report
ends with a constitution check - name each law the finding implicates, one line of evidence
it is honored, or a finding where it is not.

**And the diagnostic that tells you the laws are working as an investigative instrument rather
than a grading rubric:** *who finds the law?* If the operator hits it while drafting the
report and the adversarial pass comes back clean, the laws are bounding the work. If the
adversarial pass finds them all, the laws were not on the page when the report was written.

## Compile a law into a mechanism wherever you can

The strongest form of a law is one that cannot be violated.

- A law that says "no claim without a citation" becomes a report template with a "citation"
  column that cannot be left blank.
- A law that says "withdrawn theories never stand uncorrected" becomes the withdrawal-sweep
  step in the ladder, run every time, not remembered case by case.
- A law forbidding self-review becomes a dispatch rule: the adversarial pass is always a
  fresh-context agent, never the authoring session, enforced by which agent type is used for
  which role.

*A structural impossibility beats a review rule; a review rule beats a procedure; a procedure
beats vigilance.* Every law you can compile downward should be.

## What NOT to put in a constitution

- **Tooling preferences.** Which MCP, which query language, which dashboard. Those go in your
  operating rules.
- **Anything you would amend under mild pressure from a deadline.** If it bends when a
  requester is impatient, it was a guideline.
- **Aspirations.** "Investigations should be thorough" forbids nothing.

## After it is ratified

Cite it by number in reports, and quote the clause you are checking against rather than
paraphrasing from memory. A constraint you paraphrase is a constraint you will satisfy from
memory.

When a law turns out to be wrong, **amend it in the open** - through the owner, with the
reasoning recorded. A quietly-ignored law is worse than no law, because every report
downstream still claims to obey it.
