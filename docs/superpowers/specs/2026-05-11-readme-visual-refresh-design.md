# README Visual Refresh

**Date:** 2026-05-11
**Repo:** `phuwanart/phuwanart` (GitHub profile-README)
**Builds on:** `2026-05-11-readme-redesign-design.md` — keeps all content and layout, changes only visual styling.

## Goal

Tighten the README into a unified bold/punk-modern look by upgrading all shields-style elements to `for-the-badge`, the typing animation to a heavier monospaced font, and the streak card to the `radical` theme. No content, ordering, or section change.

## Constraints

- Only `README.md` changes — no new files in the repo.
- The Skills/socials rendering-safety rule from commit `e72e75b` still applies: anchors wrapping inline images must keep whitespace between `<a>` and the image, and between the image and `</a>`.
- Markdown image syntax `![]()` for shields badges is preferred where possible (proven safe). Anchored badges (for clickable socials) use `<a href="..."> <img ... /> </a>` with the whitespace pattern.
- Adaptive `<picture>` theming is dropped for the streak card because `radical` reads well on both GitHub light and dark themes — a single `<img>` is enough.

## Section-by-section changes

### Header

- Typing SVG URL: change `font=Fira+Code` → `font=JetBrains+Mono`; change `size=22` → `size=28`; keep `color=2F81F7`, `width=460`, the three lines, and the surrounding `<a>` link.
- Profile views badge: change `style=flat` → `style=for-the-badge`. Keep `username=phuwanart&label=Profile+views&color=0e75b6`.

### About me

- No change.

### Tech Stack

- Every badge URL: change `style=flat-square` → `style=for-the-badge`.
- Keep all 11 badges, their order, colors, logo slugs, and `logoColor` values (JavaScript stays `logoColor=black`; all others `logoColor=white`).
- Keep the 4 bold group sub-headings (Languages & Frameworks, Styling, Database, Tools).
- Markdown image syntax `![alt](url)` stays.

### GitHub Stats

- Replace the single existing `<picture>` (adaptive default+tokyonight) with a single `<img>` using the `radical` theme. No `<picture>` wrapper.
- Final block:

  ```markdown
  ### 📊 GitHub Stats

  <p align="center">
    <img src="https://streak-stats.demolab.com?user=phuwanart&theme=radical&hide_border=true" alt="GitHub streak" />
  </p>
  ```

### Connect with me

- Replace all 10 colored-SVG anchors (the `danielcranney` icon set) with shields.io `for-the-badge` social badges, each wrapped in an `<a>` that follows the whitespace-safe pattern.
- Order preserved: GitHub → LinkedIn → Hashnode → Medium → Dev.to → Stack Overflow → YouTube → X → Facebook → RSS.
- Badge format per row (logo slug and brand color filled in per platform):

  ```
  <a href="<URL>" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-<LABEL>-<HEX>?style=for-the-badge&logo=<SLUG>&logoColor=white" alt="<LABEL>" /> </a>
  ```

- Per-platform values:

  | Platform | URL | Label (URL form) | Hex | Slug |
  |---|---|---|---|---|
  | GitHub | `https://www.github.com/phuwanart` | `GitHub` | `181717` | `github` |
  | LinkedIn | `https://www.linkedin.com/in/phuwanart` | `LinkedIn` | `0A66C2` | `linkedin` |
  | Hashnode | `https://phuwanart.hashnode.dev` | `Hashnode` | `2962FF` | `hashnode` |
  | Medium | `http://www.medium.com/@phuwanart` | `Medium` | `12100E` | `medium` |
  | Dev.to | `https://www.dev.to/phuwanart` | `dev.to` | `0A0A0A` | `devdotto` |
  | Stack Overflow | `https://www.stackoverflow.com/users/65964/phuwanart` | `Stack_Overflow` | `F58025` | `stackoverflow` |
  | YouTube | `https://www.youtube.com/@PhuwanartLarpmark` | `YouTube` | `FF0000` | `youtube` |
  | X | `https://www.x.com/phuwanart` | `X` | `000000` | `x` |
  | Facebook | `https://www.facebook.com/phuwanart` | `Facebook` | `1877F2` | `facebook` |
  | RSS | `https://phuwanart.github.io/feed.xml` | `RSS` | `FFA500` | `rss` |

- The `<p align="left">` container that wraps the anchors stays.

### Support my work

- No change. BMC and Ko-fi use official button images, not shields badges — they retain their identity better than converted badges would.

## Rendering safety reminders

- Keep whitespace between `<a href="...">` and `<img>`, and between `<img />` and `</a>`, on every anchored badge. Bare `<a><img></a>` reintroduces the `e72e75b` vertical-stacking bug.
- Markdown badges in Tech Stack stay as `![alt](url)` — that path was already proven safe.

## Out of scope

- Section additions or removals.
- Replacement of typing-svg or shields.io services.
- Returning the stats / top-langs cards (still blocked on `github-readme-stats` availability).
- Profile picture or banner image.
- Section dividers (HR) beyond the existing one above Support.
