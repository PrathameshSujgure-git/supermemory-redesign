# Supermemory Design System — Style Guide

> Source of truth for all HTML designs. Every page must follow this exactly.

---

## Fonts

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=DM+Sans:wght@400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&display=swap" rel="stylesheet">
```

| Role | Family | Weight | Usage |
|------|--------|--------|-------|
| Headlines | `Space Grotesk` | 500 (Medium) | H1, H2, H3, stat values, logo |
| Body | `DM Sans` | 500 (Medium) | Body text, nav links, buttons, descriptions |
| Labels | `DM Mono` | 500 (Medium) | Section labels (ENTERPRISE, PROSUMERS), uppercase tags |

### Type Scale

| Element | Font | Size | Weight | Letter-spacing | Line-height | Color |
|---------|------|------|--------|---------------|-------------|-------|
| H1 (hero) | Space Grotesk | 64px | 500 | -3.2px | 1.1 | #0B1015 |
| H2 (section) | Space Grotesk | 52px | 500 | -2.6px | 1.1 | #0B1015 |
| H3 (card) | Space Grotesk | 28px | 500 | -1.4px | 1.25 | #0B1015 |
| Body large | DM Sans | 18px | 500 | -0.18px | 1.4 | #0B1015 |
| Body | DM Sans | 16px | 500 | -0.16px | 1.6 | #888E94 |
| Nav link | DM Sans | 15px | 500 | -0.15px | 1.4 | #0B1015 |
| Button | DM Sans | 15px | 500 | -0.15px | 1.4 | varies |
| Label | DM Mono | 12px | 500 | 0.36px | 1.5 | #1F78FF |
| Stat value | Space Grotesk | 40px | 700 | -1px | 1.1 | #0B1015 |
| Stat label | DM Sans | 14px | 500 | — | 1.4 | #888E94 |
| Trust text | DM Sans | 18px | 500 | -0.18px | 1.4 | #0B1015 |

---

## Colors

### Core Palette

| Token | Hex | RGB | Usage |
|-------|-----|-----|-------|
| `--bg` | `#F5F9FF` | 245, 249, 255 | Page background |
| `--text-primary` | `#0B1015` | 11, 16, 21 | Headlines, primary text, buttons |
| `--text-secondary` | `#888E94` | 136, 142, 148 | Body text, descriptions, stat labels |
| `--text-muted` | `#4A5568` | 74, 85, 104 | Badge text, subtle elements |
| `--accent` | `#1F78FF` | 31, 120, 255 | CTAs, labels, links, interactive blue |
| `--accent-hero` | `#0563F0` | 5, 99, 240 | Blue hero section background |
| `--accent-badge` | `#3478F6` | 52, 120, 246 | Badge dots, logo icon color |
| `--white` | `#FFFFFF` | 255, 255, 255 | Card backgrounds, badge bg |

### Borders

| Token | Value | Usage |
|-------|-------|-------|
| `--border-solid` | `1px solid #9EC7EF` | Container borders (trust, manifesto, cards) |
| `--border-dashed` | `1px dashed rgba(72, 148, 224, 0.3)` | Grid cell borders, internal dividers |
| `--border-light` | `1px solid #E2E8F0` | Badge border, subtle dividers |
| `--border-button` | `1px solid #D1D5DB` | Secondary button borders |

### Gradients

| Token | Value | Usage |
|-------|-------|-------|
| `--gradient-card` | `linear-gradient(to bottom, #D6E9FF, #F4F9FF)` | Enterprise/Prosumer card backgrounds |

---

## Layout

| Token | Value | Notes |
|-------|-------|-------|
| Max width | `1200px` | Content container |
| Design width | `1440px` | Full viewport reference |
| Container padding | `0 32px` | Horizontal page padding |
| Nav height | `89px` | Fixed |
| Nav padding | `24px 32px` | Inner padding |

### Spacing Scale

| Size | Pixels | Usage |
|------|--------|-------|
| xs | 4px | Micro gaps |
| sm | 8px | Badge gaps, tight spacing |
| md | 12px | Button gaps, card body margin |
| lg | 16px | Label margin, badge margin, headline gap |
| xl | 20px | Card internal padding, stat cells |
| 2xl | 32px | CTA gap from subtitle, nav link gap, card padding context |
| 3xl | 40px | Card padding |
| 4xl | 52px | Hero to blue section gap |
| 5xl | 64px | Section padding (manifesto, trust bottom) |
| 6xl | 80px | Hero top padding |
| 7xl | 128px | Trust section top padding |

---

## Components

### Buttons

