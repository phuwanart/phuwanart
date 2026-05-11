# GitHub Profile README Redesign

**Date:** 2026-05-11
**Repo:** `phuwanart/phuwanart` (special profile-README repo)

## Goal

Redesign `README.md` to combine three styles: **Showcase** (live GitHub stats widgets), **Personality** (typing animation, friendly tone), and **Professional** (clear sectioned structure). Use existing profile data — no new external identities.

## Constraints

- Single file: `README.md` at repo root. No build system available.
- Must render correctly on GitHub's CommonMark + HTML sanitizer (the previous version stacked Skills icons vertically due to whitespace-sensitive paragraph splitting — see commit `e72e75b`).
- All themed widgets must adapt to both light and dark GitHub themes via `<picture>` + `prefers-color-scheme` media queries.
- No JS, no external assets stored in repo — only remote URLs to image-generating services.

## Final structure (top → bottom)

1. **Header** (centered)
   - `# Hi 👋, I'm Phuwanart Larpmark`
   - Typing SVG via `readme-typing-svg.demolab.com`, three rotating lines:
     - "Ruby on Rails Developer"
     - "Crafting web apps from Bangkok 🇹🇭"
     - "Always learning, always shipping"
   - Profile views badge from `komarev.com/ghpvc/?username=phuwanart`

2. **About me**
   - 5 bullets: location, role, current focus, email, blog links
   - Current focus copy: "improving Rails performance & exploring Hotwire"
   - Blog links inline: Hashnode · Medium · Dev.to

3. **Tech Stack** — shields.io badges grouped by category
   - **Languages & Frameworks:** Ruby, Rails, JavaScript, HTML5, CSS3, Vue.js
   - **Styling:** Tailwind CSS, Bootstrap
   - **Database:** MySQL, PostgreSQL
   - **Tools:** Git
   - Format: `https://img.shields.io/badge/-<name>-<hex>?style=flat-square&logo=<slug>&logoColor=white`
   - Rails (`Ruby on Rails`) is **added** — was missing despite being core to user's identity.

4. **GitHub Stats** (Showcase)
   - Row 1: `github-readme-stats.vercel.app/api?username=phuwanart` (stats card) + `…/api/top-langs?username=phuwanart&layout=compact` (top languages card) side by side.
   - Row 2: `streak-stats.demolab.com?user=phuwanart` (streak card).
   - Each card wrapped in `<picture>` with `theme=default` (light) and `theme=tokyonight` (dark) sources.

5. **Connect with me** (renamed from "Socials")
   - Keep existing `<picture>`-based icons from `danielcranney/readme-generator` (already adaptive and rendering correctly).
   - Re-order by professional priority: GitHub → LinkedIn → Hashnode → Medium → Dev.to → Stack Overflow → YouTube → X/Twitter → Facebook → RSS.

6. **Support my work** (renamed from "Support Me")
   - Horizontal rule `---` above to act as footer separator.
   - Keep BMC + Ko-fi buttons unchanged.

## Rendering safety rules (learned from prior bug)

- Inside any `<p>` containing multiple `<a><img></a>` siblings, always put whitespace between the opening `<a>` and the inner element: `<a href="..."> <img ... /> </a>`. Bare `<a><img></a>` lines get split into separate paragraphs by GitHub's renderer.
- Prefer one icon/badge per line for readability, but verify rendering after each section is added.

## What's preserved vs. what changes

| Section | Status |
|---|---|
| Name + greeting | Preserved, moved to centered header |
| Bangkok + email | Preserved, expanded into About bullets |
| Skills icons | **Replaced** with shields.io badges, grouped by category, Rails added |
| Socials | Preserved (adaptive `<picture>` pattern works), renamed + reordered |
| Support buttons | Preserved, renamed, moved to footer with HR above |
| Typing animation | **New** |
| Profile views | **New** |
| GitHub stats / top-langs / streak cards | **New** (Showcase pillar) |

## Out of scope

- New social platforms or contact methods.
- Profile picture / banner image.
- Per-language proficiency levels on tech stack.
- Contribution graph / GitHub trophies (decided against to avoid clutter).
- Localization of the README into Thai.
