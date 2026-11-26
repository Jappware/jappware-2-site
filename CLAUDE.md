# CLAUDE.md — Jappware 2.0 site

Static one-page site. Everything lives in `index.html` (no build step).
GitHub Pages serves it from the `gh-pages` branch, so keep `main` and `gh-pages` in sync when you ship.

## Brand source of truth: "Visual identity & brand system"

Jappware's brand guidelines live in the claude.ai **Organization project "Visual identity & brand system"**
(Projects → Organization, owned by the Jappware team on claude.ai).

**Before any visual, copy or layout change, follow that brand system.**
That covers colors, typography, logo usage, spacing, radii, imagery, tone of voice and UI components.

- **In a claude.ai chat inside that project (or in "Jappware 2.0 Rebirth — Site Studio"):**
  the project knowledge is already in context. Use it directly.
- **In Claude Code (CLI, desktop or cloud):** Claude Code cannot open claude.ai Projects.
  Read the exported copy in `brand/` in this repo instead.
  If `brand/` is missing or looks outdated, **stop and ask the user** to export the latest files
  from the project into `brand/`. Do not guess brand values.
- If the brand system and `index.html` disagree, the brand system wins.
  Point out the mismatch rather than silently copying the old value.

## Current tokens used in `index.html`

These are for orientation only and may drift. Verify them against the brand system.

- Background `#0B0D0C`, surfaces `#121614` / `#1E2421` / `#232A26`, borders `#3A423D`
- Text `#EEF0EA` (primary), `#C2C8C3`, `#A3ABA5`, `#8E968F` (muted)
- Accent yellow `#F9CF0B`
- Fonts: Space Grotesk (headings), Inter (body), JetBrains Mono (kickers and labels)

## Before going live

Replace the placeholders `[CONTACT EMAIL]`, `[FIXED PRICE]`, `[FROM PRICE]` and `[MONTHLY PRICE]`.
