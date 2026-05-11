# README Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Rewrite `README.md` per the approved design (Showcase + Personality + Professional hybrid), with adaptive light/dark theming and rendering-safe HTML patterns.

**Architecture:** Single Markdown file at repo root, mixing GitHub-flavored Markdown with raw HTML. All themed widgets use `<picture>` + `prefers-color-scheme` to switch between light (`default`) and dark (`tokyonight`) variants. Tech badges via `img.shields.io`, stats via `github-readme-stats.vercel.app` and `streak-stats.demolab.com`.

**Tech Stack:** Markdown, HTML, shields.io, github-readme-stats, streak-stats, readme-typing-svg, komarev counter.

**Verification:** No automated tests apply to a profile README. Each task's "verify" step is a manual visual check — either a local Markdown preview or, for HTML-sanitizer-sensitive parts, viewing the file on GitHub after pushing. Final task pushes the full rewrite and confirms rendering on github.com/phuwanart.

---

## File Structure

- **Modify (full rewrite):** `README.md`

No other files change. The current `README.md` is 46 lines; the new version will replace it entirely.

---

### Task 1: Replace README with skeleton (centered header + empty sections)

**Files:**
- Modify: `README.md` (full overwrite)

- [ ] **Step 1: Overwrite `README.md` with skeleton**

Replace entire contents with:

```markdown
<div align="center">

# Hi 👋, I'm Phuwanart Larpmark

</div>

### 👨‍💻 About me

### 🛠️ Tech Stack

### 📊 GitHub Stats

### 🌐 Connect with me

---

### ☕ Support my work
```

- [ ] **Step 2: Visual sanity check**

Open `README.md` in any Markdown previewer (VS Code: Cmd+Shift+V). Expected: centered H1 greeting, then 5 empty H3 section headings, then HR before the last one.

- [ ] **Step 3: Commit**

```bash
git add README.md
git commit -m "Replace README with redesign skeleton"
```

---

### Task 2: Header — typing animation + profile views

**Files:**
- Modify: `README.md` (header block, between `# Hi 👋…` and `</div>`)

- [ ] **Step 1: Edit header to add typing SVG and view counter**

Replace the header block with:

```markdown
<div align="center">

# Hi 👋, I'm Phuwanart Larpmark

<a href="https://github.com/phuwanart">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&pause=1000&color=2F81F7&center=true&vCenter=true&width=460&lines=Ruby+on+Rails+Developer;Crafting+web+apps+from+Bangkok+%F0%9F%87%B9%F0%9F%87%AD;Always+learning%2C+always+shipping" alt="Typing SVG" />
</a>

<p>
  <img src="https://komarev.com/ghpvc/?username=phuwanart&label=Profile+views&color=0e75b6&style=flat" alt="Profile views" />
</p>

</div>
```

Notes on the typing SVG URL parameters:
- `font=Fira+Code` — monospace, matches dev aesthetic
- `size=22` — readable
- `color=2F81F7` — GitHub's link blue, works on both light and dark
- `center=true&vCenter=true` — center inside the SVG canvas
- `width=460` — wide enough to fit the longest line ("Crafting web apps from Bangkok 🇹🇭")
- `lines=` — three URL-encoded lines, separated by `;`. The 🇹🇭 emoji is encoded as `%F0%9F%87%B9%F0%9F%87%AD`.

- [ ] **Step 2: Verify URL fetches in a browser**

Open the typing SVG URL directly in a browser. Expected: animated SVG cycling through three lines.

Open the komarev URL. Expected: a small "Profile views: N" pill image.

- [ ] **Step 3: Commit**

```bash
git add README.md
git commit -m "Add typing animation and profile views badge to header"
```

---

### Task 3: About me — 5 bullets

**Files:**
- Modify: `README.md` (under `### 👨‍💻 About me`)

- [ ] **Step 1: Insert About bullets**

Replace `### 👨‍💻 About me` (the empty heading) with:

```markdown
### 👨‍💻 About me

- 🌏 &nbsp; Based in **Bangkok, Thailand**
- 💼 &nbsp; Ruby on Rails developer
- 🌱 &nbsp; Currently working on **improving Rails performance & exploring Hotwire**
- ✉️ &nbsp; Reach me at [phuwanart@outlook.com](mailto:phuwanart@outlook.com)
- 📝 &nbsp; I write on [Hashnode](https://phuwanart.hashnode.dev) · [Medium](https://medium.com/@phuwanart) · [Dev.to](https://dev.to/phuwanart)
```

The `&nbsp;` after each emoji is intentional spacing so the text doesn't sit flush against variable-width emojis.

- [ ] **Step 2: Visual sanity check**

Render in a Markdown previewer. Expected: 5 bullet rows with emoji + small gap + text. Email is a `mailto:` link. Blog names are hyperlinks separated by `·`.

- [ ] **Step 3: Commit**

```bash
git add README.md
git commit -m "Add About me section with role, focus, contact, blogs"
```

---

### Task 4: Tech Stack — shields.io badges grouped by category

**Files:**
- Modify: `README.md` (under `### 🛠️ Tech Stack`)

