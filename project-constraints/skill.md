---
inclusion: auto
---

# Project Constraints

`CONSTRAINTS.md` documents every engineering constraint that limits future decisions in this project.

## Purpose

- Prevents changes that would break deployment, builds, or infrastructure
- Ensures the agent respects limitations a new contributor wouldn't know
- Acts as a guardrail before proposing architecture, dependency, or infrastructure changes

## What Qualifies as a Constraint

Document every limitation that affects engineering decisions. Common categories include:

- Runtime (language version, execution environment)
- Infrastructure (hosting platform, memory limits, cold starts)
- Deployment (CI/CD pipeline, container registry, static hosting)
- Dependencies (pinned versions, forbidden libraries, license restrictions)
- Security (auth model, key management, RLS policies)
- Architecture (no ORM, no SSR, provider-agnostic, stateless)
- Performance (response time budgets, bundle size limits)
- Build System (toolchain, Node version, Docker base image)
- Hosting (free tier limits, storage quotas, request limits)
- Database (engine, version, connection method, size limits)
- AI/LLM (provider compatibility, prompt format rules)
- External Services (third-party APIs, rate limits, keep-alive requirements)

Only include categories relevant to the project.

## Decision Policy

Before proposing or implementing changes that affect architecture, dependencies, infrastructure, deployment, storage, authentication, build systems, or external services:

- Check whether an existing constraint applies
- Prefer solutions that satisfy all documented constraints
- If no compliant solution exists, explain the conflict
- Do not silently violate constraints

## Constraint Conflicts

If a user request conflicts with documented constraints:

- Explain which constraint is affected
- Explain why the request would violate it
- Suggest one or more compliant alternatives
- If the user explicitly chooses to override the constraint, warn about the consequences before proceeding

## Maintenance

Keep constraints current.

- Add new constraints when engineering limitations are discovered
- Remove constraints that no longer apply
- Update constraints when infrastructure or architecture evolves
- Never leave obsolete constraints in the document

## Writing Style

Each constraint should be:

- One or two lines
- Specific (mention versions, limits, tool names)
- Actionable (what not to do, or what must be preserved)
- Grouped by category

## Accuracy

- Never invent constraints that have not been documented or confirmed
- If a constraint is unclear, reference `CONSTRAINTS.md` at the project root for full details
- Prefer warning the user over silently blocking work
