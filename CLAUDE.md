# CLAUDE.md

Guidance for AI assistants (Claude Code, etc.) working in this repository.

## Repository status

This repo is in an initial / empty state. As of the latest commit it contains only:

- `README.md` — single line: "Love for people"
- `.git/` — fresh history (`Initial commit`)

There is no source code, package manifest, build system, test suite, lint config, or CI yet. The project name is **People**.

Because tooling has not been chosen yet, **do not assume** a language, framework, or directory layout. Confirm with the user before scaffolding anything substantive.

## What to do when asked to build something

1. Ask the user — or infer from their request — what stack they want (language, framework, package manager). Do not pick one unilaterally.
2. Once a stack is chosen, create the canonical layout for it (e.g. `package.json` + `src/` for Node, `pyproject.toml` + `src/people/` for Python) rather than inventing a custom structure.
3. Update this file with the real conventions (build/test/lint commands, directory map, key modules) as soon as they exist. Replace this "initial state" section — don't keep stale guidance around.

## Workflow conventions

### Branching

- The active development branch for AI-assisted work is `claude/add-claude-documentation-11Joc` (or whatever branch the harness specifies for the current session).
- `main` is the default branch. Do **not** push directly to `main` from an AI session; push to the assigned feature branch.
- Create the branch locally if it doesn't exist; never push to a branch other than the one specified for the session.

### Commits

- Make small, focused commits with clear messages that describe the *why*.
- Do not commit unless the user asks. When you do, prefer adding files by name over `git add -A` so secrets/large binaries don't slip in.
- Never use `--no-verify`, `--amend` on already-pushed commits, or destructive operations (`reset --hard`, `push --force`, branch deletion) without explicit user approval.

### Pull requests

- Only open a PR when the user explicitly requests one.
- Use the GitHub MCP tools (`mcp__github__*`) for all GitHub interactions — `gh` CLI is not available in this environment.
- This repo is scoped to `getrichfrfr/people`; do not touch other repositories.

### Pushing

- Use `git push -u origin <branch>`.
- On network failure, retry up to 4 times with exponential backoff (2s, 4s, 8s, 16s). Don't retry on non-network errors — diagnose them.

## Style

- Match whatever conventions exist in the file you're editing. There are none yet, so when introducing the first code, pick widely-used defaults for the chosen stack and document them here.
- Default to no comments unless the *why* is non-obvious.
- Don't create documentation files unless asked. This `CLAUDE.md` is the exception because it was explicitly requested.

## Things not to do

- Don't fabricate architecture diagrams, module overviews, or "key files" sections describing code that doesn't exist.
- Don't add CI, linters, formatters, or test frameworks speculatively — wait for the user to ask, or for a real reason tied to code that's actually being added.
- Don't expand `README.md` beyond what the user wants; its current minimal content appears intentional.
