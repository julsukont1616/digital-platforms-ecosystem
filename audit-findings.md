**Status:** complete
**Last update:** 2026-04-01 00:05
**Stage:** Audit complete
**Done:** 4 flows analysed
**Findings:** 13 recommended changes (8 missing connections, 2 direction fixes, 3 logic additions)

---

# Flow Connection Audit — Thailand Digital Ecosystem Diagram

Source reference: `D:/workspace/digital-platforms-ecosystem/ecosystem.md`

---

## DISCOVERY FLOW

### Direction issues

None. All existing arrows point correctly (source captures → routes to destination).

### Missing connections

**1. `streaming → advertising: "Ad inventory"` [verified]**
Reason: ecosystem.md section 1 explicitly describes audio-visual and streaming as monetising "through advertising, subscription, sponsorship, and creator economics." Section 10.1 lists TikTok as both a social/discovery surface and a streaming/content-distribution surface with ad inventory. Streaming is an ad-inventory supplier to the advertising node, not just a consumption endpoint. Without this edge, the diagram implies streaming is purely downstream of discovery — but it also feeds discovery by carrying ad impressions.
Direction: `streaming → advertising` (streaming supplies ad inventory to the ad system).

**2. `creators → advertising: "Sponsored content / brand campaigns"` [verified]**
Reason: ecosystem.md section 10.1 states TikTok Shop monetises through "creator affiliate, ads, mega sales/brand campaigns." Creators are not only sourcing traffic through social_commerce; they also receive ad-spend from the advertising node (brand campaign budgets flow to creators) AND they act as inventory suppliers. The value-chain matrix (section 9, row 2) says "creators" are primary actors in the discovery layer alongside ad services. The current diagram has creators only connecting into social_commerce in the discovery flow, missing the direct creators ↔ advertising relationship.
Direction: `advertising → creators` (ad spend / brand budgets flow to creators as campaign fees).

**3. `consumers → streaming: "Content browsing / subscription intent"` [single-source]**
Reason: ecosystem.md section 4.2 step 3 describes discovery as where "a user first finds ... a video ... a government service." Streaming/content platforms are discovery surfaces in their own right — users arrive at streaming for content, not only after being routed from search/social. The current discovery flow has no consumer entry point into streaming. TikTok is both the social node and has a streaming/content dimension; YouTube is a streaming search surface. This is a minor but structurally accurate gap.
Direction: `consumers → streaming` (content discovery intent).
Note: Lower priority — add only if the diagram distinguishes content browsing from transactional discovery. Could skip to avoid clutter.

### Connections with correct logic already present

`creators → social_commerce` (Creator affiliate) — correct per ecosystem.md section 10.2 step 1 "creator affiliate content."
`advertising → marketplaces` (Paid placement) and `advertising → social_commerce` (Boosted listings) — correct per section 10.2.
`social → news` (Content sharing) — correct per ecosystem.md section 1 type 8 (news aggregator receives referral traffic from social).

---

## MONEY FLOW

### Direction issues

**4. `consumers → ewallets` direction is correct, but the label "Top-up / pay" conflates two distinct flows.**
No direction fix needed, but split is worth noting: consumers top UP wallets from banks (consumers → ewallets via bank), and consumers pay merchants/platforms via ewallets. Not a diagram error, just a label note.

**5. `streaming → cards: "Card billing"` — direction is BACKWARDS for the settlement leg.**
Current diagram: `streaming → cards` suggesting streaming routes through cards. The correct reading: consumers pay streaming subscriptions via cards (`consumers → cards → streaming` is the money path). The `streaming → cards` arrow implies streaming is initiating card transactions, which misrepresents who pays whom.
Fix: Remove `streaming → cards`. Replace with `consumers → cards: "Subscription billing"` and `cards → streaming: "Subscription settlement"` if you want to show this leg. Or simplify: the consumers → ewallets and consumers → banks paths already cover the payer side; just add `cards → streaming: "Subscription revenue"` to show streaming receives settlement from the card acquirer.
Recommended minimal fix: Change direction to `cards → streaming: "Subscription settlement"` [verified — ecosystem.md section 12 money-flow matrix: "Consumer pays through bank/wallet/card/QR; platform receives settlement"].

### Missing connections

