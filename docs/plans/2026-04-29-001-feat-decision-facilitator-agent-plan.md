---
title: Add Decision-Facilitator Agent (v2)
type: feat
status: completed
date: 2026-04-29
origin: docs/brainstorms/2026-04-28-decision-architecture-v2-requirements.md
---

# Add Decision-Facilitator Agent (v2)

## Summary

The plan implements v2 of decision-architecture by adding `agents/decision-facilitator.md` (the Facilitator), a user-facing slash command `/da:decide`, a minor plugin manifest bump (1.0.0 → 1.1.0), and README + CLAUDE.md updates. The agent threads framing intake, routes to existing skills, applies adversarial pressure as a stage, and presents a decision-brief that the user pastes into the next tool. No new skills, no test infrastructure, no breaking changes. A short pre-implementation spike (U5) validates Claude Code's plugin-agent loading and skill-invocation mechanics before U1 commits to a structure.

---

## Problem Frame

Concrete grounding moment carried from origin: a recent ThinkHaven update fragmented across preflight (decision-architecture) → /ce-plan (compound-engineering) → /ce-ideate (compound-engineering) → bmad:analyst Mary (BMAD), with no thread holding context and anti-sycophancy on the page but not strong enough to keep the user inside the system. v2 solves the orchestration gap with a thin agent on top of existing primitives. (See origin for full pain narrative.)

Implementation risk is low; the only new code-shaped artifact is one markdown agent file. Design risk lives in two places: (1) Claude Code's plugin-agent loading mechanics, which the plan defers to a U5 spike; and (2) the agent's routing logic and how convincingly it threads context across stages.

---

## Requirements

- R1. The plugin ships a single agent file users can invoke to start a decision flow. (origin R1)
- R2. The agent supports four framing modes (new / stuck / pre-launch / retro) plus free-text intake. (origin R2)
- R3. The agent routes to existing skills without requiring new skills. (origin R3)
- R4. Adversarial pressure is applied as a stage in the route, not as a standalone persona. (origin R4)
- R5. Soft suggestion handoff to /ce-plan and /ce-ideate. compound-engineering not a hard dependency. (origin R5)
- R6. Voice and footer attribution preserved. (origin R6)
- R7. Existing skills and commands stay directly callable. (origin R7)

**Origin actors:** A1 (decision-architecture user), A2 (ThinkHaven user)
**Origin flows:** F1 (new), F2 (stuck), F3 (pre-launch), F4 (retro), F5 (free-text), F6 (cross-plugin handoff)
**Origin acceptance examples:** AE1 (covers R1, R2), AE2 (covers R3, R4), AE3 (covers R5), AE4 (covers R6), AE5 (covers R7)

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

- Vault integration. No Obsidian-native features, no vault paths, no daily-journal hooks.
- Replacing or merging with product-advisor.
- Public launch / marketing push tied to v2.
- Persistent memory across decisions or sessions.

### Deferred to Follow-Up Work

- README hero rework / positioning page (separate PR after v2 is settled).
- Buffer / LinkedIn announcement content (handled outside the plugin repo).
- Test infrastructure for the plugin (no current tests; introducing them is a separate scope).
- Council pattern (multi-persona ensemble) as v2.1 evolution. Higher-upside alternative deferred per origin.

---

## Context & Research

### Relevant Code and Patterns

- `skills/preflight/SKILL.md` — exemplar skill format; framing intake style for new mode.
- `skills/grill-me/SKILL.md` — exemplar adversarial skill; routing target for stuck and retro modes.
- `skills/assumption-mapper/SKILL.md`, `skills/kill-go/SKILL.md`, `skills/decision-brief/SKILL.md`, `skills/problem-framing/SKILL.md` — routing targets per framing mode.
- `commands/run-preflight.md` — exemplar command; format reference for `commands/decide.md`.
- `prompts/anti-sycophancy-system-prompt.md` — voice baseline; agent will embed core 7 rules.
- `CLAUDE.md` — voice and style rules, quality bar, framework sources.
- `PHILOSOPHY.md` — decision-architecture thesis; agent's framing should align.
- `.claude-plugin/plugin.json` — plugin manifest; minor version bump.

### Institutional Learnings

- No `docs/solutions/` directory exists in this repo. The closest prior thinking lives in vault-only `🧠 Knowledge Base/wiki/concepts/decision-architecture.md`. Agent design aligns with that wiki page (PULL, Preflight, Grill-Me, Tool-vs-Colleague framings).

