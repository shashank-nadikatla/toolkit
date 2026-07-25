---
inclusion: auto
---

# README Standards

A project README should document the project from the perspective of a new developer or user.

## Audience

Assume the reader has never seen the project before.

Provide enough context for a new developer or user to understand the project without reading the source code.

## Goals

A README should answer:

- What is this project?
- Why does it exist?
- What does it do?
- How do I run it?
- How do I configure it?

## Required Sections

### Overview

Explain:

- Project purpose
- Primary functionality
- Intended users
- Major capabilities

### Features

Summarise major features as a bullet list.

### Tech Stack

Frameworks, languages, databases, infrastructure.

### Folder Structure

Show only directories that help developers understand the project structure.

Do not include generated, temporary, cache, vendor, or dependency directories.

### Installation

Explain how to run locally. Include only commands that actually exist in the project.

### Docker

If Docker configuration exists (Dockerfile, docker-compose.yml, compose.yaml), document how to build and run.

Otherwise omit this section entirely.

### Environment Variables

Document every user-configurable environment variable.

Do not document internal runtime variables (PATH, HOME, CI, PWD, etc.).

Show only key names:

```
API_KEY — Description of what this key is for
DATABASE_URL — Description
```

Never show actual values, tokens, passwords, or secrets.

Explain what each variable is for.

### Configuration

Document configuration files when relevant (e.g., vite.config.js, tsconfig.json).

### API Overview

Summarise endpoint groups briefly.

Do not generate full API documentation — just categories and purpose.

### Architecture

If useful, briefly explain the application's major components and how they interact.

### Contributing

Include only if the project has contributing guidelines.

### License

Include only if a LICENSE file is present.

## Documentation Principles

The README should be:

- Accurate
- Concise
- Beginner-friendly
- Current
- Easy to scan

Prefer executable examples over lengthy explanations whenever practical.

Prefer documenting behaviour over implementation details.

## Never Include

- Passwords, API keys, tokens, or secrets
- Internal debugging notes
- Temporary workarounds
- AI prompts or system instructions
- Personal information
- TODO lists
- Speculative or unimplemented features

## Update Policy

- Only update sections affected by the current changes
- Preserve manually written documentation whenever possible
- Do not rewrite the entire README unnecessarily
- Keep formatting consistent with the existing document style

## Accuracy

- Never invent commands, environment variables, configuration files, APIs, or features.
- If information cannot be determined from the project, omit it rather than guessing.
- Prefer incomplete but accurate documentation over complete but speculative documentation.
