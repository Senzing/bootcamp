# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This repository is currently empty. It exists as a starting point — the workflows,
linter configs, and contribution scaffolding under `.github/`, `.vscode/`, and `.claude/`
are the canonical Senzing baseline, but no project code lives here yet.

When work begins, replace this section with:

- A short description of what the repository builds or contains.
- Build / test / lint commands (typically driven by `make`).
- Notable architecture decisions or external dependencies a contributor needs to know.
- Any CI/CD workflows specific to this project (beyond the standard add-labels /
  add-to-project / dependabot / lint-workflows / spellcheck baseline that's already wired up).

## CI/CD Workflows (baseline)

- `add-labels-standardized.yaml` — labels new/reopened issues.
- `add-to-project-senzing.yaml` / `add-to-project-senzing-dependabot.yaml` — adds issues
  and Dependabot PRs to the Senzing project board.
- `claude-pr-review.yaml` — runs Claude review on PR open/synchronize.
- `dependabot-approve-and-merge.yaml` — auto-approves and merges Dependabot PRs.
- `link-issues-to-pr-post-merge.yaml` — closes referenced issues when a PR merges.
- `lint-workflows.yaml` — super-linter pass over `.github/workflows`.
- `move-pr-to-done-dependabot.yaml` — moves merged Dependabot PRs to "Done" on the board.
- `spellcheck.yaml` — cspell over the repo.
