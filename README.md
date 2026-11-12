# Portfolio Showcase

A small static portfolio website for showing my projects. Each work has its own page, and the home page lists them all.

**Live site:** https://sikkamilladia.github.io/portofolio/

## Works

- **Business Advisor Dashboard**: a Streamlit dashboard that turns sales data into KPIs and interactive charts.
- **Movie Recommendation System**: a movie recommender using content-based and collaborative filtering.

## Built with

Plain HTML and CSS. No build step, no framework. Hosted on GitHub Pages.

## Project structure

```
index.html              Home page with the list of works
works/_template.html    Template for a new work page
works/<slug>.html       One page per work
assets/style.css        The only stylesheet (all design tokens)
assets/img/             Images for works
docs/deploy.md          How to publish on GitHub Pages
AGENTS.md / CLAUDE.md   Rules for AI agents working on this repo
```

## Working with AI

This repo includes `AGENTS.md`, which tells an AI agent the project's purpose, file naming, page format, design rules and a checklist. `CLAUDE.md` imports it so Claude Code follows the same rules.

To add a new work, ask the AI: *"Add a new work called X"*. It should copy `works/_template.html`, fill in the sections, and add one row to `index.html`, following the procedure in `AGENTS.md`.

## Publishing

Push to `main`. GitHub Pages serves the repo root. See `docs/deploy.md`.
