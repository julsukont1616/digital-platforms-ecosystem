# Phase 3: Flow Data & Toggle

## Task

Add 4 flow datasets and toggle buttons to the existing `ecosystem.html`. Remove the 3 test connections from Phase 2.

## Toggle bar

Add a row of 4 pill-shaped buttons centered below the title (y ≈ 56–80 area of the SVG, or as HTML elements above the SVG). Use HTML buttons above the SVG for easier styling.

```
[  Discovery  ] [  Money  ] [  Physical  ] [  Data & AI  ]
```

Style:
- Active pill: background = flow color, text = white, font-weight 600, border-radius 20px, padding 6px 16px
- Inactive pill: background = transparent, text = #6B6B6B, border 1px solid #E0E0E0
- Font: DM Sans, 13px
- Gap between pills: 8px
- Transition: background 200ms, color 200ms

Only one pill active at a time. Discovery is active on page load.

## Node ID reference

Use the `NODES` object and `nodeAnchors(id)` from Phases 1–2. Here are the anchor shortcuts:

- `top(id)` = `[NODES[id].x + NODES[id].w/2, NODES[id].y]`
- `bot(id)` = `[NODES[id].x + NODES[id].w/2, NODES[id].y + NODES[id].h]`
- `left(id)` = `[NODES[id].x, NODES[id].y + NODES[id].h/2]`
- `right(id)` = `[NODES[id].x + NODES[id].w, NODES[id].y + NODES[id].h/2]`

## Waypoint patterns

Use these patterns to compute waypoints for each connection. `orthoPath()` from Phase 2 renders the waypoints.

### Pattern A: Adjacent layer (span = 1)

Source exits bottom-center, target enters top-center. Horizontal jog at the gap midline.

```
midY = bot(from)[1] + (top(to)[1] - bot(from)[1]) / 2

waypoints = [ bot(from), [bot(from)[0], midY], [top(to)[0], midY], top(to) ]
```

If source and target have the same center-x, skip the jog — just 2 points: `[ bot(from), top(to) ]`.

**Offset rule:** when multiple Pattern A connections share the same inter-layer gap, offset midY by increments of 5px to prevent overlap. The connection with the widest horizontal span gets the true midline; narrower ones offset ±5, ±10, etc.

### Pattern B: Skip layer (span ≥ 2, through left gutter)

Source exits left edge, drops to a gutter track, runs vertically, enters target left edge.

```
gx = 36 - track × 14     // track 0 = x:36, track 1 = x:22, track 2 = x:8

waypoints = [ left(from), [gx, left(from)[1]], [gx, left(to)[1]], left(to) ]
```

**Downward vs upward:** pattern is the same regardless of direction. The gutter just connects the two Y positions.

### Pattern C: Lateral (same layer)

Source and target in the same row. Arc above through the inter-layer gap.

```
arcY = NODES[from].y - 18 - (nodesBetween × 8)

waypoints = [ top(from), [top(from)[0], arcY], [top(to)[0], arcY], top(to) ]
```

`nodesBetween` = number of nodes between source and target in the row (0 if adjacent).

### Pattern D: Horizontal tap (main stack → side column)

Source exits right edge, target enters left edge. Vertical jog at x=762 if Y differs.

**Same Y (within 20px):**
```
waypoints = [ right(from), left(to) ]
```

**Different Y:**
```
waypoints = [ right(from), [762, right(from)[1]], [762, left(to)[1]], left(to) ]
```

**Y-stagger rule:** if multiple taps from nearby source Y positions target the same side-column node, offset the target Y by ±5px per connection to prevent overlap at the entry point.

### Pattern D-return: Side column → main stack (dashed)

Same as Pattern D but reversed direction. Source exits left edge of side column node, target enters right edge of main stack node.

```
waypoints = [ left(from), [762, left(from)[1]], [762, right(to)[1]], right(to) ]
```

Rendered with `stroke-dasharray="6 4"` and a reverse arrowhead marker.

## Flow definitions

### Discovery (#4285F4)

