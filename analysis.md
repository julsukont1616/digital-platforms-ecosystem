# Review of `ecosystem.html` Data Layer

Overall verdict: this is a usable visual sketch of the consumer-internet stack, but it is not a clean ETDA-aligned taxonomy and it is not a fully faithful map of Thailand's digital platform ecosystem as of early 2026. The biggest problems are layer naming, missing Thai-specific control points, several weak or wrong operator examples, and flows whose arrow semantics are inconsistent.

## 1. Layers: order, naming, and taxonomy

Short answer: no, not if the claim is "this matches ETDA's 15 platform service types and Thai ecosystem reality."

- `LAYERS[0] = DEMAND` is mislabeled. `consumers` are demand. `merchants`, `creators`, and `enterprises` are supply-side, institutional, or business-side actors. That row is really `Participants` or `Demand & Supply`, not `DEMAND`.
- `LAYERS[3] = TRUST & SETTLEMENT` is mostly a payment layer, not a trust layer. The actual nodes are `promptpay`, `banks`, `ewallets`, and `cards`. Real trust nodes are missing: digital identity, KYC/KYB, moderation, ratings/reviews, complaints/redress, fraud/risk, and governance.
- `LAYERS[6] = INFRASTRUCTURE` collapses two different things into one row: access/distribution gatekeepers (`telecom`, `app_stores`, `browsers`) and backend infrastructure (`cloud`, `cdn`). Those are not the same kind of control point.
- `LAYERS[5] = INTELLIGENCE` works better as an overlay or shared backbone than as a linear layer between fulfillment and infrastructure.

Against ETDA's 15 service types, the mapping is only partial:

- Roughly represented: online marketplace, sharing economy, online communication, social media, advertising, audio-visual sharing, searching tools, cloud, ISP.
- Merged too aggressively: maps into `search`; browsers into `browsers`; operating systems into `app_stores`; hosting into `cdn`.
- Missing as explicit types: virtual assistants, separate maps, separate operating system, separate hosting service, and a true news-aggregator node.

Against Thailand reality, the bigger miss is structural:

- No governance/common-rails layer for ETDA, BOT/NITMX, PDPC, NBTC, DGA/GDX, or NDID.
- No access/onboarding layer, even though app stores, OS, browsers, telecom, identity, and payment linking are real Thai control points.
- No explicit `Thai QR` even though it is central to the payment stack.

If you want a defensible 7-layer version, a stronger order would be:

`Participants -> Access & Onboarding -> Discovery -> Conversion / Execution -> Payment & Settlement -> Fulfillment / Service Ops -> Shared Compute & AI`

Then add governance/common rails as an overlay, not a missing afterthought.

## 2. Node placement and misclassification

Short answer: no, all 26 nodes are not correctly placed.

The most obvious placement problems are these:

| Node ID | Verdict | Why |
| --- | --- | --- |
| `merchants` | Misplaced under `DEMAND` | Merchants are supply-side sellers, not demand. |
| `creators` | Misplaced under `DEMAND` | Creators supply content, attention, and commerce inventory. |
| `enterprises` | Misplaced under `DEMAND` | Enterprises/agencies are business actors, advertisers, and service operators, not demand. |
| `superapps` | Weak classification | `Grab` and `LINE MAN` fit better under `sharing economy` or `on-demand platforms` than `super-apps`. |
| `social_commerce` | Defensible but taxonomically messy | Useful as a conversion node, but it is not an ETDA top-level type and overlaps heavily with `marketplaces`. |
| `streaming` | Weak fit in `EXECUTION` | Streaming is a content/media consumption layer, not transaction execution in the same sense as commerce and on-demand services. |
| `news` | Taxonomy mismatch | If this is ETDA's `news aggregator`, the examples are wrong. If it is publishers/news content, the label is wrong. |
| `app_stores` | Better in access/onboarding | App distribution is an access gatekeeper, not just infrastructure. |
| `browsers` | Better in access/onboarding | Browsers/devices are user access surfaces, not backend infrastructure. |
| `ai_ml` | Better as overlay/backbone | AI influences discovery, conversion, fraud, support, and analytics across layers; it is not a normal single row. |

Nodes that are broadly fine where they are:

- `consumers`
- `search`
- `social`
- `messaging`
- `advertising`
- `marketplaces`
- `promptpay`
- `banks`
- `ewallets`
- `cards`
- `parcels`
- `riders`
- `warehouses`
- `telecom`
- `cloud`
- `cdn`

Even in that "fine" list, several nodes still have naming problems. The cleanest example is `promptpay`: it is correctly in the payment row, but that only proves the row should be called `Payment & Settlement`, not `Trust & Settlement`.