**6. `banks → creators: "Creator payout"` or `ewallets → creators: "Creator payout"` [verified]**
Reason: ecosystem.md section 4.2 step 8 (Outcome and feedback) explicitly states: "settlement pays merchants, creators, couriers, and drivers." The current money flow only shows `banks → merchants` (settlement). Creators are a separate economic actor in the diagram and receive payouts from platform settlement. The social_commerce and streaming nodes sit between the payment layer and creators. The most accurate representation: `ewallets → creators` (TrueMoney / wallet payouts to creators is well-evidenced — section 11 TrueMoney: "merchant acceptance, payouts"). If you prefer a single edge, `banks → creators: "Creator payout"` covers the settlement rail.
Direction: `ewallets → creators: "Creator payout"` [verified].

**7. `banks → riders: "Driver/rider payout"` [verified]**
Reason: Same section 4.2 step 8 — "settlement pays merchants, creators, couriers, and drivers." Section 10.3 (On-demand swimlane) step 4 states: "Grab collects from customers and pays merchants within 1–2 business days after fees." Riders/drivers are paid out via the banking/wallet layer. The current physical flow has riders only receiving dispatch from superapps and delivering to consumers, but there is no money settlement to riders. The money flow is missing this payout leg entirely.
Direction: `ewallets → riders: "Driver payout"` or `banks → riders: "Driver payout"` [verified].

**8. `social_commerce → ewallets: "In-app payment checkout"` [verified]**
Reason: The current money flow has `superapps → ewallets` but no equivalent for social_commerce. Ecosystem.md section 12 social-commerce order row: "TikTok Shop / social-commerce checkout stack plus bank/wallet rails" as the interim holder. Social commerce has its own checkout path through wallet/bank rails. This gap means the diagram implies social_commerce purchases have no payment leg.
Direction: `social_commerce → ewallets: "Social checkout"` [verified].

