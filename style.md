# Supermemory Design System — Style Guide (v2)

> Source of truth for all HTML designs. Every page must follow this exactly.
> Updated from visual-refinement pass — Figma node 143:863 pattern-matched.

---

## Core Principle

**Blocky, grid-based, zero border-radius.** Everything is square. No pills, no rounded corners, no circles. The design language is brutalist-minimal with dashed grid borders and solid boxed containers.

---

## Fonts

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=DM+Sans:wght@400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&display=swap" rel="stylesheet">
```

| Role | Family | Weight | Usage |
|------|--------|--------|-------|
| Headlines | `Space Grotesk` | 500 (Medium) | H1, H2, H3, stat values, logo text |
| Body | `DM Sans` | 500 (Medium) | Body text, nav links, buttons, descriptions |
| Labels | `DM Mono` | 500 (Medium) | Section labels (ENTERPRISE, PROSUMERS), uppercase tags, step numbers |

### Type Scale

| Element | Font | Size | Weight | Letter-spacing | Line-height | Color |
|---------|------|------|--------|---------------|-------------|-------|
| H1 (hero) | Space Grotesk | 64px | 500 | -3.2px | 1.1 | #0B1015 |
| H2 (section) | Space Grotesk | 56px | 500 | -2.8px | 1.1 | #0B1015 |
| H3 (card) | Space Grotesk | 26px | 500 | -1.3px | 1.2 | #0B1015 |
| Body large | DM Sans | 18px | 500 | -0.18px | 1.5 | #0B1015 |
| Body | DM Sans | 15px | 500 | -0.15px | 1.6 | #888E94 |
| Nav link | DM Sans | 15px | 500 | -0.15px | 1.4 | #0B1015 |
| Button | DM Sans | 15px | 500 | -0.15px | 1.4 | #0B0F15 |
| Label | DM Mono | 12px | 500 | 0.36px | 1.5 | #1F78FF |
| Stat value | Space Grotesk | 36px | 700 | -1px | 1.1 | #0B1015 |
| Stat label | DM Sans | 13px | 500 | — | 1.4 | #888E94 |
| Trust text | DM Sans | 18px | 500 | -0.18px | 1.4 | #0B1015 |

---

## Colors

### Core Palette

| Token | Hex | Usage |
|-------|-----|-------|
| `--bg` | `#F5F9FF` | Page background AND container background |
| `--text-primary` | `#0B1015` | Headlines, primary text, hero subtitle |
| `--text-secondary` | `#888E94` | Body text, descriptions, stat labels |
| `--accent` | `#1F78FF` | Labels, links, CTA text, interactive blue |
| `--accent-hero` | `#0563F0` | Blue hero section background |
| `--accent-dot-outer` | `rgba(0,123,255,0.5)` | Badge dot outer square |
| `--accent-dot-inner` | `#0553DB` | Badge dot inner square |
| `--btn-bg` | `#fafafa` | All button backgrounds |
| `--badge-bg` | `#DEEBFF` | Badge background |
| `--white` | `#FFFFFF` | Tweet cards, some cell backgrounds |

### Borders (CRITICAL — defines the design)

| Token | Value | Usage |
|-------|-------|-------|
| `--border-container` | `1px solid #9EC7EF` | Boxed section containers (trust, manifesto+products) |
| `--border-dashed` | `1px dashed rgba(72, 148, 224, 0.3)` | ALL internal dividers, grid cells, page side borders |
| `--border-button` | `1px solid rgba(72, 148, 224, 0.3)` | ALL buttons and badge borders |

**IMPORTANT**: There are only 2 border types:
1. **Solid #9EC7EF** — for wrapping boxed sections
2. **Dashed rgba(72,148,224,0.3)** — for everything else (internal dividers, buttons, badge, page edges)

No `#D1D5DB`, no `#E2E8F0` borders anywhere.

### Gradients

| Token | Value | Usage |
|-------|-------|-------|
| `--gradient-card` | `linear-gradient(to bottom, #D6E9FF, #F4F9FF)` | Product cards (enterprise/prosumer) |

---

## Layout

| Token | Value | Notes |
|-------|-------|-------|
| Max width | `1200px` | Content container with dashed side borders |
| Design width | `1440px` | Full viewport reference |
| Container bg | `#F5F9FF` | Same as page bg — no white container |
| Container borders | `1px dashed rgba(72,148,224,0.3)` | Left + right dashed borders |
| Nav padding | `24px 32px` | No bottom border, transparent bg |

### Spacing Scale

| Size | Pixels | Usage |
|------|--------|-------|
| xs | 4px | Micro gaps |
| sm | 8px | Badge gaps, tight spacing |
| md | 12px | Card body margin |
| lg | 16px | Hero element gap, label margin, CTA gap |
| xl | 20px | Card internal padding, stat cells |
| 2xl | 24px | Nav link gap, nav right gap |
| 3xl | 32px | Hero CTA margin-top, card padding, section padding |
| 4xl | 56px | Trust section inner padding |
| 5xl | 64px | Manifesto padding, trust bottom spacing |
| 6xl | 80px | Manifesto vertical padding |
| 7xl | 128px | Trust section top outer padding |
| 8xl | 144px | Hero top padding |

