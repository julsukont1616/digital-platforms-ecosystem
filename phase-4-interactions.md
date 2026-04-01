# Phase 4: Interactions

## Task

Add hover highlighting, connection labels, and click-to-show tooltips to the existing `ecosystem.html`.

## 1. Connection hit areas

Each connection `<path>` is hard to hover (1.5px stroke). For each visible path, add an invisible wider hit-area path on top:

```xml
<path d="[same d as connection]" stroke="transparent" stroke-width="14"
      fill="none" pointer-events="stroke" class="conn-hit" data-conn-id="..."/>
```

Set `pointer-events: stroke` on hit areas, `pointer-events: none` on the visible paths.

## 2. Hover connection

When a `.conn-hit` path is hovered:
- The corresponding visible path: stroke-width → 2.5, stroke-opacity → 0.85
- All OTHER visible paths in the active flow: stroke-opacity → 0.08
- Source and target nodes: add class `.node-highlight` (box-shadow equivalent via SVG filter or increased shadow)
- Show the connection label (see below)

On mouseout: revert all to defaults (transition 150ms).

## 3. Connection labels

Each connection has a `label` string (defined in Phase 3 flow data). Render labels as SVG groups, initially hidden (`opacity: 0`):

```xml
<g class="conn-label" data-conn-id="...">
  <rect rx="3" fill="var(--bg-card)" stroke="none" />
  <text font-size="10" font-weight="500" fill="{flow-color}">Label text</text>
</g>
```

Position each label at the **midpoint of the longest segment** in that connection's waypoint array:
- Find the segment (consecutive pair of waypoints) with the greatest length
- Place the label centered at that segment's midpoint
- The background rect should be sized to fit the text + 4px horizontal padding + 2px vertical padding

On connection hover: set that label's opacity to 1. On mouseout: back to 0.

Labels have `pointer-events: none` so they don't interfere with hovering.

## 4. Hover node

