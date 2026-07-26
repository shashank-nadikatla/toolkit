# Kiro Skills

Reusable hooks and steering files for [Kiro](https://kiro.dev).

## Available Skills

| Skill | Description |
|--------|-------------|
| Postman | Automatically synchronize Postman collections from API contract changes |
| README | Automatically update README.md when meaningful project changes are made |
| Project Log | Maintain an append-only PROJECT_LOG.md of meaningful changes across sessions |
| Backlog | Track deferred tasks, bugs, and future work in BACKLOG.md |
| Project Constraints | Document engineering limitations in CONSTRAINTS.md and enforce them before changes |

## Installation

Copy the desired skill folder into your project's `.kiro/` directory.

Example:

```
.kiro/
├── hooks/
│   └── project-log.json
└── steering/
    ├── postman-collection-standards.md
    ├── readme-standards.md
    ├── project-log-standards.md
    ├── backlog-standards.md
    └── project-constraints.md
```

See each skill's README for details.
