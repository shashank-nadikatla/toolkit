---
inclusion: auto
---

# Backlog Standards

`BACKLOG.md` is the project's persistent task backlog — items to address in future sessions.

## Purpose

- Tracks work that was identified but deferred
- Ensures nothing is forgotten across sessions and devices
- Provides future sessions with immediate awareness of pending work

## When to Add

Add to backlog when:

- A task is identified but intentionally deferred
- A bug is found but not fixed in the current session
- A refactor opportunity is noticed but out of scope
- The user says "remind me", "do this later", "add to backlog", or similar
- A limitation or tech debt is discovered during other work

## When to Remove

Remove or mark done when:

- The item is completed during a session
- The item is no longer relevant due to other changes

When completing a backlog item, remove it from BACKLOG.md entirely. Do not leave completed items in the file.

## Format

Items are grouped by priority:

```
## High

- Short actionable title — one or two sentences explaining what and why

## Medium

- Another item — context and affected files if useful

## Low

- Lower priority item — optional suggested approach
```

If priority is unclear, default to Medium.

## Entry Style

- Title should be actionable (verb-first when possible)
- Description should be concise — just enough for a future session to understand the task
- Mention affected files, routes, or components when useful
- Do not include implementation details unless they save significant discovery time

## Rules

- Never add items that are already listed
- Keep the file focused — only items that represent real future work
- Do not add speculative features the user hasn't requested
- Do not add items that were already completed in the current session
- When adding, place under the appropriate priority heading
- When removing, delete the entire bullet

## What Belongs

- Bug fixes deferred to later
- Refactors identified but out of scope
- Feature ideas confirmed by the user
- Technical debt worth addressing
- Security improvements to make later
- UI/UX issues noticed but not fixed

## What Does NOT Belong

- Completed work (that goes in PROJECT_LOG.md)
- Vague ideas without clear action
- Items the user explicitly rejected
- Wishlist features not discussed with the user

## Accuracy

- Never invent backlog items
- Only add work explicitly requested by the user or clearly identified during the current task
- If uncertain whether something belongs in the backlog, do not add it automatically

## Merge Policy

If a new task substantially overlaps an existing backlog item:

- Update the existing item instead of creating a duplicate
- Preserve the original priority unless new information clearly changes it
- Merge additional context into the existing item rather than creating fragmented tasks

## Completion

When a backlog item is completed:

- Remove it from BACKLOG.md
- Record the completed work in PROJECT_LOG.md if it resulted in a meaningful project change

## Update Policy

Only modify BACKLOG.md when the backlog itself changes.

Do not rewrite, reorder, reword, or reformat existing items unless required to:
- Add a new item
- Update an existing item with new information
- Remove a completed or obsolete item
- Merge duplicate items

## Ordering

Within each priority section:

- Append new items to the end
- Do not reorder existing items unless priority changes
