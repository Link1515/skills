---
name: git-msg
description: Generate a Conventional Commit message by git diff
---

Based on the provided git diff, generate a single Conventional Commit message that best describes the change.

Requirements:
- Follow the Conventional Commits format exactly:
  type(scope): summary
- Use only one of these types:
  feat, fix, docs, refactor, test, chore, ci, build, perf
- Choose the most appropriate type based on the actual intent of the change.
- Add a scope only when it is clear and useful from the diff.
- If the scope is unclear or too broad, omit it and use:
  type: summary
- Write the summary in imperative mood.
- Keep the summary concise and specific.
- Use lowercase for type, scope, and summary unless code symbols or proper nouns require otherwise.
- Do not end the summary with a period.
- Do not mention file counts, line counts, or implementation details unless they are essential to the intent.
- Focus on the user-visible or developer-intent outcome of the change, not a raw description of edits.

Selection guidance:
- feat: a new feature or behavior
- fix: a bug fix
- docs: documentation-only changes
- refactor: code changes that neither add a feature nor fix a bug
- test: adding or updating tests
- chore: maintenance, cleanup, or non-functional project tasks
- ci: CI/CD pipeline or workflow changes
- build: build system, dependencies, packaging, or tooling setup changes
- perf: performance improvements

Scope guidance:
- Prefer a short functional area, module, package, or feature name.
- Examples: auth, api, ui, billing, search, config
- Do not invent a highly specific scope if the diff does not support it.

Output rules:
- Output exactly one line.
- Output only the commit message.
- Do not include backticks, quotes, explanations, alternatives, bullets, or prefixes like "Suggested commit:".

Examples:
- feat(auth): add refresh token validation
- fix(api): handle missing pagination params
- docs: update local setup instructions
- refactor(ui): simplify modal state handling
- test(search): add coverage for empty query case
- chore: clean up unused helper functions
- ci: add pull request lint workflow
- build: update vite configuration
- perf(cache): reduce repeated serializer calls