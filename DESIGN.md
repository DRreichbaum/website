# Design

## Theme

**Mode**: Light  
**Strategy**: Committed — deep institutional green carries the brand identity; pure white ground lets it breathe.  
**Mood phrase**: "A well-produced field report from a boutique clean energy advisory — deep green headers on white stock, warm copper callouts, deliberate typographic spacing."

---

## Color

```css
:root {
  /* Brand */
  --color-primary:  oklch(0.35 0.095 165);  /* deep institutional teal-green */
  --color-accent:   oklch(0.60 0.115 55);   /* warm copper / amber */

  /* Surfaces */
  --color-bg:       oklch(1.000 0.000 0);   /* pure white */
  --color-surface:  oklch(0.968 0.005 160); /* faint green-tinted panel bg */

  /* Text */
  --color-ink:      oklch(0.20 0.018 165);  /* near-black, slight green cast */
  --color-muted:    oklch(0.48 0.010 160);  /* secondary text ≥4.5:1 on bg */
}
```

**Text on filled elements**:  
- `--color-primary` fills → white text (`--color-bg`)  
- `--color-accent` fills → white text (`--color-bg`)  
- `--color-surface` fills → `--color-ink`

---

## Typography

**Display / headings**: [Gloock](https://fonts.google.com/specimen/Gloock) — high-contrast bracketed serif. Carries gravitas and warmth without landing in the editorial-magazine reflex lane.  
**Body / UI**: [Source Sans 3](https://fonts.google.com/specimen/Source+Sans+3) — humanist sans-serif, excellent legibility at all sizes, warm without being casual.

```css
:root {
  --font-display: 'Gloock', Georgia, serif;
  --font-body:    'Source Sans 3', system-ui, sans-serif;
}
```

**Fluid type scale** (1.33× ratio):
```css
:root {
  --text-xs:   clamp(0.75rem,  0.70rem  + 0.25vw, 0.875rem);
  --text-sm:   clamp(0.875rem, 0.82rem  + 0.28vw, 1rem);
  --text-base: clamp(1rem,     0.95rem  + 0.25vw, 1.125rem);
  --text-lg:   clamp(1.125rem, 1.05rem  + 0.38vw, 1.333rem);
  --text-xl:   clamp(1.333rem, 1.20rem  + 0.67vw, 1.777rem);
  --text-2xl:  clamp(1.777rem, 1.50rem  + 1.40vw, 2.369rem);
  --text-3xl:  clamp(2.369rem, 1.90rem  + 2.35vw, 3.157rem);
  --text-4xl:  clamp(3.157rem, 2.40rem  + 3.80vw, 4.209rem);
}
```

**Body line length**: max 68ch.  
**Headings**: `text-wrap: balance`. Body prose: `text-wrap: pretty`.

---

## Spacing

```css
:root {
  --space-1:  0.25rem;
  --space-2:  0.5rem;
  --space-3:  0.75rem;
  --space-4:  1rem;
  --space-6:  1.5rem;
  --space-8:  2rem;
  --space-12: 3rem;
  --space-16: 4rem;
  --space-24: 6rem;
  --space-32: 8rem;
}
```

---

## Components

**Primary CTA button**: `--color-primary` bg, white text, `border-radius: 3px`, compact padding (`0.6em 1.4em`). Hover: primary lightness up ~0.05.  
**Booking CTA (Calendly)**: `--color-accent` bg, white text. This is the most prominent interactive element on the page.  
**Section dividers**: 1px rules in `--color-surface`, or spacing alone — no decorative multi-pixel borders.  
**Nav**: Minimal. Logo / name left, links right. No background on scroll unless needed for legibility.

---

## Motion

**Energy**: Calm and purposeful. One clean page-load entrance. No scroll-triggered reveals on every section — sections are visible by default.

```css
:root {
  --duration-fast: 150ms;
  --duration-base: 250ms;
  --duration-slow: 400ms;
  --ease-out: cubic-bezier(0.16, 1, 0.3, 1);
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## Layout

**Max content width**: 1100px, centered.  
**Horizontal padding**: `clamp(1.5rem, 5vw, 4rem)`.  
**Rhythm**: Generous section separation (`--space-24` to `--space-32`), tight within-section grouping.  
**Structure**: Single column on mobile. Asymmetric two-column (60/40 or 55/45) on desktop for bio and services sections.

**Z-index scale**:
```css
:root {
  --z-dropdown:       100;
  --z-sticky:         200;
  --z-modal-backdrop: 300;
  --z-modal:          400;
  --z-toast:          500;
  --z-tooltip:        600;
}
```
