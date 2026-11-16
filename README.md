# Socratic Tutor

**A portable AI tutoring skill that helps learners build understanding through questions, deliberate practice, and demonstrated mastery.**

Socratic Tutor turns a compatible AI assistant into a structured personal tutor. Instead of defaulting to long explanations, it diagnoses what the learner already knows, maps the topic into concrete subskills, asks one question at a time, revisits earlier material, and assesses mastery before declaring a course complete.

> This repository packages an agent skill, not a standalone chatbot or learning platform. It contains instructions that an AI agent can load and follow.

## What it does

- **Intent-aware activation:** ordinary questions receive ordinary answers; tutoring starts only when explicitly requested or confirmed.
- **Diagnostic placement:** 3–5 questions estimate the learner's starting point before instruction begins.
- **Skill map:** each subskill is tracked on a six-level scale, from 0 (unaware) to 5 (able to teach and handle edge cases).
- **Socratic dialogue:** one focused question per turn, with reasoning and application prioritized over passive explanation.
- **Evidence-based progression:** levels are earned through at least two independent checks, including unprompted recall.
- **Spaced review:** earlier skills are revisited, and levels can move down when retention is not demonstrated.
- **Final assessment:** completion requires a mixed assessment with coverage of every subskill and an integrative problem.
- **Portable session state:** `save state` and `resume from:` help transfer progress between conversations.

## Repository structure

```text
socratic-tutor/
├── SKILL.md             # The complete agent skill
├── README.md            # Project overview and usage
├── CONTRIBUTING.md      # Contribution guidelines
├── CODE_OF_CONDUCT.md   # Community standards
├── LICENSE              # MIT license and upstream notice
├── CHANGELOG.md         # Release history
└── docs/
    ├── DESIGN.md        # Design principles and session lifecycle
    └── INTEGRATION.md   # Installation and compatibility notes
```

## Installation

Socratic Tutor follows the common `SKILL.md` convention used by AI coding agents and assistants that support agent skills. The exact skills directory depends on the host.

### Claude Code

For a project-local installation:

```bash
mkdir -p .claude/skills/socratic-tutor
cp SKILL.md .claude/skills/socratic-tutor/SKILL.md
```

For a user-level installation, use the skills directory documented by your Claude Code version, commonly:

```bash
mkdir -p ~/.claude/skills/socratic-tutor
cp SKILL.md ~/.claude/skills/socratic-tutor/SKILL.md
```

### Codex

For a project-local installation:

```bash
mkdir -p .agents/skills/socratic-tutor
cp SKILL.md .agents/skills/socratic-tutor/SKILL.md
```

For a global installation, use the global skills directory supported by your Codex version, commonly `~/.agents/skills/`.

### Other compatible agents

Copy the `SKILL.md` file into the skill directory supported by your agent. Consult that agent's current documentation for the correct location and discovery behavior.

### Plain chat interfaces

If your assistant does not support loading skills, paste the contents of `SKILL.md` into the conversation or an appropriate custom-instructions field, then state the topic you want to learn.

## How to use it

Use explicit requests such as:

- `Teach me the fundamentals of retrieval-augmented generation.`
- `Tutor me on Python decorators.`
- `Quiz me on probability until I can solve problems independently.`
- `Drill me on database indexing.`
- `Help me master gradient descent, including edge cases.`

A one-off request such as `Explain gradient descent` should not start a tutoring session. The skill explicitly protects that boundary.

### In-session commands

| Command | Behavior |
|---|---|
| `show progress` | Display the current skill map. |
| `harder` | Increase question difficulty. |
| `easier` | Reduce question difficulty without revealing the answer. |
| `just tell me` | Explain the current question directly, then return to tutoring. |
| `save state` | Emit a compact, portable learning-state block. |
| `resume from: ...` | Restore a supplied state block and continue. |

## Mastery levels

| Level | Meaning |
|---:|---|
| 0 | Unaware |
| 1 | Heard of it |
| 2 | Can follow along |
| 3 | Can do with help |
| 4 | Can do independently |
| 5 | Can teach it and handle edge cases |

The default completion target is level **4** for every subskill. Level **5** is used when the learner explicitly requests full mastery. A level is not awarded from a single correct answer or self-reported confidence.

## Design principles

1. **Consent before tutoring.** A request for information is not automatically a request for a quiz.
2. **Retrieval before explanation.** Diagnose first; teach after the initial assessment.
3. **One question per turn.** Keep the learner actively reasoning and make evidence interpretable.
4. **Mastery is demonstrated.** Progress depends on independent performance, not time spent.
5. **Review matters.** Earlier skills are revisited and can regress when retention is weak.
6. **No false persistence.** Session state is portable text; durable storage depends on the host agent.

See [DESIGN.md](docs/DESIGN.md) for the session model and [INTEGRATION.md](docs/INTEGRATION.md) for installation notes.

## Compatibility and limitations

- No runtime, backend, database, API key, or package installation is required by the skill itself.
- The host must support skill/instruction files or allow prompt text to be pasted into a conversation.
- Tool-based exercises depend on tools provided by the host agent.
- The skill does not independently store progress, schedule notifications, or guarantee model compliance.

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting an issue or pull request. Preserve the core behavior: explicit intent, diagnostic-before-teaching, one-question turns, evidence-based progression, spaced review, and final assessment.

## Attribution

This repository is an independent packaging and documentation project based on the Socratic Tutor skill published in [Jane Street's `agent_skills` repository](https://github.com/janestreet/agent_skills/tree/master/socratic-tutor). The upstream repository identifies the work as MIT-licensed. See [LICENSE](LICENSE) for the retained upstream notice and license terms.

This project is not affiliated with, endorsed by, or sponsored by Jane Street.

## License

MIT. See [LICENSE](LICENSE).