- [ ] **Step 1: Insert grouped badges**

Replace `### 🛠️ Tech Stack` with:

```markdown
### 🛠️ Tech Stack

**Languages & Frameworks**

![Ruby](https://img.shields.io/badge/-Ruby-CC342D?style=flat-square&logo=ruby&logoColor=white)
![Ruby on Rails](https://img.shields.io/badge/-Ruby_on_Rails-CC0000?style=flat-square&logo=rubyonrails&logoColor=white)
![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/-HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/-CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![Vue.js](https://img.shields.io/badge/-Vue.js-4FC08D?style=flat-square&logo=vuedotjs&logoColor=white)

**Styling**

![Tailwind CSS](https://img.shields.io/badge/-Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Bootstrap](https://img.shields.io/badge/-Bootstrap-7952B3?style=flat-square&logo=bootstrap&logoColor=white)

**Database**

![MySQL](https://img.shields.io/badge/-MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

**Tools**

![Git](https://img.shields.io/badge/-Git-F05032?style=flat-square&logo=git&logoColor=white)
```

Notes:
- These use Markdown image syntax (`![alt](url)`), not raw HTML — shields.io badges are inline images and Markdown's `![]()` renders them inline reliably.
- Color values are each tech's official brand color.
- `logo=` uses simple-icons slugs (e.g., `vuedotjs`, `rubyonrails`, `tailwindcss`).
- JavaScript's logo is black on its yellow background — that's why `logoColor=black`.

- [ ] **Step 2: Verify each badge URL fetches**

For each badge, open the URL in a browser. Expected: a small SVG badge with the correct name, color, and logo.

- [ ] **Step 3: Visual sanity check**

Render the file in a Markdown previewer. Expected: each subgroup heading on its own line, followed by badges flowing inline (multiple per row).

- [ ] **Step 4: Commit**

```bash
git add README.md
git commit -m "Add Tech Stack with categorized shields.io badges"
```

---

### Task 5: GitHub Stats — adaptive stats + top-langs + streak cards

**Files:**
- Modify: `README.md` (under `### 📊 GitHub Stats`)

- [ ] **Step 1: Insert three cards with adaptive theming**

Replace `### 📊 GitHub Stats` with:

```markdown
### 📊 GitHub Stats

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=phuwanart&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true&count_private=true" />
    <source media="(prefers-color-scheme: light)" srcset="https://github-readme-stats.vercel.app/api?username=phuwanart&show_icons=true&theme=default&hide_border=true&include_all_commits=true&count_private=true" />
    <img src="https://github-readme-stats.vercel.app/api?username=phuwanart&show_icons=true&theme=default&hide_border=true&include_all_commits=true&count_private=true" alt="Phuwanart's GitHub stats" height="170" />
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/top-langs?username=phuwanart&layout=compact&theme=tokyonight&hide_border=true&langs_count=8" />
    <source media="(prefers-color-scheme: light)" srcset="https://github-readme-stats.vercel.app/api/top-langs?username=phuwanart&layout=compact&theme=default&hide_border=true&langs_count=8" />
    <img src="https://github-readme-stats.vercel.app/api/top-langs?username=phuwanart&layout=compact&theme=default&hide_border=true&langs_count=8" alt="Top languages" height="170" />
  </picture>
</p>

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://streak-stats.demolab.com?user=phuwanart&theme=tokyonight&hide_border=true" />
    <source media="(prefers-color-scheme: light)" srcset="https://streak-stats.demolab.com?user=phuwanart&theme=default&hide_border=true" />
    <img src="https://streak-stats.demolab.com?user=phuwanart&theme=default&hide_border=true" alt="GitHub streak" />
  </picture>
</p>
```

Notes:
- Both stat cards have `height="170"` so they line up cleanly side-by-side on wide viewports.
- `include_all_commits=true&count_private=true` makes the stats representative even if much work happens in private repos.
- `langs_count=8` caps the languages chart at 8 entries so it doesn't grow unevenly.
- Each `<picture>` has whitespace inside between child tags — same pattern that fixed the Socials section. The `<img>` is the fallback for clients that ignore `<picture>` sources.

- [ ] **Step 2: Verify each stats URL fetches**

Open each of the 6 URLs (3 light + 3 dark) in a browser. Expected: each returns an SVG card with stats. If any returns 404 or an error message, stop and report — usually means the service is down or the URL params are wrong.

- [ ] **Step 3: Commit**

```bash
git add README.md
git commit -m "Add GitHub stats, top languages, and streak cards"
```

---

### Task 6: Connect with me — port and reorder existing socials

**Files:**
- Modify: `README.md` (under `### 🌐 Connect with me`)

- [ ] **Step 1: Insert socials block in new order**

Replace `### 🌐 Connect with me` with:

