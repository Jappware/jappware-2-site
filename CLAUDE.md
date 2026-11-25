# CLAUDE.md — Jappware 2.0 website

Read this at the start of every session. It is the memory of this repo: what the site is, what it must say, what it must never say, and how to ship a change. Keep it short. When a mistake repeats, add one rule here; when a rule goes stale, delete it.

## 1. What this repo is

The public one-page site for **Jappware 2.0** — an AI-native software delivery company from Lviv.
Live: https://jappware.github.io/jappware-2-site/

The site sells one idea: **a senior engineer plus our agent framework delivers a working, tested product in days instead of months, priced by the outcome, never by the hours.**

Primary readers: CEOs/founders holding a 6-month estimate, and sceptical CTOs. Every block must answer "what does the reader learn here, and what do they do next?" If a block has no answer, it goes.

## 2. Source of truth

Content decisions come from the company manifestos (in the Claude project "Jappware 2.0 Rebirth — Site Studio", not in this repo):

- **Jappware 2.0** (founder, Andrii Rymar) — origin story, "AI is the first lens, not the cherry on top", the telescope metaphor.
- **Delivery & Engineering manifesto** — the chain instead of one-shot, the 8 principles, Organizational Intelligence, pricing by result.

If a requested change contradicts a manifesto, say so and propose a version that fits. Do not "improve" copy away from the manifesto voice.

## 3. Repo layout and stack

```
index.html   # the whole site: markup, inline <style>, one small inline <script>
README.md    # short human readme + placeholder list
```

- Plain static HTML. **No build step, no framework, no npm.** Do not introduce one without an explicit request.
- Styles live in the single `<style>` block in `<head>` (classes under `.jw`) plus inline `style=""` attributes from the original design export. Prefer reusing existing classes over adding new inline styles.
- The only JS is the case-study tab switcher (`[role="tab"]` + `aria-controls` + `hidden`). Keep it dependency-free.
- One breakpoint: `@media (max-width:760px)`. Every change must work at 375px width with no horizontal scroll.

## 4. Deploy

- GitHub Pages. Per README, Pages serves from the **`gh-pages`** branch. Check `Settings → Pages` before the first deploy of a session if unsure, and keep `main` and the published branch in sync.
- Flow: edit on `main` → commit → publish to the Pages branch → open the live URL and confirm the change is visible (Pages can lag 1–2 minutes; hard-refresh).
- A deploy is not done until you have seen the change on the live URL. "Pushed" is not "deployed".

## 5. Page map (top to bottom)

| Anchor | Block | Job |
|---|---|---|
| `#top` | Hero | The claim: "They quoted six months. We had it working in five days." CTA: call |
| — | Numbers strip | Verified CopyTrader facts only |
| — | Pains | "Sound familiar": long estimates, slipping roadmaps, untrusted AI output |
| `#value` | What you get | Week-one version, outcome price, code you own, one accountable engineer |
| `#lens` | The first lens | Pyramid → telescope (manifesto metaphor). Candidate to shorten |
| `#how` | How it works | One-shot vs the chain: Idea → Research → Requirements → Architecture → Design → Code → Tests → Deploy |
| — | The crew | 10 agents of our framework + the accountable senior engineer |
| `#cases` | Proof | CopyTrader + "Your project — bring your estimate" |
| `#pricing` | Pricing | Results, not hours. 3 offers with price placeholders |
| — | Speed = less risk | Manifesto principle 5 |
| `#manifesto` | 8 principles | Short versions of the Delivery manifesto principles |
| — | Built on experience | Organizational Intelligence: skills, rules, agents |
| — | Founder quote | Andrii Rymar |
| `#contact` | Final CTA | "Bring us the project they quoted six months for." |

## 6. Copy rules (non-negotiable)

Site copy is **English**. Discussion with the team is Ukrainian.

**Facts.** Never invent facts: clients, numbers, awards, logos, testimonials. If something is missing, write `[NEEDS DATA: …]` in the source and tell the user. Verified facts as of 2026-11-25:

