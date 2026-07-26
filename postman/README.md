# Postman Collection Sync

Automatically maintains a Postman collection from API contract changes.

## Files

- **`skill.md`** — Steering file with Postman collection standards and sync rules.

## Usage

Ask Kiro to sync your Postman collection:

```
update postman
```

Kiro will detect API contract changes and create or update the Postman collection accordingly.

## Features

- Automatic synchronization on demand
- First-run project scaffolding
- Monorepo support
- OpenAPI awareness
- Idempotent updates
- Postman Collection v2.1 compliance
- Preserves manual edits

## Installation

Copy the steering file into your project's `.kiro/` directory:

| Source | Destination |
|--------|-------------|
| `skill.md` | `.kiro/steering/postman-collection-standards.md` |

Restart Kiro if required.

## What happens

1. You ask Kiro to update Postman.
2. Kiro detects API contract changes (routes, schemas, DTOs, middleware, etc.).
3. Creates or updates the Postman collection.
4. Generates project-specific configuration on first run.
5. Keeps the collection synchronized on subsequent requests.
