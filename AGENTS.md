# AGENTS.md — Portfolio Showcase

Canonical rules for any AI agent (Claude Code, Codex, Cursor, etc.) working in this repo.
Read this whole file before changing anything.

## 1. Purpose
A static personal portfolio. The owner adds one **work page** per project (course project,
design, code, writing). The site must stay fast, readable and easy to extend by
copy-paste. Goal of these rules: a new work page can be added in minutes with no redesign.

Audience: teachers, classmates, and recruiters skimming on a phone or laptop.
Language: page text in English; keep `lang="en"`. If the owner asks for Chinese, copy the
page and set `lang="zh-Hant"`, do not mix languages inside one page.

## 2. Tech constraints (do not break)
- Plain HTML + one shared CSS file. **No build step, no framework, no npm, no JS libraries.**
- Hosted on GitHub Pages, so every link and asset path must be **relative**
  (`../assets/style.css`, never `/assets/style.css`).
- Only JavaScript allowed: small inline scripts (e.g. a copy button). None needed by default.
- Fonts: Google Fonts only (Bricolage Grotesque + Source Serif 4), with system fallbacks.
- Every page works without JS and at 360px width.

## 3. Structure
```
index.html              Home: intro + list of all works (newest first)
works/_template.html    Copy this to start a new work page. Never list it on the home page.
works/<slug>.html       One file per work
assets/style.css        The ONLY stylesheet. All design tokens live in :root
assets/img/<slug>-<n>.<ext>   Images for a work, e.g. paper-lantern-1.jpg
docs/                   Notes for the owner (deploy guide). Not published content.
AGENTS.md / CLAUDE.md   These rules (CLAUDE.md just imports AGENTS.md)
```

## 4. Naming
- `<slug>`: lowercase, ASCII, words joined by hyphens, 2–4 words (`paper-lantern`, `tide-table`).
- Images: `<slug>-<n>.jpg|png|webp`, n starts at 1. Max ~300 KB each; convert/resize if larger.
- Never rename or delete an existing work file (links may be shared). To retire a work,
  remove its row from `index.html` only and tell the owner.

## 5. Design system (defined in `assets/style.css`)
| Token | Value | Use |
|---|---|---|
| `--paper` | `#EDF1EF` | page background |
| `--ink` | `#1B2A33` | text |
| `--muted` | `#5C6F78` | secondary text |
| `--line` | `#C5D0CC` | dividers |
| `--accent` | `#2D55D6` | links, the one highlight per page |

- Headings: Bricolage Grotesque. Body: Source Serif 4 at ~1.125rem, line length ≤ 68ch.
- Layout: a single left-aligned column (`.wrap`, max 44rem). No card grids, no shadows,
  no gradients, no all-caps eyebrow labels.
- Use `--accent` sparingly: links and the work title underline only.
- **Do not add new colors, fonts or one-off inline styles.** If something is missing, add
  a class to `style.css` and reuse it.
- Keep keyboard focus visible and respect `prefers-reduced-motion` (already in the CSS).

## 6. Work page format (`works/<slug>.html`)
Always start from `works/_template.html`. Required, in this order:
1. `<title>` = `<Work title> — Portfolio`, and a `<meta name="description">` (≤ 150 chars).
2. `<h1>` work title, then a `.meta` line: year, role, tools (plain text).
3. `<h2>Overview</h2>` — 2–4 sentences: what it is, who it is for.
4. `<h2>What I did</h2>` — a short list (3–6 items) of concrete actions.
5. `<h2>Result</h2>` — outcome, numbers or lessons. Be specific; no filler.
6. Optional `<figure>` blocks with image + `alt` text (alt is mandatory) + `<figcaption>`.
7. Optional `.links` list (repo, demo, report). Links open normally; external ones get `rel="noopener"`.
8. Footer "Back to all works" link to `../index.html`.

## 7. Home page entry format
In `index.html`, inside `<ol class="works">`, add one `<li>` at the **top** (newest first):
```html
<li>
  <a href="works/<slug>.html">Work title</a>
  <span class="tag">Short type, e.g. Print design</span>
  <span class="year">2026</span>
  <p>One-sentence summary, under 140 characters.</p>
</li>
```
Title, tag and summary must match the work page's `<h1>`, `.meta` and description.

## 8. Procedure: add a new work
1. Ask the owner for: title, year, role, tools, overview, actions, result, images (if missing, use clearly marked placeholders such as "TODO: add result").
2. Pick the slug (section 4). Copy `works/_template.html` → `works/<slug>.html`.
3. Fill in every required section (section 6). Put images in `assets/img/`.
4. Add the entry to `index.html` (section 7).
5. Run the checklist (section 9). Report which files you created or changed.

## 9. Checklist before finishing
- [ ] Only files in section 3 touched; no new CSS file, no new dependency.
- [ ] All paths relative; every link resolves (open the file and click through).
- [ ] One `<h1>` per page; headings in order; every image has `alt`.
- [ ] Title/description/summary consistent between work page and index row.
- [ ] No invented facts: unknown details are marked `TODO`, not guessed.
- [ ] Page is readable at 360px width.

## 10. Never do
- Never add frameworks, bundlers, trackers, cookie banners or external scripts.
- Never fabricate awards, clients, metrics or quotes.
- Never restyle the whole site while adding content. Design changes need an explicit request and must be made in `style.css` only.
- Never commit secrets, personal phone numbers or home addresses.

## 11. Publishing
Push to `main`; GitHub Pages serves the repo root. See `docs/deploy.md`.
