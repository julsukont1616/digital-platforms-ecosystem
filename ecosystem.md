# Thailand Digital Platform Ecosystem

Last reviewed: 2026-04-01 (Asia/Bangkok)

Scope: This note combines ETDA's Digital Platform Service (DPS) taxonomy with the broader Thailand ecosystem research used for the end-to-end platform map. It is a factual ecosystem summary, not legal advice.

## Key clarification on "16 types"

- I checked official ETDA materials on 2026-04-01.
- ETDA's official DPS workshop material explicitly lists 15 top-level digital platform service types, not 16. [S1]
- ETDA's later 2025-2026 materials add risk tiers and service-specific obligations, but I did not find an official ETDA source that currently defines a 16th top-level type. [S3] [S5]
- Inference: the "16" figure is likely a mix-up between ETDA's 15 top-level service types and either subtypes such as ride sharing, social commerce, and communication commerce, or separate DPS risk buckets under sections 8, 16, and 18. [S1] [S3]

## 1. ETDA's official 15 digital platform service types

1. Online marketplace: The transaction layer for third-party goods and services. It connects business users to consumers and relies on payments, merchant onboarding, fraud control, logistics, complaints, and notice-and-takedown. ETDA moved to extra marketplace-specific obligations for 21 platforms effective 2025-12-31. [S1] [S5]
2. Sharing economy platform: The real-world coordination layer for ride sharing, car sharing, knowledge sharing, labor sharing, and space sharing. It converts platform matching into physical service delivery and therefore depends heavily on identity, insurance, transport regulation, maps, payments, and dispatch. ETDA's ride-sharing obligations were extended to take effect on 2026-03-31. [S1] [S5]
3. Online communication: General communication and commerce-enabled communication, including chat-based merchant and customer interaction. This is a discovery, CRM, support, and conversion channel rather than only a messaging utility. [S1]
4. Social media: The attention, creator, and social-commerce layer. It drives audience formation, discovery, ads, live commerce, and repeat engagement. [S1]
5. Advertising service: The monetization and traffic-allocation layer. It connects advertisers and agencies to user attention through ad networks, exchanges, targeting, and measurement. [S1]
6. Audio-visual and music sharing: The streaming and content distribution layer. It monetizes through advertising, subscription, sponsorship, and creator economics. [S1]
7. Searching tools: The intent-capture and ranking layer. Search is especially important under DPS because ETDA's section 16 rules explicitly address ranking, recommendation, and complaint handling. [S1] [S6]
8. News aggregator: The traffic-routing and information-distribution layer for news content. It affects audience flow, referral traffic, and ad economics. [S1]
9. Maps: The location and route layer. Maps connect users to stores, drivers, couriers, restaurants, and physical destinations. [S1]
10. Web browsers: The access client for web-based services. Browsers influence discoverability, defaults, standards, and user reach to the wider web. [S1]
11. Virtual assistants: The voice and task-mediation layer. These services stand between the user and downstream apps, content, and devices. [S1]
12. Operating system: The software environment that governs device behavior, permissions, default services, and much of app access. In ecosystem terms, OS providers sit at a powerful control point above apps and below users. [S1]
13. Hosting service: The backend storage and serving layer for websites and applications. Hosting is not consumer-facing in the same way as marketplaces or social media, but many other platform types depend on it. [S1]
14. Cloud service: The shared compute, storage, analytics, and AI layer that powers modern platform operations. It is now part of the regulated platform ecosystem, not merely a neutral technical utility. [S1]
15. Internet service provider: The base connectivity layer. ISPs and telecom operators make all higher platform activity possible and shape quality, reach, resilience, and cost. [S1] [S13]

## 2. What ETDA's taxonomy means structurally

ETDA's taxonomy is broader than "e-commerce." The 15 types cover the full stack:

- Demand capture and discovery: online communication, social media, advertising, searching tools, news aggregators, maps.
- Transaction and service execution: online marketplace, sharing economy.
- Software gateway and control: web browsers, virtual assistants, operating systems.
- Technical infrastructure: hosting, cloud, ISPs.
- Media and content distribution: audio-visual and music sharing.

This matters because market power in Thailand does not sit only in marketplace checkout. It also sits in discovery, ranking, messaging, app access, cloud infrastructure, and payment interoperability. [S1] [S6] [S9]

## 3. DPS regulatory model in practice

ETDA's DPS regime is risk-based, not one-size-fits-all.

1. Small or low-risk platforms and certain single-owner e-services: ETDA's notification on "brief details" applies to low-scale services with annual Thailand revenue not exceeding THB 1.8 million for natural persons or THB 50 million for juristic persons, and not more than 5,000 domestic monthly users on average. Foreign operators serving Thai users must also provide a Thailand point of contact. [S2]
2. General platforms: ETDA's 2025 workshop summary says section 8 paragraph 1 platforms must submit general information, full annual reporting, mitigation/remedy measures, and business cessation notice when relevant. [S3]
3. High-risk platforms under section 16: ETDA states that commercial platforms and search engines have extra duties, especially around public terms and conditions. [S3] [S6]
4. Very large platforms under section 18(1): ETDA says they face extra duties such as risk assessment, risk management, system security, crisis management, compliance personnel, and external assessment. [S3]
5. High-risk-by-service and sector-specific platforms under sections 18(2) and 18(3): ETDA works with sector regulators to impose extra obligations where the service has stronger public-risk implications, such as online marketplaces and ride sharing. [S3] [S5]

Current status points:

- The DPS brief-details notification took effect on 2023-08-21. [S2]
- The terms-and-conditions notification took effect on 2024-01-03. [S6]
- ETDA reported 1,920 notified platform services as of 2025-08-01. [S4]
- ETDA's January 21, 2026 update shows DPS moving further into co-regulation with agencies such as the FDA, TISI, DLT, BOT, OIC, and the Trade Competition Commission Office, depending on service type. [S5]

## 4. Whole ecosystem, end to end

### 4.1 Core nodes

