# Git Commit Instructions

## 1. Purpose
Consistent, readable commit history using Conventional Commits.

## 2. Format
`type(scope): subject`
- Subject: imperative, active voice, lower case (except proper nouns), <= 50 chars, no trailing period.
- One scope only (optional); if multiple are truly needed, prefer separate commits.

## 3. Allowed types
`feat` new functionality  
`fix` bug fix  
`docs` documentation only  
`style` formatting (no code meaning change)  
`refactor` code change not fixing bug or adding feature  
`perf` performance improvement  
`test` adding or updating tests  
`chore` maintenance (build, deps, infra)  
`ci` continuous integration configuration

## 4. Scope (examples)
`api`, `ui`, `auth`, `db`, `build`, `deps`, `config`.  
Use concise, stable identifiers. Omit if unclear.

## 5. Body
- Separate from subject by a blank line.
- Wrap at 72 chars.
- Explain what and why (avoid how if diff is clear).
- Include rationale, side effects, migration notes.
- Use bullet points `*` for lists.
- Reference issues: `Refs #123` or `Fixes #456`.

## 6. Examples

Good:
```
feat(api): add rate limiting middleware

Introduce token bucket limiter:
- configurable per route
- emits metrics (rate.limit.used)
```

Good:
```
refactor(db): unify connection pools

BREAKING CHANGE: remove per-module pool settings.
```

Bad (reasons: past tense, vague):
```
feat(ui): Added stuff
```

## 7. Checklist (before committing)
- Subject <= 50 chars
- Imperative mood
- Correct type & optional scope
- Meaningful body (if non-trivial change)
- Issues referenced
- Breaking change noted
- No trailing period in subject

## 8. Quick reference
`feat|fix|docs|style|refactor|perf|test|chore|ci`