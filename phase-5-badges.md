# Phase 5: Scale Badges

## Task

Add scale indicator badges below key nodes, and refine layer labels. Small phase — mostly positioning and styling.

## Scale badges

Badges are small pills positioned **below** their parent node card, centered horizontally, in the inter-layer gap. They are always visible regardless of active flow.

Render as SVG groups:

```xml
<g class="badge" transform="translate({cx}, {node.y + node.h + 8})">
  <rect rx="10" fill="{layerColor}10" width="{textWidth + 16}" height="18"
        x="{-(textWidth+16)/2}" y="-9"/>
  <text text-anchor="middle" font-size="10" font-weight="500"
        fill="{layerColor}" dy="3.5">{badge text}</text>
</g>
```

`{layerColor}10` means the layer color at ~6% opacity. In practice, use a hex color with low alpha or an rgba equivalent.

### Badge data

| Node ID | Badge text | Node cx | Node y+h |
|---------|-----------|---------|----------|
| promptpay | 92.2M IDs · 79.9M txn/day | 140 | 564 |
| banks | 181.8M accounts | 310 | 564 |
| ewallets | 112.3M accounts | 480 | 564 |
| messaging | 56M users (LINE) | 396 | 364 |
| social | 50M MAU (TikTok) | 259 | 364 |
| cloud | GCP BKK region Jan 2026 | 860 | 284 |
| marketplaces | #1 e-commerce market | 140 | 464 |

### Positioning constraints

- Badge center-x = parent node center-x
- Badge top = parent node bottom + 8px
- Badge must fit within the inter-layer gap (44px). Badge height is 18px, positioned 8px below the node, so it occupies y+8 to y+26 within the 44px gap. ✓
- If two badges in the same gap would overlap horizontally (their rects intersect), shift one 2px down.

## Layer label refinement

The layer labels from Phase 1 (small uppercase text above each row) should be refined:

- Position: x=48, y = layer.y_top - 10
- Font: DM Sans, 11px, weight 600, uppercase, letter-spacing 0.08em
- Fill: layer color at 70% opacity
- Add a small dot (circle r=3, same color) at x=44, y = label baseline, as a bullet indicator

If a layer label overlaps with a badge from the row above, shift the label 2px down.

## Do NOT change

- Node positions, connections, flow toggle, interactions
- Tooltip content or behavior
- Any connection waypoints

## Checkpoint

Open the file. Verify:
1. Badges appear below key nodes as colored pills
2. Badges sit cleanly in the inter-layer gap, not overlapping any node cards
3. Badges don't overlap each other
4. Badges remain visible when switching flows (they're not affected by flow toggle)
5. Layer labels are refined with dots and proper spacing
6. Toggle flows, hover nodes — badges stay in place, don't interfere
