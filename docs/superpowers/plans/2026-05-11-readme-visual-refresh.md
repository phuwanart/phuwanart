# README Visual Refresh Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Apply the approved visual refresh to `README.md` — `for-the-badge` shields throughout, JetBrains Mono typing animation, and `radical`-themed streak card. Content and section layout stay the same.

**Architecture:** Five targeted edits to one file, each landing in its own commit and producing a self-contained visual change. The streak `<picture>` collapses to a single `<img>` because `radical` reads well on both GitHub themes; everything else swaps style/theme parameters in URLs.

**Tech Stack:** Markdown, HTML, `img.shields.io`, `readme-typing-svg.demolab.com`, `streak-stats.demolab.com`, `komarev.com`.

**Verification:** No automated tests for a content-only README. Each task's verification step is grep-based assertions and a final visual check after push.

---

## File Structure

- **Modify:** `README.md` (only). Five distinct edits across five sections.

No other files change.

---

### Task 1: Header — JetBrains Mono typing + for-the-badge view counter

**Files:**
- Modify: `/Users/phuwanart/Projects/phuwanart/README.md`

- [ ] **Step 1: Replace the typing-SVG URL and view-counter URL**

In the centered `<div align="center">…</div>` header block (currently lines 5-11), apply two URL parameter changes:

For the typing SVG `<img src="…">`, change:
- `font=Fira+Code` → `font=JetBrains+Mono`
- `size=22` → `size=28`

Keep everything else in that URL identical (`pause=1000&color=2F81F7&center=true&vCenter=true&width=460&lines=…`).

For the profile-views `<img src="…">`, change:
- `style=flat` → `style=for-the-badge`

The full resulting header block must be exactly:

```markdown
<div align="center">

# Hi 👋, I'm Phuwanart Larpmark

<a href="https://github.com/phuwanart">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&size=28&pause=1000&color=2F81F7&center=true&vCenter=true&width=460&lines=Ruby+on+Rails+Developer;Crafting+web+apps+from+Bangkok+%F0%9F%87%B9%F0%9F%87%AD;Always+learning%2C+always+shipping" alt="Typing SVG" />
</a>

<p>
  <img src="https://komarev.com/ghpvc/?username=phuwanart&label=Profile+views&color=0e75b6&style=for-the-badge" alt="Profile views" />
</p>

</div>
```

- [ ] **Step 2: Verify URLs fetch**

Open both URLs in a browser:
- `https://readme-typing-svg.demolab.com?font=JetBrains+Mono&size=28&pause=1000&color=2F81F7&center=true&vCenter=true&width=460&lines=Ruby+on+Rails+Developer;Crafting+web+apps+from+Bangkok+%F0%9F%87%B9%F0%9F%87%AD;Always+learning%2C+always+shipping`
- `https://komarev.com/ghpvc/?username=phuwanart&label=Profile+views&color=0e75b6&style=for-the-badge`

Expected: animated SVG cycling 3 lines in JetBrains Mono at the new larger size, and a wider, bolder "Profile views" badge.

- [ ] **Step 3: Grep sanity check**

```bash
grep -c "JetBrains+Mono" /Users/phuwanart/Projects/phuwanart/README.md
grep -c "Fira+Code" /Users/phuwanart/Projects/phuwanart/README.md
grep -c "style=for-the-badge" /Users/phuwanart/Projects/phuwanart/README.md
grep -c "style=flat\b" /Users/phuwanart/Projects/phuwanart/README.md
```

Expected: `JetBrains+Mono` = 1, `Fira+Code` = 0, `style=for-the-badge` = 1 (the view counter), `style=flat\b` = 0.

- [ ] **Step 4: Commit**

```bash
cd /Users/phuwanart/Projects/phuwanart
git add README.md
git commit -m "Refresh header with JetBrains Mono typing and for-the-badge view counter"
```

---

### Task 2: Tech Stack — flip all 11 badges to for-the-badge

**Files:**
- Modify: `/Users/phuwanart/Projects/phuwanart/README.md`

- [ ] **Step 1: Replace badge style in all 11 Tech Stack URLs**

In the Tech Stack section (currently lines 23-46), every `![Tech](https://img.shields.io/badge/-…?style=flat-square&…)` URL must have its `style=flat-square` swapped to `style=for-the-badge`. No other URL parameters change (colors, logo slugs, logoColor all stay).

The full resulting Tech Stack section must be exactly:

```markdown
### 🛠️ Tech Stack

**Languages & Frameworks**

![Ruby](https://img.shields.io/badge/-Ruby-CC342D?style=for-the-badge&logo=ruby&logoColor=white)
![Ruby on Rails](https://img.shields.io/badge/-Ruby_on_Rails-CC0000?style=for-the-badge&logo=rubyonrails&logoColor=white)
![JavaScript](https://img.shields.io/badge/-JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![HTML5](https://img.shields.io/badge/-HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/-CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![Vue.js](https://img.shields.io/badge/-Vue.js-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white)

**Styling**

![Tailwind CSS](https://img.shields.io/badge/-Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Bootstrap](https://img.shields.io/badge/-Bootstrap-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)

**Database**

![MySQL](https://img.shields.io/badge/-MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/-PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)

**Tools**

![Git](https://img.shields.io/badge/-Git-F05032?style=for-the-badge&logo=git&logoColor=white)
```