### External References

- Compound Engineering plugin (Every Inc.): handoff target for /ce-plan and /ce-ideate. Soft suggestion only.
- BMAD Creative Intelligence Suite: dispatch-or-menu pattern adopted for framing intake.
- BMAD Builder agent typology (stateless / memory / autonomous): this agent is stateless per session.

---

## Key Technical Decisions

- **Naming convention.** File and agent name: `decision-facilitator` (lowercase, hyphenated). Concept term in prose: "Facilitator" (capitalized). Slash command: `/da:decide`. @-mention: `@decision-facilitator`.
- **Agent file in `agents/` directory.** Rationale: an agent runs its own conversation context and persona; skills are background-context activations. The Facilitator's multi-stage flow fits agent semantics. `agents/` is a new directory in this repo. Auto-discovery is verified in U5 (skills/ and commands/ are first-class plugin paths; prompts/ and frameworks/ in this repo are author conventions).
- **Command name `/da:decide`.** Rationale: matches `da:` prefix convention from CLAUDE.md, action-oriented, short. Alternatives considered: `/da:facilitate` (verbose), `/da:think` (vague), `/da:run-decision` (over-formal).
- **Default skill chains per framing mode:**
  - new → preflight → problem-framing → optional grill-me → decision-brief
  - stuck → grill-me → assumption-mapper → decision-brief
  - pre-launch → kill-go → assumption-mapper → decision-brief
  - retro → grill-me with retrospective lens (inline, no new skill)
  - free-text → agent reads intent and maps to closest of new / stuck / pre-launch
- **Routing mechanism: chosen by U5 spike.** Three options evaluated: (a) Skill tool invocation from inside agent (cleanest if available); (b) keyword-trigger via text (unreliable, avoid); (c) inline the skill question lists verbatim (self-contained, larger file). Plan defaults to (a), falls back to (c). Option (b) is explicitly rejected.
- **Cross-plugin handoff contract: brief is the artifact.** At the decision boundary the agent presents the final decision-brief markdown and instructs the user to paste it into /ce-plan or /ce-ideate. No automatic context transfer; the agent cannot fire another plugin's slash command. Phrasing accommodates users without compound-engineering installed.
- **Anti-sycophancy embedded in agent system prompt.** Rationale: keeps agent self-contained; runtime does not have to load `prompts/anti-sycophancy-system-prompt.md` separately. Cross-reference the standalone prompt for users who want the raw template.
- **Stateless per invocation.** No persistent memory across decisions or sessions. Thread-holding is conversation context within one decision flow.
- **Light-touch facilitator voice, no named persona.** Rationale: the persona is anti-sycophancy plus practitioner imperative. Naming a character (Priya / Mary / Carson equivalent) adds carrying cost without proportional value at MVP.
- **No automated tests.** Repo has no test infrastructure. Adding tests for an agent file is non-trivial (would require harness integration) and outside MVP. Verification is manual smoke testing per implementation unit.
- **Minor version bump 1.0.0 → 1.1.0.** New feature, no breaking changes.

---

## Open Questions

### Resolved During Planning

- Q: Where does routing logic live? A: Inside the agent file; no separate `references/` doc.
- Q: Does the agent load anti-sycophancy at runtime? A: No, embed core 7 rules in agent system prompt.
- Q: Does plugin.json need to declare agents explicitly? A: Verified by U5. Default assumption is directory-based discovery; if it fails, U3 adds an explicit `agents` field.
- Q: How does the agent invoke other plugin skills? A: Verified by U5. Default assumption is the Skill tool is exposed to plugin agents; fallback is inlining skill content into the agent file.

### Deferred to Implementation

- Exact wording of the agent's system prompt and framing intake. Drafted in U1, finalized during implementation.
- Edge-case handling in free-text mode when user intent is ambiguous. Default: agent asks one clarifying question before routing. Specifics during implementation.
- Whether to include a "skip to skill X" escape hatch in the framing menu. Probably yes; finalize wording in U1.

---

## Output Structure