**9. `marketplaces → banks` or `superapps → banks` for merchant settlement (not just promptpay)` [supported]**
Reason: ecosystem.md section 12 states merchant settlement goes through "Bank / wallet / card / QR → marketplace and payment partners → Merchant." The current flow shows `marketplaces → promptpay` but PromptPay is one of multiple rails. Banks directly settle merchants too. However, adding `marketplaces → banks: "Merchant settlement"` as a separate edge would duplicate logic already partially covered by the `banks → merchants` edge. Lower priority — skip to avoid clutter.

---

## PHYSICAL FLOW

### Direction issues

None. Existing arrows are directionally correct.

### Missing connections

**10. `social_commerce → parcels: "Parcel fulfillment"` or `social_commerce → warehouses: "Fulfillment"` [verified]**
Reason: ecosystem.md section 12 social-commerce money-flow row explicitly lists "logistics provider" as a final economic recipient for social commerce orders. Section 10.2 step 5 (delivery): "SPX or other network executes delivery / return" — and SPX is the logistics arm for TikTok Shop/Shopee. The current physical flow only connects `marketplaces → parcels` and `marketplaces → warehouses`, leaving social_commerce without any fulfillment path. TikTok Shop has over 3 million merchants in Thailand (section 6) — their orders require physical fulfillment.
Direction: `social_commerce → parcels: "Ship order"` [verified].

**11. `creators → riders: "Local delivery dispatch"` — this one is SPECULATIVE.**
Reason: Creators in a live-commerce context may dispatch riders for same-day delivery, but there is no direct evidence in ecosystem.md that creators independently dispatch riders. Skip this connection.

**12. `superapps → warehouses: "Fulfillment (Grab Mart / dark stores)"` [single-source]**
Reason: ecosystem.md section 10.3 on-demand swimlane describes Grab covering "food, mart, express" — Grab Mart implies dark store / warehouse fulfillment. However, ecosystem.md does not explicitly name the warehouses node as a Grab dependency. This is a reasonable inference but lower confidence. Skip to keep under 15 new edges.

---

## DATA & AI FLOW

### Direction issues

**13. `ai_ml → search`, `ai_ml → social`, `ai_ml → marketplaces` are shown as dashed arrows from ai_ml OUT. The direction is correct for ranking/recommendation outputs, but the INPUT side to ai_ml is underrepresented.**

### Missing connections

**14. `advertising → cloud: "Ad targeting / audience data"` [verified]**
Reason: ecosystem.md section 13 data-flow matrix: "Discovery and attention data" — primary collectors include ad systems; main uses include "ad targeting, audience building, retargeting"; highest-leverage actors are "search/social/ad platforms." The current data flow sends `social → cloud` and `marketplaces → cloud` and `promptpay → cloud` but skips advertising entirely. Ad systems generate and consume enormous volumes of behavioral and attribution data — this is the commercial engine of the data layer. Without `advertising → cloud`, the diagram implies ad systems operate outside the data backbone.
Direction: `advertising → cloud: "Ad & audience data"` [verified].

**15. `superapps → cloud: "Transaction & behavioural data"` [verified]**
Reason: ecosystem.md section 4.2 step 8: "user behavior becomes data for retention, ad targeting, fraud scoring, underwriting, and AI models." The current data flow sends `marketplaces → cloud` and `social → cloud` but not superapps. Superapps (Grab, LINE MAN) generate transaction, location, order, and payment data that feeds cloud analytics and AI models. Section 13 lists on-demand platforms as generators of "location and route data" and "merchant operating data" — both feed the cloud/AI layer.
Direction: `superapps → cloud: "Transaction & location data"` [verified].

**16. `cloud → ai_ml: "Model training / compute"` [verified]**
Reason: ecosystem.md section 9 value-chain row 7: "Cloud, hosting, and AI providers — ranking, recommendation, analytics, generative AI, risk scoring, and system operations are run at scale." The current data flow has ai_ml sending data TO other nodes but no edge showing cloud FEEDS ai_ml. Cloud is the compute and training infrastructure for ai_ml. The current diagram makes ai_ml appear self-contained. This is the most structurally important missing edge in the data flow — without it, the ai_ml node has no upstream feed in the data flow.
Direction: `cloud → ai_ml: "Compute / model serving"` [verified].

---

## SUMMARY TABLE — RECOMMENDED CHANGES

Priority: High (H) = fixes incorrect logic or fills a named gap from ecosystem.md. Medium (M) = adds accuracy without fixing an error. Low (L) = speculative or visual-noise risk.

| # | Flow | Change type | Edge | Label | Priority | Tag |
|---|------|-------------|------|-------|----------|-----|
| 1 | Discovery | Add | `streaming → advertising` | "Ad inventory" | H | [verified] |
| 2 | Discovery | Add | `advertising → creators` | "Brand campaign spend" | H | [verified] |
| 3 | Money | Direction fix | remove `streaming → cards`, add `cards → streaming` | "Subscription settlement" | H | [verified] |
| 4 | Money | Add | `ewallets → creators` | "Creator payout" | H | [verified] |
| 5 | Money | Add | `ewallets → riders` | "Driver payout" | H | [verified] |
| 6 | Money | Add | `social_commerce → ewallets` | "Social checkout" | H | [verified] |
| 7 | Physical | Add | `social_commerce → parcels` | "Ship order" | H | [verified] |
| 8 | Data & AI | Add | `advertising → cloud` | "Ad & audience data" | H | [verified] |
| 9 | Data & AI | Add | `superapps → cloud` | "Transaction & location data" | H | [verified] |
| 10 | Data & AI | Add | `cloud → ai_ml` | "Compute / model serving" | H | [verified] |
| 11 | Discovery | Add | `consumers → streaming` | "Content browsing" | M | [single-source] |
| 12 | Physical | Add | `superapps → warehouses` | "Dark store fulfillment" | L | [speculative] |
| 13 | Money | Add | `marketplaces → banks` | "Merchant settlement" | L | skippable |

**Total high-priority changes: 10** (within the stated limit of 15)
**Direction fixes: 1** (streaming → cards is backwards)
**New edges: 9** (plus 2 medium/low priority optional additions)

---

## GAPS IN THIS AUDIT

- The diagram does not show `telecom` or `app_stores` or `browsers` (Layer 1 ACCESS) connecting into any flow. Ecosystem.md is explicit that access is the substrate for all higher layers. However, adding access-layer edges to the four flows would require expanding scope significantly and was not part of the audit request.
- The `messaging` node has no outbound data-flow edge to cloud (LINE Official Account / messaging generates CRM and engagement data). This is a gap but lower priority than the 10 listed above.
- `ai_ml → advertising` (AI-optimised ad targeting back to the advertising node) is implied by ecosystem.md section 13 but would create a cycle with `advertising → cloud → ai_ml → advertising`. Worth noting but left out to avoid visual complexity.
