---
title: Decision Architecture v2 — Facilitator Agent
status: confirmed
date: 2026-04-28
---

# Decision Architecture v2 — Facilitator Agent

## Summary

v2 of the decision-architecture plugin adds a thin Facilitator agent over the existing 11 skills and 5 commands. The agent threads one decision across stages: framing intake (new / stuck / pre-launch / retro / free-text), routes to the right existing skill, applies adversarial pressure via grill-me plus assumption-mapper before decision-brief, and suggests handoff to /ce-plan or /ce-ideate when the decision crosses into planning or ideation territory. Public scope, anti-sycophancy voice, and ThinkHaven attribution preserved. product-advisor stays Kevin-only and separate.

---

## Problem Frame

A real decision flow today fragments across plugins. Concrete grounding moment from a recent ThinkHaven update: the flow went preflight (decision-architecture) → /ce-plan (compound-engineering) → /ce-ideate (compound-engineering) → bmad:analyst Mary (BMAD) for pushback. Four plugins, no thread holding context, anti-sycophancy on the page but not strong enough that the user didn't have to reach outside for Mary. The existing 11 skills are good primitives. They fail when the user has to compose them by hand and can't get pushback inside the system.

---

## Actors

- A1. **Public decision-architecture user** — product leader, engineer, founder using the plugin in Claude Code.
- A2. **ThinkHaven user** — the Facilitator complements the multi-advisor experience at thinkhaven.co.

---

## Flows

- F1. **New decision** — Facilitator routes preflight → problem-framing → optional grill-me → decision-brief.
- F2. **Stuck decision** — Facilitator routes grill-me → assumption-mapper → decision-brief.
- F3. **Pre-launch** — Facilitator routes kill-go → assumption-mapper → decision-brief.
- F4. **Retro** — Facilitator runs grill-me with retrospective lens (inline, no new skill).
- F5. **Free-text intake** — Facilitator reads intent, maps to closest of F1-F4.
- F6. **Cross-plugin handoff** — Facilitator suggests /ce-plan or /ce-ideate at the decision boundary; user accepts; Facilitator does not auto-fire.

---

## Acceptance Examples

- AE1 (covers R1, R2). User invokes `/da:decide`. Facilitator asks: "What kind of decision are you working on? new / stuck / pre-launch / retro, or describe in your own words." User answers "Stuck — ThinkHaven update scope creep." Facilitator says "Sounds like Stuck. Running grill-me first, then assumption-mapper before decision-brief."
- AE2 (covers R3, R4). For Stuck mode, Facilitator fires grill-me, then assumption-mapper, then decision-brief, using the existing skill files. No new skills are written.
- AE3 (covers R5). When a stuck decision crosses into "I need to plan how to implement this," Facilitator says "This crosses into implementation planning. /ce-plan handles that next, run it when you're ready." User accepts; Facilitator does not auto-fire /ce-plan.
- AE4 (covers R6). Facilitator's first response opens with anti-sycophancy framing (challenges, not validation) and ends with the standard ThinkHaven / BMAD-METHOD / data-product-operator footer.
- AE5 (covers R7). A user who knows what they want still invokes `/run-preflight` directly without going through Facilitator. The agent does not gate skill access.

---

## Requirements

- R1. The plugin ships a single agent file users can invoke to start a decision flow.
- R2. The agent supports four framing modes (new / stuck / pre-launch / retro) plus free-text intake.
- R3. The agent routes to existing skills (preflight, problem-framing, grill-me, assumption-mapper, kill-go, decision-brief, etc.) without requiring new skills.
- R4. Adversarial pressure is applied as a stage in the route (grill-me + assumption-mapper sequenced before decision-brief), not as a standalone persona.
- R5. The agent suggests handoff to /ce-plan or /ce-ideate when the decision crosses into planning or ideation territory. Soft suggestion, not auto-fire. Compound-engineering plugin is not a hard dependency.
- R6. Voice and footer attribution match existing decision-architecture conventions (imperative practitioner, anti-sycophancy, ThinkHaven / BMAD-METHOD / data-product-operator).
- R7. The plugin remains usable for users who don't invoke the agent. Existing skills and commands stay directly callable.

---

## Scope Boundaries

### Deferred for later

