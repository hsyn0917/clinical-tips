# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A personal ER clinical quick reference site (教育用) built with MkDocs + Material theme. Content is in Japanese. Deployed automatically to GitHub Pages on push to `main`.

## Build & Development Commands

Requires Python with the virtual environment activated:

```bash
# Activate virtual environment
source .venv/bin/activate

# Install dependencies (first time or after requirements.txt changes)
pip install -r requirements.txt

# Local development server with live reload
mkdocs serve

# Build static site
mkdocs build

# Deploy manually (usually done via GitHub Actions)
mkdocs gh-deploy
```

## Architecture

This is a pure documentation site — no application code. The build pipeline is:

1. Markdown files in `docs/` → MkDocs → Static HTML → GitHub Pages

**Key configuration:** `mkdocs.yml` defines site structure, navigation, and theme settings.

**Content pages** (all in `docs/`):
- `dizziness.md` — めまい triage protocol (AVS/s-EVS/t-EVS classification)
- `chest-pain.md` — 胸痛 initial assessment (ACS, dissection, PE, etc.)
- `hypokalemia.md` — 低K血症 management with diagnostic flowcharts
- `operations.md` — site governance and update workflow

**Styling:** `docs/stylesheets/extra.css` — custom CSS for mobile/iPad responsiveness and Japanese text wrapping. Media queries target ≤768px.

**Assets:** `docs/assets/` — PNG flowchart images embedded in markdown pages.

## Deployment

GitHub Actions (`.github/workflows/docs-deploy.yml`) automatically builds and deploys on push to `main`. No manual deployment needed under normal circumstances.

## Content Guidelines

- All clinical content is in Japanese
- Pages follow a consistent structure: overview → diagnostic algorithm → management → references
- Flowcharts are PNG images stored in `docs/assets/` and embedded via standard Markdown image syntax
- The site is educational reference only (`最終判断は担当医の臨床判断に基づく`)