## 3. Flow review: accuracy, directions, omissions

### Discovery flow

The strongest connections are:

- `FLOWS.discovery: consumers -> search`
- `FLOWS.discovery: consumers -> social`
- `FLOWS.discovery: merchants -> advertising`
- `FLOWS.discovery: enterprises -> advertising`
- `FLOWS.discovery: search -> marketplaces`
- `FLOWS.discovery: social -> social_commerce`

The weak or questionable connections are:

- `FLOWS.discovery: social -> superapps`
- `FLOWS.discovery: messaging -> superapps`
- `FLOWS.discovery: streaming -> advertising`
- `FLOWS.discovery: advertising -> creators`

Why they are weak:

- `social -> superapps` is possible, but it is not a core Thai discovery path in the way `social -> social_commerce` is.
- `messaging -> superapps` is even weaker. Chat commerce in Thailand usually routes to merchants, CRM, manual checkout, or social commerce, not primarily to `Grab` or `LINE MAN`.
- `streaming -> advertising` only makes sense if the arrow means "ad inventory supply." That is not the same semantic as the other discovery arrows, which mostly mean user-intent routing.
- `advertising -> creators` is a brand-spend relationship, not a standard user discovery journey.

Important missing discovery connections:

- `FLOWS.discovery` is missing `creators -> social`.
- `FLOWS.discovery` is missing `creators -> streaming`.
- `FLOWS.discovery` is missing `messaging -> social_commerce`.
- `FLOWS.discovery` is missing `search/maps -> superapps`.
- `FLOWS.discovery` is missing direct traffic such as `consumers -> marketplaces` and `consumers -> superapps`, which matters a lot in Thailand because repeat app usage is huge.

### Money flow

The strongest connections are:

- `FLOWS.money: consumers -> ewallets`
- `FLOWS.money: consumers -> banks`
- `FLOWS.money: promptpay -> banks`
- `FLOWS.money: ewallets -> banks`
- `FLOWS.money: cards -> banks`
- `FLOWS.money: banks -> merchants`
- `FLOWS.money: banks -> creators`
- `FLOWS.money: banks -> riders`

The weak or misleading connections are:

- `FLOWS.money: marketplaces -> promptpay`
- `FLOWS.money: social_commerce -> ewallets`
- `FLOWS.money: cards -> streaming`

Why they are weak:

- `marketplaces -> promptpay` is too narrow. Thai marketplace checkout is not just PromptPay. Cards, bank apps, wallets, installment flows, and platform payment stacks matter.
- `social_commerce -> ewallets` overstates wallet-led checkout. In Thailand, social commerce still heavily relies on bank transfer, PromptPay, Thai QR, and manual proof-of-payment patterns.
- `cards -> streaming` is fine as a specific example, but it is isolated and makes cards look like a streaming-only rail because the file is missing the basic `consumers -> cards` edge.

Important missing money connections:

- `FLOWS.money` is missing `consumers -> cards`.
- `FLOWS.money` is missing `marketplaces -> ewallets`.
- `FLOWS.money` is missing `marketplaces -> cards`.
- `FLOWS.money` is missing `marketplaces -> banks`.
- `FLOWS.money` is missing `social_commerce -> promptpay` or `social_commerce -> banks`.
- `FLOWS.money` is missing `superapps -> cards` and likely `superapps -> banks`.

Direction problem:

- If the arrow means payment initiation, the origin should often be the user or merchant-facing checkout node, not the rail alone. Right now the flow mixes initiation, settlement, and payout semantics in one chain.

### Physical flow

The strongest connections are:

- `FLOWS.physical: marketplaces -> parcels`
- `FLOWS.physical: marketplaces -> warehouses`
- `FLOWS.physical: superapps -> riders`
- `FLOWS.physical: social_commerce -> parcels`
- `FLOWS.physical: parcels -> consumers`
- `FLOWS.physical: riders -> consumers`

The wrong connection is:

- `FLOWS.physical: parcels -> warehouses`

That arrow is backwards in most cases. If `warehouses` means seller/platform fulfillment centers, the normal direction is `warehouses -> parcels`, not the other way around.

Important missing physical connections:

- `FLOWS.physical` should include `warehouses -> parcels`.
- `FLOWS.physical` could reasonably include `social_commerce -> riders` for same-day or local merchant delivery patterns.
- Reverse logistics and returns are completely absent.

### Data & AI flow

The strongest connections are:

