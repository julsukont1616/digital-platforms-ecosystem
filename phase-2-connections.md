# Phase 2: Orthogonal Connection Renderer

## Task

Add a connection rendering system to the existing `ecosystem.html`. This phase builds the engine. Phase 3 will add the actual flow data.

## What to add

### 1. SVG connection layer

Add a second SVG group (or a separate SVG overlay) that sits **above** the node cards. All connection paths will be drawn here. Use `pointer-events: none` on the group by default (Phase 4 will add hit areas).

### 2. Arrow markers

Add SVG `<defs>` with arrowhead markers. Each marker is a small filled triangle (viewBox "0 0 6 4", refX=6, refY=2, markerWidth=6, markerHeight=4, orient="auto"):

```xml
<marker id="arrow-discovery" viewBox="0 0 6 4" refX="6" refY="2"
        markerWidth="6" markerHeight="4" orient="auto">
  <path d="M0,0 L6,2 L0,4 Z" fill="#4285F4"/>
</marker>
<marker id="arrow-money" ...>
  <path d="M0,0 L6,2 L0,4 Z" fill="#0F6E56"/>
</marker>
<marker id="arrow-physical" ...>
  <path d="M0,0 L6,2 L0,4 Z" fill="#BA7517"/>
</marker>
<marker id="arrow-data" ...>
  <path d="M0,0 L6,2 L0,4 Z" fill="#185FA5"/>
</marker>
```

Also add reverse markers (orient="auto-start-reverse") for return arrows.

### 3. `orthoPath(waypoints, R)` function

This is the core function. Takes an array of [x, y] pairs and a corner radius R (default 6). Returns an SVG path `d` string.

**Logic:**

The waypoints define a series of horizontal and vertical segments. At each interior waypoint (not the first or last), the path rounds the corner using a quadratic bezier (Q command).

```javascript
function orthoPath(pts, R = 6) {
  if (pts.length < 2) return '';
  let d = `M${pts[0][0]},${pts[0][1]}`;

  for (let i = 1; i < pts.length - 1; i++) {
    const prev = pts[i - 1];
    const curr = pts[i];
    const next = pts[i + 1];

    // Direction vectors (normalized to -1, 0, or 1)
    const dx1 = Math.sign(curr[0] - prev[0]);
    const dy1 = Math.sign(curr[1] - prev[1]);
    const dx2 = Math.sign(next[0] - curr[0]);
    const dy2 = Math.sign(next[1] - curr[1]);

    // Approach point: R pixels before the corner
    const ax = curr[0] - dx1 * R;
    const ay = curr[1] - dy1 * R;

    // Depart point: R pixels after the corner
    const bx = curr[0] + dx2 * R;
    const by = curr[1] + dy2 * R;

    d += ` L${ax},${ay}`;
    d += ` Q${curr[0]},${curr[1]} ${bx},${by}`;
  }

  // Last point
  const last = pts[pts.length - 1];
  d += ` L${last[0]},${last[1]}`;
  return d;
}
```

**Critical:** This function assumes each consecutive pair of waypoints differs in exactly one axis (either X or Y, not both). All connections in this diagram satisfy this — they're strictly orthogonal.

### 4. Anchor helpers

Add helper functions to get connection anchor points from the NODES object:

```javascript
function nodeAnchors(id) {
  const n = NODES[id];
  return {
    top:    [n.x + n.w / 2, n.y],            // top center
    bottom: [n.x + n.w / 2, n.y + n.h],      // bottom center
    left:   [n.x, n.y + n.h / 2],            // left center
    right:  [n.x + n.w, n.y + n.h / 2],      // right center
    cx:     n.x + n.w / 2,
    cy:     n.y + n.h / 2,
  };
}
```

### 5. Test connections

Render 3 test connections to verify the system works. Style each as: stroke-width 1.5, stroke-opacity 0.6, marker-end pointing to the appropriate arrow marker, fill none.

**Test A — Adjacent layer (consumers → search):**

Goes from bottom-center of "Consumers" to top-center of "Search & Maps", with a horizontal jog at the midline of the gap between layers 0 and 1... wait — these aren't adjacent! Consumers is layer 0 (bottom at y=164), Search is layer 2 (top at y=308). There are 2 layers between them (Access and Discovery). So this is actually a skip connection.

Let's use truly adjacent pairs for the test:

**Test A — Adjacent layer, same column (consumers → telecom):**
- From: consumers bottom center = (66 + 148/2, 164) = (140, 164)
- To: telecom top center = (100 + 155/2, 208) = (177.5, 208)
- Mid Y = 164 + (208 - 164) / 2 = 186
- Waypoints: `[[140, 164], [140, 186], [177.5, 186], [177.5, 208]]`
- Color: #4285F4, marker: arrow-discovery

**Test B — Skip layer via gutter (consumers → promptpay):**
- From: consumers left center = (66, 108 + 28) = (66, 136)
- To: promptpay left center = (66, 508 + 28) = (66, 536)
- Gutter track x = 36
- Waypoints: `[[66, 136], [36, 136], [36, 536], [66, 536]]`
- Color: #0F6E56, marker: arrow-money

**Test C — Horizontal tap to side column (marketplaces → cloud):**
- From: marketplaces right center = (66 + 148, 408 + 28) = (214, 436)
- To: cloud left center = (780, 228 + 28) = (780, 256)
- Jog x = 762 (midpoint of gap between main stack and side column)
- Waypoints: `[[214, 436], [762, 436], [762, 256], [780, 256]]`
- Color: #185FA5, marker: arrow-data

**Render each as:**
```xml
<path d="[result of orthoPath(waypoints)]"
      stroke="#4285F4" stroke-width="1.5" stroke-opacity="0.6"
      fill="none" marker-end="url(#arrow-discovery)"/>
```

## Do NOT change

- Any existing node card rendering from Phase 1
- The NODES data object
- The title, layout, or styling

## Checkpoint

Open the file. You should see:
1. All node cards from Phase 1 (unchanged)
2. Three colored connection lines overlaid on the diagram:
   - Blue line from Consumers down to Telecom (short jog through gap)
   - Green line from Consumers down the left gutter to Public Rails
   - Dark blue line from Marketplaces horizontally to Cloud Providers (with a vertical jog)
3. All corners are smooth 90° turns (6px radius), no sharp corners, no curves
4. Lines do NOT cross through any node card
5. Small arrowheads at the end of each line