- CopyTrader (fintech, copy trading): client's own estimate ~6 months, team of 3. Jappware: working, spec-verified **dev-level** build in **5 days**, 1 senior engineer + agents. **Not in production yet** — may be mentioned openly.
- The 10 specialist agents (Researcher, Strategist, Analyst, Devil's Advocate, Critic, Explorer, Pen-Keeper, Test-Author, Implementer, Reviewer) are real: our own delivery framework.
- **Unverified — do not put back without confirmation:** "70+ products", "50+ engineers in Lviv", "23 skills", any dollar figures, the Night Shore case.

**Honesty (manifesto principle 8).**
- "Working" / "a working build", never "shipped" or "launched" for CopyTrader until it is live.
- No superlatives we cannot prove ("fastest", "best", "guaranteed").

**Pricing (manifesto principle 1).**
- Never show our internal cost or effort in money ($10k vs $170k style). It invites the client to cut the budget to our cost.
- Never mention hours, man-days, man-months or rates. If "hours" appears anywhere except "not hours", something is wrong.
- Show time and risk saved, not our cost. Fixed price per outcome is the default; any ongoing offer is framed by releases and quality in production, never as a rented team.

**Voice.**
- Direct, concrete, engineer-to-business. Short sentences. The reader is "you", Jappware is "we".
- Banned: "innovative solutions", "trusted partner", "cutting-edge", "leverage synergies", "end-to-end", "world-class", "passionate team".
- Prefer proof over adjectives: "Whoever wrote the code never approves it" beats "rigorous QA".

**Open placeholders** (must be replaced before showing externally): `[CONTACT EMAIL]`, `[FIXED PRICE]`, `[FROM PRICE]`, `[MONTHLY PRICE]`. No contact form or calendar yet — "Book a call" is a `mailto:`.

## 7. Visual system

Dark, calm, technical. One accent, used sparingly.

| Token | Value | Use |
|---|---|---|
| Background | `#0B0D0C` | Page |
| Surface | `#121614` | Cards, dark bands |
| Line | `#1E2421` / `#232A26` | Borders, dividers |
| Text | `#EEF0EA` / `#FFFFFF` | Headings, primary text |
| Muted | `#C2C8C3` → `#A3ABA5` → `#8E968F` | Body, captions, "old way" values |
| Light band | `#EEF0EA` bg, `#0B0D0C` text | `#how`, `#pricing` |
| Accent | `#F9CF0B` | The key number/word, primary button, kicker dot. Max one accent focus per block |

Type: **Space Grotesk** (headings, `.h`, tight tracking), **Inter** (body), **JetBrains Mono** (kickers, labels, `.mono`, uppercase). Loaded from Google Fonts.

Patterns to reuse: `.kicker` above every H2, `.btn .btn-y` (primary) / `.btn-o` (secondary) / `.btn-d` (on light), `.tag`, rounded cards (18–24px radius), 120px section padding. The "old way vs Jappware" comparison is always grey (old) vs white/accent (new).

Accessibility: keep heading order (one H1), `aria-*` on tabs, `aria-hidden` on decorative shapes, text contrast ≥ 4.5:1 (muted greys only on `#0B0D0C`/`#121614`).

## 8. How to work in this repo

We follow our own chain, not one-shot:

1. **Understand.** Restate the change and which manifesto thesis it serves. Ask if the goal is unclear.
2. **Edit small.** Targeted edits in `index.html`; never rewrite the file from a truncated read.
3. **Verify.** Open the page (local `python3 -m http.server` or the live URL): desktop and 375px, tabs still switch, no console errors, no broken anchors.
4. **Check copy against §6.** Grep for `shipped`, `hours`, `$`, `70+`, `50+`, `Night Shore`, banned clichés.
5. **Commit** with a message that says what changed and why (e.g. `Cases: remove cost figures (manifesto: results, not hours)`).
6. **Deploy and confirm on the live URL** (§4).
7. **Report** in 1–3 lines: what changed, what is live, any `[NEEDS DATA]` left.

Say "I don't know" or "not verified" instead of guessing — about facts, about Pages settings, about whether something rendered.

## 9. Backlog (next steps agreed with the team)

- Deploy the hero + cases revision ("We had it working in five days", verified numbers strip, no cost figures, Night Shore → "Your project") if it is not live yet.
- "Domains we've lived in" block (manifesto principle 4) — `[NEEDS DATA: list of domains]`.
- Real conversion path: contact form or calendar instead of `mailto:`.
- Shorten or move the telescope block; it explains our mindset more than the client's gain.
- Entry point for candidates (careers), later.
- Long term: move from the design-export markup to a maintainable stack (SEO, forms, performance) — only when explicitly requested.
