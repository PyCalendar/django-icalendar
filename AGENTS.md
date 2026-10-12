# Agent Guidelines

Generated from [browniebroke/pypackage-template](https://github.com/browniebroke/pypackage-template).

## Branches

Never commit to `master`. Always use a feature branch.

## Commits

Follow [Conventional Commits](https://www.conventionalcommits.org): `type(scope): description`
Types: `feat`, `fix`, `docs`, `chore`, `refactor`, `test`
`commitizen` hook enforces this — never skip with `--no-verify`.

Prefer atomic commits. A PR should tell a coherent story through its commit history.
No fixup commits — rebase instead to keep history clean on PR branches.

## AI use

Follow the [pycalendar AI policy](https://pycal.org/ai-policy/). For any commit you (an AI agent) write:

- In the commit body, add an `AI disclosure:` paragraph naming the exact model and version and briefly summarizing what you did.
- For `feat`/`fix` commits, also add a line `NOTICE: AI-assisted with <model-id>` so it appears in the changelog.
- Never claim human review or testing that hasn't happened.
- Don't remove the `AI Prompts:` section the `ai-prompt-auto-commit` hook appends.

Claude Code records prompts automatically (`.claude/hooks/record-prompt.py`). Other assistants should record them as described in [.github/assistant-guidelines.md](.github/assistant-guidelines.md).

## Pre-commit

Hooks run automatically on commit. Install once with `pre-commit install` (installs all hook types).

## Tests

```shell
uv run pytest
```

## Releases

Automated via GitHub Actions + `python-semantic-release`. Do not trigger manually.
Commit types determine version bumps: `feat` → minor, `fix` → patch, breaking → major.
`chore`/`docs`-only commits won't trigger a release.

## Tooling

- `uv` — package manager (`uv sync` to install deps)
- `ruff` — lint/format
- `mypy` — type checking
- Renovate — automated dependency updates