| Node | Functional role in the ecosystem | Why it matters |
| --- | --- | --- |
| Consumers and citizens | Demand, attention, identity, payment initiation, complaints, ratings, repeat usage | Every flow begins with user need and ends with user satisfaction, complaint, or retention |
| Merchants, SMEs, creators, drivers, couriers, service providers | Supply, catalog, labor, content, inventory, delivery capacity | They are the economic counterparties that platforms intermediate |
| Platform operators | Matching, ranking, recommendation, traffic allocation, checkout orchestration, moderation, policy enforcement | They sit between demand and supply and shape conversion economics |
| Advertisers, agencies, app publishers, enterprises | Demand generation, software publishing, campaign spend, business tooling | They finance discovery and provide many of the apps and services users consume |
| Banks, acquirers, e-money issuers, payment operators | Settlement accounts, issuance, acquiring, wallet balances, merchant onboarding | They carry the balance-sheet and regulated money side of the ecosystem |
| BOT and NITMX public payment rails | PromptPay, Thai QR, cross-border payment connectivity, PromptBiz | They make interoperable payments possible across banks, non-banks, merchants, and government [S7] [S8] [S9] [S10] |
| Logistics and last-mile operators | Pickup, sorting, linehaul, COD, returns, rider dispatch, parcel completion | They convert digital orders into physical outcomes [S19] |
| Cloud, hosting, and AI providers | Compute, storage, content delivery, model serving, analytics, security tooling | They host the operational and data backbone of platforms [S17] [S18] |
| Telecom and ISP operators | Mobile and fixed connectivity, service quality, reach, cybersecurity baseline | They are the access substrate for every other layer [S1] [S13] |
| DGA and GDX | Government data exchange and one-stop digital public service enablement | They connect state data and state services rather than private commerce directly [S11] |
| NDID and digital identity providers | Consent-based identity verification and authentication data exchange | They support trusted onboarding, KYC, and authentication across institutions [S12] |
| ETDA and the Electronic Transactions Commission | DPS rulemaking, notification, transparency, complaint architecture, co-regulation | They govern platform behavior and platform disclosure rather than run platforms directly [S1] [S2] [S3] [S5] [S6] |
| PDPC and PDPA compliance functions | Consent, records of processing, breach handling, data subject rights, data governance | They constrain how platforms collect, share, profile, and reuse data [S20] |
| NBTC | Telecom licensing, complaint handling, cybersecurity and personal-data-protection plan requirements for telecom licensees | It governs the connectivity layer that digital platforms depend on [S13] |
| Sector regulators | FDA, TISI, DLT, OIC, competition authorities, and others depending on service type | They add service-specific obligations where platform activity intersects regulated sectors [S5] |

Note: For PDPA operations, the official GPPC platform materials show the government compliance stack around consent management, data breach notification, records of processing, and data subject access requests. Those are practical signals of what data governance functions institutions in this ecosystem must maintain. [S20]

### 4.2 End-to-end relationship map

1. Rule-setting and public rails: ETDA, BOT, PDPC, NBTC, DGA, and sector regulators define the operating boundary. ETDA covers platform transparency and risk-based duties; BOT covers payment-system direction and shared rails; PDPC shapes lawful data handling; NBTC governs telecom access; DGA runs government exchange infrastructure; sector regulators add service-specific rules. [S3] [S5] [S9] [S11] [S13] [S20]
2. Access: consumers, merchants, creators, and service operators come online through devices, operating systems, browsers, apps, and telecom/ISP networks. Without connectivity and device software, no higher platform service can be used. [S1] [S13]
3. Discovery: search, maps, social media, online communication, and ad services capture intent and attention. This is where a user first finds a merchant, a ride, a video, an app, or a government service. Ranking and recommendation are economically decisive here. [S1] [S6]
4. Interaction and matching: platform operators connect users to merchants, content, drivers, couriers, or service providers. This is the marketplace, ride-hailing, social-commerce, content, or app-service layer where attention becomes an order, booking, stream, or workflow. [S1]
5. Trust and onboarding: before transactions scale, platforms need merchant identity, user identity, moderation, risk controls, dispute processes, and data governance. Identity and authentication may involve banks, NDID-related flows, internal KYC/KYB, or government data connections depending on the use case. [S6] [S11] [S12]
6. Money movement: checkout, transfers, QR payment, cards, e-money, and B2B trade documents move through banks and shared rails. PromptPay is the mass retail transfer and payment rail; PromptBiz adds cross-bank trade and payment data exchange for business processes. [S7] [S8] [S9] [S10]
7. Physical execution: logistics carriers, riders, warehouses, and COD networks fulfill the real-world part of the service. For e-commerce, this means parcel movement and returns. For ride-hailing and local services, it means dispatch and completed service delivery. [S5] [S19]
8. Outcome and feedback: settlement pays merchants, creators, couriers, and drivers; taxes and fees flow to the public sector; user behavior becomes data for retention, ad targeting, fraud scoring, underwriting, and AI models; complaints and audit trails feed governance and supervision. [S6] [S7] [S8] [S10] [S20]

### 4.3 The five flows that run at the same time

- Discovery flow: user need -> search/maps/social/messaging/ad systems -> platform surface -> seller or service.
- Money flow: user payment intent -> bank or wallet -> PromptPay / Thai QR / cards / acquiring -> merchant or platform settlement -> payouts to sellers, creators, drivers, and couriers. [S7] [S8] [S9]
- Physical flow: order or booking -> logistics network / rider fleet / service operator -> customer delivery or completed ride/service. [S5] [S19]
- Data and AI flow: behavior, transactions, reviews, and service events -> analytics, ranking, ad targeting, recommendations, fraud models, credit models, and AI systems -> back into discovery and operations. Section 16 transparency rules make this flow more visible. [S6] [S17] [S18]
- Governance flow: regulator rules -> platform disclosures and controls -> user complaints, moderation, notice-and-takedown, audits, enforcement, and policy updates. [S3] [S5] [S6]

## 5. Relationship notes by node

