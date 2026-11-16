# Contributing

Thank you for your interest in improving Socratic Tutor. Contributions should make the skill clearer, more reliable, more portable, or more effective at supporting genuine learning.

## What you can contribute

- Clarifications to the tutoring protocol.
- Better examples for technical and non-technical topics.
- Edge-case handling for ambiguous intent, frustration, misconceptions, and session resumption.
- Compatibility notes for additional agent environments.
- Documentation improvements and typo fixes.

## Core behavior to preserve

Unless a proposal explicitly discusses a change to the project's direction, contributions should preserve:

1. Explicit tutoring intent before starting a session.
2. A diagnostic before teaching.
3. One question per tutoring turn.
4. Evidence-based progression rather than automatic level awards.
5. Spaced review of earlier subskills.
6. A final mixed assessment before declaring completion.
7. Portable save/resume state without claiming unsupported persistence.

## Pull request process

1. Open an issue first for substantial behavioral changes.
2. Keep each pull request focused on one concern.
3. Explain the problem, proposed change, and expected learner impact.
4. Include an example interaction when changing tutoring behavior.
5. Update the README or documentation when user-facing behavior changes.
6. Check Markdown formatting and verify that the skill frontmatter remains valid YAML.

## Writing guidelines

- Prefer observable instructions over vague advice.
- Keep the tutor direct, patient, and respectful.
- Do not reward effort or confidence as a substitute for demonstrated understanding.
- Do not add platform-specific commands to the core skill unless they are clearly optional.
- Avoid adding runtime dependencies to a project that is intentionally a portable instruction file.

## Commit message suggestions

Use concise, descriptive messages, for example:

```text
docs: clarify installation paths
fix: tighten ambiguous-intent guard
feat: add guidance for learner frustration
```

By submitting a contribution, you confirm that you have the right to submit it under the repository's MIT license. Preserve third-party copyright and attribution notices when modifying upstream-derived material.
