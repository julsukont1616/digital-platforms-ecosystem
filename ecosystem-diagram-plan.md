# Thailand Digital Platform Ecosystem Diagram — v4

## Design philosophy

**Solve space statically, style dynamically.** Every node position and every connection waypoint is derivable from a simple grid formula — no DOM measurement, no layout algorithms, no force simulations. The LLM's job is to write a grid, draw polylines through pre-defined waypoints, then pour aesthetics on top via CSS and SVG filters.

The diagram should feel like a Figma-quality technical illustration: soft shadows, generous spacing, restrained color, subtle animation. Not a dev wireframe.

## Output

`D:/workspace/digital-platforms-ecosystem/ecosystem.html` — single self-contained HTML file.

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│ 1. DATA: grid constants + node/edge inventory       │  ← static JS object
│ 2. GRID: compute x,y from row/col formula           │  ← 20 lines of math
│ 3. ROUTE: orthogonal waypoints from anchors          │  ← 30 lines, 4 patterns
│ 4. RENDER: SVG rects + polylines at computed coords  │  ← declarative
│ 5. STYLE: CSS transitions, filters, dark mode        │  ← where LLM excels
│ 6. INTERACT: toggle flows, hover, tooltips           │  ← thin event handlers
└─────────────────────────────────────────────────────┘
```

---

## Layout: the grid

### Canvas

SVG `viewBox="0 0 980 780"`, scaled to fit viewport via `width: 100%; max-width: 980px`.

```
x=0        x=44       x=744      x=780    x=960
 │ gutter   │  main stack (700px)  │ gap │ side col │
 │  44px    │                      │20px │  160px   │