| Node | Receives from | Sends to | Relationship note |
| --- | --- | --- | --- |
| ETDA / ETC | Platform notifications, annual reports, T&C reports, complaints signals, sector feedback | DPS rules, service-specific obligations, self-regulation guidance, notified-status verification pathways | ETDA is the platform-governance coordinator. It is not the payment rail or the privacy authority; it is the DPS regulator. [S2] [S3] [S4] [S5] [S6] |
| BOT / NITMX | Payment data, bank and non-bank participation, payment-system needs from business and government | PromptPay, Thai QR, cross-border QR, PromptBiz direction, payment-system policy | BOT is the public payments backbone. Platforms build on top of it instead of replacing it. [S7] [S8] [S9] [S10] |
| PDPC / PDPA functions | Personal-data processing records, consent events, breach events, access requests | Privacy obligations, data-rights enforcement, governance expectations | PDPA is a horizontal constraint on platform data use, ad targeting, personalization, and AI training pipelines. [S20] |
| NBTC | Telecom licensees, complaints, service-quality and cybersecurity obligations | Licensing, complaint rules, cybersecurity and personal-data-protection plan requirements | NBTC shapes the connectivity base that every digital platform depends on. [S13] |
| DGA / GDX / Tang Rat | Government agency data, public service workflows, citizen usage | Data exchange APIs, one-stop public service channels, public verification routes | DGA is the state's digital exchange and service-delivery node. It is adjacent to private platforms, not a substitute for them. [S4] [S11] |
| NDID and digital ID providers | Identity assertions from participating institutions, customer consent | Trusted verification and authentication results to banks and service providers | NDID reduces onboarding friction for regulated use cases and supports trust-heavy services. [S12] |
| Consumers / citizens | Connectivity, platform interfaces, ads, recommendations, public services | Attention, money, identity data, reviews, complaints, behavioral data | Consumers are both customers and data subjects. Their actions create both revenue and regulatory duties. [S6] [S8] [S20] |
| Merchants / SMEs / creators / drivers / couriers | Demand from users, platform tools, ad traffic, payouts, logistics services | Goods, services, labor, content, inventory, ad budgets, tax and fee obligations | They are the supply side that platforms aggregate and discipline through ranking, fees, policy, and fulfillment terms. [S5] [S6] [S10] [S19] |
| Platform operators | User attention, merchant supply, public rules, cloud capacity, payment and identity integrations | Matching, ranking, checkout, moderation, complaint handling, payouts orchestration, audit trails | Platforms sit at the center because they transform raw demand and supply into managed transactions. [S3] [S5] [S6] |
| Banks / acquirers / e-money | User deposits, merchant onboarding, regulatory supervision, payment requests from platforms | Account issuance, acquiring, settlement, wallet services, financing, payout rails | They make platform commerce bankable and settleable. [S7] [S8] [S10] |
| Logistics operators | Orders from merchants and platforms, parcel data, pickup requests | Delivery, COD collection, tracking, returns, service-point access | Logistics determines whether digital conversion becomes a real-world outcome. [S19] |
| Cloud / hosting / AI providers | Application workloads, data, model demand from platforms and enterprises | Compute, storage, security, AI services, data residency options | They increasingly affect compliance, latency, resilience, and AI capability. [S17] [S18] |
| Advertisers / agencies / enterprises | User behavior signals, platform inventory, campaign tools | Ad spend, traffic, app installs, CRM programs, measurement demand | They fund much of the discovery layer and shape what users see first. [S14] [S16] |
| Sector regulators | Platform risk signals, complaints, product and service issues | Service-specific rules and enforcement to ETDA, platforms, and operators | Co-regulation is now part of the Thai model, especially for product standards, ride sharing, fraud, and competition. [S5] |

## 6. Current scale indicators that shape the ecosystem

| Indicator | Latest figure found | Why it matters |
| --- | --- | --- |
| PromptPay registered IDs | 92.2 million, January 2026 | Near-universal retail payment reach in Thailand [S7] |
| PromptPay transactions per day | 79.9 million, January 2026 | Shows how deeply payments are embedded in daily platform behavior [S7] |
| e-Money accounts | 112.3 million, January 2026 | Wallets remain a major part of digital payment behavior [S7] |
| Internet and mobile banking accounts | 181.8 million, January 2026 | The banking layer is deeply digitized [S7] |
| ETDA-notified platform services | 1,920 services as of 2025-08-01 | The regulated platform field is broad, not a handful of famous apps [S4] |
| DGA "Tang Rat" accounts | More than 42 million accounts as of 2025-08-04 article | Public digital services are now large enough to be part of the same ecosystem logic [S4] |
| LINE users in Thailand | Over 56 million active users in Thailand | Messaging and CRM are central to Thai digital demand capture [S14] |
| TikTok users in Thailand | More than 50 million monthly users | Social discovery and video commerce are central to the ecosystem [S15] [S16] |
| TikTok merchants in Thailand | More than 3 million merchants | Social commerce is no longer marginal [S15] |
| Google Cloud Bangkok region | Launched 2026-01-21 | Local cloud and AI infrastructure changes latency, compliance, and data-residency options [S18] |

## 7. Representative ecosystem reading by layer

1. Demand layer: consumers, tourists, citizens, merchants, SMEs, creators, drivers, couriers, enterprises, and agencies enter with a need to buy, sell, reach, move, pay, verify, or comply.
2. Access layer: telecom networks, ISPs, devices, browsers, and operating systems create the usable surface of the digital economy.
3. Discovery layer: search, maps, social media, online communication, and advertising services decide what gets seen and by whom.
4. Execution layer: marketplaces, sharing-economy apps, streaming apps, and SaaS/public-service apps convert attention into transactions or recurring usage.
5. Trust layer: identity, authentication, moderation, fraud controls, reviews, complaint systems, and T&C disclosures make platform activity governable and scalable.
6. Payment layer: PromptPay, Thai QR, cards, e-money, banks, acquirers, and PromptBiz convert intent into settled money.
7. Fulfillment layer: parcel networks, service points, COD systems, rider fleets, and dispatch systems turn platform orders into real outcomes.
8. Data and AI layer: analytics, recommendation engines, ad systems, risk scoring, and model infrastructure continuously optimize the rest of the stack.
9. Governance layer: ETDA, BOT, PDPC, NBTC, DGA, and sector regulators shape every other layer through rules, standards, reporting, and enforcement.

## 8. Strategic conclusions

