# Project Log

Automatically maintains an append-only `PROJECT_LOG.md` that records meaningful changes across Kiro sessions.

## Files

- **`hook.json`** — Kiro hook definition. Triggers at the end of each session to evaluate whether new entries should be appended.
- **`skill.md`** — Steering file defining the log format, entry style, and append-only rules.

## Features

- Triggers automatically at the end of every Kiro session
- Append-only — never edits or deletes history
- Deduplicates entries before appending
- Groups related changes into single logical entries
- Provides continuity across sessions, devices, and contributors

## Installation

Copy the files into your project's `.kiro/` directory:

| Source | Destination |
|--------|-------------|
| `hook.json` | `.kiro/hooks/project-log.json` |
| `skill.md` | `.kiro/steering/project-log-standards.md` |

Restart Kiro if required.

## What happens

1. A Kiro session ends.
2. The hook evaluates whether any persistent project knowledge changed (features, bugs, APIs, config, dependencies, etc.).
3. If changes are detected, reads the existing `PROJECT_LOG.md` and appends a summary under today's date.
4. Skips if the change was already recorded.

## Log format

Entries are grouped under date headers:

```
## 2025-07-25
- Added Postman collection auto-sync hook and steering file
```

See `skill.md` for full format and style rules.
