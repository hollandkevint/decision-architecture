# AGENTS.md

Context for AI coding agents (Claude Code, Codex, Cursor, Gemini, and any other tool reading this file) working in the Decision Architecture repository.

This file is the canonical agent context. `CLAUDE.md` redirects here for backward compatibility.

## Project

Decision Architecture is a structured-thinking toolkit for making better decisions before you build. It ships as a Claude Code plugin (skills, agents, commands, prompts, frameworks). The prompts and frameworks are also designed to be portable to any LLM-driven workflow.

## Voice & Style

- Imperative, practitioner language: "Ask X", "Probe Y", "Surface Z"
- No consulting jargon, no corporate speak
- Direct, specific, actionable
- Challenge assumptions by default — anti-sycophancy is a feature

## File Structure

| Path | Purpose |
|------|---------|
| `skills/<name>/SKILL.md` | Background-context skills (Claude Code: activate on keyword match) |
| `agents/<name>.agent.md` | Foreground agents (Claude Code: invoke via slash command or @-mention) |
| `commands/<name>.md` | User-facing entry points (Claude Code prefix: `/da:`) |
| `prompts/` | Standalone prompts that work with any LLM |
| `frameworks/` | Reference documents for decision practice |
| `docs/brainstorms/` | Origin requirements documents |
| `docs/plans/` | Implementation plans |
| `.claude-plugin/plugin.json` | Plugin manifest |

Tools other than Claude Code can read the prompts and frameworks directly. Skills and agents follow the Claude Code plugin format; equivalent invocation patterns vary by tool.

## Conventions

- Each skill: YAML frontmatter (`name`, `description`, `user-invocable`) plus imperative guidance. Cross-reference related skills, don't duplicate content.
- Each agent (added v1.1): `<name>.agent.md` in `agents/`. Frontmatter is `name`, `description` (with activation keywords), `model`, `tools`. Body is imperative system prompt with anti-sycophancy core embedded. Voice matches skills; no named persona characters. Agents are self-contained — they inline the question lists and templates they need rather than reading sibling skill files at runtime.
- Plugin manifest at `.claude-plugin/plugin.json` declares metadata. Directory-based discovery handles `skills/`, `commands/`, `agents/`.

## Quality Bar

- Useful output on first use (no learning curve)
- Works for coding AND non-coding decisions
- Session takes under 15 minutes
- Output is shareable markdown
- Every skill includes the footer linking to ThinkHaven, BMAD-METHOD, and data-product-operator

## Framework Sources

- Decision architecture wiki (curated practitioner notes)
- BMAD-METHOD analyst (Mary) and architect (Winston) patterns
- BMAD Creative Intelligence Suite (Victor, Dr. Quinn, Maya)
- Nate Jones, Matt Pocock, Stuart Winter-Tear, Alex MH Smith
