# Project Report — Flowdesk Landing Page

**Intern:** Muskan  
**Task:** Task 2 — Responsive SaaS Landing Page  
**Organisation:** Synent  
**Date:** July 2026

---

## 1. Objective

The objective of this task was to design and develop a fully responsive, accessible, and visually polished marketing landing page for a fictional SaaS product called **Flowdesk** — a team project management tool — using only **HTML5 and CSS3**, with no JavaScript frameworks or build tools.

---

## 2. Tools & Technologies Used

| Tool / Technology | Purpose |
|---|---|
| HTML5 | Page structure and semantic markup |
| CSS3 | Styling, layout, animations, and responsive design |
| CSS Custom Properties | Design token system (colours, shadows) |
| CSS Grid | Hero, feature grid, and contact section layouts |
| CSS Keyframes | All animations (float, pulse, rise, drift) |
| VS Code + Live Server | Development environment |
| Chrome DevTools | Responsive testing across breakpoints |

---

## 3. Approach & Methodology

### Step 1 — Research & Planning
Before writing any code, I studied several modern SaaS landing pages to understand:
- What sections are standard (hero, features, contact, footer)
- How visual hierarchy is used to guide users toward a CTA
- What makes a dark-mode design feel premium vs flat

I then sketched the rough layout on paper: a split two-column hero with a UI preview on the right, followed by a features grid and a contact section.

### Step 2 — Design System
I established the design system first by defining all CSS custom properties on `:root`:
- **Colours** — a navy dark background, sky-blue and violet accents, coral for CTAs, gold for highlights
- **Shadows** — a single `--shadow` token reused across cards and modals
- **Typography** — fluid font sizes using `clamp()` to scale smoothly between mobile and desktop without breakpoint hacks

### Step 3 — HTML Markup
I wrote fully semantic HTML5 with:
- A single `<h1>` per page
- `<section>`, `<article>`, `<aside>`, `<nav>`, `<form>` elements appropriately
- `aria-label` and `aria-labelledby` on interactive and decorative regions
- Explicit `<label for>` pairing on every form input

### Step 4 — Layout
CSS Grid handled all major layouts:
- **Hero**: `grid-template-columns: 1fr 0.92fr` — copy on left, UI preview on right
- **Features**: `repeat(3, 1fr)` — 9 cards in a 3-column grid
- **Contact**: `1fr minmax(320px, 420px)` — copy + form side by side
- A single `width: min(1120px, calc(100% - 32px))` container kept all sections centred with comfortable edge padding on mobile

### Step 5 — Animations
All animations are CSS keyframes only — no JavaScript:
- **Background**: slow-moving radial gradients + a drifting dot-grid pattern on `::before`
- **Logo**: subtle `scale + rotate` pulse
- **Mockups**: independent `floatDesktop` and `floatMobile` keyframes give the UI preview a sense of life
- **Feature cards**: staggered `cardRise` fade-in with `animation-delay` per card
- **Timeline bars / progress bar**: alternating `scaleX` pulses to simulate live data

### Step 6 — Responsiveness
Two breakpoints were used:
- **≤ 860px** — hero stacks vertically, feature grid becomes 2 columns, contact stacks
- **≤ 620px** — header wraps to column, buttons go full-width, preview stacks to single column

Tested on Chrome DevTools for: iPhone SE (375px), iPad (768px), and standard 1440px desktop.

### Step 7 — Accessibility
- All animations respect `@media (prefers-reduced-motion: reduce)` — durations collapse to `0.01ms`
- Focus styles use a gold `outline` + `border-color` on all form inputs
- Colour contrast maintained between `--ink` (#f8fbff) and `--surface` (#121b31) — passes WCAG AA

---

## 4. Challenges & Solutions

| Challenge | Solution |
|---|---|
| Positioning the mobile mockup over the desktop mockup | Used `position: absolute` on `.mobile-preview` within a relative container, then switched to `position: static` in a CSS Grid layout at ≤ 860px |
| Creating animated bar charts without JavaScript | Used CSS `scaleX` keyframes with `transform-origin: left` on block-level `<span>` elements |
| Fluid typography that works at all screen sizes | Used `clamp(min, preferred, max)` values — e.g. `clamp(2.25rem, 7vw, 4.85rem)` for `<h1>` |
| Keeping background animations subtle | Tuned opacity values on radial gradients and the dot-grid pattern independently |

---

## 5. Key Learnings

- **CSS custom properties** are extremely powerful for maintaining design consistency — changing one token updates the entire page
- **CSS Grid** with `minmax()` and `min()` can handle complex, responsive layouts without media query overuse
- **CSS animations** can create rich, engaging UIs without any JavaScript — keeping the codebase lean
- **Accessibility** should be planned from the start (semantic HTML, ARIA), not bolted on at the end
- **`prefers-reduced-motion`** is a simple but important inclusion for inclusive design

---

## 6. Result

A fully responsive, animated, dark-mode SaaS landing page for Flowdesk built with:
- **218 lines** of semantic HTML
- **841 lines** of CSS (design system + layout + components + animations + media queries)
- **0 JavaScript** files
- **0 external dependencies**

The page scores well on readability, visual hierarchy, and accessibility fundamentals.

---

## 7. Screenshots

See the `screenshots/` folder for:
- `hero.png` — Hero section with animated UI mockups
- `features.png` — 9-card features grid
- `contact.png` — Contact form and details
- `footer.png` — Footer with links
- 'mobile-view.png' - Mobile View
---

*Muskan — Synent Internship Task 2 — July 2026*