- Decision registry as standalone skill (write a dated decision record to a /Decisions/ folder).
- Reversibility classifier (one-way / two-way door).
- Decision-scoped retrospective loop (pre-mortem → post-mortem closure linkage).
- Options-matrix template skill.
- "When to use which decision framework" MOC inside the plugin.
- Multi-decision projects, decision portfolio view, archaeology across past decisions.

### Outside this product's identity

- Vault integration. No Obsidian-native features, no vault paths, no daily-journal hooks. decision-architecture stays a generic Claude Code plugin.
- Replacing or merging with product-advisor. The BMAD agent stays Kevin-only and separate.
- Public launch / marketing push tied to v2.
- Persistent memory across decisions or sessions. Each invocation is stateless. Thread-holding is within one decision flow only.

### Deferred to Follow-Up Work

- README hero rework / positioning page for v2 launch (separate PR).
- Buffer / LinkedIn announcement content (handled outside the plugin repo).
- Test infrastructure for the plugin (no current tests; introducing them is a separate scope).

---

## Key Decisions

- **Plugin shape**: v2 is an evolution of the existing public decision-architecture repo, not a Kevin-personal plugin and not a replacement for product-advisor.
- **Agent shape**: Facilitator (thin router) with adversarial pressure as a stage, not the whole persona. Council pattern (multi-persona ensemble) deferred to v2.1 as the higher-upside alternative.
- **Voice**: light-touch facilitator, no named character (no Priya / Mary / Carson equivalent). Anti-sycophancy is the persona, not a system-prompt aspiration.
- **Handoff posture**: cross-plugin handoff (/ce-plan, /ce-ideate) is a soft suggestion the user accepts. Compound-engineering is not a hard dependency.
- **Statelessness**: agent is stateless per invocation. Thread-holding is conversation context within one decision flow, not a written record file.
- **Output**: no new artifact written by the agent itself. Only the existing decision-brief skill writes markdown, as today.
- **Distribution**: ships inside the existing decision-architecture repo on a minor version bump. Current users get the agent on update.

---

## Dependencies / Assumptions

- Claude Code plugin format supports `agents/` directory discovery (consistent with the existing skills/commands directory pattern).
- compound-engineering plugin handoffs reference standard slash commands (/ce-plan, /ce-ideate) that exist in the public compound-engineering plugin.
- **Durability bet**: the wedge is cross-plugin stage routing (Facilitator knows when to call /ce-plan or /ce-ideate from inside decision-architecture). As base models get smarter at single-skill execution, the agent's value sits in heterogeneous routing across plugins, not in persona depth. If models get good enough that explicit routing becomes obsolete, v2 was still worthwhile because the artifact set documents the decision-stage taxonomy.

---

## Outstanding Questions

### Resolved in dialogue

- Q: What is v2's relationship to product-advisor and decision-architecture v1? A: Evolution of decision-architecture v1; product-advisor stays separate Kevin-only.
- Q: What is the agent's shape (Facilitator / Adversary / Council)? A: Facilitator with adversarial as a stage.
- Q: What is MVP? A: Core agent + existing skills/utilities/commands. No new skills, no registry, no vault, no launch.

### Deferred to plan-time

- Command name (e.g., `/da:decide`, `/da:facilitate`, `/da:run-decision`).
- Default skill chains for each framing mode.
- Whether the agent file uses skill-style YAML frontmatter or the standard Claude Code agent format.
- Whether `agents/` is auto-discovered by Claude Code or requires explicit declaration in plugin.json.

---

## Sources & References

- Origin brainstorm: this skill session, 2026-04-28.
- product-advisor BMAD agent: vault path `.bmad-kevin-creator/agents/product-advisor.md`.
- decision-architecture v1: this repo (11 skills, 5 commands, 4 prompts, 2 frameworks).
- compound-engineering plugin: https://github.com/EveryInc/compound-engineering-plugin (handoff target).
- BMAD CIS module: https://github.com/bmad-code-org/bmad-module-creative-intelligence-suite (architecture comparison).
- BMAD Builder: https://github.com/bmad-code-org/bmad-builder (architecture comparison).
- Knowledge Base scan: vault path `🧠 Knowledge Base/` (Nate Jones prompt suite, decision-shaped frameworks).