```

### Vertical rhythm

All Y positions computed from two constants:

```
NODE_H    = 56px     // node card height
GAP       = 44px     // inter-layer gap
Y_START   = 108px    // first layer top (below title + toggle bar)
```

Layer top Y = `Y_START + layerIndex × (NODE_H + GAP)`

| Layer | Index | Y_top | Y_center | Y_bottom |
|-------|-------|-------|----------|----------|
| Demand | 0 | 108 | 136 | 164 |
| Access | 1 | 208 | 236 | 264 |
| Discovery | 2 | 308 | 336 | 364 |
| Execution | 3 | 408 | 436 | 464 |
| Trust & Settlement | 4 | 508 | 536 | 564 |
| Fulfillment | 5 | 608 | 636 | 664 |

Total canvas height: 664 + 56 (bottom padding) + some legend space ≈ **780px**. Fits 1080p comfortably.

### Horizontal positioning

Nodes within a layer are evenly distributed across the 700px main stack (x=44 to x=744).

Formula for node `j` of `N` nodes in a layer, with node width `W`:

```
gap     = (700 - N × W) / (N + 1)
node_x  = 44 + gap + j × (W + gap)          // left edge
node_cx = node_x + W/2                       // center x
```

| Layer | N | W (px) | Gap (px) | Node left-edges |
|-------|---|--------|----------|-----------------|
| Demand | 4 | 148 | 22 | 66, 236, 406, 576 |
| Access | 3 | 155 | 56 | 100, 311, 522 |
| Discovery | 5 | 118 | 19 | 63, 200, 337, 474, 611 |
| Execution | 4 | 148 | 22 | 66, 236, 406, 576 |
| Trust & Settlement | 4 | 148 | 22 | 66, 236, 406, 576 |
| Fulfillment | 3 | 155 | 56 | 100, 311, 522 |

### Side column (Data & AI)

Three nodes stacked vertically at x=780, width=160:

| Node | Y_top | Y_center |
|------|-------|----------|
| Cloud Providers | 228 | 256 |
| AI/ML Platforms | 388 | 416 |
| CDN & Hosting | 548 | 576 |

Vertical positions chosen to align roughly with layers 1–2, 3, and 4–5 for clean horizontal taps.

Subtle background band: full-height rect from y=200 to y=600, x=770 to x=970, fill #185FA5 at 4% opacity, rounded corners 12px.

---

## Node inventory

Each node has: `id`, `name`, `examples` (2-3 Thai operators), optional `badge` (scale indicator).

### Layer 0 — Demand (#534AB7)
| id | name | examples |
|----|------|----------|
| consumers | Consumers & Citizens | 66M internet users |
| merchants | Merchants & SMEs | 3.4M LINE OA, 1M+ Shopee sellers |
| creators | Creators & Drivers | Grab drivers, LINE creators |
| enterprises | Enterprises & Agencies | Listed firms, govt agencies |

### Layer 1 — Access (#BA7517)
| id | name | examples |
|----|------|----------|
| telecom | Telecom / ISPs | AIS, TRUE, DTAC (now TRUE) |
| app_stores | OS & App Stores | Apple, Google Play |
| browsers | Browsers & Devices | Chrome, Samsung, OPPO |

### Layer 2 — Discovery (#4285F4)
| id | name | examples |
|----|------|----------|
| search | Search & Maps | Google, Apple Maps, Longdo |
| social | Social Media | Facebook, TikTok, X, Instagram |
| messaging | Messaging | LINE, WhatsApp, Telegram |
| advertising | Advertising | Google Ads, Meta Ads, TikTok Ads |
| news | News & Content | Thairath, Matichon, THE STANDARD |

### Layer 3 — Execution (#D85A30)
| id | name | examples |
|----|------|----------|
| marketplaces | Marketplaces | Shopee, Lazada, TikTok Shop |
| superapps | Super-apps | Grab, LINE MAN, Robinhood |
| social_commerce | Social Commerce | Facebook Shops, LINE Shopping, TikTok |
| streaming | Streaming & Content | YouTube, Netflix, MONOMAX, Viu |

### Layer 4 — Trust & Settlement (#0F6E56)
| id | name | examples | badge |
|----|------|----------|-------|
| promptpay | Public Rails | PromptPay, PromptBiz | 92.2M IDs · 79.9M txn/day |
| banks | Banks & Acquirers | SCB, KBANK, BBL, KTB; incl. NDID, KYC/KYB | 181.8M accounts |
| ewallets | E-Wallets | TrueMoney, Rabbit LINE Pay, ShopeePay | 112.3M accounts |
| cards | Card Networks | Visa, Mastercard, JCB, UnionPay | |

Identity infrastructure (NDID digital ID, bank KYC/KYB, platform moderation) is embedded within these Trust & Settlement nodes — surfaced in tooltips rather than as separate nodes.

### Layer 5 — Fulfillment (#BA7517)
| id | name | examples |
|----|------|----------|
| parcels | Parcel Networks | Kerry, Flash, J&T, Thailand Post |
| riders | Rider Fleets | Grab, LINE MAN, Lalamove |
| warehouses | Warehouses | Shopee Xpress hubs, Lazada sort centers |

### Side column — Data & AI (#185FA5)
| id | name | examples | badge |
|----|------|----------|-------|
| cloud | Cloud Providers | AWS, Google Cloud (BKK), Azure | GCP BKK region Jan 2026 |
| ai_ml | AI/ML Platforms | OpenAI, Anthropic, SCB 10X | |
| cdn | CDN & Hosting | Cloudflare, CAT CDN, local DCs | |

---

## Connection routing

### Orthogonal path with rounded corners

All connections are SVG `<path>` elements using only horizontal and vertical segments. At each 90° turn, a small arc (radius `R = 6px`) rounds the corner.

A path through waypoints `[(x0,y0), (x1,y1), (x2,y2), ...]` is rendered as:

```
M x0,y0
L (approaching x1,y1 minus R in the incoming direction)
Q x1,y1 (departing x1,y1 plus R in the outgoing direction)
L (approaching x2,y2 minus R)
Q x2,y2 (departing x2,y2 plus R)
... etc
L xN,yN
```

The Q (quadratic bezier) through the corner point creates a smooth 6px radius turn. This is the **only** curve in the entire system.

### 4 routing patterns

Every connection falls into exactly one of these patterns. Each produces an explicit waypoint array.

#### Pattern A: Adjacent layer (down, span=1)

Source exits bottom-center, target enters top-center. One horizontal jog through the inter-layer gap.

```
mid_y = source.y_bottom + GAP/2

waypoints = [
  (source.cx, source.y_bottom),     // exit bottom
  (source.cx, mid_y),               // down to gap midline
  (target.cx, mid_y),               // horizontal jog
  (target.cx, target.y_top)         // enter top
]
```

If source.cx == target.cx (vertically aligned), this collapses to a straight vertical line — just two points, no turns.

**Offset rule**: if multiple connections share the same gap, offset `mid_y` by ±6px per connection to prevent overlap. Connections are sorted by horizontal span (widest first gets the true midline).

#### Pattern B: Skip layer (span ≥ 2, through left gutter)

Source exits left edge, routes down through the gutter, enters target left edge. Gutter track X assigned per connection (track 0 = x:36, track 1 = x:24, track 2 = x:12).

```
gx = 36 - track × 12     // gutter track x

