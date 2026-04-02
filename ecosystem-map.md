# Thailand Digital Platform Ecosystem — Relationship Map

> **Purpose:** Single source of truth for all nodes, layers, and connections in the ecosystem diagram.
> Edit this file, then ask Claude to incorporate changes into `ecosystem.html`.
>
> **Sources:** BOT Payment Report Jan 2026, ETDA Platform Registry, DataReportal Digital 2025.

---

## How to edit

- **Add a node:** Add a row to the relevant layer table. Pick a unique `id` (lowercase, underscores).
- **Remove a node:** Delete its row and remove all connections referencing it.
- **Add a connection:** Add a row to the relevant flow table. Use existing node `id` values.
- **Flags:** `lateral` = same-layer horizontal link. `dashed` = non-transactional / intelligence flow.
- **Move a node between layers:** Change its layer table. Update the `layer` number.

When asking Claude to sync changes back to HTML, share this file and describe what changed.

---

## Layers

| # | Layer ID | Label | Color | Notes |
|---|----------|-------|-------|-------|
| 0 | participants | PARTICIPANTS | #534AB7 | End users and supply-side actors |
| 1 | access | ACCESS | #BA7517 | Connectivity and distribution gates |
| 2 | discovery | DISCOVERY & CONTENT | #4285F4 | How users find, consume, and share |
| 3 | execution | EXECUTION | #D85A30 | Where transactions and services happen |
| 4 | payment | PAYMENT & SETTLEMENT | #0F6E56 | How money moves |
| 5 | fulfillment | FULFILLMENT | #BA7517 | Physical delivery |
| 6 | intelligence | INTELLIGENCE | #7C3AED | AI/ML models and services |
| 7 | infra | DIGITAL INFRASTRUCTURE | #185FA5 | Cloud, CDN, compute |

---

## Nodes

### Layer 0 — PARTICIPANTS

| id | Name | Subtitle | Tooltip |
|----|------|----------|---------|
| consumers | Consumers & Citizens | 66M internet users | Thai internet population. 57M social media users. 54M e-commerce buyers. |
| merchants | Merchants & SMEs | 3.4M LINE OA | 3.4M LINE Official Accounts. 1M+ Shopee sellers. 500K+ Lazada sellers. 3M+ TikTok Shop merchants. |
| creators | Creators | YouTube, TikTok, LINE | YouTube/TikTok content creators. LINE sticker creators. TikTok Shop affiliates. Live commerce hosts. |
| enterprises | Enterprises & Agencies | Listed firms, govt | SET-listed companies. Government agencies. Large corporates and MNCs. |

### Layer 1 — ACCESS

| id | Name | Subtitle | Tooltip |
|----|------|----------|---------|
| telecom | Telecom / ISPs | AIS, TRUE, 3BB | AIS (46M subs). TRUE (incl. former dtac, 34M+). Fixed broadband: TRUE, AIS Fibre, 3BB. |
| app_stores | OS & App Stores | Apple, Google Play | Mobile app distribution: Apple App Store. Google Play Store. Huawei AppGallery. Samsung Galaxy Store. |
| browsers | Browsers | Chrome, Safari, Samsung Internet | Chrome (dominant). Safari. Samsung Internet. Firefox. In-app browsers. |

### Layer 2 — DISCOVERY & CONTENT

| id | Name | Subtitle | Tooltip |
|----|------|----------|---------|
| search | Search & Maps | Google, Longdo | Google (90%+ share). Apple Maps. Longdo Map (Thai local). Google Maps. |
| social | Social Media | Facebook, TikTok, X | Facebook (50M). TikTok (50M MAU). Instagram (18M). X/Twitter. Threads. |
| messaging | Messaging | LINE, WhatsApp | LINE (56M users, dominant). WhatsApp. Telegram. Facebook Messenger. |
| advertising | Advertising | Google Ads, Meta Ads | Google Ads. Meta/Facebook Ads. TikTok Ads. LINE Ads. Programmatic DSPs. |
| news | News & Media | Thairath, THE STANDARD | Thairath Online. Matichon. THE STANDARD. Workpoint. Khaosod. |
| streaming | Streaming | YouTube, Netflix, Viu | YouTube (dominant video discovery). Netflix. MONOMAX (Thai). Viu. Disney+. WeTV. |