- `FLOWS.data: ai_ml -> search`
- `FLOWS.data: ai_ml -> social`
- `FLOWS.data: ai_ml -> marketplaces`
- `FLOWS.data: marketplaces -> cloud`
- `FLOWS.data: social -> cloud`
- `FLOWS.data: superapps -> cloud`
- `FLOWS.data: cloud -> ai_ml`
- `FLOWS.data: cloud -> cdn`
- `FLOWS.data: cloud -> browsers`

The weak or wrong connections are:

- `FLOWS.data: promptpay -> cloud`
- `FLOWS.data: cloud -> app_stores`
- `FLOWS.data: cdn -> telecom`

Why they are weak:

- `promptpay -> cloud` is too blunt. It implies public-rail payment data just "flows to cloud providers," which is not a good way to describe Thai payment infrastructure.
- `cloud -> app_stores` labeled as `App hosting` is conceptually wrong. App stores distribute binaries; they are not the normal destination of backend hosting flows.
- `cdn -> telecom` is defensible as delivery path, but it is not really the same thing as a data/AI relationship.

Important missing data/AI connections:

- `FLOWS.data` is missing `streaming -> cloud`.
- `FLOWS.data` is missing `streaming -> cdn`.
- `FLOWS.data` is missing `social_commerce -> cloud`.
- `FLOWS.data` is missing payment analytics links from `banks`, `ewallets`, and `cards`.
- `FLOWS.data` is missing operational telemetry links from `parcels`, `riders`, and `warehouses`.

This flow has the biggest semantic problem in the whole file:

- `ai_ml -> search` is model output.
- `marketplaces -> cloud` is data exhaust/workload placement.
- `cloud -> browsers` is delivery/infrastructure serving.

Those are three different arrow meanings inside one flow.

## 4. Node subtitles: factual correctness of examples

Some subtitles are fine. Several are weak. A few are wrong.

| Node ID | Verdict | Comment |
| --- | --- | --- |
| `consumers` | Slightly stale | `66M internet users` is not crazy, but by the 2026 reporting cycle the figure is closer to the high-60M range. |
| `merchants` | Plausible but loose | `3.4M LINE OA` may be directionally right, but LINE Official Accounts are not a clean synonym for merchants/SMEs. |
| `creators` | Fine | `YouTube, TikTok, LINE` is broad but fair. |
| `enterprises` | Fine but vague | Not wrong, just generic. |
| `search` | Weak | For `Search & Maps`, the subtitle should mention `Google Search` and `Google Maps`, not just `Google, Longdo`. |
| `social` | Weak choice | `Facebook, TikTok, X` is not false, but `Instagram` is more representative in Thailand than `X`. |
| `messaging` | Weak choice | `LINE, WhatsApp` is not false, but `Facebook Messenger` is more representative than `WhatsApp` in Thai commerce. |
| `advertising` | Fine | `Google Ads, Meta Ads` is clean. |
| `news` | Taxonomy issue | `Thairath, THE STANDARD` are publishers, not news aggregators. |
| `marketplaces` | Fine | `Shopee, Lazada, TikTok Shop` is correct for Thailand. |
| `superapps` | Label problem more than example problem | `Grab, LINE MAN` are important, but this should be an on-demand/sharing-economy node, not a `super-apps` node. |
| `social_commerce` | Weak | `FB Shops, LINE Shopping` is thin. `Facebook Marketplace` is more relevant than `FB Shops`. |
| `streaming` | Fine | `YouTube, Netflix, MONOMAX` is reasonable. |
| `promptpay` | Fine | `PromptPay, PromptBiz` is defensible. |
| `banks` | Fine | `SCB, KBANK, BBL` is reasonable. |
| `ewallets` | Mostly fine | `TrueMoney, LINE Pay` is acceptable, but be consistent with `LINE Pay` versus `Rabbit LINE Pay`. |
| `cards` | Fine | `Visa, Mastercard, JCB` is accurate. |
| `parcels` | Wrong/outdated | `Kerry` is outdated branding. The listed operator is `KEX Express` in 2026. |
| `riders` | Fine | `Grab, LINE MAN, Lalamove` is fair. |
| `warehouses` | Fine | `Shopee Xpress, Lazada hubs` is acceptable. |
| `ai_ml` | Weak | `OpenAI, Anthropic, Gemini` are fine. `SCB 10X` and `VISTEC` are not equivalent platform operators in this slot. |
| `telecom` | Misleading | `AIS, TRUE, DTAC` is not correct as operator logic in 2026. `dtac` is no longer a separate operator after the True-dtac amalgamation. |
| `app_stores` | Fine | `Apple, Google Play` is fine. |
| `browsers` | Wrong | `Chrome, Samsung` mixes a browser with a device brand. If you mean browser, it should be `Samsung Internet`. |
| `cloud` | Fine | `AWS, GCP, Azure` is accurate. |
| `cdn` | Wrong/outdated | `Cloudflare, CAT CDN` is outdated. `CAT Telecom` is not the right current entity in 2026. |

