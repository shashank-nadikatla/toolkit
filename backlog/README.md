# Backlog

Automatically maintains a `BACKLOG.md` file that tracks deferred tasks, bugs, and future work across Kiro sessions.

## Files

- **`skill.md`** — Steering file defining backlog format, entry rules, and maintenance policies.

## Usage

Ask Kiro to add or manage backlog items:

```
add to backlog: refactor auth middleware
```

Kiro will also automatically add items when tasks are identified but deferred during a session.

## Features

- Tracks deferred tasks, bugs, refactors, and tech debt
- Groups items by priority (High / Medium / Low)
- Deduplicates and merges overlapping items
- Removes completed items automatically
- Append-only ordering within priority groups
- Never invents or speculates — only records real work

## Installation

Copy the steering file into your project's `.kiro/` directory:

| Source | Destination |
|--------|-------------|
| `skill.md` | `.kiro/steering/backlog-standards.md` |

Restart Kiro if required.

## What it does

1. During a session, Kiro identifies work that is deferred or out of scope.
2. Adds actionable entries to `BACKLOG.md` under the appropriate priority.
3. When a backlog item is completed, removes it and records the work in `PROJECT_LOG.md`.
4. Never rewrites, reorders, or reformats existing items unless necessary.
