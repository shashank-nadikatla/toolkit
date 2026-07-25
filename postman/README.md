# Postman Collection Sync

Automatically maintains a Postman collection from API contract changes.

## Files

- **`hook.json`** — Kiro hook definition that triggers on API file saves.
- **`skill.md`** — Steering file with Postman collection standards used by the hook.

## Features

- Automatic synchronization
- First-run project scaffolding
- Monorepo support
- OpenAPI awareness
- Idempotent updates
- Postman Collection v2.1 compliance
- Preserves manual edits

## Installation

Copy the files into your project's `.kiro/` directory:

| Source | Destination |
|--------|-------------|
| `hook.json` | `.kiro/hooks/postman-sync.json` |
| `skill.md` | `.kiro/steering/postman-collection-standards.md` |

Restart Kiro if required.

## What happens

1. Save an API file.
2. Kiro detects API contract changes.
3. Creates or updates the Postman collection.
4. Generates project-specific configuration on first run.
5. Keeps the collection synchronized afterwards.
