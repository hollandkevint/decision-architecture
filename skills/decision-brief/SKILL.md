---
name: decision-brief
version: 1.0.0
description: >
  One-page decision brief that passes the Simple/Surprising/Easy test. Turns a messy
  decision into a constraint that generates action. Based on Alex MH Smith's creative
  brief framework. Activates on "write a brief", "decision brief", "one-pager",
  "clarify the direction", "what's the constraint", or "make this simple."
user-invocable: false
---

## The SSE Test

A brief must pass three tests. If it fails any, rewrite.

**Simple** — Points in one direction. Hard to go off track. If two people read it and go in different directions, it's not simple enough.

**Surprising** — Makes you think "I never thought of it that way." If it sounds like every other brief, it's decoration, not direction.

**Easy** — Anyone should immediately have rough ideas for how to act on it. If only "creatives" or "strategists" can use it, it's too abstract.

Patagonia's "cause no unnecessary harm" passes all three. It generates decisions: free repairs, organic cotton, no Black Friday. "Eco-friendly clothing" generates nothing.

## Process

### Step 1: What's the Decision?

Ask: "What decision are you trying to make? State it as a question."

Good: "Should we invest in building a self-serve analytics tier?"
Bad: "We need to think about our analytics strategy."

If it's not a question, make it one. Decisions are questions with stakes.

### Step 2: What's the Tension?

Every real decision has a tension — two legitimate forces pulling in opposite directions.

Ask: "What makes this hard? What are you torn between?"

Examples:
- Speed vs. quality
- Short-term revenue vs. long-term positioning
- Serving current users vs. attracting new ones
- Technical debt vs. feature velocity

If there's no tension, there's no real decision. It's just a task.

### Step 3: What's the Constraint?

Turn the tension into a constraint. A constraint isn't a limit — it's a generator.

Ask: "Given the tension, what's the one thing that must be true for this to succeed?"

This becomes the brief. One sentence. Test it against SSE.

### Step 4: Test Against SSE

Read the constraint back to the user. Apply each test:

- **Simple:** "If you handed this to a new team member, would they know what to do?"
- **Surprising:** "Does this feel obvious or does it reframe something?"
- **Easy:** "Can you immediately think of 3 actions that follow from this?"

If it fails any test, rewrite. Iterate until it passes all three.

### Step 5: Generate 3 Actions

Prove the brief works by generating 3 concrete actions that follow directly from the constraint. If you can't generate 3, the brief isn't generative enough.

## Output

```markdown
# Decision Brief: [Decision Question]
Date: [date]

## The Decision
[Question form]

## The Tension
[Two forces in opposition]

## The Brief
> [One sentence — the constraint that generates action]

## SSE Check
- Simple: [Pass/Fail — evidence]
- Surprising: [Pass/Fail — evidence]
- Easy: [Pass/Fail — evidence]

## 3 Actions This Generates
1. [action]
2. [action]
3. [action]
```

Based on Alex MH Smith's creative brief framework.

---

Part of the [ThinkHaven Method Kit](https://github.com/hollandkevint/thinkhaven-method-kit) by Kevin Holland.
Full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