1. Thailand's digital platform ecosystem is a multi-layer system, not a marketplace chart. Discovery, communication, identity, payment rails, cloud, and logistics are as important as storefronts.
2. ETDA's DPS regime should be read as a full-stack platform governance model. It explicitly reaches beyond commerce into search, social, browsers, operating systems, hosting, cloud, and ISPs. [S1]
3. Public rails matter. PromptPay and PromptBiz are shared infrastructure for private platforms, while GDX and Tang Rat pull public services into the same digital behavior loop. [S4] [S8] [S10] [S11]
4. Governance is moving from registration to operational control. The current Thai model is increasingly about risk-based duties, ranking transparency, complaint handling, notice-and-takedown, seller verification, and sector co-regulation. [S3] [S5] [S6]
5. The same platform action creates multiple consequences at once: a money event, a logistics event, a data event, and a governance event. That is the correct way to read the ecosystem end to end.

## 9. Report-grade value-chain matrix

The table below is the strict value-chain view that I would use to build a board-level or policy report.

| Value-chain stage | Primary actors | What happens | Main value created | Main value captured | Main data created | Main control points |
| --- | --- | --- | --- | --- | --- | --- |
| 0. Governance and common rails | ETDA, BOT, PDPC, NBTC, DGA, sector regulators, NDID, NITMX | Rules, standards, public infrastructure, identity and payment interoperability are defined | Trust, interoperability, auditability, lower coordination cost | Public policy outcomes, lower system-wide friction, safer market formation | Notification data, payment statistics, compliance records, complaint data | DPS, PDPA, telecom licensing, payment-system policy, government data exchange rules [S2] [S3] [S5] [S7] [S9] [S11] [S13] [S20] |
| 1. Access and onboarding | ISPs, telecoms, device OS providers, browsers, app stores, banks, identity providers | Users and businesses come online, install apps, create accounts, verify identity, link payment sources | Reach, access, account portability, user readiness | Subscription revenue, app-distribution control, account stickiness | Device IDs, login data, KYC/KYB records, consent records | NBTC telecom obligations, PDPA consent and breach handling, digital identity rules [S13] [S20] |
| 2. Discovery and demand formation | Search, maps, social media, online communication, ad-tech, creators, agencies | User intent is captured and demand is routed to merchants, apps, services, or content | Attention, traffic, app installs, lead generation, audience building | Advertising spend, promotion spend, creator fees, sponsored ranking value | Query data, audience segments, clickstream, location data, ad attribution | ETDA ranking/recommendation transparency for applicable platforms, PDPA constraints on profiling [S6] [S14] [S15] [S16] [S32] [S33] [S34] |
| 3. Conversion and order capture | Marketplaces, social-commerce operators, on-demand apps, merchant CRM tools, POS and merchant systems | Attention becomes cart, booking, order, booking dispatch, or service request | Matching efficiency, checkout readiness, seller productivity, order density | Transaction fees, SaaS/POS fees, merchant tool fees, ad upsell | Basket data, inventory, menu/catalog data, merchant response data, review intent | Platform T&C, merchant identity checks, complaint systems, seller verification, service rules [S6] [S22] [S24] [S27] [S30] |
| 4. Payment authorization and settlement | Banks, acquirers, wallet issuers, PromptPay, Thai QR, PromptBiz, merchant acquiring apps | Money is authorized, transferred, reconciled, and settled | Lower payment friction, faster cash conversion, broader merchant acceptance | Transaction-based fees, wallet economics, acquiring fees, financing cross-sell | Payment instructions, settlement records, payment timestamps, e-receipts, financing signals | BOT payment rules, bank supervision, security standards, reconciliation obligations [S7] [S8] [S9] [S10] [S23] [S29] [S30] |
| 5. Fulfillment and service execution | SPX, Lazada Logistics, rider fleets, drivers, couriers, warehouses, merchant operations teams | Orders are packed, routed, delivered, or served in person | Physical completion, service reliability, delivery speed, customer experience | Logistics fees, service fees, courier economics, premium delivery economics | Tracking events, route data, proof-of-delivery, returns, support tickets | Product safety, transport rules, rider/driver regulation, operational SLAs [S5] [S19] [S21] [S25] [S28] |
| 6. Post-transaction retention and expansion | Platforms, ad systems, CRM systems, lenders, insurers, loyalty programs, public complaint channels | Behavior is converted into repeat demand, financing, support, refunds, ratings, or enforcement | Retention, lifetime value, credit expansion, fraud reduction, policy learning | Subscription, membership, ad re-spend, financial products, upsell revenue | Cohort data, RFM data, repayment records, complaint and remedy records | PDPA, ETDA complaint-handling and T&C disclosure, lending/risk controls [S3] [S6] [S10] [S22] [S23] [S30] [S31] |
| 7. Shared compute and AI backbone | Cloud, hosting, AI platforms, developer tooling providers | Ranking, recommendation, analytics, generative AI, risk scoring, and system operations are run at scale | Speed, resilience, personalization, automation, lower marginal operating cost | Compute/storage/network revenue, AI service revenue, managed-service revenue | Model-training data, logs, embeddings, operational telemetry | Data residency, security controls, PDPA-aligned processing, sector-specific compliance [S17] [S18] |

## 10. The five matrices that raise confidence from "ecosystem map" to "value-chain map"

### 10.1 Node inventory by ETDA type

This is an analytical operator map. Where a company is directly supported by an official source, I cite it. Where an example is a market-structure inference, I say so explicitly.

