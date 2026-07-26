# Kiro Skills

Reusable hooks and steering files for [Kiro](https://kiro.dev).

## Available Skills

| Skill | Description |
|--------|-------------|
| Postman | Automatically synchronize Postman collections from API contract changes |
| README | Automatically update README.md when meaningful project changes are made |
| Project Log | Maintain an append-only PROJECT_LOG.md of meaningful changes across sessions |

## Installation

Copy the desired skill folder into your project's `.kiro/` directory.

Example:

```
.kiro/
├── hooks/
│   └── postman-sync.json
└── steering/
    └── postman-collection-standards.md
```

See each skill's README for details.
