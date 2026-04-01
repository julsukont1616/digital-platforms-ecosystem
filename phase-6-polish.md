# Phase 6: Dark Mode, Responsive & Final Polish

## Task

Final pass: add dark mode support, responsive behavior, and visual refinements.

## 1. Dark mode

Add CSS that responds to `@media (prefers-color-scheme: dark)`. Also add a small toggle button (sun/moon icon) in the top-right corner that manually overrides the system preference using a `data-theme` attribute on the root element.

### Color overrides in dark mode

| Token | Light | Dark |
|-------|-------|------|
| Page background | #F6F6F4 | #141416 |
| Card fill | #FFFFFF | #1E1E22 |
| Card shadow | rgba(0,0,0,0.06) | rgba(0,0,0,0.30) |
| Card shadow hover | rgba(0,0,0,0.10) | rgba(0,0,0,0.40) |
| Text primary | #1A1A1A | #E8E8E8 |
| Text secondary | #6B6B6B | #8B8B8B |
| Text muted | #9B9B9B | #666666 |
| Side column band | rgba(24,95,165,0.04) | rgba(24,95,165,0.08) |
| Tooltip background | #FFFFFF | #1E1E22 |
| Tooltip shadow | rgba(0,0,0,0.12) | rgba(0,0,0,0.50) |
| Connection label bg | #FFFFFF | #1E1E22 |
| Inactive pill bg | transparent | transparent |
| Inactive pill border | #E0E0E0 | #333333 |
| Inactive pill text | #6B6B6B | #888888 |
| Badge fill bg | {color}10 (6% opacity) | {color}20 (12% opacity) |

Layer colors and flow colors stay the same in dark mode — they're already designed to work on dark backgrounds.

### Implementation

Use CSS custom properties for all colors. Define defaults in `:root`, overrides in `[data-theme="dark"]` and `@media (prefers-color-scheme: dark)`:

```css
:root {
  --bg: #F6F6F4;
  --bg-card: #FFFFFF;
  --text-primary: #1A1A1A;
  --text-secondary: #6B6B6B;
  --shadow-card: 0 1px 3px rgba(0,0,0,0.06), 0 1px 2px rgba(0,0,0,0.04);
  --shadow-hover: 0 4px 12px rgba(0,0,0,0.10);
  /* ... etc */
}

@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) {
    --bg: #141416;
    --bg-card: #1E1E22;
    --text-primary: #E8E8E8;
    --text-secondary: #8B8B8B;
    --shadow-card: 0 1px 3px rgba(0,0,0,0.30);
    --shadow-hover: 0 4px 16px rgba(0,0,0,0.40);
  }
}

[data-theme="dark"] {
  --bg: #141416;
  --bg-card: #1E1E22;
  /* ... same overrides */
}
```

Update all SVG elements to use these variables. For SVG fills and strokes that currently use hardcoded hex values, switch to `var(--bg-card)` etc. where applicable.

### Dark mode toggle button

Small circular button (32×32px), position: fixed, top-right corner (top: 16px, right: 16px). Contains a sun icon (light mode) or moon icon (dark mode). Use simple SVG icons, not an icon library.

```javascript
function toggleTheme() {
  const root = document.documentElement;
  const current = root.getAttribute('data-theme');
  const next = current === 'dark' ? 'light' : 'dark';
  root.setAttribute('data-theme', next);
}
```

## 2. Responsive behavior

### Medium screens (768px – 979px)

```css
@media (max-width: 979px) {
  /* Side column moves below main stack */
  /* SVG viewBox stays the same, but the container scales down */
  /* The SVG's width: 100% handles this naturally */
}
```

Since the diagram is an SVG with a fixed viewBox, it scales proportionally. At 768px viewport, the 980px viewBox renders at ~78% size. Cards are still readable at this scale. No layout changes needed — SVG scaling handles it.

### Small screens (< 768px)

At this width, the scaled SVG becomes too small to read. Switch to a simplified view:

```css
@media (max-width: 767px) {
  .diagram-svg { display: none; }
  .mobile-view { display: block; }
}
```

Create a `.mobile-view` div (hidden by default on desktop) that shows the ecosystem as a **styled vertical list**:

```html
<div class="mobile-view">
  <div class="mobile-layer" style="--layer-color: #534AB7">
    <div class="mobile-layer-label">DEMAND</div>
    <div class="mobile-node">Consumers & Citizens — 66M internet users</div>
    <div class="mobile-node">Merchants & SMEs — 3.4M LINE OA</div>
    <!-- ... -->
  </div>
  <!-- repeat for each layer -->
</div>
```

Style:
- Each layer: left border 3px solid layer color, padding-left 12px, margin-bottom 16px
- Layer label: uppercase, 11px, weight 600, layer color
- Node: 13px, weight 400, color --text-primary, padding 6px 0
- No connections, no flow toggle on mobile

The flow toggle pills should still appear on mobile but display a short text summary instead of activating SVG connections:

```
[Discovery] → "Consumers find products via search, social, and messaging, which drive traffic to marketplaces and super-apps."
```

## 3. Visual refinements

### Subtle grid lines

Add faint horizontal lines at each inter-layer gap midpoint to create visual rhythm:

```xml
<line x1="44" y1="{gapMidY}" x2="744" y2="{gapMidY}"
      stroke="var(--text-muted)" stroke-opacity="0.08" stroke-width="0.5"/>
```

Gap midpoints: 186, 286, 386, 486, 586.

### Connection glow on hover

When a connection is highlighted (hover), add a subtle glow effect via SVG filter:

```xml
<filter id="conn-glow">
  <feGaussianBlur in="SourceGraphic" stdDeviation="3" result="blur"/>
  <feMerge>
    <feMergeNode in="blur"/>
    <feMergeNode in="SourceGraphic"/>
  </feMerge>
</filter>
```

Apply via style on hover: `filter: url(#conn-glow)`.

### Active flow pill indicator

Add a small animated dot or underline below the active pill to make the selection more visible:

```css
.flow-pill.active::after {
  content: '';
  display: block;
  width: 16px;
  height: 2px;
  background: white;
  border-radius: 1px;
  margin: 4px auto 0;
  animation: fadeIn 200ms ease;
}
```

### Footer

Add a small footer line below the diagram (font-size 10px, color --text-muted):

"Sources: BOT Payment Report Jan 2026, ETDA Platform Registry, DataReportal Digital 2025. Diagram shows ecosystem structure, not all possible connections."

## Do NOT change

- Node positions, connection waypoints, flow data
- Core interaction logic (hover, tooltip, flow toggle)
- The NODES object or orthoPath function

## Checkpoint

Open the file. Verify:
1. Light mode: looks correct (should be unchanged from Phase 5)
2. Click the theme toggle — entire diagram switches to dark mode smoothly
3. Dark mode: cards are dark, text is light, shadows are deeper, layer colors pop
4. Toggle back to light — correct
5. Resize browser to 800px — diagram scales proportionally, still readable
6. Resize to 600px — mobile view appears: vertical list, no SVG
7. Flow pills on mobile show text summaries
8. Subtle grid lines visible between layers (very faint)
9. Connection hover glow works in both light and dark mode
10. Footer text visible below the diagram