| ETDA type | Function in value chain | Thai-market operator examples | Confidence note |
| --- | --- | --- | --- |
| Online marketplace | Multi-seller product discovery, cart, checkout, seller tools, dispute handling, logistics orchestration | Shopee, Lazada, TikTok Shop [S25] [S26] [S27] [S35] [S36] | High confidence |
| Sharing economy platform | Dispatch and matching for transport, messenger, delivery, and other shared-capacity services | Grab, LINE MAN RIDE, related rider/driver networks [S5] [S21] [S22] [S24] | High confidence |
| Online communication | Merchant-customer chat, CRM, campaigns, support, lead generation | LINE Official Account and related LINE business stack [S14] [S32] [S33] [S34] | High confidence |
| Social media | Audience formation, creator economy, live commerce, cultural discovery, ad inventory | TikTok, LINE ecosystem social surfaces; Meta/Instagram/Facebook are also important in practice but not separately sourced in this note | Medium confidence for the broader set; high for TikTok/LINE [S15] [S16] [S32] |
| Advertising service | Paid discovery, audience targeting, app installs, retargeting, merchant promotion | LINE Ads / Gain Friends Ads, TikTok Shop Ads, Shopee ad products, GrabAds, TrueMoney Ad Solution [S21] [S25] [S31] [S32] [S36] | High confidence on role, mixed confidence on full vendor list |
| Audio-visual and music sharing | Attention monetization, creator distribution, subscription and ad inventory | TikTok, YouTube and streaming apps are the practical layer in Thailand; TikTok is directly sourced here [S15] [S16] | Medium confidence on full vendor list |
| Searching tools | Query capture, ranking, referral traffic, ad load, app and store discovery | Search engines active in Thailand; in practice the current ecosystem map centers Google Search as the main example. This is an inference from market structure rather than a separate market-share study. | Medium confidence |
| News aggregator | Information distribution and traffic routing | LINE TODAY and other aggregators exist in practice; this note does not separately source a Thai market-share study | Medium confidence |
| Maps | Geolocation, route optimization, local search, dispatch accuracy | GrabMaps is directly evidenced; global mapping providers also matter in practice [S27] | Medium confidence |
| Web browsers | User access to web services, default search and web control point | Major global browsers active in Thailand; examples are analytical rather than specifically sourced here | Medium confidence |
| Virtual assistants | Voice/task routing into downstream services and devices | Global assistants active in Thailand; not separately sourced in this note | Low-to-medium confidence |
| Operating systems | Device permissions, defaults, app distribution leverage, payment and identity integration | Android and iOS dominate the practical access layer; this is an ecosystem inference rather than a cited market-share claim | Medium confidence |
| Hosting service | Application hosting, storage, delivery, reliability | Hosting providers, CDNs, and managed infrastructure are part of the backend layer; not individually inventoried here | Medium confidence |
| Cloud service | Compute, storage, data, AI, developer stack | Google Cloud Bangkok region; AWS and Azure are also active in practice but only Google is directly sourced here [S17] [S18] | High confidence on the layer, medium on the full operator set |
| Internet service provider | Mobile/fixed internet, traffic carriage, baseline service quality | Mobile and broadband telecom operators under NBTC supervision [S13] | High confidence on the layer |

Note on ad services row: the exact operator list is split across multiple platform stacks. For report use, it is more accurate to think of advertising as embedded inside social, marketplace, and super-app ecosystems rather than as a standalone sector. Shopee ad revenue, TikTok Shop Ads, LINE Ads, GrabAds, and TrueMoney Ad Solution all point in that direction. [S21] [S25] [S31] [S32] [S36]

### 10.2 Marketplace and social-commerce swimlane

| Step | Buyer side | Platform side | Seller side | Money side | Fulfillment side | Governance side |
| --- | --- | --- | --- | --- | --- | --- |
| 1. Discovery | User sees search results, social content, creator affiliate content, campaign traffic | Platform ranks listings, serves ads, or routes traffic via creator/affiliate surfaces | Seller funds ads, optimizes listings, joins campaigns | No settlement yet | None yet | Ranking, ad labeling, and recommendation logic may trigger section 16 transparency duties [S6] [S25] [S32] [S36] |
| 2. Consideration | User opens product page, reviews, chats, or watches live content | Platform provides PDP, recommendation, trust and review surfaces | Seller provides catalog, stock, images, prices, response handling | No settlement yet | Serviceability and shipping promise are calculated | Review handling, T&C, counterfeit/safety obligations, product governance start to matter [S5] [S6] |
| 3. Order capture | User adds to cart and checks out | Platform records order and allocates seller/warehouse/logistics path | Seller confirms stock or uses managed fulfillment | Buyer pays through bank/wallet/card/QR; platform or partner reconciles | Pickup/packing order is created | Payment records, identity, address, and consent handling become binding [S7] [S8] [S25] [S27] [S30] |
| 4. Settlement split | User waits for delivery | Platform allocates economics among transaction fee, ads, subsidies, logistics, and service fees | Seller receives net proceeds after fee deductions | Marketplace revenue is mainly transaction-based fees and ads; logistics sits in value-added services for Shopee [S25] | Carrier/rider gets job and fee | Complaint, refund, and chargeback logic become important [S6] [S25] |
| 5. Delivery and support | User receives parcel or initiates return | Platform tracks SLA, support, and post-purchase communications | Seller handles quality issues, returns, stock reconciliation | Refunds or COD reconciliations may occur | SPX or other network executes delivery / return [S19] [S25] [S27] [S28] | Product-standard, notice-and-takedown, and redress obligations apply [S5] [S6] |
| 6. Retention loop | User reviews, reorders, follows account or creator | Platform reuses behavior for ranking, retargeting, membership, and personalization | Seller reinvests in ads/promotions and may adopt more tools | Financing or wallet products may be cross-sold | Delivery history improves ETA and routing | PDPA, profiling limits, and complaint records remain active [S6] [S20] [S25] [S32] [S36] |

### 10.3 On-demand mobility, food, and local-services swimlane

| Step | Consumer | Platform | Merchant / driver / rider | Payment | Operations | Governance |
| --- | --- | --- | --- | --- | --- | --- |
| 1. Demand creation | User opens app for food, ride, mart, or express | Platform exposes menus, maps, price, ETA, promo | Merchant or driver is made discoverable | Payment method pre-linked or selected | Maps, availability, dispatch logic activate | Service quality, identity, route safety, and local law matter [S5] [S21] [S24] |
| 2. Matching | User confirms order or ride | Platform assigns rider/driver/merchant and optimizes route | Merchant accepts order; rider/driver receives job | Fare/food price is authorized or reserved | Dispatch and ETA are updated live | Worker onboarding, vehicle legality, insurance, and complaint systems matter [S5] [S21] [S22] [S24] |
| 3. Service execution | User waits for food or ride | Platform tracks status, support, and incentives | Merchant prepares order; rider/driver executes delivery or trip | Cashless option reduces physical cash handling [S21] [S23] | Pickup, trip tracking, drop-off, proof of completion | Safety tooling, public-risk management, and rider/driver regulation apply [S5] [S21] [S24] |
| 4. Settlement | User receives service | Platform computes platform fee, delivery fee, incentives, and net payouts | Merchant or driver receives net payout; may access working capital or benefits | Grab states it collects from customers and pays merchants within 1-2 business days after fees; credit can be offered to merchants [S22] | Support and refund handling continue | Complaint, suspension, and dispute procedures must exist [S6] [S22] |
| 5. Retention / growth | User repeats if service quality is good | Platform uses ratings, cohorts, and targeting to improve retention | Merchant invests in promos/ads; driver stays if economics work | Wallet, financing, insurance, and loyalty deepen lock-in | Repeat usage improves dispatch density | ETDA, sector regulators, and PDPA remain relevant [S5] [S6] [S21] [S22] [S24] |