```markdown
### 🌐 Connect with me

<p align="left">
<a href="https://www.github.com/phuwanart" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/github.svg" width="32" height="32" /> </picture> </a>
<a href="https://www.linkedin.com/in/phuwanart" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/linkedin.svg" width="32" height="32" /> </picture> </a>
<a href="https://phuwanart.hashnode.dev" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/hashnode-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/hashnode.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/hashnode.svg" width="32" height="32" /> </picture> </a>
<a href="http://www.medium.com/@phuwanart" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/medium-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/medium.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/medium.svg" width="32" height="32" /> </picture> </a>
<a href="https://www.dev.to/phuwanart" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/devdotto-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/devdotto.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/devdotto.svg" width="32" height="32" /> </picture> </a>
<a href="https://www.stackoverflow.com/users/65964/phuwanart" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/stackoverflow-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/stackoverflow.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/stackoverflow.svg" width="32" height="32" /> </picture> </a>
<a href="https://www.youtube.com/@PhuwanartLarpmark" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/youtube-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/youtube.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/youtube.svg" width="32" height="32" /> </picture> </a>
<a href="https://www.x.com/phuwanart" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/twitter-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/twitter.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/twitter.svg" width="32" height="32" /> </picture> </a>
<a href="https://www.facebook.com/phuwanart" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/facebook-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/facebook.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/facebook.svg" width="32" height="32" /> </picture> </a>
<a href="https://phuwanart.github.io/feed.xml" target="_blank" rel="noreferrer"> <picture> <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/rss-dark.svg" /> <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/rss.svg" /> <img src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/socials/rss.svg" width="32" height="32" /> </picture> </a>
</p>
```

Notes:
- Each `<a>` has whitespace before `<picture>` and after `</picture>` — preserves the rendering-safe pattern.
- Order: GitHub → LinkedIn → Hashnode → Medium → Dev.to → Stack Overflow → YouTube → X/Twitter → Facebook → RSS.

- [ ] **Step 2: Commit**

```bash
git add README.md
git commit -m "Add Connect section with reordered social icons"
```

---

### Task 7: Support footer

**Files:**
- Modify: `README.md` (under `### ☕ Support my work`)

- [ ] **Step 1: Insert support buttons under the HR**

Replace `### ☕ Support my work` with:

```markdown
### ☕ Support my work

<p align="left">
  <a href="https://www.buymeacoffee.com/phuwanart" target="_blank" rel="noreferrer"> <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" width="150" alt="Buy Me a Coffee" /> </a>
  <a href="https://www.ko-fi.com/phuwanart" target="_blank" rel="noreferrer"> <img src="https://storage.ko-fi.com/cdn/kofi2.png?v=3" width="150" alt="Ko-fi" /> </a>
</p>
```

Both anchors use the same whitespace-around-img pattern.

- [ ] **Step 2: Commit**

```bash
git add README.md
git commit -m "Add Support footer with Buy Me a Coffee and Ko-fi"
```

---

### Task 8: Final QA — read whole file, push, verify on GitHub

**Files:**
- Read only: `README.md`

- [ ] **Step 1: Read the final README end-to-end**

Open `README.md` in the editor. Confirm: 6 sections in the correct order (Header, About me, Tech Stack, GitHub Stats, Connect with me, Support my work). No leftover empty headings. No duplicate sections.

- [ ] **Step 2: Local Markdown preview**

Render in a Markdown previewer one more time. Note that the previewer will NOT render `<picture>` theme-switching correctly — it will show the fallback `<img>`. That's expected; the real test is GitHub.

- [ ] **Step 3: Push to GitHub**

```bash
git push origin main
```

- [ ] **Step 4: Visual verification on GitHub**

Open https://github.com/phuwanart in a browser. Verify in order:

1. Greeting H1 centered, typing animation cycling through 3 lines, profile views badge visible below.
2. About me bullets render with emoji + spacing + bold + correct links.
3. Tech Stack: 4 group headings, each followed by badges flowing inline. **No vertical stacking.**
4. GitHub Stats: stats + top-langs side-by-side on wide viewport; streak below.
5. Connect with me: 10 social icons in a horizontal row. **No vertical stacking.**
6. HR, then Support my work with BMC and Ko-fi buttons in a row.

- [ ] **Step 5: Toggle GitHub theme and re-verify**

Switch GitHub's appearance setting between Light and Dark. Verify that:
- Social icons swap variants (this already worked before).
- Stats / top-langs / streak cards swap themes between `default` and `tokyonight`.

- [ ] **Step 6: If any section fails to render correctly, stop and report**

Do not attempt blind fixes. Report which section broke and what it looks like. The whitespace-around-`<img>` rule from `e72e75b` is the most likely culprit if any inline row stacks vertically.

---

## Notes for the implementer

- **DRY:** Each task touches exactly one section. The repetition between Connect icons (10 nearly-identical `<a>` blocks) is intentional — abstracting them would require templating that GitHub does not support.
- **YAGNI:** No trophy widgets, no contribution graphs, no profile banner image, no localized variants — explicitly out of scope per the spec.
- **TDD:** Inapplicable to a content-only Markdown file. The closest analog is verifying each external URL in a browser before committing (Tasks 2, 4, 5) and the final visual QA on GitHub (Task 8).
- **Commits:** Each task ends with a focused commit. Push only once, at Task 8, so the redesign lands as a coherent sequence rather than a stream of WIP commits to a public profile.
