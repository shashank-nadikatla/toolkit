# Postman Collection Sync

Automatically maintains a Postman collection from API contract changes.

## Files

- **`hook.json`** — Kiro hook definition.
- **`postman-steering.md`** — Generic Postman collection standards used by the hook.

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
| `postman-steering.md` | `.kiro/steering/postman-collection-standards.md` |

Restart Kiro if required.

## What happens

1. Save an API file.
2. Detect API contract changes.
3. Create or update the Postman collection.
4. Generate project-specific configuration on first run.
5. Keep the collection synchronized afterwards.