### Layer 3 — EXECUTION

| id | Name | Subtitle | Tooltip |
|----|------|----------|---------|
| marketplaces | Marketplaces | Shopee, Lazada, TikTok Shop | Shopee (#1 GMV). Lazada. TikTok Shop (fastest growing). NocNoc. |
| superapps | Super-apps | Grab, LINE MAN, Bolt | Grab (ride-hail + food + pay). LINE MAN (food + messenger). Bolt (ride-hail, Bangkok). |
| social_commerce | Social Commerce | FB Shops, LINE Shopping | Facebook Shops & Marketplace. LINE Shopping. TikTok Shop. Instagram Shopping. |

### Layer 4 — PAYMENT & SETTLEMENT

| id | Name | Subtitle | Tooltip |
|----|------|----------|---------|
| promptpay | Public Rails | PromptPay, PromptBiz | PromptPay: 92.2M IDs registered (Jan 2026). 79.9M daily transactions. PromptBiz for B2B. |
| banks | Banks & Acquirers | SCB, KBANK, BBL | 181.8M internet/mobile banking accounts (Jan 2026). SCB, KBANK, BBL, KTB, Krungsri. |
| ewallets | E-Wallets | TrueMoney, Rabbit LINE Pay | 112.3M e-money accounts (Jan 2026). TrueMoney. Rabbit LINE Pay. ShopeePay. GrabPay. |
| cards | Card Networks | Visa, Mastercard, JCB | Visa. Mastercard. JCB (strong in TH). UnionPay. Local debit scheme. |

### Layer 5 — FULFILLMENT

| id | Name | Subtitle | Tooltip |
|----|------|----------|---------|
| parcels | Parcel Networks | KEX, Flash, J&T | KEX Express (formerly Kerry). Flash Express. J&T Express. Thailand Post. SPX Express. |
| riders | Rider Fleets | Grab, LINE MAN, Lalamove | Grab. LINE MAN. Lalamove. Bolt (launched Bangkok 2020). Food delivery + courier. |
| warehouses | Warehouses | Shopee Xpress, Lazada hubs | Shopee Xpress fulfillment hubs. Lazada sort centers. KEX warehouses. 3PL providers. |

### Layer 6 — INTELLIGENCE

| id | Name | Subtitle | Tooltip |
|----|------|----------|---------|
| ai_ml | AI & Machine Learning | OpenAI, Anthropic, Gemini, SCB 10X, VISTEC | OpenAI API. Anthropic Claude. Google Gemini. SCB 10X (local AI). VISTEC research. |

### Layer 7 — DIGITAL INFRASTRUCTURE

| id | Name | Subtitle | Tooltip |
|----|------|----------|---------|
| cloud | Cloud Providers | AWS, GCP, Azure | AWS (longest presence). Google Cloud Bangkok region (launched Jan 2026). Azure. Alibaba Cloud. |
| cdn | CDN & Hosting | Cloudflare, Akamai, INET | Cloudflare. Akamai. Local data centers: INET, TRUE IDC, NT (formerly CAT). |

---

## Connections

### Discovery Flow

How users find, discover, and reach platforms.

| # | From | To | Label | Flags | Notes |
|---|------|----|-------|-------|-------|
| D01 | consumers | telecom | Go online | | |
| D02 | consumers | app_stores | Install apps | | |
| D03 | consumers | browsers | Open web | | |
| D04 | telecom | app_stores | Mobile data | lateral | Telecom enables app downloads |
| D05 | telecom | browsers | Fixed broadband | lateral | Telecom enables web access |
| D06 | app_stores | social | Install social apps | | |
| D07 | app_stores | messaging | Install messaging | | |
| D08 | app_stores | streaming | Install content apps | | |
| D09 | app_stores | marketplaces | Install commerce apps | | |
| D10 | app_stores | superapps | Install service apps | | |
| D11 | browsers | search | Web search | | |
| D12 | browsers | news | Read publishers | | |
| D13 | browsers | streaming | Watch in browser | | |
| D14 | merchants | advertising | Ad spend | | |
| D15 | enterprises | advertising | Enterprise campaigns | | |
| D16 | consumers | marketplaces | Direct / repeat | | Skip discovery layer |
| D17 | consumers | superapps | Direct / repeat | | Skip discovery layer |
| D18 | creators | social | Content creation | | |
| D19 | creators | streaming | Creator content | | |
| D20 | creators | social_commerce | Creator affiliate | | |
| D21 | search | news | News lookup | lateral | Within discovery layer |
| D22 | search | marketplaces | Product search | | |
| D23 | search | superapps | Maps discovery | | |
| D24 | social | marketplaces | Social referral | | |
| D25 | social | superapps | Content to commerce | | |
| D26 | social | social_commerce | In-app shops | | |
| D27 | messaging | superapps | Chat-to-service | | |
| D28 | messaging | social_commerce | Chat commerce | | |
| D29 | advertising | marketplaces | Paid placement | | |
| D30 | advertising | superapps | App install / demand | | |
| D31 | advertising | social_commerce | Boosted listings | | |
| D32 | streaming | social_commerce | Creator-led commerce | | |
| D33 | news | marketplaces | Affiliate traffic | | |
| D34 | advertising | creators | Brand campaigns | | Reverse flow (upward) |

### Money Flow

How money moves between participants, platforms, and infrastructure.

| # | From | To | Label | Flags | Notes |
|---|------|----|-------|-------|-------|
| M01 | consumers | ewallets | Top-up / pay | | |
| M02 | consumers | banks | Bank transfer | | |
| M03 | consumers | cards | Card payment | | |
| M04 | marketplaces | promptpay | QR checkout | | |
| M05 | marketplaces | ewallets | Wallet checkout | | |
| M06 | marketplaces | cards | Card checkout | | |
| M07 | marketplaces | banks | Bank app checkout | | |
| M08 | superapps | ewallets | In-app payment | | |
| M09 | superapps | promptpay | QR checkout | | |
| M10 | superapps | banks | Bank app checkout | | |
| M11 | superapps | cards | Card payment | | |
| M12 | social_commerce | ewallets | Social checkout | | |
| M13 | social_commerce | banks | Bank transfer | | |
| M14 | social_commerce | cards | Card payment | | |
| M15 | social_commerce | promptpay | QR payment | | |
| M16 | streaming | cards | Subscription checkout | | |
| M17 | merchants | marketplaces | Seller fees / commission | | Money from merchants to platforms |
| M18 | merchants | social_commerce | Store tools / commission | | |
| M19 | streaming | app_stores | App-store commission | | Revenue share to app stores |
| M20 | marketplaces | warehouses | Fulfillment fees | | |
| M21 | banks | merchants | Merchant settlement | | Payout: banks → merchants |
| M22 | banks | creators | Creator payout | | Payout: banks → creators |
| M23 | banks | parcels | Logistics fees | | |
| M24 | banks | riders | Rider payout | | |
| M25 | promptpay | banks | Interbank rails | lateral | Payment layer lateral |
| M26 | ewallets | banks | Float settlement | lateral | Payment layer lateral |
| M27 | cards | banks | Card acquiring | lateral | Payment layer lateral |

### Physical Flow

How goods and services are physically delivered.

| # | From | To | Label | Flags | Notes |
|---|------|----|-------|-------|-------|
| P01 | merchants | parcels | Self-fulfillment | | Merchants ship directly |
| P02 | marketplaces | parcels | Ship order | | |
| P03 | marketplaces | warehouses | Fulfillment | | |
| P04 | superapps | riders | Dispatch rider | | |
| P05 | social_commerce | parcels | Ship order | | |
| P06 | social_commerce | riders | Local delivery | | |
| P07 | parcels | consumers | Delivery | | Return to consumers |
| P08 | riders | consumers | Last-mile | | Return to consumers |
| P09 | warehouses | parcels | Pack & ship | lateral | Fulfillment layer lateral |

### Data & AI Flow

How data flows down to infrastructure and intelligence flows back up.

| # | From | To | Label | Flags | Notes |
|---|------|----|-------|-------|-------|
| **AI output (upward, dashed)** | | | | | |
| A01 | ai_ml | search | Search ranking | dashed | |
| A02 | ai_ml | social | Content ranking | dashed | |
| A03 | ai_ml | marketplaces | Recommendations | dashed | |
| A04 | ai_ml | advertising | Targeting / optimization | dashed | |
| A05 | ai_ml | superapps | Matching & pricing | dashed | Rider dispatch, dynamic pricing |
| A06 | ai_ml | streaming | Recommendations | dashed | YouTube/Netflix core product |
| A07 | ai_ml | social_commerce | Product ranking | dashed | Feed and live commerce ranking |
| **Data exhaust (downward to cloud)** | | | | | |
| A08 | consumers | cloud | Behavior / identity data | | |
| A09 | merchants | cloud | Catalog / seller data | | |
| A10 | creators | cloud | Content / audience data | | |
| A11 | marketplaces | cloud | Transaction data | | |
| A12 | social | cloud | Engagement data | | |
| A13 | promptpay | cloud | Payment data | | |
| A14 | enterprises | cloud | Enterprise workloads | | |
| A15 | advertising | cloud | Ad & audience data | | |
| A16 | superapps | cloud | Location & txn data | | |
| A17 | streaming | cloud | Viewing data | | |
| A18 | social_commerce | cloud | Commerce data | | |
| A19 | banks | cloud | Financial data | | |
| A20 | ewallets | cloud | Wallet txn data | | |
| A21 | cards | cloud | Card network data | | |
| A22 | news | cloud | Readership data | | |
| **Infrastructure** | | | | | |
| A23 | cloud | ai_ml | Compute / model serving | | Cloud feeds AI layer |
| A24 | cloud | cdn | Content delivery | lateral | Infra layer lateral |
| A25 | cdn | streaming | Content serving | dashed | CDN serves streaming content |

---

## Mobile Summaries

Short descriptions shown on mobile per flow view.

| Flow | Summary |
|------|---------|
| discovery | Telecom enables app stores and browsers, which feed search, social, news, and streaming. These convert into marketplaces, super-apps, and social commerce. |
| money | Consumers pay through banks, wallets, cards, and QR. Merchants pay platform fees and commissions. Banks settle funds back to merchants and creators. |
| physical | Marketplaces ship via parcel networks and warehouses. Super-apps dispatch riders. Merchants also self-fulfill via parcels. Goods reach consumers. |
| data | Participant, platform, and financial data accumulates in cloud infrastructure. AI feeds ranking, matching, pricing, and recommendations back into the journey. CDN serves content to streaming and media. |
| overview | All platforms and infrastructure layers in the Thai digital ecosystem. |

---

## Known gaps (not yet implemented)

These were identified during review but not added to the diagram. Add them above if/when ready.

- **Regulatory layer:** BOT, NBTC, TCCT/OTP, SEC, DES/ETDA. Shapes every layer.
- **Government digital platforms:** Pao Tang, Tang Rat, ThaiD. Interact with payment, identity, cloud.
- **BNPL / embedded finance:** Atome, akulaku, platform credit. Sits between payment and execution.
- **Crypto exchanges:** Bitkub, Coins.co.th, Upbit TH. Adjacent to payment layer.
- **Cross-border linkages:** PromptPay-PayNow, PromptPay-DuitNow, regional platform dependencies.
- **Social ↔ messaging cross-referral:** Was in an earlier version, removed. Could restore as lateral.
- **Social → news content sharing:** Was in an earlier version, removed. Could restore as lateral.
