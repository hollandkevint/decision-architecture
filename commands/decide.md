---
name: decide
description: "Run a decision through the decision-facilitator agent. Framing intake, existing-skill routing, adversarial pressure, decision-brief, and optional handoff to /ce-plan or /ce-ideate."
user-invocable: true
---

# Decide

Invoke the `decision-facilitator` agent to thread one decision across stages: framing intake (new / stuck / pre-launch / retro / free-text), routing through ThinkHaven Method Kit skills (preflight, problem-framing, grill-me, assumption-mapper, kill-go, decision-brief), adversarial pressure as a stage, and a final decision-brief.

## Steps

1. Activate the `decision-facilitator` agent. (Equivalent to invoking `@decision-facilitator` directly.)
2. Let the agent run its framing intake and skill routing. Do not interfere with anti-sycophancy pushback — that's the point.
3. The agent produces a decision-brief at the end and instructs how to paste it into `/ce-plan` or `/ce-ideate` if the user wants to plan implementation or broaden options.

Agent definition: `agents/decision-facilitator.agent.md`.