waypoints = [
  (source.x_left, source.cy),       // exit left
  (gx, source.cy),                  // horizontal to gutter
  (gx, target.cy),                  // vertical in gutter
  (target.x_left, target.cy)        // enter left
]
```

Track assignment: sort skip connections by vertical span (longest = outermost track).

#### Pattern C: Lateral (same layer, arc above)

Source and target are in the same row. Route up through the gap above.

```
arc_y = source.y_top - 16 - (nodes_between × 8)    // rise higher if nodes between

waypoints = [
  (source.cx, source.y_top),        // exit top
  (source.cx, arc_y),               // up into gap
  (target.cx, arc_y),               // horizontal
  (target.cx, target.y_top)         // enter top
]
```

#### Pattern D: Horizontal tap (main stack → side column)

Source exits right edge, target enters left edge. If Y differs, one vertical jog in the open space between stack and column.

**Same-Y case** (source.cy ≈ target.cy within 20px):
```
waypoints = [
  (source.x_right, source.cy),
  (target.x_left, target.cy)        // straight horizontal
]
```

**Different-Y case**:
```
jog_x = 762    // midpoint of the 20px gap between stack and column

waypoints = [
  (source.x_right, source.cy),
  (jog_x, source.cy),               // horizontal to gap
  (jog_x, target.cy),               // vertical jog
  (target.x_left, target.cy)        // enter target
]
```

**Y-stagger rule**: if multiple taps from the same layer target the same side-column node, offset each by ±6px on the target end to prevent overlap.

---

## Connection inventory

### Discovery flow (#4285F4)

| from | to | pattern | label |
|------|----|---------|-------|
| consumers | search | A | Search intent |
| consumers | social | A | Feed browsing |
| consumers | messaging | A | Direct messaging |
| merchants | advertising | A | Ad spend |
| search | marketplaces | A | Product search |
| social | superapps | A | Content → commerce |
| social | social_commerce | A | In-app shops |
| messaging | superapps | A | Chat commerce |
| advertising | marketplaces | A | Paid placement |
| advertising | social_commerce | A | Boosted listings |
| social | messaging | C | Cross-referral |

### Money flow (#0F6E56)

| from | to | pattern | label |
|------|----|---------|-------|
| consumers | ewallets | B (skip 0→4) | Top-up |
| consumers | banks | B (skip 0→4) | Bank transfer |
| marketplaces | promptpay | A | Checkout |
| superapps | ewallets | A | In-app pay |
| promptpay | banks | C | Settlement |
| banks | merchants | B (skip 4→0) | Payout |
| ewallets | banks | C | Withdrawal |

### Physical flow (#BA7517)

| from | to | pattern | label |
|------|----|---------|-------|
| marketplaces | parcels | A (skip 3→5) | Ship order |
| marketplaces | warehouses | A (skip 3→5) | Fulfillment |
| superapps | riders | A (skip 3→5) | Dispatch |
| parcels | consumers | B (skip 5→0) | Last mile |
| riders | consumers | B (skip 5→0) | Delivery |
| parcels | warehouses | C | Sort & stage |

### Data & AI flow (#185FA5)

| from | to | pattern | label |
|------|----|---------|-------|
| marketplaces | cloud | D | Transaction data |
| superapps | cloud | D | Behavioral data |
| social | cloud | D | Content signals |
| social_commerce | cloud | D | Commerce signals |
| promptpay | cloud | D | Payment analytics |
| ai_ml | marketplaces | D (return) | Recommendations |
| ai_ml | social | D (return) | Content ranking |
| ai_ml | search | D (return) | Search ranking |
| cloud | ai_ml | lateral in col | Data pipeline |
| ai_ml | cdn | lateral in col | Model serving |

Return arrows (AI → platforms): use **dashed stroke** + leftward arrowhead to distinguish from data-in arrows.

Side column internal connections (cloud → ai_ml → cdn): straight vertical lines within the column, rendered as simple downward paths.

---

## Visual design

### Color system

```css
:root {
  /* surface */
  --bg:            #F6F6F4;
  --bg-card:       #FFFFFF;
  --bg-side:       rgba(24, 95, 165, 0.04);

  /* text */
  --text-primary:  #1A1A1A;
  --text-secondary:#6B6B6B;
  --text-muted:    #9B9B9B;

  /* layer colors */
  --c-demand:      #534AB7;
  --c-access:      #BA7517;
  --c-discovery:   #4285F4;
  --c-execution:   #D85A30;
  --c-trust:       #0F6E56;
  --c-fulfillment: #BA7517;
  --c-data:        #185FA5;

  /* flow colors (match layer of primary activity) */
  --f-discovery:   #4285F4;
  --f-money:       #0F6E56;
  --f-physical:    #BA7517;
  --f-data:        #185FA5;

  /* depth */
  --shadow-card:   0 1px 3px rgba(0,0,0,0.06), 0 1px 2px rgba(0,0,0,0.04);
  --shadow-hover:  0 4px 12px rgba(0,0,0,0.10), 0 2px 4px rgba(0,0,0,0.06);
  --radius:        8px;
  --radius-sm:     5px;
}
```

Dark mode overrides via `@media (prefers-color-scheme: dark)`:
```css
  --bg:            #141416;
  --bg-card:       #1E1E22;
  --bg-side:       rgba(24, 95, 165, 0.08);
  --text-primary:  #E8E8E8;
  --text-secondary:#8B8B8B;
  --shadow-card:   0 1px 3px rgba(0,0,0,0.30);
  --shadow-hover:  0 4px 16px rgba(0,0,0,0.40);