```
decision-architecture/
├── agents/                          # NEW (U1 creates dir; U5 confirms auto-discovery)
│   └── decision-facilitator.md      # NEW (U1)
├── commands/
│   ├── decide.md                    # NEW (U2)
│   ├── run-preflight.md             # existing, unchanged
│   └── ...                          # 4 other existing commands
├── .claude-plugin/
│   └── plugin.json                  # MODIFY (U3)
├── README.md                        # MODIFY (U4)
├── CLAUDE.md                        # MODIFY (U4)
├── docs/
│   ├── brainstorms/
│   │   └── 2026-04-28-decision-architecture-v2-requirements.md
│   └── plans/
│       └── 2026-04-29-001-feat-decision-facilitator-agent-plan.md
├── skills/                          # unchanged (11 skills)
├── prompts/                         # unchanged (4 prompts)
└── frameworks/                      # unchanged (2 frameworks)
```

---

## High-Level Technical Design

> *This illustrates the intended approach and is directional guidance for review, not implementation specification. The implementing agent should treat it as context, not code to reproduce.*

```
User invokes /da:decide  OR  @decision-facilitator
        │
        ▼
Agent system prompt loads:
  • Anti-sycophancy core (7 rules embedded)
  • Light-touch facilitator voice
  • Footer rule (ThinkHaven / BMAD-METHOD / data-product-operator)
        │
        ▼
Framing intake question:
  "What kind of decision are you working on?
    1. New — not framed yet
    2. Stuck — draft isn't landing
    3. Pre-launch — pressure-test before shipping
    4. Retro — learn from a recent one
   Or describe in your own words."
        │
        ├── new        → preflight → problem-framing → [optional grill-me] → decision-brief
        ├── stuck      → grill-me → assumption-mapper → decision-brief
        ├── pre-launch → kill-go → assumption-mapper → decision-brief
        ├── retro      → grill-me (retrospective lens, inline)
        └── free-text  → map intent → one of the above
        │
        ▼
At decision boundary, agent presents the decision-brief and instructs:
  "Paste this into /ce-plan to plan implementation"
  "Paste this into /ce-ideate to broaden options"
  (compound-engineering plugin required for both slash commands)
  The brief IS the artifact. No automatic context transfer.
        │
        ▼
Footer: ThinkHaven / BMAD-METHOD / data-product-operator
```

---

## Implementation Units

- U5. **Plugin agent format and routing spike**

**Goal:** Validate Claude Code's plugin-agent loading and skill-invocation mechanics before U1 commits to a structure. De-risks two assumptions: (1) `agents/` auto-discovers in plugins, (2) the agent can invoke other plugin skills via the Skill tool.

**Requirements:** None directly (de-risking unit; outcomes shape U1, U3).

**Dependencies:** None. Runs first.

**Files:**
- Research only. Findings recorded in commit message and folded into U1 / U3 approach if anything diverges from defaults.

**Approach:**
- Confirm `agents/` directory in a Claude Code plugin auto-discovers vs requiring an explicit `agents` field in plugin.json.
- Confirm Claude Code agent frontmatter schema for plugin-bundled agents (vs project-level `.claude/agents/`). Document the required and optional fields.
- Determine the routing mechanism. Try in order:
  - (a) **Skill tool invocation from inside agent.** Build a one-file scratch agent that calls the Skill tool to invoke `preflight`. Confirm whether the Skill tool is exposed to plugin agents in their default tool set.
  - (b) **Keyword-trigger via text.** Emit text containing skill activation keywords. Confirm whether existing skills activate from agent output. (Expected: unreliable.)
  - (c) **Inline skill content.** Copy preflight's question list verbatim into the agent. Confirm voice and structure carry.
- Confirm cross-plugin command suggestion is text-only. The agent cannot programmatically run `/ce-plan`; the user must paste the brief into the next plugin's slash command.
- Test activation-keyword competition. Install scratch plugin with both an agent and a skill that share keywords; confirm `/da:decide` dispatches the agent without skill interference.

**Patterns to follow:**
- Existing public Claude Code plugin examples (compound-engineering, BMAD CIS) for plugin-distributed agent format reference.
- Run a 15-30 minute scratch test plugin if direct documentation is incomplete.

**Test scenarios:**
- Test expectation: none — research spike. Manual confirmation of each finding.

**Verification:**
- Routing mechanism for U1 chosen explicitly: (a) Skill tool, (c) inline content, or hybrid. Option (b) keyword-trigger remains rejected.
- `agents/` directory loading characterized (auto vs explicit declaration in plugin.json).
- Frontmatter schema documented in spike notes; becomes input to U1.
- Activation keyword competition behavior characterized.
- Spike findings noted in commit message and propagated to U1, U3 approach if defaults need updating.

