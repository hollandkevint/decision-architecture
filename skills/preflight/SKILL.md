---
name: preflight
version: 1.0.0
description: >
  7-question clarity exercise before any AI session or major decision. Pen-and-paper
  discipline adapted for interactive use. Activates on "preflight", "before we start",
  "clarify my thinking", "what am I trying to do", "help me think through this",
  "I'm about to start", or "pre-session checklist."
user-invocable: false
---

## The 7 Questions

Walk the user through each question sequentially. Do NOT skip ahead. Do NOT accept vague answers. Push back on anything that isn't specific enough to act on.

### 1. What am I actually trying to accomplish?

Ask for the outcome, not the task. "Build a dashboard" is a task. "Enable regional managers to compare quarterly performance without waiting for the analytics team" is an outcome.

If the user gives a task, ask: "That's what you're doing. What changes in the world when it's done?"

### 2. Why does this matter?

Consequence of success AND failure. Both sides. If the user can't articulate why failure matters, the work might not matter enough to do.

Ask: "What happens if you succeed? What happens if you don't do this at all?"

### 3. What does "done" look like?

Specific, observable description. Not "a good dashboard" but "a self-serve report that 5 regional managers use weekly without asking the data team for help."

If it's not specific enough to verify, push back: "How would someone else know this was done?"

### 4. What does "wrong" look like?

This is the most important question. Name the failure modes. What would make this a waste of time? What would make it actively harmful?

Ask: "If this goes badly, what does that look like? What's the worst version of 'done'?"

CRITICAL: Most people skip this question. Don't let them. Failure modes are where the real thinking happens.

### 5. What do I already know that I haven't written down?

Institutional knowledge, context, prior attempts, political dynamics, constraints nobody documents.

Ask: "What would a new person on this project not know that would bite them?"

### 6. What are the pieces?

Decomposition and dependencies. What are the 3-7 major components? What depends on what? What's the critical path?

Ask: "If you had to break this into chunks, what are they? Which ones can't start until others finish?"

### 7. What's the hard part?

Where does uncertainty live? What haven't you figured out yet? What scares you about this?

Ask: "What part of this keeps you up at night? Where's the risk you can't control?"

## Output

After all 7 questions, produce a preflight brief:

```markdown
# Preflight Brief: [Topic]
Date: [date]

## Outcome
[Answer to Q1 — one sentence]

## Stakes
- Success: [Q2 success side]
- Failure: [Q2 failure side]

## Definition of Done
[Q3 — specific, observable]

## Failure Modes
[Q4 — numbered list]

## Context & Constraints
[Q5 — what's not written down]

## Components & Dependencies
[Q6 — decomposition with critical path noted]

## Hard Parts
[Q7 — where uncertainty lives]

## Recommended First Step
[Your recommendation based on the hard parts]
```

## Principle

Clarity you bring to AI > clarity AI can generate for you. This exercise forces the user to think before the AI thinks for them.

Based on Nate Jones' Human Prompt Preflight framework.

---

Part of the [ThinkHaven Method Kit](https://github.com/hollandkevint/thinkhaven-method-kit) by Kevin Holland.
Full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
