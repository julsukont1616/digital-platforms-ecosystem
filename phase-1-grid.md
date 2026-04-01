# Phase 1: Static Grid

## Task

Create `ecosystem.html` — a single self-contained HTML file. Render a static grid of node cards. No connections, no interactions.

## Page setup

- DM Sans font via Google Fonts CDN
- Centered container, max-width 980px
- Background: #F6F6F4
- Title at top: "Thailand Digital Platform Ecosystem" (22px, weight 600, color #1A1A1A)

## How the grid works

The entire diagram is one SVG element with `viewBox="0 0 980 780"` and `width: 100%; max-width: 980px`.

Content is split into a **main stack** (x=44 to x=744, width 700px) and a **side column** (x=780 to x=940, width 160px).

Left gutter: x=0 to x=44 (reserved, empty for now).

### Vertical rhythm

```
NODE_H  = 56    // card height in px
GAP     = 44    // space between layers
Y_START = 108   // top of first layer (leaves room for title + toggle bar)
```

Layer top Y = `Y_START + layerIndex × (NODE_H + GAP)`

### Horizontal positioning

For a layer with N nodes of width W in the 700px main stack:

```
spacing = (700 - N × W) / (N + 1)
node_x  = 44 + spacing + j × (W + spacing)    // j = 0, 1, 2, ...
```

## Layer data

Render these 6 layers top to bottom. Each layer has a **label** (small uppercase text, 11px, weight 600, layer color, positioned 8px above the first node's top-left corner).

### Layer 0 — "DEMAND" — color #534AB7 — 4 nodes, W=148

| j | x | Name | Subtitle |
|---|---|------|----------|
| 0 | 66 | Consumers & Citizens | 66M internet users |
| 1 | 236 | Merchants & SMEs | 3.4M LINE OA |
| 2 | 406 | Creators & Drivers | Grab, LINE creators |
| 3 | 576 | Enterprises & Agencies | Listed firms, govt |

Y_top = 108, Y_bottom = 164

### Layer 1 — "ACCESS" — color #BA7517 — 3 nodes, W=155

| j | x | Name | Subtitle |
|---|---|------|----------|
| 0 | 100 | Telecom / ISPs | AIS, TRUE, DTAC |
| 1 | 311 | OS & App Stores | Apple, Google Play |
| 2 | 522 | Browsers & Devices | Chrome, Samsung |

Y_top = 208, Y_bottom = 264

### Layer 2 — "DISCOVERY" — color #4285F4 — 5 nodes, W=118

| j | x | Name | Subtitle |
|---|---|------|----------|
| 0 | 63 | Search & Maps | Google, Longdo |
| 1 | 200 | Social Media | Facebook, TikTok, X |
| 2 | 337 | Messaging | LINE, WhatsApp |
| 3 | 474 | Advertising | Google Ads, Meta Ads |
| 4 | 611 | News & Content | Thairath, THE STANDARD |

Y_top = 308, Y_bottom = 364

### Layer 3 — "EXECUTION" — color #D85A30 — 4 nodes, W=148

| j | x | Name | Subtitle |
|---|---|------|----------|
| 0 | 66 | Marketplaces | Shopee, Lazada, TikTok Shop |
| 1 | 236 | Super-apps | Grab, LINE MAN |
| 2 | 406 | Social Commerce | FB Shops, LINE Shopping |
| 3 | 576 | Streaming | YouTube, Netflix, MONOMAX |

Y_top = 408, Y_bottom = 464

### Layer 4 — "TRUST & SETTLEMENT" — color #0F6E56 — 4 nodes, W=148

| j | x | Name | Subtitle |
|---|---|------|----------|
| 0 | 66 | Public Rails | PromptPay, PromptBiz |
| 1 | 236 | Banks & Acquirers | SCB, KBANK, BBL |
| 2 | 406 | E-Wallets | TrueMoney, LINE Pay |
| 3 | 576 | Card Networks | Visa, Mastercard, JCB |

Y_top = 508, Y_bottom = 564

### Layer 5 — "FULFILLMENT" — color #BA7517 — 3 nodes, W=155

| j | x | Name | Subtitle |
|---|---|------|----------|
| 0 | 100 | Parcel Networks | Kerry, Flash, J&T |
| 1 | 311 | Rider Fleets | Grab, LINE MAN, Lalamove |
| 2 | 522 | Warehouses | Shopee Xpress, Lazada hubs |

Y_top = 608, Y_bottom = 664

## Side column — "DATA & AI" — color #185FA5

Background band: SVG rect from (770, 200) to (970, 600), fill #185FA5 at 4% opacity, rx=12.

Label "DATA & AI" at (780, 220), same style as layer labels but color #185FA5.

3 nodes stacked vertically, each W=160, H=56, x=780:

| Node | Y_top | Name | Subtitle |
|------|-------|------|----------|
| Cloud Providers | 228 | Cloud Providers | AWS, Google Cloud, Azure |
| AI/ML Platforms | 388 | AI/ML Platforms | OpenAI, Anthropic, SCB 10X |
| CDN & Hosting | 548 | CDN & Hosting | Cloudflare, CAT CDN |

## Node card style

Each card is an SVG group containing:

1. **Background rect:** fill #FFFFFF, rx=8, with a subtle drop shadow via SVG filter:
   ```xml
   <filter id="shadow">
     <feDropShadow dx="0" dy="1" stdDeviation="2" flood-opacity="0.06"/>
   </filter>
   ```

2. **Left border accent:** a small rect (width 2.5px, full card height, layer color, rx=1) at the card's left edge. Clip or overlay so it appears as a colored left border.

3. **Name text:** 12px, weight 600, fill #1A1A1A. Positioned at x+10, y_top+22.

4. **Subtitle text:** 10.5px, weight 400, fill #6B6B6B. Positioned at x+10, y_top+40.

Text must not overflow the card width. If a name is long, use a shorter version or reduce font size for that card.

## Data structure suggestion

Store everything in a JS array so later phases can look up node positions by ID:

```javascript
const NODES = {
  consumers:       { layer: 0, x: 66,  w: 148, y: 108, h: 56, color: '#534AB7', name: 'Consumers & Citizens', sub: '66M internet users' },
  merchants:       { layer: 0, x: 236, w: 148, y: 108, h: 56, color: '#534AB7', name: 'Merchants & SMEs', sub: '3.4M LINE OA' },
  creators:        { layer: 0, x: 406, w: 148, y: 108, h: 56, color: '#534AB7', name: 'Creators & Drivers', sub: 'Grab, LINE creators' },
  enterprises:     { layer: 0, x: 576, w: 148, y: 108, h: 56, color: '#534AB7', name: 'Enterprises & Agencies', sub: 'Listed firms, govt' },
  telecom:         { layer: 1, x: 100, w: 155, y: 208, h: 56, color: '#BA7517', name: 'Telecom / ISPs', sub: 'AIS, TRUE, DTAC' },
  app_stores:      { layer: 1, x: 311, w: 155, y: 208, h: 56, color: '#BA7517', name: 'OS & App Stores', sub: 'Apple, Google Play' },
  browsers:        { layer: 1, x: 522, w: 155, y: 208, h: 56, color: '#BA7517', name: 'Browsers & Devices', sub: 'Chrome, Samsung' },
  search:          { layer: 2, x: 63,  w: 118, y: 308, h: 56, color: '#4285F4', name: 'Search & Maps', sub: 'Google, Longdo' },
  social:          { layer: 2, x: 200, w: 118, y: 308, h: 56, color: '#4285F4', name: 'Social Media', sub: 'Facebook, TikTok, X' },
  messaging:       { layer: 2, x: 337, w: 118, y: 308, h: 56, color: '#4285F4', name: 'Messaging', sub: 'LINE, WhatsApp' },
  advertising:     { layer: 2, x: 474, w: 118, y: 308, h: 56, color: '#4285F4', name: 'Advertising', sub: 'Google Ads, Meta Ads' },
  news:            { layer: 2, x: 611, w: 118, y: 308, h: 56, color: '#4285F4', name: 'News & Content', sub: 'Thairath, THE STANDARD' },
  marketplaces:    { layer: 3, x: 66,  w: 148, y: 408, h: 56, color: '#D85A30', name: 'Marketplaces', sub: 'Shopee, Lazada, TikTok Shop' },
  superapps:       { layer: 3, x: 236, w: 148, y: 408, h: 56, color: '#D85A30', name: 'Super-apps', sub: 'Grab, LINE MAN' },
  social_commerce: { layer: 3, x: 406, w: 148, y: 408, h: 56, color: '#D85A30', name: 'Social Commerce', sub: 'FB Shops, LINE Shopping' },
  streaming:       { layer: 3, x: 576, w: 148, y: 408, h: 56, color: '#D85A30', name: 'Streaming', sub: 'YouTube, Netflix, MONOMAX' },
  promptpay:       { layer: 4, x: 66,  w: 148, y: 508, h: 56, color: '#0F6E56', name: 'Public Rails', sub: 'PromptPay, PromptBiz' },
  banks:           { layer: 4, x: 236, w: 148, y: 508, h: 56, color: '#0F6E56', name: 'Banks & Acquirers', sub: 'SCB, KBANK, BBL' },
  ewallets:        { layer: 4, x: 406, w: 148, y: 508, h: 56, color: '#0F6E56', name: 'E-Wallets', sub: 'TrueMoney, LINE Pay' },
  cards:           { layer: 4, x: 576, w: 148, y: 508, h: 56, color: '#0F6E56', name: 'Card Networks', sub: 'Visa, Mastercard, JCB' },
  parcels:         { layer: 5, x: 100, w: 155, y: 608, h: 56, color: '#BA7517', name: 'Parcel Networks', sub: 'Kerry, Flash, J&T' },
  riders:          { layer: 5, x: 311, w: 155, y: 608, h: 56, color: '#BA7517', name: 'Rider Fleets', sub: 'Grab, LINE MAN, Lalamove' },
  warehouses:      { layer: 5, x: 522, w: 155, y: 608, h: 56, color: '#BA7517', name: 'Warehouses', sub: 'Shopee Xpress, Lazada hubs' },
  cloud:           { layer: -1, x: 780, w: 160, y: 228, h: 56, color: '#185FA5', name: 'Cloud Providers', sub: 'AWS, Google Cloud, Azure' },
  ai_ml:           { layer: -1, x: 780, w: 160, y: 388, h: 56, color: '#185FA5', name: 'AI/ML Platforms', sub: 'OpenAI, Anthropic, SCB 10X' },
  cdn:             { layer: -1, x: 780, w: 160, y: 548, h: 56, color: '#185FA5', name: 'CDN & Hosting', sub: 'Cloudflare, CAT CDN' },
};
```

This NODES object is critical. Later phases will read `NODES[id]` to compute anchor points for connections.

## Checkpoint

Open the file in a browser. You should see:
- 6 rows of white cards with colored left borders, evenly spaced
- 3 cards in a right-side column with a faint blue background band
- Layer labels above each row
- Title at the top
- No overlapping text, no misaligned cards
- Clean, generous spacing throughout