**Estimated effort:** 15-30 minutes.

---

- U1. **decision-facilitator agent definition**

**Goal:** Create the agent file at `agents/decision-facilitator.md` with persona, framing intake logic, skill routing per mode (per U5 findings), cross-plugin handoff phrasing, and standard footer.

**Requirements:** R1, R2, R3, R4, R6, R7

**Dependencies:** U5 (spike findings determine routing mechanism and frontmatter schema).

**Files:**
- Create: `agents/decision-facilitator.md`

**Approach:**
- **Routing mechanism per U5.** Default plan: Skill tool invocation if available to plugin agents (cleanest skill chaining). Fallback: inline the relevant skill question lists into the agent file (self-contained, larger file, but reliable). Avoid keyword-trigger hacks; they don't preserve thread-holding.
- YAML frontmatter (Claude Code agent format per U5 spike): `name`, `description` (with activation keywords: "decision", "decide", "stuck", "pre-launch", "pressure test", "retro", "facilitate decision"), `tools` field including the Skill tool if U5 confirms availability.
- System prompt body: anti-sycophancy core embedded verbatim from `prompts/anti-sycophancy-system-prompt.md`. The seven rules: (1) never lead with agreement, (2) challenge every assumption stated as fact, (3) identify three failure modes before strengths, (4) evaluate "Is this good?" as conditional truth, (5) force tradeoff choices when metrics conflict, (6) name avoidance when user sidesteps, (7) recommend killing when evidence supports. Plus light-touch facilitator role description and quality bar (<15 min sessions, shareable markdown, push back on vague answers).
- Framing intake: 4 numbered modes plus free-text. BMAD CIS dispatch-or-menu pattern adapted.
- Skill routing logic per framing mode per the Key Technical Decisions list. **Adversarial pressure is delivered by grill-me + assumption-mapper inside the chain. Do NOT create a separate "pressure" step outside those skills.**
- **Cross-plugin handoff contract.** At the decision boundary the agent presents the final decision-brief markdown and instructs the user to paste it. The brief IS the artifact that crosses plugins; no automatic context transfer. Phrasing template: `"Here's your decision-brief. To plan implementation, paste this into /ce-plan's first prompt. To broaden options, paste it into /ce-ideate. Both require the compound-engineering plugin."` Users without compound-engineering still get a usable brief and paste it into whatever planning tool they prefer.
- Footer: standard ThinkHaven / BMAD-METHOD / data-product-operator triple, matching skill convention.

**Patterns to follow:**
- `skills/preflight/SKILL.md` for imperative voice and 7-question framing intake style.
- `skills/grill-me/SKILL.md` for routing-via-tree style and pushback phrasing.
- `prompts/anti-sycophancy-system-prompt.md` for the verbatim 7 rules.

**Test scenarios (manual smoke tests):**
- Happy path: Invoke `/da:decide`. Agent presents framing menu. User selects "stuck" with topic "ThinkHaven update scope creep." Agent fires grill-me, then assumption-mapper, then decision-brief in order. Outcome: a decision-brief markdown is produced.
- Happy path: Invoke `/da:decide` with "new" mode and topic "I'm thinking about a sales-led growth motion." Agent fires preflight first, then problem-framing, asks if grill-me is wanted. Outcome: clean preflight brief plus problem frame.
- Edge case: Invoke `/da:decide` with no follow-up input. Agent asks framing question, does not error or hang.
- Edge case: User picks "free-text" with ambiguous input ("just thinking about stuff"). Agent asks one clarifying question rather than defaulting silently.
- Error path: A skill referenced in a chain has been renamed in a future repo state. Agent surfaces the missing skill and offers free-text mode rather than crashing.
- Integration: At the decision boundary, agent presents the decision-brief with paste-instructions for /ce-plan. User without compound-engineering installed can still copy the brief and use it elsewhere.
- Anti-sycophancy: Smoke-test with a vague intent ("I want to build a thing for users"). Agent challenges or interrogates rather than affirms.
- Footer: Final agent response includes the ThinkHaven / BMAD-METHOD / data-product-operator footer.

**Verification:**
- Agent file parses as valid Claude Code agent (frontmatter valid per U5 schema, body well-formed markdown).
- All four framing modes route to documented skill chains via U5's chosen mechanism.
- Anti-sycophancy is operative on smoke-test prompts.
- Footer present and consistent with existing skills.

