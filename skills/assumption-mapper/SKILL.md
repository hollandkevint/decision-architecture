---
name: assumption-mapper
version: 1.0.0
description: >
  Extract and rank assumptions from any plan, idea, or strategy. Identifies what to
  test first. Anti-sycophancy tool — surfaces beliefs the user treats as facts. Activates
  on "what am I assuming", "assumptions", "what could go wrong", "blind spots",
  "stress test my thinking", or "what haven't I considered?"
user-invocable: false
---

## How It Works

Listen to the user describe their plan, idea, or strategy. Then extract every assumption hiding in what they said.

### Step 1: Gather the Plan

Ask: "Walk me through your plan, idea, or strategy. Don't filter — include the parts you're less sure about."

Let the user talk. Don't interrupt to challenge yet. Take notes on every claim, projection, or expectation embedded in their description.

### Step 2: Extract Assumptions

Review everything the user said. For each statement that could be wrong, create an assumption entry:

**Types of assumptions:**

| Type | What it sounds like | Example |
|------|-------------------|---------|
| **Market** | "People want this" / "They'll pay for it" | "Product managers need better decision tools" |
| **Technical** | "We can build this" / "It will work" | "Claude can maintain 6 distinct personas in one session" |
| **Behavioral** | "Users will do X" / "They'll adopt it" | "Users will complete a 30-minute session" |
| **Economic** | "The unit economics work" / "We can afford it" | "$39 for 10 sessions is a price point that converts" |
| **Competitive** | "Nobody else does this" / "We're differentiated" | "No tool provides multi-perspective AI disagreement" |
| **Timing** | "Now is the right time" / "The market is ready" | "AI sycophancy is a recognized problem in 2026" |

### Step 3: Rank by Risk

Score each assumption on two dimensions:

**Impact if wrong (1-5):** If this assumption is false, how badly does it break the plan?
**Confidence level (1-5):** How much evidence supports this assumption?

| Impact if Wrong | Confidence | Priority |
|----------------|------------|----------|
| High (4-5) | Low (1-2) | **Test immediately** — this is where plans die |
| High (4-5) | High (4-5) | Monitor — verify the evidence is current |
| Low (1-2) | Low (1-2) | Acknowledge but don't prioritize |
| Low (1-2) | High (4-5) | Ignore — low risk, high confidence |

### Step 4: Design Tests

For every "test immediately" assumption, suggest the cheapest way to validate or invalidate it:

- **Conversation test (1 hour):** Talk to 3 people in the target market. Ask about the problem, not the solution.
- **Behavior test (1 day):** Create a landing page, fake door, or signup form. Measure clicks, not opinions.
- **Build test (1 week):** Build the smallest version that tests the assumption. Ship it to 5 people. Measure usage.
- **Data test (1 hour):** Search for existing data that confirms or contradicts. Google Trends, competitor revenue, industry reports.

### Step 5: Present the Map

## Output

```markdown
# Assumption Map: [Plan Name]
Date: [date]

## Test Immediately (High Impact, Low Confidence)
| # | Assumption | Type | Impact | Confidence | Cheapest Test |
|---|-----------|------|--------|------------|---------------|
| 1 | [assumption] | [type] | X/5 | X/5 | [test] |

## Monitor (High Impact, High Confidence)
| # | Assumption | Type | Evidence |
|---|-----------|------|----------|
| 1 | [assumption] | [type] | [what supports it] |

## Acknowledged (Low Impact)
- [assumption 1]
- [assumption 2]

## Summary
- Total assumptions found: [N]
- Test immediately: [N]
- Biggest risk: [the #1 assumption to test first and why]
```

## Anti-Sycophancy Note

The user may push back on assumptions you surface. "No, I know that's true." Ask: "How do you know? What's the evidence?" If the evidence is "I just know" or "everyone says so," that's a low-confidence assumption regardless of how the user feels about it.

---

Part of the [Decision Architecture](https://github.com/hollandkevint/decision-architecture) toolkit by Kevin Holland.
Full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