---

## Components

### Buttons (ALL share the same style)

**There is only ONE button style.** Primary, secondary, nav — all identical.

```css
.btn {
  font-family: 'DM Sans', sans-serif;
  font-size: 15px;
  font-weight: 500;
  padding: 10px 24px;
  border-radius: 0;                              /* ZERO — blocky */
  border: 1px solid rgba(72, 148, 224, 0.3);     /* dashed-blue border */
  background: #fafafa;
  color: #0B0F15;
  cursor: pointer;
  transition: all 0.2s ease;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  letter-spacing: -0.15px;
  line-height: 1.4;
  white-space: nowrap;
}

.btn:hover {
  border-color: rgba(72, 148, 224, 0.6);
  background: #f0f4f8;
}
```

Hero buttons add `min-width: 167px`. Nav button is identical. Full-width adds `width: 100%`.

### Badge

```css
.badge {
  display: inline-flex;
  align-items: stretch;
  gap: 0;
  padding: 0;
  background: #DEEBFF;
  border: 1px solid rgba(72, 148, 224, 0.3);
  border-radius: 0;
  font-family: 'DM Sans', sans-serif;
  font-size: 15px;
  font-weight: 500;
  color: #0B1015;
  letter-spacing: -0.15px;
  line-height: 1.4;
}

/* Left compartment: dot + "Research" label, border-right divider */
/* Right compartment: text + arrow */
/* Dot: 12x12 outer (rgba(0,123,255,0.5)), 7.2x7.2 inner (#0553DB), both square */
```

### Section Labels

```css
.section-label {
  font-family: 'DM Mono', monospace;
  font-size: 12px;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.36px;
  color: #1F78FF;
}
```

### CTA Links

```css
.cta-link {
  font-family: 'DM Sans', sans-serif;
  font-size: 15px;
  font-weight: 500;
  color: #1F78FF;
  display: inline-flex;
  align-items: center;
  gap: 4px;
  transition: gap 0.2s ease;
}
.cta-link:hover { gap: 8px; }
```

### Cards (product cards)

```css
.card {
  background: linear-gradient(to bottom, #D6E9FF, #F4F9FF);
  /* Internal structure uses dashed borders for grid cells */
  /* No border-radius anywhere */
}
```

### Stat Cells

```css
.stat-cell {
  border-top: 1px dashed rgba(72, 148, 224, 0.3);
  border-right: 1px dashed rgba(72, 148, 224, 0.3);
  padding: 20px;
}
```

### Trust Grid Cells

```css
.trust-cell {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 88px;
  border-right: 1px dashed rgba(72, 148, 224, 0.3);
  border-top: 1px dashed rgba(72, 148, 224, 0.3);
}
```

### Bordered Container (boxed sections)

```css
.bordered-container {
  border: 1px solid #9EC7EF;
}
```

Used for: trust section wrapper, manifesto+products wrapper.

### Step Numbers

```css
.step-num {
  width: 28px;
  height: 28px;
  border-radius: 0;
  background: transparent;
  border: 1px solid #9EC7EF;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'DM Mono', monospace;
  font-size: 12px;
  font-weight: 500;
  color: #1F78FF;
}
```

### Pricing List Items

```css
/* Em-dash prefix instead of checkmarks */
li::before {
  content: '—';
  color: #1F78FF;
  font-family: 'DM Mono', monospace;
  font-size: 10px;
}
```

### Price Pro Tag

```css
.price-tag {
  padding: 2px 6px;
  background: transparent;
  border: 1px solid #9EC7EF;
  border-radius: 0;
  font-family: 'DM Mono', monospace;
  font-size: 11px;
  font-weight: 500;
  color: #1F78FF;
  text-transform: uppercase;
  letter-spacing: 0.3px;
}
```

---

## Signature Visual Patterns

### 1. Dashed Grid Borders
The design's most distinctive visual feature. ALL internal divisions use:
```
border: 1px dashed rgba(72, 148, 224, 0.3)
```
Applied to: trust logo cells, stat cells, plugin cells, card dividers, page side borders, button borders, badge borders.

### 2. Solid Blue Containers
Wrapping containers for major sections:
```
border: 1px solid #9EC7EF
```
Applied to: trust section, manifesto+products section.

### 3. Blue Hero Section
Full-width blue band with dot pattern:
```css
.blue-hero {
  background-color: #0563F0;
  background-image: radial-gradient(rgba(255,255,255,0.12) 1px, transparent 1px);
  background-size: 20px 20px;
  height: 560px;
}
```