### 10.4 Content, software, and public-service swimlane

| Step | User | Platform | Institution / publisher | Money | Data | Governance |
| --- | --- | --- | --- | --- | --- | --- |
| Discovery | User arrives via search/social/message/app store | Platform serves content or software listing | Publisher supplies content or service | Ad impression or subscription lead may be generated | Query, watch, install, click data | Ranking and ad disclosure matter [S6] |
| Consumption | User streams, subscribes, installs, or completes service workflow | Platform authenticates and delivers experience | Publisher / agency / public body fulfills digital service | Revenue may be ad, subscription, IAP, or public budget-funded | Engagement and completion data are created | PDPA, T&C, and service continuity matter [S6] [S20] |
| Post-use | User reviews, renews, or returns | Platform retargets or personalizes | Publisher refines content or service | Renewals or repeat use create LTV | Behavioral and model-training signals accumulate | Complaint handling and data rights remain relevant [S6] [S20] |

## 11. Monetization matrix

This is the clearest way to understand where value is actually captured.

| Actor class | Main monetization levers | Evidence in this ecosystem |
| --- | --- | --- |
| Marketplaces | Transaction-based fees, advertising, logistics value-added services, memberships, seller tools | Sea states Shopee core marketplace revenue mainly consists of transaction-based fees and advertising revenues, while value-added services mainly consist of logistics services. It also highlights continued investment in logistics, VIP membership, and content ecosystem growth. [S25] |
| Marketplaces with export angle | Cross-border seller acquisition and export enablement | Shopee's SIP with DITP positions the platform as an export gateway for Thai entrepreneurs. [S26] |
| Lazada-style marketplace stack | Secure payments, distribution network, marketing analytics, branded mall participation | Lazada explicitly frames Marketplace as seller access to customers through payment, customer care, distribution, and marketing analytics; LazMall adds authenticity and fast delivery positioning. [S27] |
| On-demand super-apps | Take rates from transactions, delivery/service fees, merchant promotion, ad products, financial services | Grab combines ride, food, mart, express, pay, ads, maps, merchant finance, and business services in one platform stack. [S21] [S22] [S23] |
| Merchant-enablement platforms | POS/software subscriptions, merchant digital solutions, payment integration, vertical SaaS expansion | LINE MAN Wongnai positions Merchant Digital Solutions as one of its three core businesses and has integrated FoodStory and later JERA Cloud into this strategy. [S24] |
| Social / messaging business platforms | Paid reach, follower acquisition, CRM tooling, data resource activation | LINE Gain Friends Ads is an auction product for growing audiences; LINE Official Account provides broadcast, rich content, coupons, loyalty cards, and chat tags; Business Manager links data resources across LINE OA and LINE Ads. [S32] [S33] [S34] |
| Discovery-commerce platforms | Affiliate, ads, live commerce, brand campaigns, mall programs | TikTok Shop Thailand highlights creator affiliate, ads, mega sales/brand campaigns, mall, and live as core growth tools. [S15] [S35] [S36] |
| Wallets and merchant finance providers | Wallet transactions, merchant acceptance, ad-payment products, payouts, SME finance | TrueMoney for Business includes merchant acceptance, payouts, ads solutions, and a virtual SME card for ad buyers; TrueMoney also supports wallet, bank, and card-funded merchant payments. [S30] [S31] |
| Merchant-acquiring bank apps | QR acceptance, account-linked payment, reporting, MDR on some instruments, merchant tool upsell | K PLUS SHOP is an acquiring workflow for QR acceptance, transaction reporting, and QR-based merchant acceptance. [S29] |
| Public payment rails | Not primarily monetized like private platforms; value is systemic efficiency and interoperability | BOT describes PromptPay and PromptBiz as infrastructure that lowers cost and improves business/government processes. [S8] [S10] |
| Logistics networks | Delivery fees, fulfillment services, premium speed options, enterprise logistics contracts | SPX and Lazada Logistics both present end-to-end seller logistics as a product in itself. [S19] [S28] |
| Cloud / AI providers | Compute, storage, security, AI/ML, data residency and compliance value | Google's Thailand investment and Bangkok cloud region are positioned as enabling AI, low latency, data residency, and compliance-sensitive workloads. [S17] [S18] |

## 12. Money-flow matrix by use case

| Use case | Payer | Interim holder / processing layer | Final economic recipients | Typical fee pools |
| --- | --- | --- | --- | --- |
| Marketplace order | Consumer | Bank / wallet / card / QR -> marketplace and payment partners | Merchant, logistics provider, platform, sometimes affiliate/creator | Transaction fee, ad fee, logistics fee, payment fee, promotion funding [S7] [S8] [S25] [S27] [S30] |
| Social commerce order | Consumer | TikTok Shop / social-commerce checkout stack plus bank/wallet rails | Merchant, creator affiliate, platform, logistics provider | Affiliate payout, ad fee, platform fee, logistics fee [S15] [S35] [S36] |
| Ride-hailing trip | Consumer | Super-app payment stack plus bank/wallet/card | Driver, platform, acquiring/payment counterparties | Service fee, payment fee, incentive funding [S21] [S23] |
| Food delivery order | Consumer | Super-app payment stack | Restaurant, rider, platform, payment counterparties | Commission/take rate, delivery fee, promo spend, ad spend, payment fee [S21] [S22] [S23] |
| Business trade flow | Buyer business | Bank + PromptBiz trade and payment data transmission | Seller business, lenders, tax/e-document counterparties | Bank service fee where applicable, software integration cost, financing spread [S10] |
| Wallet-funded online advertising | MSME / ad buyer | Wallet / virtual card / ad platform billing layer | Ad platform, card network where relevant, wallet provider | Ad spend, payment-processing economics, FX if relevant [S31] |
| Public-service disbursement / collection | Government or citizen | PromptPay / bank / government service stack | Intended citizen, government agency, public institution | Low-friction infrastructure cost rather than marketplace take rate [S8] [S11] |