```

### Typography

DM Sans via Google Fonts CDN.

| Element | Size | Weight | Color |
|---------|------|--------|-------|
| Diagram title | 22px | 600 | --text-primary |
| Flow toggle pill (active) | 13px | 600 | white on flow color |
| Flow toggle pill (inactive) | 13px | 500 | --text-secondary on transparent |
| Layer label | 11px | 600 | layer color, uppercase, letter-spacing 0.05em |
| Node name | 12px | 600 | --text-primary |
| Node examples | 10.5px | 400 | --text-secondary |
| Scale badge | 10px | 500 | layer color on layer color at 10% opacity |
| Connection label | 10px | 500 | flow color |
| Tooltip title | 13px | 600 | --text-primary |
| Tooltip body | 11.5px | 400 | --text-secondary |

### Node cards

- White (`--bg-card`) rounded rect, `--radius`, `--shadow-card`
- 2px left border in layer color (subtle categorical cue)
- Padding: 10px 12px
- On hover: `--shadow-hover`, translate Y -1px
- When active in a flow: full opacity
- When inactive: opacity 0.35, shadow removed
- Transition: all 200ms ease

### Layer labels

Small uppercase text, positioned 6px above the first node in each layer, left-aligned at x=48. Layer color. No background, no box — just floating type.

### Side column

Subtle background band (--bg-side), rounded 12px. "Data & AI" label at top in #185FA5. Nodes styled identically to main stack nodes but with left border in #185FA5.

### Connection lines

- Stroke width: 1.5px default, 2.5px on hover
- Stroke color: flow color at 50% opacity default, 90% on hover
- Rounded corners: 6px radius at every turn
- Arrowhead: small triangle marker (6×4px), same color as line
- Return arrows (AI → platforms): `stroke-dasharray: 6 4`, arrowhead points left
- Transition: opacity 200ms, stroke-width 150ms

### Connection labels

- Flow-colored text on a `--bg-card` background pill (padding 2px 6px, border-radius 3px)
- Positioned at the midpoint of the longest segment in the path
- `pointer-events: none`
- Fade in with connections (200ms)
- Only shown on hover (to keep default view clean) OR always shown for connections with ≤3 connections in the active flow

### Scale badges

Small pills below their parent node, in the inter-layer gap:
- Background: layer color at 8% opacity
- Text: layer color, 10px, font-weight 500
- Border-radius: 10px
- Padding: 2px 8px
- Positioned: centered below node, offset 6px down
- Always visible (not affected by flow toggle)

### Hover tooltip

Appears on node click or long-hover (300ms):
- Floating card: `--bg-card`, `--shadow-hover`, border-radius 10px
- Max-width: 220px
- Content: node name (bold), operator list, scale data, contextual note
- Positioned in nearest inter-layer gap or beside the node
- Subtle fade-in (150ms)
- Arrow/caret pointing to source node

### SVG glow filter (for active nodes)

```svg
<filter id="glow">
  <feGaussianBlur stdDeviation="2" result="blur"/>
  <feComposite in="SourceGraphic" in2="blur" operator="over"/>
