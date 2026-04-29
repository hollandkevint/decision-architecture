---
title: Add AGENTS.md for tool-agnostic context
type: feat
status: completed
date: 2026-04-29
---

# Add AGENTS.md for tool-agnostic context

## Summary

Add `AGENTS.md` at the repo root as the canonical agent-agnostic context file so the plugin works with any AI coding agent (Claude Code, Codex, Cursor, Gemini, etc.). Mirror the content currently in `CLAUDE.md` reframed without Claude-specific phrasing. Shrink `CLAUDE.md` to a one-line pointer at `AGENTS.md` for backward compatibility. Lightweight, 2 units, lands on the same `feat/decision-facilitator-agent` branch as the v2 PR.

## Requirements

- R1. Repo provides a single canonical context file (`AGENTS.md`) usable by any AI coding agent.
- R2. Content covers: project overview, voice/style, file structure, plugin conventions (skills, commands, agents, prompts, frameworks), quality bar, framework sources.
- R3. `CLAUDE.md` continues to exist as a thin pointer so tools that only check for `CLAUDE.md` still find context.
- R4. No content drift between `AGENTS.md` and `CLAUDE.md` (achieved by `CLAUDE.md` being a redirect, not a duplicate).
- R5. No behavioral change to skills, agents, commands, or prompts.

## Scope Boundaries

- Per-agent sibling files (`codex.md`, `cursor.md`, `gemini.md`) — out. AGENTS.md is the agnostic convention.
- Refactoring skills/commands/agents to remove any tool-specific phrasing — out. They already use generic LLM-facing language.
- Empirical install/test across Codex, Cursor, Gemini — out (manual user verification post-merge).
- README section advertising cross-agent support — out unless requested later.

### Deferred to Follow-Up Work

- README mention of cross-agent support — separate PR if desired.
- Validating AGENTS.md against any emerging schema (e.g., agents.md/spec) — defer until spec stabilizes.

## Context & Research

### Relevant Code and Patterns

- `CLAUDE.md` (current) — source of voice rules, file structure, agent format note, quality bar, framework sources. Mirror content into `AGENTS.md` with tool-agnostic framing.
- `README.md` — mentions plugin install via `/plugin marketplace add`. Keep separate from AGENTS.md scope.
- `.claude-plugin/plugin.json` — plugin manifest. Not modified by this plan.

### External References

- AGENTS.md convention (2026): emerging cross-agent standard for repository-level AI context. Single file, markdown, agnostic to specific tooling. Used by Codex, Cursor, and increasingly Claude Code.
- ce-plan protocol: "AGENTS.md guidance that materially affects the plan, with CLAUDE.md used only as compatibility fallback when present." Confirms AGENTS.md is the primary modern convention.

## Key Technical Decisions

- **AGENTS.md is canonical; CLAUDE.md is a redirect.** Avoids content drift. Modern tools read AGENTS.md; older Claude Code versions still find context via CLAUDE.md → AGENTS.md.
- **Tool-agnostic framing throughout AGENTS.md.** No "Claude," "Anthropic-specific," or "Claude Code" assumptions in the body. Plugin format references are factual ("Claude Code plugin format"), not prescriptive.
- **Same branch as v2 PR (`feat/decision-facilitator-agent`).** Rides with PR #2. Both relate to making the plugin usable across tools.
- **No content additions beyond what's already in CLAUDE.md.** Mirror, don't expand. Future additions can land separately.

## Open Questions

### Resolved During Planning

- Q: Same branch or new? A: Same branch as v2 PR (per Phase 0.7 confirmation).
- Q: Delete CLAUDE.md or keep as redirect? A: Keep as one-line redirect (per Phase 0.7 confirmation).
- Q: Match AGENTS.md to a specific schema? A: No — schema is still emerging; follow common convention.

### Deferred to Implementation

- Exact wording of the redirect line in CLAUDE.md — finalized in U2.
- Whether to include a "How AI agents should interact with this repo" section beyond conventions — start without it; add only if implementation reveals a clear need.

## Implementation Units