## 13. Data-flow and control-point matrix

| Data class | Primary collectors | Main uses | Highest-leverage actors | Main governance issues |
| --- | --- | --- | --- | --- |
| Identity and onboarding data | Banks, wallets, platforms, NDID-related participants, public-service systems | KYC/KYB, fraud prevention, account recovery, compliance | Banks, platform operators, digital identity providers | Consent, lawful basis, security, cross-system sharing [S12] [S20] |
| Discovery and attention data | Search, social, ads, messaging, creator ecosystems | Ranking, ad targeting, audience building, retargeting | Search/social/ad platforms | Profiling, ad disclosure, audience sharing, minors safeguards [S6] [S32] [S33] [S34] |
| Transaction data | Marketplaces, super-apps, banks, PromptPay, PromptBiz, wallets | Settlement, reconciliation, credit/risk models, merchant analytics | Platforms, banks, financial providers | Payment security, data minimization, financing use, audit trail [S7] [S8] [S10] [S23] |
| Location and route data | Maps, ride-hailing, food delivery, parcel networks | ETA, dispatch, routing, proof of service | On-demand platforms, maps, logistics providers | Safety, retention policies, sensitive movement patterns [S21] [S27] |
| Merchant operating data | POS, merchant apps, CRM, marketplace back office | Menu/inventory sync, campaign optimization, cash-flow management | Merchant-enablement platforms and marketplaces | Interoperability, switching costs, access rights, fair use of merchant data [S22] [S24] [S27] [S30] |
| Review and complaint data | Platforms, ETDA complaint channels, customer service tools | Trust signals, redress, ranking input, enforcement | Platform operators, ETDA | Defamation, moderation quality, redress process, transparency [S6] |
| AI and model data | Cloud, platforms, ad-tech, lending/risk teams | Recommendation, fraud detection, underwriting, service automation, GenAI operations | Platforms with large first-party data and cloud/AI providers | Explainability, training-data governance, privacy, bias, security [S17] [S18] [S20] [S24] [S25] |

Interpretation:

- The most powerful private control points are discovery, identity, payment orchestration, and merchant operating software.
- The most powerful public control points are DPS supervision, national payment rails, telecom access rules, and government data exchange.
- The most underappreciated control point is merchant tooling. Once POS, CRM, payouts, ads, and logistics are bundled together, the platform becomes infrastructure for the merchant, not just a sales channel. [S22] [S24] [S30]

## 14. Regulator-to-obligation matrix

| Institution | Regulated or influenced nodes | What it practically changes in the value chain |
| --- | --- | --- |
| ETDA / ETC | Digital platform operators across the 15 types, with extra duties for high-risk classes | Registration and annual reporting, T&C disclosure, ranking/recommendation transparency, complaint handling, seller/user treatment, service suspension/termination processes, co-regulation with sector agencies [S2] [S3] [S5] [S6] |
| BOT | Banks, non-bank payment providers, payment operators, business-process digitization participants | Shared rails such as PromptPay and PromptBiz, payment-system direction, e-payment adoption, interoperable QR and trade-data flows [S7] [S8] [S9] [S10] |
| PDPC / PDPA implementation stack | Any entity processing personal data | Consent, records of processing, breach notification, data subject access handling, limits on profiling and secondary use [S20] |
| NBTC | Telecom and internet access providers | Service availability, complaint handling, cybersecurity plans, personal-data-protection planning at the connectivity layer [S13] |
| DGA | Government agencies and public-service integrators | State data exchange, one-stop public services, digital document and registry interoperability [S11] |
| Sector regulators such as FDA, TISI, DLT, OIC, competition authorities | Specific platform verticals such as marketplaces, ride-sharing, insurance, and product categories | Product safety enforcement, service-specific checks, legal onboarding conditions, competition oversight, notice-and-takedown escalation [S5] |

## 15. What is still missing if the goal is a full institutional-grade report

Even after the expansion above, a fully institutional-grade report would still benefit from five more layers:

1. Company-by-company inventory for each ETDA type in Thailand, separated into Thai operators, regional operators, and global operators.
2. Empirical sizing by layer: GMV, orders, merchant counts, ad spend, wallet flows, parcel volume, and ride volume.
3. Regulatory mapping at the notice/article level for each major operator category.
4. Competitive structure analysis: concentration, switching costs, multi-homing, and dependency on foreign-controlled control points.
5. International comparison: how Thailand's DPS model differs from the EU DSA/DMA approach, Indonesia's platform rules, and Singapore's model.

## Sources

[S1] ETDA, "DPS workshop" article listing 15 platform types, 2023-10-17. https://www.etda.or.th/th/pr-news/DPS_workshop.aspx

[S2] ETDA translation, "Notification of the Electronic Transactions Commission Re: Characteristics of Digital Platform Services Required to Notify the Brief Details," effective 2023-08-21. https://www.etda.or.th/getattachment/Regulator/DigitalPlatform/law/01-Clean-ETC-Notification-Brief-Details-Platforms.pdf.aspx?lang=th-TH

[S3] ETDA, DPS workshop meeting summary, 2025-06-12, describing risk tiers under sections 8, 16, and 18 and self-regulation direction. https://www.etda.or.th/th/pr-news/ETDA-dps_workshop_meeting.aspx

[S4] ETDA, Tang Rat / notified-platform update, published 2025-08-04, reporting 1,920 notified services as of 2025-08-01 and more than 42 million Tang Rat accounts. https://www.etda.or.th/th/pr-news/DPS_Tang_Rath.aspx

[S5] ETDA, 2026 DPS press update, published 2026-01-21, covering marketplace obligations, ride-sharing measures, co-regulation, and sector-regulator coordination. https://www.etda.or.th/th/pr-news/dps_press.aspx

[S6] ETDA translation, "Notification of the Electronic Transactions Development Agency No. DPS. 4/2556 Re: Details on the Publication of Notice of Terms and Conditions of Digital Platform Services for Users' Knowledge," effective 2024-01-03. https://www.etda.or.th/getattachment/Regulator/DigitalPlatform/law/04-Clean-ETDA-Notification-DPS-4-2566-%28Notice-of-Terms-and-Conditions%29-%28ps%29.pdf.aspx?lang=th-TH

