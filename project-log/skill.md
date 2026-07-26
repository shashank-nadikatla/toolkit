---
inclusion: auto
---

# Project Log Standards

`PROJECT_LOG.md` is the project's persistent memory — an append-only audit trail of meaningful changes across sessions, devices, and contributors.

## Purpose

- Provides continuity across chat sessions
- Synchronises context across devices and contributors
- Records decisions and rationale for future reference
- Enables any new session to understand recent history immediately

## Format

Entries are grouped under date headers:

```
## YYYY-MM-DD
- Entry describing one logical change
```

If today's date header already exists, append under it. Otherwise add a new date header at the end.

## Entry Style

Each entry should:

- Begin with a verb (Added, Fixed, Removed, Changed, Refactored, Created, Moved)
- Describe one logical change per bullet
- Mention affected files, routes, or modules when useful
- Be factual and specific
- Be exactly one bullet point
- Be one or two lines maximum
- Include reasoning only when the decision is non-obvious

## What to Log

- Features added, removed, or changed
- Bug fixes
- Refactors that change architecture or public behaviour
- API changes (routes, methods, payloads)
- Schema or database changes
- Dependency additions or removals
- Configuration or environment variable changes
- Docker or infrastructure changes
- CI/CD pipeline changes
- Build or deployment changes
- AI prompts, hooks, or steering files that affect future behaviour
- Security fixes or performance improvements

## What NOT to Log

- Formatting or whitespace changes
- Typos or comment edits
- Variable renames
- Code movement without behaviour change
- Generated file updates (lockfiles with no dependency change)
- Trivial refactors that don't change interfaces

## Append-Only Rules

- Always append to the end
- Never reorder history
- Never edit historical entries
- Never delete historical entries
- Corrections should be appended as new entries

## Duplicate Detection

- Read the existing PROJECT_LOG.md before appending
- Do not append an entry if the same change has already been recorded
- Group related changes into one concise bullet when they form a single logical unit

## Grouping

- If multiple changes serve one purpose, combine into a single entry
- Example: "Added defensive guardrails to all master prompts for short JDs" (not 5 separate bullets per prompt function)

## Accuracy

- Never invent changes that did not occur.
- Base entries only on work completed during the current task.
- If a change cannot be confirmed, omit it rather than speculate.
- Prefer concise, factual summaries over detailed narratives.

## Exclusions

Persistent project knowledge excludes temporary experiments, abandoned work, exploratory code, debug-only changes, and reverted changes.