---

- U2. **User-facing command: `/da:decide`**

**Goal:** Create `commands/decide.md` exposing the slash command that invokes the decision-facilitator agent.

**Requirements:** R1, R7

**Dependencies:** U1 (agent must exist before command can invoke it). Implicitly U5 (via U1).

**Files:**
- Create: `commands/decide.md`

**Approach:**
- YAML frontmatter: `name: decide`, `description: "Run a decision through the decision-facilitator agent. Framing intake, skill routing, adversarial pressure, optional cross-plugin handoff."`, `user-invocable: true`.
- Body: brief description of what the command does plus the instruction to invoke the agent (`@decision-facilitator` style or equivalent skill-invocation per U5 findings).
- Slash command surfaces as `/da:decide` (the `da:` prefix comes from the plugin's namespace).

**Patterns to follow:**
- `commands/run-preflight.md` (same pattern; replace skill ref with agent ref).

**Test scenarios (manual):**
- Happy path: With plugin installed, invoke `/da:decide` from Claude Code. The decision-facilitator agent activates and asks the framing question.
- Discovery: `/da:decide` appears in the Claude Code slash-command list when the plugin is installed.
- Integration: From `/da:decide`, the agent's first response uses anti-sycophancy framing (validates U1's voice via the command surface).

**Verification:**
- Slash command resolves to the decision-facilitator agent without errors.
- User flow from `/da:decide` to agent first response works in a smoke test.

---

- U3. **Plugin manifest bump**

**Goal:** Update `.claude-plugin/plugin.json` for v2 (description mentions agent, version 1.0.0 → 1.1.0, optional `agents` field per U5).

**Requirements:** R6 (preserve metadata and attribution).