- [ ] **Step 2: Grep sanity check**

```bash
grep -c "style=flat-square" /Users/phuwanart/Projects/phuwanart/README.md
grep -c "style=for-the-badge" /Users/phuwanart/Projects/phuwanart/README.md
grep -c "shields.io/badge" /Users/phuwanart/Projects/phuwanart/README.md
```

Expected: `style=flat-square` = 0, `style=for-the-badge` = 12 (11 Tech Stack + 1 view counter from Task 1), `shields.io/badge` = 11.

- [ ] **Step 3: Commit**

```bash
cd /Users/phuwanart/Projects/phuwanart
git add README.md
git commit -m "Flip Tech Stack badges to for-the-badge style"
```

---

### Task 3: GitHub Stats — collapse to single radical-themed streak card

**Files:**
- Modify: `/Users/phuwanart/Projects/phuwanart/README.md`

- [ ] **Step 1: Replace the streak `<picture>` block with a single `<img>`**

In the GitHub Stats section (currently the lone `<p align="center">` wrapping a `<picture>` for the streak card), replace the entire `<p align="center">…</p>` block with this:

```markdown
<p align="center">
  <img src="https://streak-stats.demolab.com?user=phuwanart&theme=radical&hide_border=true" alt="GitHub streak" />
</p>
```

The full resulting GitHub Stats section must be exactly:

```markdown
### 📊 GitHub Stats

<p align="center">
  <img src="https://streak-stats.demolab.com?user=phuwanart&theme=radical&hide_border=true" alt="GitHub streak" />
</p>
```

- [ ] **Step 2: Verify URL fetches**

Open `https://streak-stats.demolab.com?user=phuwanart&theme=radical&hide_border=true` in a browser. Expected: streak card in radical theme (dark background, pink/orange accents).

- [ ] **Step 3: Grep sanity check**

```bash
grep -c "streak-stats.demolab.com" /Users/phuwanart/Projects/phuwanart/README.md
grep -c "theme=radical" /Users/phuwanart/Projects/phuwanart/README.md
grep -c "theme=tokyonight" /Users/phuwanart/Projects/phuwanart/README.md
grep -c "theme=default" /Users/phuwanart/Projects/phuwanart/README.md
grep -c "<picture>" /Users/phuwanart/Projects/phuwanart/README.md
```

Expected: `streak-stats.demolab.com` = 1, `theme=radical` = 1, `theme=tokyonight` = 0, `theme=default` = 0, `<picture>` = 10 (all from the Connect section anchors; the streak picture wrapper is now gone).

- [ ] **Step 4: Commit**

```bash
cd /Users/phuwanart/Projects/phuwanart
git add README.md
git commit -m "Switch streak card to radical theme, drop adaptive picture wrapper"
```

---

### Task 4: Connect with me — replace 10 anchors with for-the-badge social shields

**Files:**
- Modify: `/Users/phuwanart/Projects/phuwanart/README.md`

- [ ] **Step 1: Replace the entire Connect with me block**

Find the `### 🌐 Connect with me` section. Replace everything from `### 🌐 Connect with me` through the closing `</p>` (inclusive) with EXACTLY this block:

```markdown
### 🌐 Connect with me

<p align="left">
<a href="https://www.github.com/phuwanart" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" /> </a>
<a href="https://www.linkedin.com/in/phuwanart" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /> </a>
<a href="https://phuwanart.hashnode.dev" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-Hashnode-2962FF?style=for-the-badge&logo=hashnode&logoColor=white" alt="Hashnode" /> </a>
<a href="http://www.medium.com/@phuwanart" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-Medium-12100E?style=for-the-badge&logo=medium&logoColor=white" alt="Medium" /> </a>
<a href="https://www.dev.to/phuwanart" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-dev.to-0A0A0A?style=for-the-badge&logo=devdotto&logoColor=white" alt="Dev.to" /> </a>
<a href="https://www.stackoverflow.com/users/65964/phuwanart" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-Stack_Overflow-F58025?style=for-the-badge&logo=stackoverflow&logoColor=white" alt="Stack Overflow" /> </a>
<a href="https://www.youtube.com/@PhuwanartLarpmark" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="YouTube" /> </a>
<a href="https://www.x.com/phuwanart" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-X-000000?style=for-the-badge&logo=x&logoColor=white" alt="X" /> </a>
<a href="https://www.facebook.com/phuwanart" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-Facebook-1877F2?style=for-the-badge&logo=facebook&logoColor=white" alt="Facebook" /> </a>
<a href="https://phuwanart.github.io/feed.xml" target="_blank" rel="noreferrer"> <img src="https://img.shields.io/badge/-RSS-FFA500?style=for-the-badge&logo=rss&logoColor=white" alt="RSS" /> </a>
</p>
```

