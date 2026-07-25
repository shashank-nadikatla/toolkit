# README Auto-Update

Automatically updates the project's README.md when meaningful changes are made during a Kiro session.

## Files

- **`hook.json`** — Kiro hook definition. Triggers at the end of each session to evaluate whether README updates are needed.
- **`skill.md`** — Steering file defining README structure, content standards, and documentation principles.

## Features

- Triggers automatically at the end of every Kiro session
- Updates only sections affected by changes
- Skips formatting-only, refactoring, or internal changes
- Preserves manually written documentation
- Follows consistent README standards

## Installation

Copy the files into your project's `.kiro/` directory:

| Source | Destination |
|--------|-------------|
| `hook.json` | `.kiro/hooks/readme-update.json` |
| `skill.md` | `.kiro/steering/readme-standards.md` |

Restart Kiro if required.

## What happens

1. A Kiro session ends.
2. The hook evaluates whether changes affect public documentation.
3. If relevant changes are detected, README.md is updated following the standards in `skill.md`.
4. Only affected sections are modified; the rest is preserved.