**Dependencies:** U1, U2, U5 (manifest may need an explicit `agents` field if U5 reveals that directory-based discovery doesn't work).

**Files:**
- Modify: `.claude-plugin/plugin.json`

**Approach:**
- Bump `"version": "1.0.0"` → `"1.1.0"`.
- Update `description` to append a sentence about the Facilitator: "v2 adds a Facilitator agent that threads decisions across stages."
- Add keyword `"agent"` to the keywords array if not already present.
- Add explicit `agents` field declaration if and only if U5 reveals that directory-based discovery does not work for plugin-bundled agents.

**Patterns to follow:**
- Existing plugin.json shape, no schema invention.

**Test scenarios:**
- Test expectation: none — pure manifest update. Manual JSON validation: file parses as valid JSON; install plugin from this commit and confirm version reads as 1.1.0 in Claude Code's plugin list.

**Verification:**
- plugin.json is valid JSON.
- Description and keywords reflect v2 capabilities.

---

- U4. **README.md and CLAUDE.md updates**

**Goal:** Document the Facilitator agent so users discover and invoke it. Maintain existing voice and structure.

**Requirements:** R6 (voice preserved). Discovery-shaped: makes the agent visible to new users.

**Dependencies:** U1, U2 (agent and command must exist before docs reference them). Implicitly U5 (via U1).

**Files:**
- Modify: `README.md`
- Modify: `CLAUDE.md`

**Approach:**
- README: add a section near the top describing the Facilitator agent: what it does, how to invoke (`/da:decide` or `@decision-facilitator`), the four framing modes, expected output (a decision-brief that the user pastes into the next tool). Add to the existing capabilities list. Keep voice (imperative, anti-sycophancy first).
- CLAUDE.md: add a brief note under "Skill Structure" about the new `agents/` directory and the agent format conventions for future agent additions. One paragraph; no expansion.

**Patterns to follow:**
- Existing README sections (Capabilities, Quick Start).
- CLAUDE.md voice rules (imperative practitioner language, anti-sycophancy as feature).

**Test scenarios:**
- Test expectation: none — documentation update. Manual: README renders correctly on GitHub; a new user reading it understands what the agent does and how to use it within 60 seconds.

**Verification:**
- README mentions the Facilitator prominently with a clear invocation example.
- CLAUDE.md voice and quality-bar rules apply to agent files (not just skills).

---

## System-Wide Impact

- **Interaction graph:** New agent invokes existing skills via the routing mechanism confirmed in U5 (Skill tool preferred; inline content fallback). No skill internals change. New `agents/` directory; auto-discovery is verified in U5. Note: existing skills/ and commands/ are first-class plugin discovery paths in Claude Code; prompts/ and frameworks/ in this repo are author conventions, not evidence that all top-level dirs auto-discover.
- **Activation keyword competition:** The agent's `description` keywords ("decision", "decide", "stuck") may overlap with existing skill keywords (e.g., preflight activates on "help me think through this"). Resolution order in Claude Code is undocumented. Expected behavior: foreground agent dispatch wins when invoked via slash command (`/da:decide`) or @-mention; background skill activation continues for pure keyword input. Verify in U5.
- **Error propagation:** Agent failures (malformed framing, missing skill) fall back to free-text mode and surface the error to the user. Detailed error handling deferred to U1 implementation.
- **State lifecycle risks:** Agent is stateless per session. No state persistence concerns.
- **API surface parity:** New `/da:decide` command and `@decision-facilitator` agent are new public APIs. Existing 5 commands and 11 skills unchanged. Existing 4 prompts and 2 frameworks unchanged.
- **Integration coverage:** Cross-plugin handoff is text-only. The agent presents a decision-brief and the user manually pastes it into /ce-plan or /ce-ideate. No runtime coupling. Plugin works fully when compound-engineering is not installed.
- **Unchanged invariants:** All 11 existing skills, all 5 existing commands, all 4 prompts, both frameworks remain unchanged and directly callable. Anti-sycophancy voice and ThinkHaven attribution preserved across all surfaces.

---

## Risks & Dependencies

| Risk | Mitigation |
|------|------------|
| Agent file format or `agents/` directory loading diverges from Claude Code's expected schema; plugin won't load | U5 spike validates format and directory discovery before U1 commits to a structure. If U5 reveals incompatibility, the plan collapses U1 + U2 into a single command file with the agent persona inline (no separate agents/ file). This is a hard prerequisite, not a footnote. |
| Skill tool is not exposed to plugin agents; the "agent fires skill" model breaks | U5 confirms availability. Fallback: inline the relevant skill question lists in the agent file. Larger file but self-contained and reliable. |
| Routing logic feels arbitrary or too rigid for users with non-canonical decisions | Document chains in Key Technical Decisions; treat them as defaults users can override via free-text mode; iterate based on use feedback after v2 ships |
| Anti-sycophancy embedding loses fidelity vs the standalone prompt | Copy core 7 rules verbatim from `prompts/anti-sycophancy-system-prompt.md`; cross-reference the standalone prompt in agent docs so it stays the canonical source |
| Cross-plugin handoff is annoying for users without compound-engineering installed | Phrasing acknowledges the dependency openly; the brief is usable in any planning tool, not just /ce-plan |
| Activation keyword overlap causes confusing dispatch (skill activates instead of agent on free-form input) | U5 characterizes resolution order; agent's description keywords are tightened if overlap creates conflicts |
| Naming collision if future agents are added | `decision-facilitator` is descriptive enough; future agents have distinct names |
| README expansion drifts away from v1's tight format | U4 maintains existing section structure; add to existing capabilities list rather than restructuring |

---

## Documentation / Operational Notes

- README updates surface the agent to new users (U4).
- CLAUDE.md updates document the agent format convention for future contributors (U4).
- No CI, no automated rollout. Plugin updates via standard Claude Code plugin install flow.
- Version bump signals a minor feature addition; users updating from 1.0.0 see no breaking changes.
- Recommended commit sequencing: U5 first (spike notes; may not produce a code commit), then U1, U2, U3, U4 each as atomic commits in dependency order.

---

## Sources & References

- **Origin document:** `docs/brainstorms/2026-04-28-decision-architecture-v2-requirements.md`
- Existing skills referenced: `skills/preflight/SKILL.md`, `skills/grill-me/SKILL.md`, `skills/assumption-mapper/SKILL.md`, `skills/kill-go/SKILL.md`, `skills/decision-brief/SKILL.md`, `skills/problem-framing/SKILL.md`
- Existing command pattern: `commands/run-preflight.md`
- Voice baseline: `prompts/anti-sycophancy-system-prompt.md`
- Project conventions: `CLAUDE.md`, `PHILOSOPHY.md`, `README.md`
- Plugin manifest: `.claude-plugin/plugin.json`
- External handoff target: Compound Engineering plugin (https://github.com/EveryInc/compound-engineering-plugin)
- Architecture comparison: BMAD CIS module, BMAD Builder, EveryInc compound-engineering-plugin (analyzed in origin brainstorm session)
