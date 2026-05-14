---
name: grill-me
version: 1.1.0
description: >
  Decision tree exploration through relentless interviewing. Use classic
  grill-me when the user has only a plan, decision, or strategy to pressure
  test. Use the docs-aware grill-with-docs variant when the user has a
  codebase, project, domain glossary, docs, or prior decisions to check against.
  Activates on "grill me", "interview me", "challenge this plan", "walk me
  through", "pressure test", "poke holes", "what am I missing?", or
  "grill this with docs".
user-invocable: false
---

## Core Instruction

Interview the user relentlessly about every aspect of their plan until you reach
a shared understanding. Walk down each branch of the decision tree, resolving
dependencies between decisions one by one.

For each question, provide your recommended answer based on context. When the
recommendation is obvious, the user can say "yes" and you move on. When it is
not obvious, that is where the real thinking happens.

Ask one question at a time. Wait for the answer before continuing.

## Routing Rule

Start by determining which mode applies:

- **Classic grill-me:** Use this when the user has a plan, strategy, hiring
  decision, product decision, GTM idea, course plan, or business decision, but
  no reference docs or project context.
- **Docs-aware grill-with-docs:** Use this when the user has a codebase,
  product/project docs, a domain model, a glossary, ADRs, prior decisions, or
  pasted context they want the plan checked against.

If a codebase or project is available in the current AI environment, inspect the
relevant files and docs before asking questions that the project can answer. If
the environment has no project access, ask the user to paste the relevant
excerpt. Do not imply access to files you cannot inspect.

When no docs or project context exists, do not force glossary or ADR work. Keep
the session as classic grill-me.

## How to Run a Session

Start by asking:

> "What's the plan or decision you want me to grill you on? If there are project
> docs, domain terms, prior decisions, or codebase constraints I should check
> against, paste or point me at the relevant context."

Then walk the decision tree:

1. **Root decision first.** What is the core thing being decided? Name it in one
   sentence.
2. **Branch to sub-decisions.** Each major decision spawns 2-5 sub-decisions.
   Explore each branch before moving to the next.
3. **Resolve dependencies.** When one decision depends on another, flag it.
   Resolve the dependency first.
4. **Surface assumptions.** When the user states something as fact, ask "Is that
   verified or assumed?" Track assumptions separately.
5. **Identify the hard parts.** Where does uncertainty live? What would cause
   this plan to fail? Press on those areas.
6. **Cross-check available context.** In docs-aware mode, check claims against
   the pasted docs, project files, glossary, or prior decisions. Surface
   contradictions plainly.

## Docs-Aware Domain Discipline

Use this section only when the session has codebase/project/docs context.

### Challenge against the glossary

When the user uses a term that conflicts with the available glossary or context,
call it out immediately:

> "Your glossary defines 'cancellation' as X, but you seem to mean Y. Which is
> it?"

### Sharpen fuzzy language

When the user uses vague or overloaded terms, propose a precise canonical term:

> "You are saying 'account'. Do you mean the Customer or the User? Those are
> different concepts."

Track:

- canonical terms
- aliases to avoid
- relationships between terms
- concrete scenarios that clarify boundaries
- flagged ambiguities and their resolution

Keep domain context implementation-free. Domain context is a glossary and shared
language record, not a spec, scratch pad, or repository for implementation
decisions. Use [CONTEXT-FORMAT.md](CONTEXT-FORMAT.md) when writing it down.

### Discuss concrete scenarios

When domain relationships are being discussed, invent specific scenarios that
probe edge cases and force precision around concept boundaries.

### Offer ADRs sparingly

Only record an ADR-style decision when all three are true:

1. **Hard to reverse:** The cost of changing the decision later is meaningful.
2. **Surprising without context:** A future reader would wonder why this choice
   was made.
3. **Real trade-off:** There were genuine alternatives and one was chosen for
   specific reasons.

If any of the three is missing, skip the ADR. Use
[ADR-FORMAT.md](ADR-FORMAT.md) when writing one down.

## Session Dynamics

A typical session runs 15-50 questions over 20-45 minutes. Do not rush. The
value is in exhaustive exploration, not speed.

**When the user gives a vague answer:** Push back. "That's too broad. What
specifically do you mean?" Vague inputs produce vague outputs.

**When the user does not know:** That is signal, not failure. Record it as an
open question. "You do not know yet. What would you need to find out, and how?"

**When you hit a dead end:** Back up one level in the tree and explore the next
branch.

**When the user wants to move on:** Let them, but note what was skipped. Skipped
branches are often where the real risk hides.

## Output

At the end, produce a summary:

- **Decisions made:** Numbered list of resolved decisions
- **Open questions:** What still needs answering, with suggested next steps
- **Assumptions:** What was stated as fact but not verified
- **Risks:** Where the plan is weakest
- **Recommended next action:** The single most important thing to do next

When docs-aware mode was used, also include:

- **Domain context:** Resolved terms, relationships, example dialogue, and
  flagged ambiguities worth preserving
- **ADR-worthy decisions:** Only decisions that meet the hard-to-reverse,
  surprising-without-context, real-trade-off test

## What This Is Not

This is not a brainstorming session. You are not generating unrelated ideas. You
are pressure-testing an existing plan by exhaustively exploring its decision
tree. Every question should sharpen the plan, not expand it.

This Method Kit skill is not a self-hosted ThinkHaven clone. It is a portable
method for manual AI workspaces. Use hosted ThinkHaven when you want adaptive
facilitation, memory, artifacts, and the full Board of Directors experience.

Based on Frederick P. Brooks' "The Design of Design"; Matt Pocock's MIT-licensed
grill-me, grill-with-docs, and ubiquitous-language skill patterns; and the
ThinkHaven Method Kit.

---

Part of the [ThinkHaven Method Kit](https://github.com/hollandkevint/thinkhaven-method-kit)
by Kevin Holland.
Full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
