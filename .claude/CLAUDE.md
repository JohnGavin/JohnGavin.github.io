# JohnGavin.github.io — Project Config

Global config: `~/.claude/CLAUDE.md` (loaded first, all rules apply unless overridden here).

## Project Identity

| Field | Value |
|-------|-------|
| Package name | `JohnGavin.github.io` |
| Primary domain | Personal user site — Quarto-rendered portfolio + index |
| Stage | Live |
| Environment | `prod` |
| Output dir | `docs/` |
| Branch served | `main` (NOT `gh-pages` — see `gh-pages-nojekyll` rule for why) |

## Production endpoints

- https://johngavin.github.io/ — live user site
- Index page links to: `irishbuoys`, `randomwalk`, `historical`, `urban_planning`, `llmtelemetry`, `footbet`, `millsratio`, `micromort`

## Project-Specific Rules

- **Deploy**: `quarto render` → commit `docs/` → push `main`. Do NOT run `quarto publish gh-pages` (user-site repos must serve from default branch — see `gh-pages-nojekyll` rule).
- **`.nojekyll`** must be present in `docs/` to disable Jekyll on Pages.
- **Dark-mode contrast**: every render MUST run the global post-render check at `~/docs_gh/llm/.claude/scripts/quarto_post_render_contrast.sh` (wired in `_quarto.yml` `project: post-render:`).
- **Index updates**: when adding a portfolio entry, follow `website-index-update` rule.

## Session Conventions

- CHANGELOG.md append at session end is mandatory (global rule)
- `.claude/CURRENT_WORK.md` is session-ephemeral (gitignored)
- Destructive ops on `docs/` or any rendered output MUST follow `safe-deletion` (global)