### 4. Card Gradients
Product cards use a subtle blue-to-white gradient:
```
background: linear-gradient(to bottom, #D6E9FF, #F4F9FF);
```

### 5. Zero Border Radius (EVERYWHERE)
```
border-radius: 0;
```
Applied to: buttons, badge, step numbers, avatars, social icons, plugin icons, pricing tags. The only exception is hamburger menu lines (1px radius).

### 6. Page Container
```css
.page-grid {
  max-width: 1200px;
  margin: 0 auto;
  border-left: 1px dashed rgba(72, 148, 224, 0.3);
  border-right: 1px dashed rgba(72, 148, 224, 0.3);
  background: #F5F9FF;
}
```

---

## Hover / Transition Defaults

```css
transition: all 0.2s ease;
```

| Element | Hover behavior |
|---------|---------------|
| Nav links | `opacity: 0.7` |
| All buttons | `border-color: rgba(72,148,224,0.6); background: #f0f4f8` |
| CTA link | Arrow gap `4px → 8px` |
| Badge | `border-color: rgba(72,148,224,0.6)` |
| Trust logos | `opacity: 0.7` |

---

## Responsive Breakpoints

| Breakpoint | Changes |
|-----------|---------|
| `≤ 1024px` | H1 → 48px, H2 → 42px. Container side borders removed. Cards stack 1-col. Nav links hide, mobile menu shows. Trust grid → 4 cols. Trust wrapper padding → 64px 0 32px. |
| `≤ 768px` | Nav padding → 16px 20px. H1 → 36px, H2 → 32px. Hero CTAs stack vertical. Blue hero → 240px. Trust grid → 3 cols. All grids → 1 col. |
| `≤ 480px` | H1 → 30px. Cell padding → 20px. Plugin grid stays 1-col. |

---

## CSS Reset (use on every page)

```css
*, *::before, *::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: 'DM Sans', sans-serif;
  font-weight: 500;
  background: #F5F9FF;
  color: #0B1015;
  line-height: 1.5;
  overflow-x: hidden;
}

a {
  text-decoration: none;
  color: inherit;
}
```

---

## Logo Assets (Figma API)

| Company | URL |
|---------|-----|
| Caret | `https://www.figma.com/api/mcp/asset/17ee1db8-42d1-47d3-98de-80cd4fca7442` |
| Composio | `https://www.figma.com/api/mcp/asset/19f3a702-9cda-4fe7-a009-6bafe67b0d82` |
| Cluely | `https://www.figma.com/api/mcp/asset/2daaaeac-b98c-44c7-8a83-912b26b8f94f` |
| Montra | `https://www.figma.com/api/mcp/asset/d090e42a-70bb-4f17-9a09-914f95f8b46a` |
| Motion | `https://www.figma.com/api/mcp/asset/351dd9bb-b5b6-48e2-9ef3-f16aeb6d79a8` |
| MedTech Vendors | `https://www.figma.com/api/mcp/asset/2c9ddded-5b1b-4a24-b0e3-fa15c064b876` |
| perspective | `https://www.figma.com/api/mcp/asset/0b495eee-98af-449f-bafa-8b47d3fd69c9` |
| SlothMD | `https://www.figma.com/api/mcp/asset/4ca4e82c-393e-4876-bff9-2c6c37f648c0` |
| scira | `https://www.figma.com/api/mcp/asset/2f32a5d3-3247-4d2f-8c4e-be3db894bcfd` |
| mixus | `https://www.figma.com/api/mcp/asset/1c549d07-0581-4cf4-9d2b-eb5c291e8b2c` |
| ASU | `https://www.figma.com/api/mcp/asset/6cd71614-18c9-4769-b576-e97547e39ce5` |
| P icon | `https://www.figma.com/api/mcp/asset/1a92a034-1530-4844-94a2-74a7e6af4b1b` |

## Plugin Assets (Figma API)

| Plugin | URL |
|--------|-----|
| OpenClaw | `https://www.figma.com/api/mcp/asset/d22062aa-d8c1-4c07-8a14-b52d517c261f` |
| Claude Code | `https://www.figma.com/api/mcp/asset/3a60b543-2cf5-4779-8a57-34a4d1b78235` |
| OpenCode | `https://www.figma.com/api/mcp/asset/c831d077-e934-4887-b46c-05c396426c90` |

---

## File Structure

```
supermemory-redesign/
├── index.html              ← Homepage
├── enterprise.html         ← Enterprise landing page
├── plugins.html            ← Plugins landing page
├── visual-refinement/
│   └── index.html          ← Visual refinement workspace
├── history.html            ← Iteration history viewer
├── history.json            ← Iteration log (auto-updated)
├── style.md                ← THIS FILE (design system v2)
├── 01-homepage.md          ← Copy/wireframe doc
├── figma-reference.png     ← Figma screenshot reference
└── snapshots/              ← Versioned HTML snapshots
```