</filter>
```

Applied subtly to active-flow nodes via CSS class toggle.

### Connection draw-in animation

When a flow is activated, connections animate in using `stroke-dasharray` + `stroke-dashoffset`:

```css
.conn path {
  stroke-dasharray: var(--path-length);
  stroke-dashoffset: var(--path-length);
  transition: stroke-dashoffset 400ms ease-out, opacity 200ms;
}
.conn.active path {
  stroke-dashoffset: 0;
}
```

Each connection's `--path-length` is computed once at init via `path.getTotalLength()`.

---

## Interactions

### Flow toggle

- 4 pill buttons in a horizontal bar below the title
- Active pill: filled with flow color, white text
- Inactive pills: transparent background, muted text
- On click: swap active class, transition connections (draw-in animation), transition node opacity
- On page load: Discovery flow active by default

### Hover connection

- Hovered path: stroke-width 2.5, opacity 0.9, label appears
- All other paths in flow: opacity 0.1
- Source and target nodes: elevated shadow
- Hit area: invisible wider stroke (12px) for easy targeting

### Hover node

- All connections touching that node: highlight (stroke-width 2.2, opacity 0.9)
- All other connections: opacity 0.1
- Connected nodes: elevated shadow
- Hovered node: `--shadow-hover`, slight scale(1.02)

### Click node → tooltip

- Shows floating tooltip with full operator list and scale data
- Click outside or click again to dismiss
- No layout shift, no SVG redraw

---

## Responsive behavior

- **≥980px**: full layout (main stack + side column)
- **768–979px**: side column moves below main stack as a horizontal row; Data & AI taps become short downward connections. Main stack stretches to full width.
- **<768px**: single column, 2 nodes per row, connections hidden except for a simplified "flow summary" text below each layer. Essentially a styled list with layer groupings. No SVG routing attempted.

---

## Implementation notes for LLM

1. **Start with the grid.** Write the LAYERS and SIDE_COLUMN data objects with all node IDs and metadata. Write the grid math (6 lines) that produces `{x, y, w, h, cx, cy}` for every node. Console.log positions and verify before rendering anything.

2. **Render nodes.** SVG `foreignObject` wrapping HTML divs for each node (easier text styling than pure SVG text). Position using the computed grid. Verify visually: all cards in clean rows, correct spacing.

3. **Render one connection type at a time.** Start with Pattern A (adjacent). Get the waypoint formula right. Render as `<path>`. Verify: no overlaps, clean corners. Then add Pattern B, C, D one at a time.

4. **Add flow toggle.** Group connections by flow. Toggle visibility. Verify: correct connections per flow, fade transitions work.

5. **Add interactions.** Hover highlight, tooltip, draw-in animation. These are pure CSS class toggles + thin JS event handlers.

6. **Polish.** Dark mode, scale badges, glow filters, responsive breakpoints. This is where time should be spent — the spatial layout is already solved.

---

## Verification checklist

1. 6 layers render with correct node count and positions
2. Side column renders with 3 Data & AI nodes, background band visible
3. Grid positions: no node overlaps another, even spacing within each row
4. Each flow toggle shows correct connections, hides others
5. Pattern A connections: clean orthogonal paths through inter-layer gaps
6. Pattern B connections: routed through left gutter, no box crossing
7. Pattern C connections: arcs above nodes in gap, clear of adjacent nodes
8. Pattern D connections: horizontal from main stack to side column
9. Return arrows (dashed) distinguishable from forward arrows
10. All corners are 90° with 6px radius, no bezier bulges or bow-ties
11. Hover connection: highlight + dim others + label appears
12. Hover node: connected paths highlight
13. Click node: tooltip with operator list (including identity infra for Trust & Settlement nodes), no layout shift
14. Scale badges visible below nodes, not overlapping connections
15. Dark mode: all colors adapt correctly
16. Draw-in animation plays on flow switch
17. No line crosses through any node box (visual inspection per flow)
18. No label overlaps another label or node
19. Fits 1080p viewport without scroll
