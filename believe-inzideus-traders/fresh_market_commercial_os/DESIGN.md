---
name: Fresh Market Commercial OS
colors:
  surface: '#faf8ff'
  surface-dim: '#d2d9f4'
  surface-bright: '#faf8ff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f2f3ff'
  surface-container: '#eaedff'
  surface-container-high: '#e2e7ff'
  surface-container-highest: '#dae2fd'
  on-surface: '#131b2e'
  on-surface-variant: '#3e4a3d'
  inverse-surface: '#283044'
  inverse-on-surface: '#eef0ff'
  outline: '#6e7b6c'
  outline-variant: '#bdcaba'
  surface-tint: '#006e2d'
  primary: '#006b2c'
  on-primary: '#ffffff'
  primary-container: '#00873a'
  on-primary-container: '#f7fff2'
  inverse-primary: '#62df7d'
  secondary: '#006d30'
  on-secondary: '#ffffff'
  secondary-container: '#92f5a4'
  on-secondary-container: '#007233'
  tertiary: '#8d4b00'
  on-tertiary: '#ffffff'
  tertiary-container: '#b15f00'
  on-tertiary-container: '#fffbff'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#7ffc97'
  primary-fixed-dim: '#62df7d'
  on-primary-fixed: '#002109'
  on-primary-fixed-variant: '#005320'
  secondary-fixed: '#95f8a7'
  secondary-fixed-dim: '#79db8d'
  on-secondary-fixed: '#00210a'
  on-secondary-fixed-variant: '#005323'
  tertiary-fixed: '#ffdcc3'
  tertiary-fixed-dim: '#ffb77d'
  on-tertiary-fixed: '#2f1500'
  on-tertiary-fixed-variant: '#6e3900'
  background: '#faf8ff'
  on-background: '#131b2e'
  surface-variant: '#dae2fd'
typography:
  display-lg:
    fontFamily: Space Grotesk
    fontSize: 40px
    fontWeight: '700'
    lineHeight: 48px
    letterSpacing: -0.02em
  display-lg-mobile:
    fontFamily: Space Grotesk
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
    letterSpacing: -0.02em
  headline-lg:
    fontFamily: Space Grotesk
    fontSize: 28px
    fontWeight: '600'
    lineHeight: 36px
    letterSpacing: -0.01em
  headline-lg-mobile:
    fontFamily: Space Grotesk
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
    letterSpacing: -0.01em
  headline-md:
    fontFamily: Space Grotesk
    fontSize: 22px
    fontWeight: '600'
    lineHeight: 28px
  headline-sm:
    fontFamily: Space Grotesk
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 24px
  body-lg:
    fontFamily: Hanken Grotesk
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-md:
    fontFamily: Hanken Grotesk
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  body-sm:
    fontFamily: Hanken Grotesk
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
  label-lg:
    fontFamily: Hanken Grotesk
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 20px
    letterSpacing: 0.01em
  label-md:
    fontFamily: Hanken Grotesk
    fontSize: 12px
    fontWeight: '600'
    lineHeight: 16px
    letterSpacing: 0.02em
  label-sm:
    fontFamily: Hanken Grotesk
    fontSize: 11px
    fontWeight: '700'
    lineHeight: 14px
    letterSpacing: 0.04em
  currency-display:
    fontFamily: Space Grotesk
    fontSize: 24px
    fontWeight: '700'
    lineHeight: 28px
    letterSpacing: -0.01em
  currency-table:
    fontFamily: Hanken Grotesk
    fontSize: 15px
    fontWeight: '600'
    lineHeight: 20px
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 1rem
  gutter-tablet: 1.25rem
  gutter-desktop: 1.5rem
  margin: 1rem
  margin-tablet: 1.5rem
  margin-desktop: 2rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 1rem
  space-lg: 1.5rem
  space-xl: 2rem
---

## Brand & Style

This design system serves high-velocity grocery retail, wholesale operations, and point-of-sale inventory management. The aesthetic balances agricultural freshness with the structured rigor of commercial enterprise software.

