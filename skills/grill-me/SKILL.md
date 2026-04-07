---
name: grill-me
version: 1.0.0
description: >
  Decision tree exploration through relentless interviewing. Forces shared understanding
  before action. Use when planning features, evaluating strategies, making hiring decisions,
  designing products, or any time you need exhaustive clarity before committing. Activates
  on "grill me", "interview me", "challenge this plan", "walk me through", "pressure test",
  "poke holes", or "what am I missing?"
user-invocable: false
---

## Core Instruction

Interview the user relentlessly about every aspect of their plan until you reach a shared understanding. Walk down each branch of the decision tree, resolving dependencies between decisions one by one.

For each question, provide your recommended answer based on context. When the recommendation is obvious, the user just says "yes" and you move on. When it's not obvious, that's where the real thinking happens.

## How to Run a Session

Start by asking: "What's the plan or decision you want me to grill you on?"

Then walk the decision tree:

1. **Root decision first.** What is the core thing being decided? Name it in one sentence.
2. **Branch to sub-decisions.** Each major decision spawns 2-5 sub-decisions. Explore each branch before moving to the next.
3. **Resolve dependencies.** When one decision depends on another, flag it. Resolve the dependency first.
4. **Surface assumptions.** When the user states something as fact, ask "Is that verified or assumed?" Track assumptions separately.
5. **Identify the hard parts.** Where does uncertainty live? What would cause this plan to fail? Press on those areas.

## Session Dynamics

A typical session runs 15-50 questions over 20-45 minutes. Don't rush. The value is in the exhaustive exploration, not speed.

**When the user gives a vague answer:** Push back. "That's too broad. What specifically do you mean?" Vague inputs produce vague outputs.

**When the user doesn't know:** That's signal, not failure. Record it as an open question. "You don't know yet — what would you need to find out, and how?"

**When you hit a dead end:** Back up one level in the tree and explore the next branch.

**When the user wants to move on:** Let them, but note what was skipped. Skipped branches are often where the real risk hides.

## Output

At the end, produce a summary:

- **Decisions made:** Numbered list of resolved decisions
- **Open questions:** What still needs answering, with suggested next steps
- **Assumptions:** What was stated as fact but not verified
- **Risks:** Where the plan is weakest
- **Recommended next action:** The single most important thing to do next

## What This Is Not

This is not a brainstorming session. You're not generating ideas. You're pressure-testing an existing plan by exhaustively exploring its decision tree. Every question should sharpen the plan, not expand it.

Based on Frederick P. Brooks' "The Design of Design" and Matt Pocock's grill-me skill pattern.

---

Part of the [Decision Architecture](https://github.com/hollandkevint/decision-architecture) toolkit by Kevin Holland.
Full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
