# synent-task2-landingpage-muskan

# Flowdesk — Responsive SaaS Landing Page

> **Internship Task 2 | Synent**
> A fully responsive, animated marketing landing page for **Flowdesk** — built with pure HTML5 & CSS3. Zero dependencies. Zero build step. Zero JavaScript.

---

## Table of Contents

- [Task Overview](#task-overview)
- [About This Project](#about-this-project)
- [Methodology](#methodology)
- [Project Structure](#project-structure)
- [Sections Breakdown](#sections-breakdown)
- [Design System](#design-system)
- [Animations](#animations)
- [Responsive Breakpoints](#responsive-breakpoints)
- [Accessibility](#accessibility)
- [Contact Form](#contact-form)
- [Screenshots](#screenshots)
- [Getting Started](#getting-started)
- [How to Extend](#how-to-extend)
- [Known Issues](#known-issues)
- [Commit History](#commit-history)
- [License](#license)

---

## Task Overview

| Field | Detail |
|---|---|
| **Task** | Task 2 — Responsive SaaS Landing Page |
| **Product** | Flowdesk |
| **Intern** | Muskan |
| **Organization** | Synent |
| **Tech stack** | HTML5 · Vanilla CSS3 |
| **JavaScript** | None |
| **Dependencies** | None |
| **Build tool** | None — open `index.html` directly in any browser |
| **Pages** | 1 (single-page, anchor navigation) |
| **Responsive** | ✅ Mobile · Tablet · Desktop |
| **Animations** | ✅ CSS keyframe animations |
| **Accessibility** | ✅ Semantic HTML · ARIA · `prefers-reduced-motion` |

---

## About This Project

This landing page was designed and developed as **Task 2** of my internship at Synent. The goal was to build a production-quality, responsive marketing page for **Flowdesk** — a fictional SaaS product for team project management.

**What I focused on:**

- Designing a dark-mode design system using CSS custom properties (design tokens)
- Building smooth CSS-only animations — floating UI mockups, animated timeline bars, progress pulses, and staggered card entrance effects
- Ensuring full responsiveness across mobile (< 620 px), tablet (≤ 860 px), and desktop
- Following accessibility best practices — semantic HTML5, ARIA labels and IDs, focus styles, and `prefers-reduced-motion` support
- Writing clean, well-structured, and maintainable code with zero external dependencies

---

## Methodology

### 1. Research & Planning
Studied modern SaaS landing pages to understand structure, visual hierarchy, and CTA placement. Identified the four key sections: Hero, Features, Contact, Footer. Chose a dark-mode aesthetic with vibrant accent colors to create a premium feel.

### 2. Design System First
Defined all color tokens as CSS custom properties on `:root` before writing any component styles. Established a consistent type scale using `clamp()` for fluid, responsive typography. Planned button variants, card styles, and spacing rhythm upfront.

### 3. Layout & Markup
Wrote semantic HTML5 with a logical heading hierarchy (`h1 → h2 → h3`). Used CSS Grid throughout: two-column hero split, three-column features grid, and two-column contact layout — all collapsing gracefully at smaller breakpoints.

### 4. Visual Enhancements
Added layered radial gradient backgrounds for depth. Built a drifting dot-grid pattern using a `::before` pseudo-element. Created animated product mockups (desktop + mobile) using only CSS — no images required.

### 5. Responsiveness
Applied two breakpoints (`860px`, `620px`) to adapt layouts from desktop to tablet to mobile. Tested on Chrome DevTools for iPhone SE (375 px), iPad (768 px), and 1440 px desktop.

### 6. Accessibility & Polish
Added `aria-label` and `aria-labelledby` to all key regions with matching IDs verified in the HTML. Ensured all inputs have paired `<label>` elements. Added `@media (prefers-reduced-motion: reduce)` to collapse all animations for users who prefer it.

---

## Project Structure

```
synent-task2-landingpage-muskan/
├── index.html            # Full page markup — semantic HTML5, single file
├── styles.css            # Design tokens, layout, components, animations, media queries
├── screenshots/
│   ├── hero.png          # Hero section
│   ├── features.png      # Features grid
│   ├── contact.png       # Contact section
│   └── footer.png        # Footer
├── report/
│   └── report.md         # Detailed project report (objective, methodology, learnings)
├── LICENSE               # MIT License
└── README.md             # This file
```

---

## Sections Breakdown

### Header (`<header class="site-header">`)
- **Brand logo** — animated gradient mark with `logoPulse` keyframe
- **Navigation** — Features · Start · Contact (smooth-scroll anchor links via `href="#id"`)

### Hero (`<section class="hero" aria-labelledby="hero-title">`)
- Eyebrow label, fluid `<h1 id="hero-title">` headline, sub-copy paragraph
- **CTA buttons** — *Start free* (primary gradient) · *See features* (ghost/secondary)
- **Animated interface preview** — desktop mockup with metric cards, timeline bars, and a task card; floating mobile mockup alongside

### Features (`<section class="features" id="features" aria-labelledby="features-title">`)
- `display: grid` three-column layout (→ two-col tablet, → one-col mobile)
- Nine feature cards with staggered `cardRise` entrance animations

| # | Feature | Description |
|---|---|---|
| 01 | Smart priorities | Ranked daily tasks for every team member |
| 02 | Shared timelines | Milestones, owners, and deadlines in one view |
| 03 | Decision notes | Meeting outcomes kept beside the project work |
| 04 | Weekly reports | Automatic progress snapshots |
| 05 | Team chat | In-context task discussions |
| 06 | File sharing | Documents and design files for the whole team |
| 07 | Calendar sync | Deadlines connected to your calendar |
| 08 | Progress tracking | Visual project health updates |
| 09 | Secure access | Role-based team permissions |

### Contact (`<section class="contact" id="contact" aria-labelledby="contact-title">`)
- Left column: contact details (email, phone, office hours, location)
- Right column: static contact form — name, email, message
- See [Contact Form](#contact-form) for implementation notes

### Footer (`<footer class="footer">`)
- Brand repeat, tagline, Privacy / Terms / email links

---

## Design System

All tokens are CSS custom properties on `:root` in `styles.css`:

```css
:root {
  --ink:            #f8fbff;               /* Primary text */
  --muted:          #b7c3d7;               /* Secondary / placeholder text */
  --surface:        #121b31;               /* Card / panel background */
  --surface-strong: #192642;               /* Elevated surface */
  --soft:           #20385f;               /* Sidebar / active state */
  --line:           rgba(255,255,255,0.12);/* Borders */
  --accent:         #38bdf8;               /* Sky blue accent */
  --accent-dark:    #7c3aed;               /* Violet accent */
  --gold:           #facc15;               /* Highlights / focus color */
  --coral:          #fb7185;               /* CTA / warning color */
  --mint:           #34d399;               /* Success / positive color */
  --shadow:         0 24px 70px rgba(0,0,0,0.35);
}
```

### Typography (fluid scale via `clamp()`)

| Element | Size | Weight |
|---|---|---|
| `h1` | `clamp(2.25rem, 7vw, 4.85rem)` | 800 |
| `h2` | `clamp(1.8rem, 4vw, 3rem)` | 800 |
| `h3` | `1.2rem` | 800 |
| Body | `1rem` / `1.12rem` (hero) | 400 |
| Eyebrow | `0.78rem` uppercase | 800 |

### Button Variants

| Class | Style |
|---|---|
| `.button.primary` | Coral → Violet gradient, coral glow shadow |
| `.button.secondary` | Frosted glass (8% white), subtle border |

Both buttons lift `-2px` on hover via `transform: translateY(-2px)`.

---

## Animations

All animations are CSS keyframes only — no JavaScript. Every animation is disabled for users with `prefers-reduced-motion: reduce` (durations collapse to `0.01ms`).

| Keyframe | Element | Effect | Duration |
|---|---|---|---|
| `backgroundMove` | `body` | Slow gradient shift | 12 s, alternate |
| `patternSlide` | `body::before` | Dot-grid drift | 18 s, linear |
| `logoPulse` | `.brand-mark` | Scale + rotate pulse | 3 s |
| `floatDesktop` | `.product-preview` | Vertical float ±14 px | 5 s |
| `floatMobile` | `.mobile-preview` | Float ±18 px + 2° tilt | 4.4 s |
| `barGrow` | `.timeline span` | Horizontal scale 0.72 → 1 | 2.4 s, alternate |
| `progressPulse` | `.phone-progress span` | Horizontal scale 0.68 → 1 | 2 s, alternate |
| `cardRise` | `.feature-card` | Fade + rise, staggered delay | 0.7 s per card |

---

## Responsive Breakpoints

| Breakpoint | Layout Changes |
|---|---|
| `> 860px` | 2-col hero · 3-col feature grid · 2-col contact |
| `≤ 860px` | Hero stacks vertically · feature grid → 2 col · contact → 1 col · mobile preview repositioned inline |
| `≤ 620px` | Header wraps to column · buttons go full-width · interface preview stacks to 1 col |

---

## Accessibility

| Feature | Implementation |
|---|---|
| Semantic HTML5 | `<header>` `<main>` `<section>` `<article>` `<aside>` `<footer>` `<nav>` `<form>` |
| Heading hierarchy | Single `<h1 id="hero-title">` · `<h2>` per section · `<h3>` per card |
| ARIA labels | `aria-label` on brand links and decorative preview containers |
| ARIA labelledby | `aria-labelledby="hero-title"` → `id="hero-title"` ✅ · `aria-labelledby="features-title"` → `id="features-title"` ✅ · `aria-labelledby="contact-title"` → `id="contact-title"` ✅ |
| Form labels | Every `<input>` and `<textarea>` paired with `<label for="...">` |
| Focus styles | Gold `outline` + `border-color` on all form inputs |
| Reduced motion | `@media (prefers-reduced-motion: reduce)` collapses all animations |
| Language | `lang="en"` declared on `<html>` |

---

## Contact Form

The contact form (`<form class="contact-form">`) is **static** — it has no `action` attribute and no JavaScript handler. Form submissions are **not sent to any backend**. This is intentional for this internship task, which focused on the front-end design and layout.

To make it functional in a real project:

```html
<!-- Option A: Formspree (no backend needed) -->
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">

<!-- Option B: Custom API -->
<!-- Add a fetch() POST in a <script> tag -->
```

---

## Screenshots

### Hero Section
![Hero Section](screenshots/hero.png)

### Features Section
![Features Section](screenshots/features.png)

### Contact Section
![Contact Section](screenshots/contact.png)

### Footer
![Footer](screenshots/footer.png)

### Mobile View
|[Mobile View](screenshots/mobile-view.png)

---

## Getting Started

No server or build tool required. Clone and open directly:

```bash
# 1. Clone the repository
git clone https://github.com/muskan03120/synent-task2-landingpage-muskan.git

# 2. Navigate into the folder
cd synent-task2-landingpage-muskan

# 3. Open in browser
#    Windows
start index.html
#    macOS
open index.html
#    Linux
xdg-open index.html

# 4. Or use a local dev server (recommended for hot reload)
python -m http.server 8080
# → visit http://localhost:8080
```

> **VS Code tip:** Install the **Live Server** extension, right-click `index.html` → *Open with Live Server* for instant hot reload.

---

## How to Extend

**Change the color palette**
Edit the CSS custom properties in `:root` inside `styles.css`. The entire color system cascades from there — one token change updates every component.

**Update page copy**
All text lives as plain HTML in `index.html`. No templating engine — just edit the text nodes directly.

**Add a new feature card**
Copy any `<article class="feature-card">` inside `.feature-grid`, update the number, heading, and description. The CSS Grid auto-flows new cards. Add a matching `animation-delay` rule in `styles.css` to continue the staggered entrance pattern.

**Swap the font**
The page currently uses the system font stack (`Arial, Helvetica, sans-serif`). To use a Google Font:
1. Add a `<link>` in `<head>` of `index.html`
2. Update `font-family` on `body` in `styles.css`

**Wire up the contact form**
See the [Contact Form](#contact-form) section for backend integration options.

---

## Known Issues

- The contact form does not submit data (static only — see [Contact Form](#contact-form))
- No hamburger/drawer menu on mobile; the nav links wrap horizontally at ≤ 620 px
- The interface preview mockup is CSS-only (no real screenshots of a live product)
- No JavaScript interactivity (scroll animations, active nav state, form validation) — out of scope for this task

---

## Commit History

This project was built with **7 meaningful commits** following a logical development workflow:

| # | Commit Message | What Was Done |
|---|---|---|
| 1 | `init: project setup with base HTML structure` | `index.html` skeleton with semantic sections |
| 2 | `feat: add design system and global styles` | CSS tokens, typography, reset, animated background |
| 3 | `feat: build hero section with animated UI preview` | Hero copy, CTA buttons, desktop + mobile mockups |
| 4 | `feat: add features grid and contact section` | 9-card feature grid and full contact form layout |
| 5 | `feat: add footer and responsive breakpoints` | Footer, 860 px and 620 px media queries |
| 6 | `chore: add screenshots and project report` | `screenshots/` folder and `report/report.md` |
| 7 | `docs: add detailed README for submission` | Final README with methodology and documentation |

---

## License

This project is licensed under the **MIT License**.

```
MIT License

Copyright (c) 2026 Muskan

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.


## Future Improvements

- Add smooth scrolling animations
- Improve accessibility
- Add dark mode
- Integrate contact form with backend
```

---

*Built by Muskan — Synent Internship Task 2 — July 2026*
*Pure HTML5 & CSS3 · No frameworks · No JavaScript · No dependencies*