Critical rendering rule: every `<a>` keeps one space between `rel="noreferrer">` and `<img`, AND one space between `/>` and `</a>`. Both spaces are mandatory to avoid the bug from commit `e72e75b`.

- [ ] **Step 2: Verify a representative URL fetches**

Open `https://img.shields.io/badge/-GitHub-181717?style=for-the-badge&logo=github&logoColor=white` in a browser. Expected: a tall, bold black GitHub badge with the white wordmark. Open one more (`https://img.shields.io/badge/-X-000000?style=for-the-badge&logo=x&logoColor=white`) to confirm the `x` slug renders.

- [ ] **Step 3: Grep sanity check**

```bash
grep -c "danielcranney/readme-generator" /Users/phuwanart/Projects/phuwanart/README.md
grep -c '<a href="' /Users/phuwanart/Projects/phuwanart/README.md
grep -c "noreferrer\"><" /Users/phuwanart/Projects/phuwanart/README.md
grep -c "shields.io/badge.*for-the-badge.*logoColor" /Users/phuwanart/Projects/phuwanart/README.md
```

Expected:
- `danielcranney/readme-generator` = 0 (all colored-SVG anchors removed)
- `<a href="` = 13 (1 typing-SVG link, 10 socials, 2 support buttons)
- `noreferrer\"><` = 0 (no unsafe whitespace-free anchor)
- `shields.io/badge.*for-the-badge.*logoColor` = 21 (11 Tech Stack badges + 10 social badges)

- [ ] **Step 4: Commit**

```bash
cd /Users/phuwanart/Projects/phuwanart
git add README.md
git commit -m "Replace social icons with for-the-badge shields"
```

---

### Task 5: Final QA + push

**Files:**
- Read only: `/Users/phuwanart/Projects/phuwanart/README.md`

- [ ] **Step 1: Read the final README end-to-end**

Open `README.md`. Confirm in order:

1. Header — JetBrains Mono typing SVG, view counter as `for-the-badge`
2. About me — 5 bullets, unchanged
3. Tech Stack — 4 bold subgroups + 11 `for-the-badge` badges, unchanged grouping/order
4. GitHub Stats — single `radical` streak `<img>` (no `<picture>`)
5. Connect with me — 10 `for-the-badge` social anchors
6. `---` HR
7. Support my work — BMC and Ko-fi anchors unchanged

- [ ] **Step 2: Combined grep sanity check**

```bash
cd /Users/phuwanart/Projects/phuwanart
grep -c "style=flat-square" README.md       # expect: 0
grep -c "style=flat\b" README.md             # expect: 0
grep -c "style=for-the-badge" README.md      # expect: 22 (1 view counter + 11 tech + 10 socials)
grep -c "theme=radical" README.md            # expect: 1
grep -c "theme=tokyonight\|theme=default" README.md   # expect: 0
grep -c "Fira+Code" README.md                # expect: 0
grep -c "JetBrains+Mono" README.md           # expect: 1
grep -c "danielcranney/readme-generator" README.md    # expect: 0
grep -c "noreferrer\"><" README.md           # expect: 0 (no unsafe pattern)
```

If any count diverges from expected, STOP and report which one, do NOT push.

- [ ] **Step 3: Working tree status**

```bash
git status
```

Expected: working tree clean, 4 new commits ahead of origin/main (Tasks 1-4).

- [ ] **Step 4: Push**

```bash
git push origin main
```

- [ ] **Step 5: Visual verification on GitHub** (user-performed, not the implementer's responsibility)

Implementer reports back with the commit range pushed. The user opens https://github.com/phuwanart to confirm:

1. Typing animation renders in JetBrains Mono at larger size, cycling three lines.
2. Profile views badge is now the wider `for-the-badge` style.
3. Tech Stack badges are tall and bold (`for-the-badge`), grouped under 4 bold sub-headings, still flowing horizontally.
4. Streak card renders in `radical` theme (dark with pink/orange accents) on both light and dark GitHub themes.
5. Connect with me row shows 10 bold social `for-the-badge` shields in order GitHub → LinkedIn → Hashnode → Medium → Dev.to → Stack Overflow → YouTube → X → Facebook → RSS, flowing horizontally with no vertical stacking.
6. Support buttons (BMC and Ko-fi) appear unchanged.

If any section stacks vertically, the root cause is almost always missing whitespace inside an `<a>` tag — see commit `e72e75b`.

---

## Notes for the implementer

- **DRY:** Each task is one focused edit. There's no shared abstraction to extract — repetition across the 10 social anchors is intentional since GitHub doesn't support templating in Markdown.
- **YAGNI:** No new sections, no new services, no profile picture, no GitHub stats card return — explicitly out of scope per the spec.
- **TDD:** Inapplicable to a content-only Markdown file. Grep counts in each task act as the assertion layer.
- **Commits:** One commit per task. Push only at Task 5, after all four edits land, so the profile updates as a coherent visual refresh.
