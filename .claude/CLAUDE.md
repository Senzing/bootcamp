# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

The landing page for the Senzing Agentic AI Bootcamp, published with GitHub Pages at
`https://hub.senzing.com/bootcamp/`. It pitches the bootcamp and sends a potential
Bootcamper to one of three platform pages:

- Claude: `https://hub.senzing.com/senzing-bootcamp-claude-plugin`
- Kiro: `https://hub.senzing.com/senzing-bootcamp-kiro-power`
- ChatGPT: `https://hub.senzing.com/senzing-bootcamp-chatgpt-plugin`

Page content (modules, outcomes, requirements, plan minimums) is adapted from the READMEs of
`Senzing/senzing-bootcamp-claude-plugin`, `Senzing/senzing-bootcamp-kiro-power` and
`Senzing/senzing-bootcamp-chatgpt-plugin`. When those change, check the page still matches.

## Layout

- `docs/index.html`: the single page. Hand-written HTML, no JavaScript.
- `docs/index.css`: hand-written stylesheet; brand colors are custom properties on `:root`.
- `docs/.nojekyll`: files are served as-is, with no Jekyll processing.
- `docs/images/`: logo, 32 px favicon, 180 px apple-touch icon, promo video poster.
- `docs/video/`: the two-minute promo video (MP4, captions burned in), played on demand in the
  `#watch` section.

There is no build step, package manager, framework or test suite.

## Conventions

- **Style:** the Senzing "Obsidian & Ember" brand system (the `senzing-brand` skill): dark nav
  and hero, alternating white / warm off-white body sections, dark closing call to action and
  footer; Roboto from Google Fonts; the ember gradient only for hero accents and the primary
  call to action.
- **Paths must be relative** (`images/logo.png`, not `/images/logo.png`). The site is served
  under `/bootcamp/`, so a root-absolute path resolves against the `hub.senzing.com` root
  (`Senzing/senzing.github.io`) and breaks.
- **External resources:** only Google Fonts. No analytics, cookies or third-party scripts.
- **Phone width:** no horizontal scroll at 360 px.

## Checks

The spellcheck is the only CI check that applies to `docs/`. Run it locally with:

```bash
npx --yes cspell@9 lint --config .vscode/cspell.json --no-progress --gitignore "**"
```

Add new product or brand terms to `words` in `.vscode/cspell.json`. `lint-workflows`
(super-linter) runs only when `.github/workflows/**` changes.

To preview, open `docs/index.html` in a browser. `main` requires signed commits and an
approving code-owner review.

## Publishing

`hub.senzing.com` is the custom domain of `Senzing/senzing.github.io`, so this repo's Pages
site appears at `/bootcamp/`. Pages is enabled in this repo's settings (deploy from branch
`main`, folder `/docs`), so every merge to `main` publishes the page. After a merge, check the
build with `gh api repos/Senzing/bootcamp/pages/builds/latest` and the live page.

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