When a node card is hovered (attach listeners to the node's SVG group `#node-{id}`):
- All connections touching that node: stroke-width → 2.2, stroke-opacity → 0.85, show their labels
- All OTHER connections in the active flow: stroke-opacity → 0.08
- The hovered node: slight upward translate (transform: translateY(-1px) or SVG equivalent) + enhanced shadow filter
- All connected nodes (the other end of highlighted connections): same enhanced shadow
- Non-connected nodes: remain at current opacity

On mouseout: revert all.

## 5. Click node → tooltip

On clicking a node card, show a floating tooltip with detailed info.

Tooltip is an HTML div (not SVG) positioned absolutely over the diagram:

```html
<div class="tooltip" style="left: {x}px; top: {y}px;">
  <div class="tooltip-title">{node name}</div>
  <div class="tooltip-body">{full operator list}</div>
</div>
```

Style:
- Background: #FFFFFF (dark mode: #1E1E22)
- Border-radius: 10px
- Box-shadow: 0 4px 16px rgba(0,0,0,0.12)
- Max-width: 220px
- Padding: 12px 14px
- Title: 13px, weight 600, color #1A1A1A
- Body: 11.5px, weight 400, color #6B6B6B, line-height 1.5
- Fade-in: opacity 0→1 over 150ms

Positioning logic:
- Default: below the node, horizontally centered
- If below would overflow the SVG bottom: position above the node
- If horizontally off-screen: shift left/right to stay within bounds

Dismiss: click outside the tooltip, or click the same node again. Only one tooltip visible at a time.

Tooltip content per node (use this data, add it to the NODES object or a separate TOOLTIPS object):

```javascript
const TOOLTIPS = {
  consumers:       'Thai internet population. 57M social media users. 54M e-commerce buyers.',
  merchants:       '3.4M LINE Official Accounts. 1M+ Shopee sellers. 500K+ Lazada sellers. 3M+ TikTok Shop merchants.',
  creators:        'Grab driver-partners. LINE sticker creators. YouTube/TikTok content creators. Food delivery riders.',
  enterprises:     'SET-listed companies. Government agencies. Large corporates and MNCs.',
  telecom:         'AIS (46M subs). TRUE (34M). DTAC merged into TRUE. Fixed: TRUE, AIS Fibre, 3BB.',
  app_stores:      'Apple App Store. Google Play Store. Huawei AppGallery. Samsung Galaxy Store.',
  browsers:        'Chrome (dominant). Safari. Samsung Internet. OPPO, Vivo, Xiaomi devices.',
  search:          'Google (90%+ share). Apple Maps. Longdo Map (Thai local). Google Maps.',
  social:          'Facebook (50M). TikTok (50M MAU). Instagram (18M). X/Twitter. Threads.',
  messaging:       'LINE (56M users, dominant). WhatsApp. Telegram. Facebook Messenger.',
  advertising:     'Google Ads. Meta/Facebook Ads. TikTok Ads. LINE Ads. Programmatic DSPs.',
  news:            'Thairath Online. Matichon. THE STANDARD. Workpoint. Khaosod.',
  marketplaces:    'Shopee (#1 GMV). Lazada. TikTok Shop (fastest growing). NocNoc. JD Central (closed).',
  superapps:       'Grab (ride-hail + food + pay). LINE MAN (food + messenger). Robinhood (food, Thai-owned).',
  social_commerce: 'Facebook Shops & Marketplace. LINE Shopping. TikTok Shop. Instagram Shopping.',
  streaming:       'YouTube (dominant). Netflix. MONOMAX (Thai). Viu. Disney+ Hotstar. WeTV.',
  promptpay:       'PromptPay: 92.2M IDs registered (Jan 2026). 79.9M daily transactions. PromptBiz for B2B.',
  banks:           '181.8M accounts (Jan 2026). SCB, KBANK, BBL, KTB, Krungsri. NDID digital identity. Bank KYC/KYB.',
  ewallets:        '112.3M e-money accounts (Jan 2026). TrueMoney. Rabbit LINE Pay. ShopeePay. GrabPay.',
  cards:           'Visa. Mastercard. JCB (strong in TH). UnionPay. Local debit scheme.',
  parcels:         'Kerry Express. Flash Express. J&T Express. Thailand Post. Best Express. Ninja Van.',
  riders:          'Grab. LINE MAN. Lalamove. Bolt (entered 2024). Food delivery + courier.',
  warehouses:      'Shopee Xpress fulfillment hubs. Lazada sort centers. Kerry warehouses. 3PL providers.',
  cloud:           'AWS (longest presence). Google Cloud Bangkok region (launched Jan 2026). Azure. Alibaba Cloud.',
  ai_ml:           'OpenAI API. Anthropic Claude. Google Gemini. SCB 10X (local AI). VISTEC research.',
  cdn:             'Cloudflare. CAT Telecom CDN. Akamai. Local data centers (INET, TRUE IDC).',
};
```

## 6. Draw-in animation (connection appear)

When a flow is toggled, connections should animate in using stroke-dashoffset:

```css
.flow-group path.conn-line {
  transition: stroke-dashoffset 400ms ease-out, opacity 200ms;
}
```

On flow activation:
1. For each connection path, compute total length: `path.getTotalLength()`
2. Set `stroke-dasharray` and `stroke-dashoffset` to that length (hides the path)
3. Force reflow (read offsetHeight or use requestAnimationFrame)
4. Set `stroke-dashoffset` to 0 (draws the path in)

On flow deactivation: just set opacity to 0 (no reverse animation needed).

## Do NOT change

- Node positions, grid layout, NODES object
- orthoPath function
- Connection waypoints from Phase 3
- Toggle button logic (extend it, don't replace)

## Checkpoint

Open the file. Verify:
1. Hover a connection line — it thickens, others dim, label appears at midpoint
2. Move mouse away — everything reverts smoothly
3. Hover a node card — all its connections highlight, label appears, node elevates slightly
4. Click a node — tooltip appears with operator list
5. Click outside — tooltip dismisses
6. Switch flows — connections draw in with animation (stroke grows from start to end)
7. Labels don't overlap node cards
8. Tooltip doesn't overflow the container
