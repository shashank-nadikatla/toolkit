# README Auto-Update

Automatically updates the project's README.md when meaningful changes are made during a Kiro session.

## Files

- **`skill.md`** — Steering file defining README structure, content standards, and documentation principles.

## Features

- Updates only sections affected by changes
- Skips formatting-only, refactoring, or internal changes
- Preserves manually written documentation
- Follows consistent README standards
- Never includes secrets, speculative features, or AI instructions

## Installation

Copy the steering file into your project's `.kiro/` directory:

| Source | Destination |
|--------|-------------|
| `skill.md` | `.kiro/steering/readme-standards.md` |

Restart Kiro if required.

## Usage

Ask Kiro to update your README:

```
update readme
```

Kiro will follow the standards defined in `skill.md` to update only the relevant sections based on your current project state.

## What it does

The steering file instructs Kiro to keep your README accurate and up-to-date by following a defined structure (overview, features, tech stack, installation, etc.) and a strict set of documentation principles — only updating what changed, never guessing, and never exposing secrets.
