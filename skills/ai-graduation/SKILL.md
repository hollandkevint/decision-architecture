---
name: ai-graduation
version: 1.0.0
description: >
  7-move decision gate for AI deployment. Prevents early promise from becoming
  unquestioned infrastructure. Based on Stuart Winter-Tear's AI Graduation Path.
  Activates on "AI deployment", "graduation", "should we scale this AI", "pilot to
  production", "AI governance", "prove this works", or "when is this ready?"
user-invocable: false
---

## The Principle

A pilot does not earn authority because it can be repeated. It earns authority when the organisation understands the conditions under which it holds and the conditions under which it breaks.

## The 7 Moves

Walk through each move as a decision gate. The user must demonstrate readiness at each gate before advancing. Skipping gates is the primary failure mode.

### Move 1: Contain

**Gate question:** "Is this AI application running in a bounded, observable environment?"

Requirements:
- Defined scope (what it does, what it doesn't)
- Clear boundary conditions (when does it apply, when doesn't it)
- Human in the loop for all consequential outputs
- No access to systems it shouldn't touch

If the AI is running without clear boundaries, stop here. Containment first.

### Move 2: Instrument

**Gate question:** "Can you measure what this AI is actually doing?"

Requirements:
- Logging of inputs, outputs, and decisions
- Baseline metrics established (accuracy, latency, cost, error rate)
- Ability to compare AI decisions against human decisions
- Monitoring for drift (is performance changing over time?)

If you can't measure it, you can't evaluate it. Instrument before you trust.

### Move 3: Verify

**Gate question:** "Have you tested this against known-good answers?"

Requirements:
- Test set with ground truth (known correct answers)
- Performance measured against human baseline
- Edge cases explicitly tested (what happens at the boundaries?)
- Failure modes documented (when does it break? how does it fail?)

### Move 4: Prove

**Gate question:** "Can you demonstrate this works in the conditions where you plan to use it?"

Requirements:
- Tested in production-like environment (not just dev/staging)
- Tested with real users (not just the team that built it)
- Performance validated under realistic load and data quality
- Stakeholders have seen it work AND seen it fail

CRITICAL: Proving means showing both success AND failure conditions. A demo that only shows the happy path proves nothing.

### Move 5: Narrow

**Gate question:** "Have you defined the specific, limited scope for production use?"

Requirements:
- Explicit scope: what decisions this AI is authorized to make
- Explicit exclusions: what decisions require human override
- Escalation path: what happens when the AI encounters something outside its scope
- Rollback plan: how do you revert if it goes wrong

### Move 6: Widen

**Gate question:** "Based on proven performance in the narrow scope, what's the next increment?"

Requirements:
- Evidence from narrow deployment supports expansion
- New scope is an incremental extension, not a leap
- New edge cases identified and tested
- Monitoring from Move 2 is still active and shows stable performance

### Move 7: Standardise

**Gate question:** "Is this AI application ready to become organizational infrastructure?"

Requirements:
- Documentation exists for operators (not just builders)
- Training exists for users
- SLA defined and monitored
- Incident response procedure documented
- Regular review cadence established (quarterly minimum)

## Output

```markdown
# AI Graduation Assessment: [AI Application Name]
Date: [date]

## Current Position
Move [N] of 7: [Move Name]

## Gate Assessment
| Move | Status | Evidence | Gap |
|------|--------|----------|-----|
| 1. Contain | [Pass/Fail/Partial] | [evidence] | [what's missing] |
| 2. Instrument | [Pass/Fail/Partial] | [evidence] | [what's missing] |
| 3. Verify | [Pass/Fail/Partial] | [evidence] | [what's missing] |
| 4. Prove | [Pass/Fail/Partial] | [evidence] | [what's missing] |
| 5. Narrow | [Pass/Fail/Partial] | [evidence] | [what's missing] |
| 6. Widen | [Pass/Fail/Partial] | [evidence] | [what's missing] |
| 7. Standardise | [Pass/Fail/Partial] | [evidence] | [what's missing] |

## Recommendation
[Which move to focus on next and what needs to happen]

## Warning Signs
[Anything that suggests the organization is trying to skip gates]
```

Based on Stuart Winter-Tear's AI Graduation Path.

---

Part of the [ThinkHaven Method Kit](https://github.com/hollandkevint/thinkhaven-method-kit) by Kevin Holland.
Full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