### Tone & Character
- **Vital & Fresh:** Vibrant emerald greens signal fresh inventory, thriving trade, and system health.
- **Pragmatic & Operable:** High contrast, large tactile hit areas, and zero ornamental clutter ensure fast operator adoption in busy store aisles or checkout counters.
- **Trustworthy & Crisp:** Stark white backdrops paired with charcoal typography guarantee immediate readability under uneven fluorescent store lighting or outdoor sunlight.

### Design Paradigm
The interface employs a **Tactile Modernist** approach:
- Flat color fields layered over subtle tinted surfaces (`#f0fdf4`).
- Utilitarian line-drawn structural boundaries with soft corner articulation to balance speed and warmth.
- Dense data displays paired with generous touch surfaces (minimum 48px hit areas for primary mobile and POS actions).

## Colors

The palette is tuned specifically for fast visual parsing of fresh grocery inventory status, cash flows, and alert conditions.

### Primary & Action Scale
- **Primary Emerald (`#16a34a`):** Interactive actions, primary action buttons, active tabs, confirmed transactions, and high stock states.
- **Deep Emerald (`#15803d`):** Hover and pressed states, table header accents, and high-emphasis focal items.
- **Surface Green Tint (`#f0fdf4`):** Background fill for metric cards, highlighted order lines, inventory summaries, and active selection tiles.

### Semantic & Warning Palette
- **Amber / Gold (`#d97706`):** Low-stock warnings, pending payments, partial fulfillment states, and batch expiration alerts within 3 days.
- **Error / Critical (`#dc2626`):** Out-of-stock indicators, cancelled orders, voided receipts, and sync failures.
- **Success Tone (`#16a34a`):** In-stock confirmation, paid invoices, reconciled registers.

### Neutrals & Surfaces
- **Canvas (`#ffffff`):** Base canvas for extreme optical clarity.
- **Subtle Surface (`#f8fafc`):** Table rows alternating fill and secondary panels.
- **Border / Divider (`#e2e8f0`):** Hairline structure definitions.
- **Charcoal Text Primary (`#0f172a`):** Highest visual priority: product titles, rupee currency figures, and SKU IDs.
- **Slate Text Muted (`#64748b`):** Secondary metadata: batch codes, weight units (kg, g, pcs), timestamps.

## Typography

The pairing of **Space Grotesk** and **Hanken Grotesk** establishes a blend of technical ledger utility and modern clarity.

### Display & Headlines (Space Grotesk)
Space Grotesk provides a semi-industrial, structured personality. Its geometric proportions make numbers, billing IDs, metric figures, and category banners prominent and unambiguous across scanning angles.

### Body, Labels & Ledger (Hanken Grotesk)
Hanken Grotesk delivers neutral, high x-height clarity. It excels in compact item descriptions, stock level tallies, and modal receipts.

### Currency Formatting Rules
- All currency values must use the Indian Rupee symbol (`₹`) with a non-breaking space before the integer value (e.g., `₹ 1,450.00`).
- When presented in dense tables, use tabular figures (`font-variant-numeric: tabular-nums`) so decimal columns align vertically for error-free scanning during register balancing.

## Layout & Spacing

The layout is built around a mobile-first, high-density fluid grid adaptable to handheld barcode devices, counter tablets, and wide POS terminals.

### Screen Adaptations
- **Mobile (< 640px):** Single-column stack with persistent bottom action bars. Standard margin is `1rem`, grid uses 4 columns. List items expand horizontally with swipe actions for quick stock adjustments.
- **Tablet / POS (640px – 1024px):** Split layout with 8 columns. Dual-pane mode displays the active basket on the right (40% width) and searchable product catalog/categories on the left (60% width).
- **Desktop / Back Office (> 1024px):** 12-column layout with pinned vertical navigation, expansive inventory data tables, and batch analytics cards.

### Touch Targets
All clickable nodes on mobile and POS views require a minimum dimension of `48px` by `48px`. Secondary icons and quick increment steppers (`+` / `-`) must use minimum `40px` tap targets with `space-xs` padding buffers.

## Elevation & Depth

