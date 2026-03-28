---
name: git-msg
description: Generate an English Conventional Commit message from a provided git diff.
---

Based on the provided git diff, write exactly one Conventional Commit message in English.

## Guidelines

- Infer the commit intent from the actual diff content
- Prioritize the main developer-intent outcome over raw edit descriptions

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