| # | From → To | Pattern | Label | Notes |
|---|-----------|---------|-------|-------|
| 1 | consumers → search | B (skip 0→2, track 0) | Search intent | Span=2, use gutter |
| 2 | consumers → social | B (skip 0→2, track 1) | Feed browsing | Span=2, use gutter |
| 3 | consumers → messaging | B (skip 0→2, track 2) | Direct messaging | Span=2, use gutter |
| 4 | merchants → advertising | B (skip 0→2, track 0) | Ad spend | Span=2, right-side gutter? No — use left gutter but from merchants which is at x=236. Route: left(merchants) → gutter → left(advertising). Track shared with #1 is fine because they're in different Y ranges. Actually merchants left is far from gutter — let's route out the bottom instead. Use a modified pattern: bot(merchants) → down to layer 2 gap midY → horizontal to top(advertising). This is effectively Pattern A with span=2. Simpler: treat as Pattern A with midY in the gap between layer 1 and 2 (y = 264 + (308-264)/2 = 286). waypoints: [bot(merchants), [bot(merchants)[0], 286], [top(advertising)[0], 286], top(advertising)] |
| 5 | search → marketplaces | A | Product search | Adjacent 2→3 |
| 6 | social → superapps | A | Content → commerce | Adjacent 2→3 |
| 7 | social → social_commerce | A | In-app shops | Adjacent 2→3 |
| 8 | messaging → superapps | A | Chat commerce | Adjacent 2→3 |
| 9 | advertising → marketplaces | A | Paid placement | Adjacent 2→3 |
| 10 | advertising → social_commerce | A | Boosted listings | Adjacent 2→3 |
| 11 | social ↔ messaging | C | Cross-referral | Lateral in layer 2, 0 nodes between |

**Revised routing for connections 1–3 (Demand → Discovery, span=2):**

These skip layer 1 (Access). Route through the left gutter:
- #1: consumers → search. left(consumers)=(66,136) → gutter track 0 (x=36) → left(search)=(63,336). Waypoints: `[[66,136],[36,136],[36,336],[63,336]]`
- #2: consumers → social. left(consumers)=(66,136) → gutter track 1 (x=22) → left(social)=(200,336). But left(social) is at x=200 which is far from the gutter. Better: exit bottom of consumers, route down through the gap. Actually the cleanest approach for all skip connections in Discovery: exit bottom, run a vertical segment through the Access layer's left side in the gutter, enter target top. Same Pattern B: `[[66,136],[36,136],[36,336],[200,336]]` — this works because the horizontal segment at y=336 runs above the Discovery layer nodes (y_top=308) ... no, 336 is the center of Discovery nodes. That would cross through them.

**Corrected approach:** For skip connections from layer 0 to layer 2, use the gutter for the full vertical run, then enter from the left:
- `[[66,136],[36,136],[36,336],[63,336]]` — the horizontal entry at y=336 goes from x=36 (gutter) to x=63 (Search left edge). This runs at the cy of the Discovery row, but x=36 to x=63 is entirely in the gutter zone (x < 63), so it doesn't cross any node. ✓
- For social at x=200: `[[66,136],[22,136],[22,336],[200,336]]` — the horizontal at y=336 goes from x=22 to x=200. This passes through x=63 to x=181 which is the Search node (x=63, w=118, right edge=181). **This crosses the Search card!**

**Fix:** Enter from the top instead of left. Change the last segment to arrive at top(social):
- `[[66,136],[22,136],[22,308],[259,308]]` — but y=308 is the top of Discovery nodes, and x=259 is top-center of Social (x=200+118/2=259). The horizontal at y=308 runs along the very top edge of the cards. Tight but doesn't cross into them.

**Cleaner fix:** Enter at y = top - 2 to be safe:
- consumers → social: `[[66,136],[22,136],[22,306],[259,306],[259,308]]` — comes in 2px above the row, then drops to top.

**Simplest correct approach for skip connections entering non-leftmost nodes:**

Route in the gutter down to just above the target layer (y = target.y - 2), then horizontal to above target center, then drop in:
```
gutterY = NODES[to].y - 2
waypoints = [
  left(from),
  [gx, left(from)[1]],       // horizontal to gutter
  [gx, gutterY],              // vertical in gutter
  [top(to)[0], gutterY],      // horizontal to above target (in the inter-layer gap)
  top(to)                     // drop into target
]
```

This ensures the horizontal run happens in the inter-layer gap (2px above the row), which is always clear of nodes.

**Applying this:**

