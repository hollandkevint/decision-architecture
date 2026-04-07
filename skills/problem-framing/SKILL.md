---
name: problem-framing
version: 1.0.0
description: >
  9-step systematic problem diagnosis. Define the problem before designing the solution.
  Uses root cause analysis, force field analysis, and structured evaluation. Adapted from
  BMAD Creative Intelligence Suite (Dr. Quinn). Activates on "diagnose this problem",
  "root cause", "why isn't this working", "what's really going on", "problem framing",
  "five whys", or "systems thinking."
user-invocable: false
---

## The 9 Steps

Walk through each step in order. Do not skip to solutions. The ur-problem is to define the problem.

### Step 1: Define the Problem

Ask: "Describe the problem in one sentence. Who is affected, and what's the observable impact?"

Push back if the user names a solution disguised as a problem. "We need a dashboard" is a solution. "Regional managers can't compare quarterly performance without emailing the analytics team" is a problem.

### Step 2: Is/Is Not Analysis

Narrow the scope. What IS the problem? What is it NOT?

| Dimension | IS | IS NOT |
|-----------|-----|--------|
| What | [specific symptoms] | [things that look similar but aren't this] |
| Where | [where it happens] | [where it doesn't happen] |
| When | [when it occurs] | [when it doesn't occur] |
| Who | [who's affected] | [who's not affected] |

The distinctions reveal the boundary conditions. Problems that happen everywhere are different from problems that happen in specific contexts.

### Step 3: Diagnose Root Causes

Use Five Whys. Ask "Why?" five times, drilling past symptoms to root causes.

Rules:
- Each "Why?" must point to a cause, not a person
- Stop when you reach something the user can change
- Branch when there are multiple causes at any level
- If "Why?" produces a shrug, that's an open question to investigate

### Step 4: Force Field Analysis

What forces push toward solving this problem? What forces resist?

| Driving Forces (push toward change) | Restraining Forces (resist change) |
|--------------------------------------|------------------------------------|
| [list specific forces with strength 1-3] | [list specific forces with strength 1-3] |

The strategy isn't always to add more driving force. Sometimes reducing a restraining force is cheaper and more effective.

### Step 5: Generate Solutions

Now — and only now — generate solutions. At least 3, max 7. For each:
- One sentence describing the solution
- Which root cause it addresses
- Estimated effort (hours/days/weeks)
- Key risk

Include at least one "do nothing" option with explicit consequences.

### Step 6: Evaluate Against Criteria

Define 3-5 evaluation criteria BEFORE scoring. Common ones:
- Impact on root cause (not symptoms)
- Feasibility with available resources
- Time to first result
- Reversibility (can you undo it if wrong?)

Score each solution 1-5 on each criterion. Present as a decision matrix.

### Step 7: Recommend

Pick the highest-scoring solution. Explain why in 2-3 sentences. Name what would change your recommendation.

### Step 8: Define Success Metrics

How will you know the problem is actually solved (not just addressed)?
- Leading indicator: what changes first?
- Lagging indicator: what confirms the problem is gone?
- Timeline: when should you see each indicator?

### Step 9: Identify What Could Go Wrong

Pre-mortem: "This solution failed. What happened?"

Name 2-3 failure modes and a mitigation for each. If a failure mode has no mitigation, flag it as an accepted risk.

## Output

```markdown
# Problem Diagnosis: [Problem Name]
Date: [date]

## Problem Statement
[One sentence from Step 1]

## Is/Is Not
[Table from Step 2]

## Root Causes
[Five Whys chain from Step 3]

## Force Field
[Table from Step 4]

## Solutions Considered
[Numbered list with effort/risk from Step 5]

## Decision Matrix
[Scoring table from Step 6]

## Recommendation
[From Step 7]

## Success Metrics
[From Step 8]

## Risks & Mitigations
[From Step 9]
```

Adapted from BMAD Creative Intelligence Suite problem-solving workflow (Dr. Quinn).

---

Part of the [Decision Architecture](https://github.com/hollandkevint/decision-architecture) toolkit by Kevin Holland.
Full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
