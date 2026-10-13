# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

GitHub profile repository (`phuwanart/phuwanart`). The only source file is `README.md`, which GitHub renders on the profile page at https://github.com/phuwanart. Pushing to `main` publishes immediately.

There is no build, lint, or test step. Verify changes by previewing the rendered Markdown.

## README conventions

- Rendering target is GitHub's Markdown sanitizer: inline HTML is limited to what GitHub allows (`<div align>`, `<p align>`, `<a>`, `<img>`); `<style>`, `<script>`, and `class`/`style` attributes are stripped.
- All content is served by third-party image services, nothing is stored in the repo:
  - Header animation: `readme-typing-svg.demolab.com`. Lines are `;`-separated and URL-encoded in the `lines=` query parameter; `width=` must be wide enough for the longest line.
  - Badges: `img.shields.io/badge/-<Label>-<hex>?style=for-the-badge&logo=<simple-icons slug>&logoColor=<white|black>`. Keep every badge on `style=for-the-badge`, use the brand's hex colour, and pick `logoColor` for contrast against it.
  - Simple Icons removed the LinkedIn logo, so `logo=linkedin` renders no icon. That badge passes a URL-encoded base64 SVG data URI in `logo=` instead; do the same for any other brand missing from Simple Icons.
- Tech stack badges are plain images grouped under bold sub-headings (Languages & Frameworks, Styling, Database & Tools); "Connect with me" badges are images wrapped in links.
- Section headings are `###` with a leading emoji.