| # | Waypoints |
|---|-----------|
| 1 | consumers → search: `[left(consumers), [36, 136], [36, 306], [122, 306], top(search)]` = `[[66,136],[36,136],[36,306],[122,306],[122,308]]` |
| 2 | consumers → social: `[[66,136],[22,136],[22,306],[259,306],[259,308]]` |
| 3 | consumers → messaging: `[[66,136],[8,136],[8,306],[396,306],[396,308]]` |
| 4 | merchants → advertising: `[bot(merchants), [310, 286], [533, 286], top(advertising)]` = `[[310,164],[310,286],[533,286],[533,308]]`. midY=286 is in gap between Access(264) and Discovery(308). ✓ But vertical from y=164 to y=286 — does this cross Access layer nodes? Access nodes are at y=208–264. The vertical at x=310 passes through Access node "OS & App Stores" (x=311, w=155). x=310 is 1px left of that node. Tight! Shift to x=308 for safety: `[[310,164],[308,164],[308,286],[533,286],[533,308]]` |
| 5–10 | Pattern A, straightforward gap jogs between layer 2 and 3 (gap midY = 364 + (408-364)/2 = 386) |
| 11 | social ↔ messaging: `[top(social), [259, 290], [396, 290], top(messaging)]` = `[[259,308],[259,290],[396,290],[396,308]]`. arcY = 308 - 18 = 290. In gap between Access(264) and Discovery(308). ✓ |

### Money (#0F6E56)

| # | From → To | Pattern | Waypoints |
|---|-----------|---------|-----------|
| 1 | consumers → ewallets | B skip 0→4, track 0 | `[[66,136],[36,136],[36,506],[475,506],[475,508]]` (475 = top-center of ewallets: 406+148/2=480. Actually let me recalc: ewallets x=406, w=148, cx=480. So: `[[66,136],[36,136],[36,506],[480,506],[480,508]]`) |
| 2 | consumers → banks | B skip 0→4, track 1 | `[[66,136],[22,136],[22,506],[310,506],[310,508]]` (banks cx=236+148/2=310) |
| 3 | banks → merchants | B skip 4→0, track 2 | `[[236,536],[8,536],[8,106],[310,106],[310,108]]` (merchants cx=236+148/2=310, enter top. gutterY=108-2=106) |
| 4 | marketplaces → promptpay | A adj 3→4 | `[[140,464],[140,486],[140,486],[140,508]]` — same cx! Direct vertical: `[[140,464],[140,508]]` (marketplaces cx=66+74=140, promptpay cx=66+74=140) |
| 5 | superapps → ewallets | A adj 3→4, midY=486 | `[[310,464],[310,486],[480,486],[480,508]]` |
| 6 | promptpay ↔ banks | C lateral, 0 between | `[[140,508],[140,490],[310,490],[310,508]]` arcY=508-18=490. In gap between Execution(464) and T&S(508). ✓ |
| 7 | ewallets ↔ banks | C lateral, 0 between | `[[480,508],[480,493],[310,493],[310,508]]` arcY slightly different to avoid overlap with #6: 508-15=493. ✓ Hmm, but the horizontal at y=493 from x=310 to x=480 passes over the "Banks" card (x=236 to 384) and "E-Wallets" (x=406 to 554). y=493 is above y=508 (top of layer 4) so it's in the gap. ✓ |

### Physical (#BA7517)

| # | From → To | Pattern | Waypoints |
|---|-----------|---------|-----------|
| 1 | marketplaces → parcels | B skip 3→5, track 0 | `[[66,436],[36,436],[36,606],[177,606],[177,608]]` (parcels cx=100+155/2=177.5≈178) |
| 2 | marketplaces → warehouses | B skip 3→5, track 1 | `[[66,436],[22,436],[22,606],[600,606],[600,608]]` (warehouses cx=522+155/2=599.5≈600) |
| 3 | superapps → riders | B skip 3→5, track 2 | `[[236,436],[8,436],[8,606],[389,606],[389,608]]` (riders cx=311+155/2=388.5≈389) |
| 4 | parcels → consumers | B skip 5→0, track 0 | `[[100,636],[36,636],[36,106],[140,106],[140,108]]` |
| 5 | riders → consumers | B skip 5→0, track 1 | `[[311,636],[22,636],[22,106],[140,106]]` — wait, this shares the endpoint with #4. Offset: `[[311,636],[22,636],[22,111],[140,111],[140,108]]` (enter 3px below to split, or offset cx: enter at consumers cx+5=145). Let's keep it simple: `[[311,636],[22,636],[22,103],[140,103],[140,108]]` |
| 6 | parcels ↔ warehouses | C lateral, 1 between (riders) | `[[178,608],[178,584],[600,584],[600,608]]` arcY=608-18-8=582≈584. In gap between T&S(564) and Fulfillment(608). ✓ |