- U1. **Create AGENTS.md**

**Goal:** Add `AGENTS.md` at repo root with tool-agnostic content covering project overview, voice/style, file structure, plugin conventions, quality bar, and framework sources.

**Requirements:** R1, R2, R5

**Dependencies:** None.

**Files:**
- Create: `AGENTS.md`

**Approach:**
- Mirror current `CLAUDE.md` sections: Voice & Style, Skill Structure (now broader: file structure + plugin conventions), Quality Bar, Framework Sources.
- Reframe with agent-agnostic phrasing. No "Claude," "Anthropic," or "Claude Code"-specific instructions in the body. Plugin-format references stay factual where structurally true (e.g., "Claude Code plugin format" describes the file layout the plugin uses).
- Add a brief project overview at the top: "Decision Architecture — toolkit of skills, agents, commands, prompts for structured decision-making. Works with any AI coding agent supporting the Claude Code plugin format or equivalent."
- Include the v2 agent format convention (currently the last bullet under Skill Structure in `CLAUDE.md`) as part of the Conventions section.

**Patterns to follow:**
- Existing `CLAUDE.md` for content and voice.
- Standard AGENTS.md examples (from compound-engineering, BMAD plugins) for top-level structure if visible during implementation.

**Test scenarios:**
- Test expectation: none — pure documentation file. Manual verification: a user reading only AGENTS.md (no CLAUDE.md, no README.md) understands the project's voice rules, file structure, and conventions in under 90 seconds.

**Verification:**
- AGENTS.md exists at repo root.
- All sections present: project overview, voice/style, file structure, plugin conventions (including agent format from v1.1), quality bar, framework sources.
- No Claude-specific phrasing in instructions to agents.

---

- U2. **Shrink CLAUDE.md to redirect pointer**

**Goal:** Replace the current content of `CLAUDE.md` with a one-line pointer to `AGENTS.md` so tools that only look for `CLAUDE.md` still resolve context, without duplicating content.

**Requirements:** R3, R4, R5

**Dependencies:** U1 (AGENTS.md must exist first).

**Files:**
- Modify: `CLAUDE.md`

**Approach:**
- Replace full content with a 1-3 line redirect: title + sentence pointing to AGENTS.md. Example:
  ```markdown
  # CLAUDE.md

  Agent context for this repository lives in [AGENTS.md](AGENTS.md). This file is retained for backward compatibility with tools that look for `CLAUDE.md` specifically.
  ```
- Do not duplicate AGENTS.md content here. The whole point is to avoid drift.

**Patterns to follow:**
- The redirect convention used in repos that have already migrated to AGENTS.md (compound-engineering's CLAUDE.md, BMAD's pattern when present).

**Test scenarios:**
- Test expectation: none — pure documentation file. Manual verification: a Claude Code instance opening only `CLAUDE.md` (no AGENTS.md awareness) follows the redirect link to find AGENTS.md.

**Verification:**
- CLAUDE.md is under 5 lines.
- Contains a clear pointer to AGENTS.md (relative link).
- Does not contain duplicated voice rules, file structure, or convention text.

## Risks & Dependencies

| Risk | Mitigation |
|------|------------|
| Older Claude Code versions don't follow CLAUDE.md → AGENTS.md links and lose context | Keep AGENTS.md content readable as a standalone file; the redirect line is a hint, but agents that read CLAUDE.md raw will see the file path and can fetch it. Acceptable risk for the cleanup benefit. |
| AGENTS.md schema standardizes later and our format diverges | Schema is still emerging in 2026. Follow common convention; revise when a real spec lands. Out of scope for this plan. |
| Content in AGENTS.md drifts from skills/agents over time | Plan includes Quality Bar and Framework Sources sections that are stable. Operational drift is a maintenance concern, not a v2 PR concern. |

## Sources & References

- `CLAUDE.md` (current) — source content for AGENTS.md mirror.
- `.claude-plugin/plugin.json` — plugin manifest (not modified).
- ce-plan protocol — confirms AGENTS.md as the primary modern convention.
