# Project Constraints

Maintains a `CONSTRAINTS.md` file that documents engineering limitations Kiro must respect before proposing changes.

## Files

- **`skill.md`** — Steering file defining what qualifies as a constraint, how to enforce them, and how to handle conflicts.

## Usage

Ask Kiro to add or check constraints:

```
add constraint: must use Node 20 LTS
```

Kiro will also automatically check `CONSTRAINTS.md` before proposing architecture, dependency, or infrastructure changes.

## Features

- Documents runtime, infrastructure, deployment, and dependency limitations
- Acts as a guardrail before architectural decisions
- Warns when a request conflicts with a documented constraint
- Suggests compliant alternatives when conflicts arise
- Keeps constraints current — removes obsolete ones, adds newly discovered ones
- Never silently violates a constraint

## Installation

Copy the steering file into your project's `.kiro/` directory:

| Source | Destination |
|--------|-------------|
| `skill.md` | `.kiro/steering/project-constraints.md` |

Restart Kiro if required.

## What it does

1. Before proposing changes to architecture, dependencies, infrastructure, or deployment, Kiro checks `CONSTRAINTS.md`.
2. If a constraint applies, Kiro respects it or explains the conflict.
3. When new limitations are discovered, they are added to `CONSTRAINTS.md`.
4. Obsolete constraints are removed as infrastructure evolves.
