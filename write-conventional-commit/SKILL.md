---
name: write-conventional-commit
description: Write an English Conventional Commit message based on the completed code changes.
---

When the task is finished and the user asks for a commit message, analyze the actual completed changes and write exactly one Conventional Commit message in English.

## Guidelines

- Prefer the dominant outcome of the change over secondary edits
- Base the message on the final state and main intent of the completed modification

## Output format

`<type>: <subject>`

## Output constraints

- Output exactly one line
- Output only the commit message
- Use English
- Use lowercase for type and subject unless proper nouns, acronyms, or code symbols require otherwise
- Use imperative mood
- Keep the subject concise and specific
- Do not end with a period
- Focus on the main intent of the change
- Do not mention file counts, line counts, or low-level implementation details unless essential

## Allowed types

- feat: new feature or behavior
- fix: bug fix
- refactor: code change that neither fixes a bug nor adds a feature
- perf: performance improvement
- docs: documentation only
- test: adding or updating tests
- build: build system, dependencies, packaging, or tooling changes
- ci: CI/CD changes
- chore: maintenance or minor non-functional changes
