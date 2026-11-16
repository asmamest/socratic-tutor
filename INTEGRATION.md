# Integration Guide

Socratic Tutor is distributed as a single `SKILL.md` file. Install it in the skill directory recognized by your AI agent.

## General steps

1. Clone or download this repository.
2. Create a folder named `socratic-tutor` in the host agent's skills directory.
3. Copy `SKILL.md` into that folder.
4. Restart or reload the agent if required.
5. Explicitly request tutoring, for example: `Tutor me on SQL query optimization.`

## Example project-local locations

```text
# Claude Code-style project skills
.claude/skills/socratic-tutor/SKILL.md

# Codex-style project skills
.agents/skills/socratic-tutor/SKILL.md
```

These are example conventions, not a guarantee that every version or configuration uses these exact paths. Check the host's current documentation.

## Plain chat assistants

If the assistant cannot load skill files, paste the contents of `SKILL.md` into the conversation or a supported custom-instructions field.

## Portability notes

- The skill uses YAML frontmatter and Markdown instructions.
- It has no runtime dependencies.
- Practical exercises require tools supplied by the host.
- Save/resume works through a text state block; it is not automatic database persistence.