This design system avoids heavy shadows, using **tonal layering with structural borders** to keep interface response quick on low-powered POS hardware and tablet displays.

### Layer Hierarchy
1. **Level 0 (Canvas):** Pure `#ffffff` for page backgrounds, receipts, and order slips.
2. **Level 1 (Soft Containers):** `#f0fdf4` tint for highlighted inventory cards, totals summaries, and selected items. Bordered with a 1px stroke of `rgba(22, 163, 74, 0.15)`.
3. **Level 2 (Interactive Floating Surfaces):** Dropdowns, quick lookup popovers, and sticky sub-headers use an ultra-light ambient shadow: `0px 4px 12px rgba(15, 23, 42, 0.06)`, framed with a crisp `#e2e8f0` border.
4. **Level 3 (Modal / Checkout Drawers):** Backdrop dimming at `rgba(15, 23, 42, 0.45)` with canvas sheet elevated by `0px 10px 25px -5px rgba(15, 23, 42, 0.12)`.

## Shapes

The system implements **Roundedness Level 2** (`0.5rem` / `8px` base border radius).

### Shape Application Guidelines
- **Base Components (`rounded` / `8px`):** Standard input fields, quantity selector buttons, table cards, alert banners, and product thumbnail frames.
- **Large Panels (`rounded-lg` / `16px`):** Summary containers, POS checkout summary pads, modal windows, and category filter cards.
- **Badges & Quick Action Tags:** Compact badges use `rounded-full` (`9999px`) to create an immediate pill profile distinct from square inventory cards.

## Components

### Buttons
- **Primary:** Background `#16a34a`, label `#ffffff` in `label-lg`, height `48px` on mobile/POS, `8px` border radius. Hover state transitions to `#15803d`. Active/pressed scales down slightly (`scale(0.98)`).
- **Secondary:** Background `#f0fdf4`, border `1px solid rgba(22, 163, 74, 0.3)`, text `#15803d`.
- **Tertiary / Utility:** Transparent background, text `#0f172a`, hover background `#f8fafc`.
- **Destructive:** Background `#dc2626`, label `#ffffff`, used exclusively for voiding items or stock write-offs.

### Cards & Tiles
- **Product POS Tile:** Crisp `#ffffff` container with `1px solid #e2e8f0`, `8px` radius. Features high-contrast price tag in `currency-display` (`#0f172a`), item title in `headline-sm`, and an immediate stock status badge in the top right corner.
- **Summary Metric Card:** Background `#f0fdf4` with subtle border `1px solid rgba(22, 163, 74, 0.2)`. Large numerical readout in `display-lg` (`#15803d`).

### Status Badges & Chips
- **In Stock:** `#dcfce7` background, `#15803d` text, `label-sm`, pill shape.
- **Low Stock:** `#fef3c7` background, `#d97706` text, `label-sm`, pill shape. Always displays exact units remaining (e.g., `Only 4 kg left`).
- **Out of Stock:** `#fee2e2` background, `#dc2626` text, `label-sm`, pill shape.

### Form Inputs & Fast Barcode Entry
- **Input Fields:** Minimum height `48px`, background `#ffffff`, border `1px solid #cbd5e1`, `8px` border radius. Focus ring creates a crisp `2px solid #16a34a` outline without blur.
- **Barcode / SKU Input:** Dedicated field with visual scanner icon prefix, monospaced numeric styling, and immediate auto-select on focus for rapid barcode gun scanning.

### Checkboxes, Steppers & Radios
- **Quantity Steppers:** Three-element joined block (`-` button, numerical input, `+` button), total height `44px`. Stepper buttons `#f8fafc` with `#0f172a` icons.
- **Selection Controls:** Checkbox and radio elements use `#16a34a` active fills with high-contrast white ticks.

### POS Sticky Bar (Mobile / Tablet)
A fixed bottom panel elevated above the navigation with `#ffffff` background, `1px solid #e2e8f0` top border, showing: Total Items, Grand Total in `currency-display`, and a prominent full-height "Charge / Bill" button in `#16a34a`.