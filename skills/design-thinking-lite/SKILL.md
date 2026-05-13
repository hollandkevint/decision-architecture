---
name: design-thinking-lite
version: 1.0.0
description: >
  7-step human-centered design process. Context, empathize, define, ideate, prototype,
  test, iterate. Lightweight version of full design thinking for strategic decisions.
  Adapted from BMAD Creative Intelligence Suite (Maya). Activates on "design thinking",
  "user-centered", "empathy mapping", "how would users feel", "design this experience",
  or "human-centered."
user-invocable: false
---

## The 7 Steps

### Step 1: Context

Establish the landscape before diving in.

Ask:
- "Who are we designing for?" (specific people, not segments)
- "What's the current experience?" (what happens today, step by step)
- "What triggered this work?" (why now)
- "What constraints are non-negotiable?" (budget, timeline, technology, regulation)

### Step 2: Empathize

Understand the human experience. Not what users SAY they want — what they DO, FEEL, and STRUGGLE with.

Ask: "Walk me through the last time [the person you're designing for] encountered this situation. What happened? What did they do? How did they feel?"

Build an empathy snapshot:

| Dimension | What you know |
|-----------|--------------|
| **Does** | Observable behaviors and actions |
| **Thinks** | Beliefs and assumptions they hold |
| **Feels** | Emotions during the experience |
| **Pain points** | Specific frustrations and friction |
| **Workarounds** | Creative hacks they've invented |

CRITICAL: If the user is guessing about empathy data (hasn't talked to actual users), flag it. "You're describing what you think users feel. Have you verified this with real people?"

### Step 3: Define

Synthesize empathy into a problem statement.

Format: "[Person] needs a way to [need] because [insight]."

The insight is the key. "Because they're frustrated" is weak. "Because they make the decision at 6am on their phone before their first meeting and need the answer in under 30 seconds" is an insight.

### Step 4: Ideate

Generate solutions. Quantity over quality. Defer judgment.

Rules:
- Minimum 5 ideas, max 10
- Include at least one "ridiculous" idea (stretches thinking)
- Include at least one "do the simplest possible thing" idea
- No evaluation during ideation

After generating, cluster into themes and pick the top 3 to evaluate.

### Step 5: Prototype

Define the cheapest way to test each of the top 3 ideas.

| Idea | Prototype | Time to Build | What It Tests |
|------|-----------|---------------|---------------|
| [idea 1] | [prototype method] | [time] | [hypothesis] |
| [idea 2] | [prototype method] | [time] | [hypothesis] |
| [idea 3] | [prototype method] | [time] | [hypothesis] |

Prototype methods (cheapest first):
- Paper sketch or wireframe (1 hour)
- Clickable mockup (half day)
- Concierge/manual delivery (1 day)
- Working prototype (1 week)

### Step 6: Test

Define how to evaluate each prototype.

Ask:
- "Who will test this?" (specific people, not hypothetical users)
- "What behavior would confirm this works?" (observable, not self-reported)
- "What would make you abandon this direction?" (define failure before testing)

### Step 7: Iterate

Based on test results, decide:
- **Proceed:** Evidence supports the direction. Build the real version.
- **Pivot:** The problem is real but the solution missed. Return to Step 4 with new constraints.
- **Kill:** The problem wasn't what you thought. Return to Step 2 with fresh empathy research.

## Output

```markdown
# Design Thinking Brief: [Project Name]
Date: [date]

## Context
[Step 1 summary]

## Empathy Snapshot
[Step 2 table]

## Problem Statement
[Step 3 — Person needs X because Y]

## Top 3 Ideas
[Step 4 — clustered and selected]

## Prototype Plan
[Step 5 table]

## Test Plan
[Step 6 — who, what behavior, what kills it]

## Decision After Testing
[Proceed / Pivot / Kill — with rationale]
```

Adapted from BMAD Creative Intelligence Suite design-thinking workflow (Maya).

---

Part of the [ThinkHaven Method Kit](https://github.com/hollandkevint/thinkhaven-method-kit) by Kevin Holland.
Full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