### Data & AI (#185FA5)

| # | From → To | Pattern | Waypoints |
|---|-----------|---------|-----------|
| 1 | marketplaces → cloud | D, diff Y | `[[214,436],[762,436],[762,256],[780,256]]` |
| 2 | superapps → cloud | D, diff Y | `[[384,436],[762,436]]` — same Y as #1! Offset #2's source Y by +5: `[[384,441],[762,441],[762,261],[780,261]]` |
| 3 | social → cloud | D, diff Y | `[[318,336],[762,336],[762,251],[780,251]]` (social right=200+118=318) |
| 4 | social_commerce → cloud | D, diff Y | `[[554,436],[762,436]]` — collision with #1 at y=436. Offset to 446: `[[554,446],[762,446],[762,266],[780,266]]` |
| 5 | promptpay → cloud | D, diff Y | `[[214,536],[762,536],[762,271],[780,271]]` (promptpay right=66+148=214) |
| 6 | ai_ml → marketplaces | D-return, dashed | `[[780,416],[762,416],[762,436],[214,436]]` — collision at y=436 with #1. Offset: `[[780,421],[762,421],[762,441],[214,441]]`. Wait, also collision with #2. Let's use y=451: `[[780,421],[762,421],[762,451],[214,451]]` |
| 7 | ai_ml → social | D-return, dashed | `[[780,416],[762,416],[762,341],[318,341]]` (social right=318, cy=336, offset +5) |
| 8 | ai_ml → search | D-return, dashed | `[[780,411],[762,411],[762,346],[181,346]]` (search right=63+118=181, cy=336, offset +10) |

**Note on collisions:** The waypoints above include manual Y-offsets to avoid lines overlapping. If any collisions remain, adjust by ±5px. The key constraint: no horizontal segment should share the exact same Y with another horizontal segment in the same flow if they overlap in X range.

## Rendering

For each flow, create an SVG `<g>` element with class `flow-{name}` (e.g., `flow-discovery`). Inside, render each connection as a `<path>` using `orthoPath(waypoints)`.

```javascript
// All connections hidden by default except active flow
document.querySelectorAll('.flow-group').forEach(g => g.style.opacity = 0);
document.querySelector('.flow-discovery').style.opacity = 1; // default

function setActiveFlow(name) {
  document.querySelectorAll('.flow-group').forEach(g => {
    g.style.opacity = g.classList.contains(`flow-${name}`) ? 1 : 0;
  });
  // Update pill buttons
  document.querySelectorAll('.flow-pill').forEach(btn => {
    btn.classList.toggle('active', btn.dataset.flow === name);
  });
  // Dim inactive nodes
  Object.keys(NODES).forEach(id => {
    const el = document.getElementById(`node-${id}`);
    if (!el) return;
    const active = FLOW_NODES[name].includes(id);
    el.style.opacity = active ? 1 : 0.35;
    el.style.transition = 'opacity 200ms';
  });
}
```

`FLOW_NODES` is an object mapping each flow name to the list of node IDs involved in that flow.

Connection path style:
- `stroke`: flow color
- `stroke-width`: 1.5
- `stroke-opacity`: 0.5
- `fill`: none
- `marker-end`: url(#arrow-{flow})
- Return arrows (Data & AI #6–8): add `stroke-dasharray="6 4"`, use reverse marker

Node dimming: nodes not in the active flow get `opacity: 0.35`. Transition 200ms.

## Do NOT change

- Node card positions, styles, or the NODES data object
- The orthoPath function (unless fixing a bug)
- Arrow marker definitions

## Checkpoint

Open the file. Verify:
1. Four toggle pills appear below the title
2. Discovery is active by default — its connections are visible, nodes not in the flow are dimmed
3. Click Money — Discovery connections disappear, Money connections appear, different nodes dim
4. Click Physical — Physical connections appear
5. Click Data & AI — horizontal taps to side column visible, dashed return arrows visible
6. All connections have clean 90° corners with rounded radius
7. No connection line crosses through a node card
8. No two connection lines overlap (share the exact same path segment)
