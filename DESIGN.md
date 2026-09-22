# Ember & Ground — Design System
> An independent specialty coffee roastery landing page. Dark, editorial, tactile — the feeling of a handwritten menu in a warmly lit roastery.

**Brand name:** Ember & Ground  
**Tagline:** *Small-batch roasted. Carefully sourced. Honestly served.*  
**Theme:** Dark-first, editorially warm

---

## 1. Color Palette

All colors are defined as CSS custom properties on `:root`. Every color reference in `index.html` must use a variable — no hard-coded hex values.

### Contrast check (WCAG AA minimum 4.5:1 for normal text, 3:1 for large text)
- `--color-bone` (#ffffff) on `--color-obsidian` (#0e1311): ≈ 19.5:1 ✓
- `--color-bone` (#ffffff) on `--color-ash-charcoal` (#1a1a1a): ≈ 16.7:1 ✓
- `--color-silver` (#b3b3b3) on `--color-obsidian` (#0e1311): ≈ 9.1:1 ✓
- `--color-obsidian` (#0e1311) on `--color-linen` (#f6f7f2): ≈ 17.4:1 ✓
- `--color-obsidian` (#0e1311) on `--color-citron` (#faf080): ≈ 14.2:1 ✓
- `--color-obsidian` (#0e1311) on `--color-lichen-green` (#cadcac): ≈ 8.9:1 ✓

```css
:root {
  /* ── Canvas & Surfaces ── */
  --color-obsidian:       #0e1311;  /* Primary page background — near-black with faint green undertone */
  --color-ash-charcoal:   #1a1a1a;  /* Elevated surface — nav, cards, dividers, outlined button edges */
  --color-graphite:       #2a2a2a;  /* Card inner surface — slightly lifted from ash for layering */
  --color-pure-black:     #000000;  /* Maximum contrast — SVG strokes, deepest borders */

  /* ── Text ── */
  --color-bone:           #ffffff;  /* Primary text on dark canvases — sharp, high-contrast */
  --color-silver:         #b3b3b3;  /* Secondary / muted text — tasting notes, captions, subtext */
  --color-graphite-text:  #666666;  /* Tertiary text — footnotes, timestamps on light surfaces */

  /* ── Light / Inverted Surfaces ── */
  --color-linen:          #f6f7f2;  /* Warm off-white — price pills, inverted sections, soft fills */
  --color-sand-khaki:     #dfdbca;  /* Hairline borders and dividers on light surfaces */

  /* ── Brand Accents (use sparingly — badges and fine details only) ── */
  --color-ember:          #c0502a;  /* Warm ember-red — hero backdrop wash, decorative strokes */
  --color-antique-gold:   #cfa53b;  /* Aged brass — limited/special badge borders */
  --color-citron:         #faf080;  /* Pale yellow — "New Release" badge fill */
  --color-lichen-green:   #cadcac;  /* Sage — category badge fill */
  --color-olive-bark:     #4d4a31;  /* Deep olive — announcement bar background */
}
```

### Color Role Summary

| Token | Role |
|---|---|
| `--color-obsidian` | Page background, hero, section fills |
| `--color-ash-charcoal` | Nav, card borders, raised surfaces |
| `--color-graphite` | Card inner backgrounds |
| `--color-pure-black` | SVG strokes, deepest outlines |
| `--color-bone` | Primary text, button text on dark |
| `--color-silver` | Secondary text, captions, meta |
| `--color-linen` | Price pills, inverted light fills |
| `--color-sand-khaki` | Hairlines, dividers, input outlines |
| `--color-ember` | Hero gradient, decorative accents |
| `--color-antique-gold` | Special/limited badge border |
| `--color-citron` | New-release badge fill |
| `--color-lichen-green` | Category badge fill |
| `--color-olive-bark` | Announcement bar |

---

## 2. Typography

### Font Families

Both fonts sourced from Google Fonts. Import at most two weights per family.

```css
/* Google Fonts import */
@import url('https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;1,300;1,400&family=Inter:wght@400;500&display=swap');

:root {
  --font-serif:  'Cormorant Garamond', ui-serif, Georgia, 'Times New Roman', serif;
  --font-sans:   'Inter', ui-sans-serif, system-ui, -apple-system, sans-serif;
}
```

### Font Roles

| Family | Role | Rationale |
|---|---|---|
| `--font-serif` (Cormorant Garamond Italic) | Headlines, product names, section labels, hero copy, manifesto | Elegant, editorial voice — italic form gives the coffee-journal feel |
| `--font-sans` (Inter) | Body copy, nav, buttons, captions, price, metadata, footer | Clean geometric workhorse — readable at 11–16px, unobtrusive |

### Type Scale

Base: `1rem = 16px`. All sizes in `rem`.

```css
:root {
  /* Scale */
  --text-caption:     0.6875rem;  /* 11px — uppercase labels, meta tags */
  --text-small:       0.75rem;    /* 12px — footnotes, helper text */
  --text-body:        1rem;       /* 16px — body copy */
  --text-subheading:  1.125rem;   /* 18px — card subtitles, nav links */
  --text-heading-sm:  1.3125rem;  /* 21px — card product names */
  --text-heading:     1.875rem;   /* 30px — section headings */
  --text-heading-lg:  2.25rem;    /* 36px — large section headings */
  --text-display:     2.625rem;   /* 42px — hero display text */

  /* Line Heights */
  --leading-tight:    1.15;
  --leading-snug:     1.25;
  --leading-normal:   1.4;
  --leading-relaxed:  1.6;

  /* Weights */
  --weight-light:     300;
  --weight-regular:   400;
  --weight-medium:    500;
}
```

### Typography Rules

- Serif is **always italic** when used for headlines and product names — this is the non-negotiable editorial signature.
- Serif weight: 300 (light italic) for display/manifesto, 400 (regular italic) for headings and product names.
- Sans weight: 400 for body/nav, 500 for labels and buttons.
- Sans uppercase at `--text-caption` uses `letter-spacing: 0.08em` for badge and label readability.
- No heading may use weight 600 or higher — the whisper-quiet tone relies on lightness.

---

## 3. Spacing & Layout System

Base unit: **8px**.

```css
:root {
  /* Spacing Scale */
  --space-1:   4px;
  --space-2:   8px;
  --space-3:   12px;
  --space-4:   16px;
  --space-5:   20px;
  --space-6:   24px;
  --space-8:   32px;
  --space-10:  40px;
  --space-12:  48px;
  --space-16:  64px;
  --space-20:  80px;
  --space-24:  96px;
  --space-40:  160px;

  /* Layout */
  --max-width:         1320px;
  --gutter:            clamp(1rem, 4vw, 3rem);
  --section-gap:       var(--space-20);   /* 80px vertical between sections */
  --card-padding:      var(--space-5);    /* 20px internal card padding */

  /* Border Radius */
  --radius-sm:         4px;   /* cards, badges, inputs, buttons, nav elements */
  --radius-full:       60px;  /* price pills only */
  --radius-circle:     9999px; /* icon circles */

  /* Shadow */
  --shadow-card:  rgba(0, 0, 0, 0.06) 0px 2px 12px -3px;
  --shadow-lift:  rgba(0, 0, 0, 0.12) 0px 4px 16px -4px;
}
```

### Layout Rules
- Content is contained in a centered wrapper: `max-width: var(--max-width)`, `padding-inline: var(--gutter)`.
- Sections stack vertically with `padding-block: var(--section-gap)`.
- Grid uses CSS Grid; Flexbox for alignment within rows.
- No floats.

---

## 4. Section Inventory

The page contains **exactly these sections in this order**:

| # | Section | Purpose |
|---|---|---|
| 1 | **Announcement Bar** | Single-line strip at top — shipping or time-limited offer message |
| 2 | **Primary Navigation** | Sticky header with logo, nav links, and utility actions |
| 3 | **Hero** | Two-column editorial hero — typographic index left, product visual right |
| 4 | **Manifesto** | Full-width brand statement in large italic serif prose |
| 5 | **Featured Menu** | 4-card grid of signature drinks with name, description, and price |
| 6 | **Story / Why Us** | Two-column split — roastery narrative left, three values right |
| 7 | **Testimonials** | Two short customer quotes with name and attribution |
| 8 | **Visit Us / Hours** | Map placeholder + opening hours + address |
| 9 | **Final CTA** | Full-width dark call-to-action to order or visit |
| 10 | **Footer** | Logo, nav links, social links, legal line |

---

## 5. Component Specs

### 5.1 Primary Button
Used for the main call-to-action (e.g. "Order Online", "Visit Us").

- Background: `--color-pure-black`
- Text: `--color-bone`, `--font-sans`, `--text-body`, `--weight-medium`
- Border: `1px solid --color-ash-charcoal`
- Radius: `--radius-sm` (4px)
- Padding: `var(--space-3) var(--space-8)` (12px 32px)
- **Hover:** background → `--color-ash-charcoal`, border-color → `--color-bone`; `transition: background 220ms ease, border-color 220ms ease`
- **Focus-visible:** `outline: 2px solid --color-bone; outline-offset: 3px`

### 5.2 Secondary Button / Ghost Button
Used for secondary actions (e.g. "See Full Menu", "Learn More").

- Background: `transparent`
- Text: `--color-bone`, `--font-sans`, `--text-body`, `--weight-medium`
- Border: `1px solid --color-sand-khaki`
- Radius: `--radius-sm`
- Padding: `var(--space-3) var(--space-8)`
- **Hover:** border-color → `--color-bone`; `transition: border-color 220ms ease`
- **Focus-visible:** same as primary

### 5.3 Editorial Link (typographic CTA)
Used for hero CTAs ("Shop Now", "Limited Time").

- No background, no border
- Text: `--font-serif`, italic, `--text-subheading`, `--color-bone`
- **Hover:** text-decoration underline, color → `--color-silver`
- Transition: `color 180ms ease`

### 5.4 Product Card (Dark)
Used in the Featured Menu section.

- Background: `--color-graphite`
- Border: `1px solid --color-ash-charcoal`
- Radius: `--radius-sm`
- Padding: 0 (image flush top, text in padding block below)
- Shadow: `--shadow-card`
- Image area: upper ~55% — CSS gradient placeholder on `--color-ember` toned background
- Text area: `--card-padding` (20px) all sides
- Product name: `--font-serif` italic, `--text-heading-sm`, `--color-bone`
- Description: `--font-sans`, `--text-body`, `--color-silver`, `--leading-relaxed`
- Price pill: see 5.5
- **Hover:** `transform: translateY(-3px)`, `box-shadow: --shadow-lift`; `transition: transform 240ms ease, box-shadow 240ms ease`

### 5.5 Price Pill
Inline chip anchored bottom of card text area.

- Background: `--color-linen`
- Text: `--font-sans`, `--text-body`, `--weight-medium`, `--color-obsidian`
- Radius: `--radius-full` (60px)
- Padding: `var(--space-1) var(--space-4)` (4px 16px)
- No border, no shadow

### 5.6 Editorial Tag Badge
Small category or status label.

- Radius: `--radius-sm` (4px)
- Padding: `var(--space-1) var(--space-2)` (4px 8px)
- Text: `--font-sans`, `--text-caption`, `--weight-medium`, uppercase, `letter-spacing: 0.08em`, `--color-obsidian`
- Fill variants:
  - New Release: `--color-citron` background
  - Category: `--color-lichen-green` background
  - Special/Limited: `--color-linen` background, `1px solid --color-antique-gold`

### 5.7 Nav Link
- Text: `--font-sans`, `--text-body`, `--weight-medium`, `--color-bone`
- No underline by default
- **Hover:** underline appears, color → `--color-silver`
- Transition: `color 180ms ease`
- **Focus-visible:** `outline: 2px solid --color-bone; outline-offset: 3px`

### 5.8 Testimonial Card
- Background: `--color-ash-charcoal`
- Border: `1px solid` `--color-graphite`
- Radius: `--radius-sm`
- Padding: `var(--space-8)` (32px)
- Quote text: `--font-serif` italic, `--text-heading-sm`, `--color-bone`, `--leading-normal`
- Attribution: `--font-sans`, `--text-small`, `--color-silver`, `--weight-medium`, uppercase

---

## 6. Motion Rules

CSS-only — no JavaScript, no scroll animation libraries.

| Element | Property | Duration | Easing |
|---|---|---|---|
| Nav links | `color` | 180ms | `ease` |
| Editorial links | `color`, `text-decoration` | 180ms | `ease` |
| Primary / ghost buttons | `background`, `border-color` | 220ms | `ease` |
| Product cards | `transform`, `box-shadow` | 240ms | `ease` |
| Badge on card hover (via card) | `opacity` | 200ms | `ease` |

**Rules:**
- Maximum transition duration: 300ms. Anything longer feels sluggish.
- Only `transform`, `opacity`, `color`, `background-color`, `border-color`, and `box-shadow` may be transitioned — never layout properties (`width`, `height`, `padding`).
- Use `prefers-reduced-motion` media query to disable all transforms and transitions for users who have requested it.
- No scroll-triggered animation (requires JS). Cards are always visible. Hover states are the only interactive motion.

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    transition-duration: 0.01ms !important;
    animation-duration: 0.01ms !important;
  }
}
```

---

## 7. Responsive Breakpoints

```css
:root {
  /* Breakpoints (used in media queries — not as variables directly, listed for reference) */
  /* sm:  480px  — small phones landscape, stack hero, single-column grid */
  /* md:  768px  — tablet, 2-column product grid, show nav */
  /* lg: 1024px  — desktop, 3-column product grid, full hero split */
  /* xl: 1320px  — max-width cap kicks in */
}
```

| Breakpoint | Key Changes |
|---|---|
| < 480px (base) | Single column everywhere. Nav collapses to logo + hamburger icon (CSS-only toggle via `:focus-within` or checkbox). Type scale reduces display to `--text-heading-lg`. |
| ≥ 480px (sm) | Hero stacks vertically. Product grid: 1 column. Story section stacks. |
| ≥ 768px (md) | Product grid: 2 columns. Story section side-by-side. Testimonials side-by-side. Nav links visible inline. |
| ≥ 1024px (lg) | Product grid: 4 columns. Hero splits into left index (35%) and right visual (65%). |
| ≥ 1320px (xl) | Max-width container engaged — gutters grow, content stops expanding. |

---

## 8. Non-Negotiables

1. **No external frameworks** — no Tailwind, Bootstrap, or any CSS utility library.
2. **No JavaScript** — zero `<script>` tags. All interactivity is pure CSS.
3. **All colors via variables** — every color in `index.html` must reference a `--color-*` custom property, never a raw hex value.
4. **All spacing via variables** — use `--space-*` tokens. No magic numbers.
5. **No external raster images** — all visuals are inline SVG or CSS gradients, annotated with an HTML comment explaining what they represent.
6. **No Lorem Ipsum** — all copy is real, persuasive, and on-brand for *Ember & Ground*.
7. **Serif is always italic** — never set a heading in the serif in roman (non-italic) style.
8. **No weight 600+** — serif stays 300–400; sans stays 400–500.
9. **Radius 60px exclusively for price pills** — no other element uses `--radius-full`.
10. **WCAG AA compliance** — all text/background combinations verified in the contrast table above.
11. **Single `<h1>`** — exactly one `<h1>` on the page (the hero headline). All other headings use `<h2>`–`<h4>`.
12. **Section order** — implement every section in the exact order defined in Section 4.

---

## CSS File Structure

Organize `style.css` (or `<style>` block) in this exact order:

```
1. @import (Google Fonts)
2. @layer reset     — box-sizing, margin/padding zero-out, img/svg max-width
3. @layer variables — :root with all custom properties
4. @layer base      — html, body, h1–h6, p, a, ul, button defaults
5. @layer layout    — .wrapper, .section, grid helpers
6. @layer components — .btn, .card, .badge, .price-pill, .nav-link, .testimonial
7. @layer sections  — .announcement, .nav, .hero, .manifesto, .menu, .story, .testimonials, .visit, .cta, .footer
8. @layer responsive — all @media queries, in ascending breakpoint order
9. @layer motion    — transitions, hover states, prefers-reduced-motion
```

---

## Quick Reference Card

```
Canvas:      #0e1311   Obsidian
Text:        #ffffff   Bone
Muted text:  #b3b3b3   Silver
Border:      #1a1a1a   Ash Charcoal
Light fill:  #f6f7f2   Linen
Accent:      #c0502a   Ember (gradient only)
Badge Y:     #faf080   Citron
Badge G:     #cadcac   Lichen Green

Serif:   Cormorant Garamond — italic only for headings
Sans:    Inter — 400/500 only

Base unit:   8px
Max width:  1320px
Section gap: 80px
Card radius:   4px
Pill radius:  60px
```