## 5. Tooltip accuracy

Some tooltips are strong. Some are sloppy. A few are plainly wrong.

The strongest tooltips:

- `promptpay`: the January 2026 BOT figures are correct.
- `banks`: the `181.8M accounts (Jan 2026)` figure is correct for internet/mobile banking accounts.
- `ewallets`: the `112.3M e-money accounts (Jan 2026)` figure is correct.
- `cloud`: `Google Cloud Bangkok region (launched Jan 2026)` is correct.

The tooltips with clear problems:

- `riders`: `Bolt (entered 2024)` is wrong. Bolt launched in Bangkok on 2020-07-30 and marked five years in Thailand in 2025. This should be corrected or removed.
- `parcels`: `Kerry Express` is outdated branding for Thailand in 2026. Use `KEX Express` if you want the current company/operator name.
- `cdn`: `CAT Telecom CDN` is outdated. If you want a local state-linked operator, use the current entity name, not the pre-merger CAT branding.
- `banks`: `NDID digital identity` does not belong inside the banks tooltip. NDID is a separate identity/trust infrastructure and should be its own node if you want to show trust properly.
- `browsers`: this tooltip mixes browser software with device OEMs. That is the same category mistake as the subtitle.
- `search`: it mixes search market share, map providers, and an over-weighted `Apple Maps` mention. That is not a clean description of Thai discovery behavior.
- `social_commerce`: it duplicates `TikTok Shop`, which is already in `marketplaces`, and it leans on `Instagram Shopping`, whose significance in Thailand is not established in this file.
- `superapps`: `Robinhood` may still exist, but including it as a core super-app without caveat overstates its current strategic weight.
- `ai_ml`: `SCB 10X (local AI)` is overstated. SCB 10X is not a mainstream Thai AI platform operator equivalent to OpenAI, Anthropic, or Google.

The tooltips that are probably directionally right but should be tightened:

- `consumers`: the social-media and e-commerce-buyer numbers need dates and sources in the text, or they should be removed.
- `merchants`: `3M+ TikTok Shop merchants` is supportable, but `1M+ Shopee sellers` and `500K+ Lazada sellers` are not obviously current or sourced in this file.
- `social`: the metrics are mixed. `TikTok (50M MAU)` is one metric style, while `Facebook (50M)` and `Instagram (18M)` are presented without the same framing.
- `telecom`: the subscriber numbers may be roughly fine, but the operator/entity framing is still messy because `TRUE` and `dtac` are not separate operators anymore.
- `ewallets`: the node subtitle says `LINE Pay`, while the tooltip says `Rabbit LINE Pay`. Pick one naming convention and stick to it.

## 6. Structural issues in the diagram itself

This is where the file is weakest.

- It mixes three different things in one model: ETDA service taxonomy, value-chain layers, and flow overlays. Those are related, but they are not identical.
- The top row is called `DEMAND` even though three of its four nodes are supply-side or business-side.
- The `TRUST & SETTLEMENT` row mostly contains payment rails and instruments, while the actual trust stack is absent.
- The Thai public-infrastructure reality is under-modeled. There is no ETDA, BOT/NITMX, PDPC, NBTC, DGA/GDX, NDID, or Thai QR node/overlay.
- `app_stores` and `browsers` are treated like backend infrastructure when they are really access/distribution gatekeepers.
- `streaming` is bolted into a commerce ladder where it does not naturally fit.
- `ai_ml` is drawn as one giant actor node, but in reality AI is a capability layer spread across search, ads, marketplaces, payments, risk, support, and cloud.
- Direct usage loops are underrepresented. Thai users often go straight to Shopee, Lazada, Grab, LINE MAN, YouTube, Netflix, or LINE without first passing through search/social every time.
- The arrow semantics are inconsistent across flows. Some arrows mean traffic, some mean money, some mean inventory, some mean data exhaust, and some mean infrastructure service delivery.

Blunt conclusion:

This HTML data layer is not ready to be described as a faithful Thailand digital platform ecosystem map. It is a compressed consumer-platform sketch with some good instincts, but it is too commerce-centric, too light on governance/common rails, and too loose with category boundaries to claim ETDA alignment. If the goal is a policy-grade or institution-grade ecosystem diagram, this needs a structural rewrite, not just cosmetic cleanup.
