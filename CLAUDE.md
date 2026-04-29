# CLAUDE.md — Decision Architecture Plugin

## Voice & Style
- Imperative, practitioner language: "Ask X", "Probe Y", "Surface Z"
- No consulting jargon, no corporate speak
- Direct, specific, actionable
- Challenge assumptions by default — anti-sycophancy is a feature

## Skill Structure
- Each skill: YAML frontmatter + imperative guidance
- Skills activate as background context on keyword match
- Commands are user-facing entry points (prefix: `/da:`)
- Cross-reference related skills, don't duplicate content
- **Agents** (added v1.1): `<name>.agent.md` in `agents/` directory. Frontmatter is `name`, `description` (with activation keywords), `model`, `tools`. Body is imperative system prompt with anti-sycophancy core embedded. Agents read `skills/<name>/SKILL.md` at runtime to walk users through them — preserves thread-holding without depending on Skill tool availability. Voice matches skills; no named persona characters.

## Quality Bar
- Useful output on first use (no learning curve)
- Works for coding AND non-coding decisions
- Session takes <15 minutes
- Output is shareable markdown
- Every skill includes the footer linking to ThinkHaven, BMAD-METHOD, and data-product-operator

## Framework Sources
- Decision architecture wiki (Kevin's Obsidian vault)
- BMAD-METHOD analyst (Mary) and architect (Winston) patterns
- BMAD Creative Intelligence Suite (Victor, Dr. Quinn, Maya)
- Nate Jones, Matt Pocock, Stuart Winter-Tear, Alex MH Smith