[S7] Bank of Thailand, Payment Data Indicators, January 2026. https://www.bot.or.th/content/dam/bot/documents/en/research-and-publications/reports/payment-report/payment-data-indicators/2026/202601_payment_indicator.pdf

[S8] Bank of Thailand, PromptPay. https://www.bot.or.th/en/financial-innovation/digital-finance/digital-payment/promptpay.html

[S9] Bank of Thailand, Payment Systems Policy. https://www.bot.or.th/en/our-roles/payment-systems/payment-systems-policy.html

[S10] Bank of Thailand, PromptBiz. https://www.bot.or.th/en/financial-innovation/digital-finance/digital-payment/promptbiz.html

[S11] DGA, Government Data Exchange (GDX), updated 2025-01-06. https://www.dga.or.th/our-services/digital-platform-services/dga-gdx/

[S12] NDID, license announcement, 2023-12-12. https://ndid.co.th/en/ndid-officially-obtains-a-business-license-for-digital-identity-verification-and-authentication-services/

[S13] NBTC, telecom licensee guide showing complaint, cybersecurity, and personal-data-protection obligations for telecom service providers. https://telecom-license.nbtc.go.th/getattachment/LicenseCompliance/guide_for_licensee/license_s/guide_license_s.pdf.aspx

[S14] LINE for Business Thailand, user-base and targeting context. https://lineforbusiness.com/th-en/success-stories/persona-targeting

[S15] TikTok Thailand, Thailand commitment and user / merchant scale. https://newsroom.tiktok.com/tiktok-supports-thailand-national-digital-economy-agenda?lang=th-TH

[S16] TikTok SEA update, published 2025-11-25, giving the 50 million Thailand monthly-user figure. https://newsroom.tiktok.com/tiktok-surpasses-460-million-users-in-southeast-asia-inks-partnership-with-vietnams-ministry-of-culture-sports-and-tourism?lang=en

[S17] Google Thailand, infrastructure investment and cloud/data-center plan, published 2024-09-30. https://blog.google/intl/th-th/company-news/technology/2024_09_ai-samart-thailand/

[S18] Google Cloud, Bangkok cloud region launch, published 2026-01-21. https://blog.google/intl/th-th/company-news/inside-google/google-cloud-region-in-bangkok/

[S19] SPX Express Thailand, logistics, pickup, drop-off, COD, and nationwide coverage. https://spx.co.th/en

[S20] GPPC / PDPC, official training page showing the operational PDPA compliance stack: records of processing, consent management, breach notification, and data subject access request management. https://gppc.pdpc.or.th/%E0%B8%AD%E0%B8%9A%E0%B8%A3%E0%B8%A1%E0%B8%9B%E0%B8%8F%E0%B8%B4%E0%B8%9A%E0%B8%B1%E0%B8%95%E0%B8%B4%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%95%E0%B8%B4%E0%B8%94%E0%B8%95%E0%B8%B1%E0%B9%89%E0%B8%87/

[S21] Grab Thailand homepage, showing the integrated consumer, driver, merchant, enterprise, payments, ads, maps, and financial-services stack. https://www.grab.com/th/

[S22] GrabMerchant Thailand, merchant onboarding, merchant app operations, settlement, and merchant working-capital references. https://www.grab.com/th/merchant/

[S23] GrabPay Thailand, cashless payment across Grab services. https://www.grab.com/th/en/consumer/finance/pay/

[S24] LINE MAN Wongnai "About Us", including its on-demand services, merchant digital solutions, financial services, POS integration, LINE Pay integration, and AI-driven strategy. https://lmwn.com/about-us/

[S25] Sea Q4 & FY 2025 earnings prepared remarks, covering Shopee monetization, transaction-based fees, advertising revenue, logistics services, SPX scale, content ecosystem, and Thailand grocery delivery use case. https://cdn.sea.com/investor/4Q2025/JcKns4LaJC8bxcQdJwXz/2026.03.03%20Sea%20Fourth%20Quarter%20and%20Full%20Year%202025%20Earnings%20Call%20Transcript.pdf

[S26] Sea / Shopee DITP partnership announcement, describing Shopee International Platform (SIP) as a gateway for Thai entrepreneurs into regional markets. https://www.sea.com/news/301

[S27] Lazada Group "About", describing the platform's technology, logistics, payments capabilities, LazMall, Marketplace, and cross-border business. https://group.lazada.com/en/about/

[S28] Lazada Group supply-chain and logistics page, describing Lazada Logistics as an end-to-end service for brands and sellers. https://group.lazada.com/en/careers/department/supply-chain-logistics/

[S29] KASIKORNBANK, K PLUS SHOP, showing merchant QR acceptance, transaction reporting, supported payment sources, and fee logic. https://www.kasikornbank.com/en/personal/Digital-banking/Pages/k-plus-shop.aspx

[S30] TrueMoney online merchant page, showing merchant acceptance, payouts, ads solutions, and online-payment integration routes. https://www.truemoney.com/online-merchant-walk-in/

[S31] TrueMoney for Business ad-payment announcement, including TrueMoney SME Card and direct-wallet payment for ad buyers. https://www.truemoney.com/a/news-announcement-47/

[S32] LINE Gain Friends Ads, official LINE OA advertising product. https://lineforbusiness.com/th/service/line-oa-features/gain-friends-ads

[S33] LINE Official Account update, covering broadcast, rich content, e-coupon, loyalty cards, chat tags, and API connectivity. https://lineforbusiness.com/th-en/news/20200116_10

[S34] LINE Business Manager help center, covering linking between LINE Official Account, LINE Ads, and shared audience/tag resources. https://lineforbusiness.com/th-en/helpcenter/businessmanager

[S35] TikTok Shop Thailand / Thailand commitment update, including more than three million merchants on the platform in Thailand. https://newsroom.tiktok.com/tiktok-supports-thailand-national-digital-economy-agenda?lang=th-TH

[S36] TikTok Shop ThaiRisers update, identifying TikTok Shop creators affiliate, ads, mega sale / brand campaigns, TikTok Shop Mall, and LIVE as key growth tools. https://newsroom.tiktok.com/tiktok-shop-spotlights-50-thai-brands-on-the-rise-with-tiktokshopthairisers?lang=th-TH