**Primary (dark)**
```css
.btn-primary {
  font-family: 'DM Sans', sans-serif;
  font-size: 15px;
  font-weight: 500;
  padding: 10px 30px;
  height: 41px;
  border-radius: 100px;
  border: none;
  background: #0B1015;
  color: #fff;
  cursor: pointer;
  transition: all 0.2s ease;
  display: inline-flex;
  align-items: center;
}
```

**Secondary (bordered)**
```css
.btn-secondary {
  font-family: 'DM Sans', sans-serif;
  font-size: 15px;
  font-weight: 500;
  padding: 10px 24px;
  height: 41px;
  border-radius: 100px;
  border: 1px solid #D1D5DB;
  background: transparent;
  color: #0B1015;
  cursor: pointer;
  transition: all 0.2s ease;
  display: inline-flex;
  align-items: center;
}
```

**Nav button**
```css
.btn-nav {
  /* Same as btn-secondary but padding: 10px 22px */
  padding: 10px 22px;
  /* Hover: bg #0B1015, color #fff, border-color #0B1015 */
}
```

### Badge / Pill

```css
.badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 5px 10px;
  background: #fff;
  border: 1px solid #E2E8F0;
  border-radius: 100px;
  font-family: 'DM Sans', sans-serif;
  font-size: 14px;
  font-weight: 500;
  color: #0B1015;
}
/* Contains: blue dot (12x12, bg #3478F6, radius 4px) + divider (1x14, bg #E2E8F0) + text + arrow */
```

### Section Labels (uppercase tags)

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
  font-size: 16px;
  font-weight: 500;
  color: #1F78FF;
  /* Arrow slides on hover: gap 4px → 8px */
  transition: gap 0.2s ease;
}
```

### Cards

```css
.card {
  background: linear-gradient(to bottom, #D6E9FF, #F4F9FF);
  padding: 40px;
  /* Internal structure uses dashed borders for grid cells */
}
```

### Stat Cells (dashed border grid)

```css
.stat-cell {
  border: 1px dashed rgba(72, 148, 224, 0.3);
  padding: 20px;
  margin-right: -1px;  /* overlap borders */
  margin-bottom: -1px;
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
  border-bottom: 1px dashed rgba(72, 148, 224, 0.3);
}
```

### Bordered Container (signature pattern)

```css
.bordered-container {
  max-width: 1200px;
  margin: 0 auto;
  border: 1px solid #9EC7EF;
}
```

---

## Signature Visual Patterns

### 1. Dashed Grid Borders
The design's most distinctive visual feature. All internal divisions use:
```
border: 1px dashed rgba(72, 148, 224, 0.3)
```
Applied to: trust logo cells, stat cells, plugin cells, card dividers.

### 2. Solid Blue Containers
Outer containers use solid blue borders:
```
border: 1px solid #9EC7EF
```
Applied to: trust section, manifesto section, cards wrapper.

### 3. Blue Hero Section
Full-width blue band with dot pattern:
```css
.blue-hero {
  background-color: #0563F0;
  background-image: radial-gradient(rgba(255,255,255,0.15) 1px, transparent 1px);
  background-size: 20px 20px;
  height: 561px;
}
```

### 4. Card Gradients
Cards use a subtle blue-to-white gradient:
```
background: linear-gradient(to bottom, #D6E9FF, #F4F9FF);
```

---

## Responsive Breakpoints

| Breakpoint | Changes |
|-----------|---------|
| `≤ 1024px` | H1 → 48px, H2 → 40px. Cards stack to 1 column. Nav links hide. Trust grid → 3 columns. |
| `≤ 768px` | Nav height → 64px, padding → 16px 20px. H1 → 36px. Hero CTAs stack vertical. Blue hero → 300px, icon → 80px. Trust grid → 2 columns. Stats/plugin grids → 1 column. H2 → 32px. |
| `≤ 480px` | H1 → 30px. Card padding → 24px. |

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

## Hover / Transition Defaults

```css
transition: all 0.2s ease;
```

| Element | Hover behavior |
|---------|---------------|
| Nav links | `opacity: 0.7` |
| Primary button | `opacity: 0.9` |
| Secondary button | `border-color: #0B1015` |
| Nav button | `bg: #0B1015, color: #fff, border-color: #0B1015` |
| CTA link | Arrow gap `4px → 8px` |
| Badge | `border-color: #3478F6` |

---

## File Structure

```
supermemory-redesign/
├── index.html          ← Current working design
├── history.html        ← Iteration history viewer
├── history.json        ← Iteration log (auto-updated)
├── style.md            ← THIS FILE (design system)
├── 01-homepage.md      ← Copy/wireframe doc
├── figma-reference.png ← Figma screenshot reference
└── snapshots/
    ├── v1.html         ← First iteration
    └── v2.html         ← Figma-exact match
```
