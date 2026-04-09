**PaySitters Platform: RECOVER-First Architecture Sprint**

Post-Meeting Synthesis  |  To: Matt Stephenson (CEO) & Evan Rains (CSO)

From: Chris McCarthy  |  OB.1 AI Solutions  |  chris@ob1ai.co  |  April 2026  |  Confidential

**MEETING RECAP**

Matt, Team: thank you for a productive series of sessions over the past two weeks. Between the deep-dives on behavioral science methodology, product rebuild scope, the three-way alignment call, and the follow-up strategic context sessions, we have strong shared direction on what needs to happen next.

This brief captures what was heard, synthesizes it into a build framework, and proposes phased execution focused on one priority: a functional, user-serving RECOVER application that proves traction, supports the Beyond Finance partnership conversation, and is architecturally ready for Equifax distribution when that relationship activates. Singles and doubles first. Enterprise data stack comes online once traction exists.

**WHAT WE HEARD: SHARED PRIORITIES**

**Equifax is a future accelerant, not a prerequisite.** The architecture is being built so that every decision made now is Equifax-compatible. No rebuild required when that integration activates. But the MVP ships on its own merits.

**The current app is not prime-time ready.** Clean-slate rebuild. React Native v1 served the 1,000-member cohort; the next version serves 100K.

**RECOVER ships first.** Self-service arrears resolution is the highest-leverage module. It validates the behavioral thesis, generates immediate revenue, and creates the traction data that unlocks everything downstream.

**Core UX: deep-link simplicity.** Consumer gets link, enters name/email, account pulls up, pays instantly. Every screen serves that flow.

**Five vendor verticals, one platform.** Utilities, ISP, Insurance, Services, and ARM/Collections all onboard through the same portal, submit data in the same schema, and deliver consumers into the same payment experience. White-labeled per partner for FCRA compliance.

**Pattern recognition over autonomous agents.** Every interaction feeds real-time behavioral insights. AI synthesizes and surfaces. Humans decide.

**Data priorities:** form completion rates, user flow analytics, conversion funnel visibility, vendor onboarding pipeline tracking.

**SOC 2 compliance** scoped into architecture from day one, not bolted on. Required for Equifax partnership and institutional credibility.

**RECOVER MVP ARCHITECTURE**

RECOVER is the entry point. The self-service arrears resolution module proves the core thesis: consumers want to resolve debt when the framing preserves dignity and gives them control. Payment arrangements break at \~65% industry-wide because they are forced, not chosen. RECOVER inverts this.

The MVP consumer journey is a single linear flow with five defined stages:

| STAGE | NAME | DESCRIPTION | KEY METRIC |
| :---- | :---- | :---- | :---- |
| 1 | ENTRY | Consumer receives branded deep-link from biller or agency partner. Zero app download. No login wall. SMS, email, mail, or QR. Supports third-party biller handoff without new account creation. | Link click-through rate by channel (SMS, email, mail, QR) |
| 2 | IDENTIFY | Minimal data capture (name \+ email). Account auto-populates from biller/agency data file. Friction measured in seconds, not screens. | Profile completion rate (target: 83%+, validated against 1K-user cohort) |
| 3 | RESOLVE | Arrears consumer enters RECOVER. Balance displayed. Self-service payment slider: settlement, 3-payment, or custom (1-12 months). Consumer chooses. IKEA Effect: self-directed plans stick. | Settlement acceptance rate; custom plan completion rate |
| 4 | PAY | Daily micro-repayment: one tap, calibrated amount, confirmed. Amount calibrated to real-time balance and pay cadence. Pay cadence treated as a first-class data input, not inferred from bank transactions. | Daily active rate; repayment velocity; streak % |

**Analytics instrumented at every stage.** Every funnel transition is a tracked event with drop-off analysis. PostHog (product analytics, session replay, feature flags) \+ Supabase (transactional DB, RLS tier gating) form the measurement backbone. Event taxonomy defined before instrumentation begins.

**Behavioral science is infrastructure, not decoration.** Scripting, timing, colors, and framing are proprietary IP baked into the platform. Dignity-first language. Consumer-controlled plans. Shame-avoidance architecture throughout.

**FIVE-VERTICAL VENDOR FRAMEWORK**

PaySitters serves five vendor verticals. Each has distinct consumer pain points, data requirements, and integration patterns, but all funnel through the same platform architecture:

| VERTICAL | VENDOR TYPE | CONSUMER PAIN | PAYSITTERS ACTION | DATA INPUTS |
| :---- | :---- | :---- | :---- | :---- |
| Utilities | Electric, gas, water, sewer | Disconnection threats, $31B+ national arrears | Bridge payment on bill date; RECOVER self-service for arrears resolution | Bill amount, due date, account status, pay cadence |
| ISP / Telecom | Cable, internet, wireless, streaming bundles | Service interruption, early termination fees, credit damage | Timing-gap bridge; auto-enrollment via biller deep link | Monthly charge, billing cycle, service tier, payment history |
| Insurance | Auto, renters, health deductibles, premium finance | Policy lapse, coverage gaps, premium spikes | SHIELD emergency guarantee; structured factoring | Premium amount, policy dates, deductible, claim triggers |
| Services | Medical, dental, auto repair, childcare, property mgmt | Unexpected bills, payment plan friction, collections escalation | Vendor network \+ pre-authorized SHIELD; RECOVER for existing arrears | Invoice amount, vendor ID, service date, member authorization |
| ARM / Collections | Debt settlement aggregators, collection agencies, portfolio buyers | Broken payment arrangements (\~65% failure rate), adversarial framing, consumer disengagement | RECOVER self-service resolution; generalized agency partner portal | Portfolio file: account ID, original creditor, current balance, last payment date, contact permissions, fee share terms |

**Design principle:** the platform is vendor-agnostic. A utility biller and a debt settlement servicer both onboard through the same portal, submit data in the same schema, and deliver consumers into the same payment experience. White-labeled per partner for FCRA compliance.

**BEYOND FINANCE: THE FIFTH-VERTICAL PROOF POINT**

Beyond Finance is one of the largest debt settlement aggregators in the U.S. PaySitters has an active partnership conversation scheduled with their COO. The strategic fit is significant:

**Beyond Finance clients have a monthly escrow deposit ($400-$900/month)** that funds their settlement program over 24-48 months. From PaySitters' perspective, that deposit is structurally identical to a utility bill. Same recurring obligation. Same timing sensitivity. Same consequence for missed payments. The platform treats it as another biller in the same schema.

**Ontological lock-in:** When a Beyond Finance client adds their escrow deposit to PaySitters alongside their utility, telecom, and insurance bills, the settlement program stops being a separate anxiety. It becomes a managed component of their unified financial identity. The Goldilocks Zone absorbs it.

**Post-graduation flywheel:** A consumer who completes a Beyond Finance program with PaySitters running underneath does not need to be re-acquired as a financial wellness customer. The graduation event becomes a natural upsell to CLARITY \+ BRIDGE. Retention without re-acquisition cost.

The build reflects this: 'Debt Settlement Program Deposit' is an explicit biller category in the Vendor Onboarding Portal Spec. Escrow servicer routing logic is included in the payment rail architecture. The Beyond Finance consumer journey is included in the wireframes and high-fidelity mockups, and those mockups are available as a demo asset for the COO conversation.

**EQUIFAX INTEGRATION READINESS**

Every architectural decision in this sprint is made so that the Equifax integration activates without a rebuild. The MVP is Equifax-ready, not Equifax-dependent. Three integration points are mapped:

| EQUIFAX ASSET | FUTURE INTEGRATION POINT | ARCHITECTURE DECISION NOW |
| :---- | :---- | :---- |
| NCTUE (430M+ records) | Enrollment targeting: identifies timing-gap households within biller portfolios | Data schema accepts NCTUE-formatted portfolio files without transformation |
| Work Number / Income360 | Verified pay cadence for daily micro-payment calibration | Pay cadence is a first-class data input, not inferred from bank transactions |
| Financial Durability Score | Eligibility scoring for Bridge credit line and RECOVER segmentation | Eligibility engine accepts external score inputs, not just internal data |

The System Audit includes an Equifax Integration Readiness section mapping each of these assets to a specific architectural decision. The Phase 2 SOW includes an Equifax Integration Phase milestone.

**4-WEEK ARCHITECTURE SPRINT**

This sprint delivers seven independent assets through an iterative compounding model. Each week builds on the previous: audit findings feed wireframe decisions, wireframes inform mockups, mockups shape the pitch deck, the pitch deck frames the SOW. Nothing is throwaway.

| WEEK | SCOPE \+ DELIVERABLES |
| :---- | :---- |
| Week 1Audit \+ Intel | RECOVER UX audit (severity-rated findings, annotated screenshots, mobile-first evaluation). Portica demo gap analysis. Competitive intelligence sweep (YNAB, Monarch, DailyPay, Rocket Money, ARM fintech). Equifax Integration Readiness assessment. Build brief gap mapping. Week 1 summary brief delivered to PaySitters team. |
| Week 2Wireframes \+ System | RECOVER consumer flow wireframes (5 screens with behavioral science annotations). Beyond Finance escrow deposit journey wireframed as biller. Generalized agency partner portal (portfolio upload, resolution dashboard, compliance trail, fee share reporting). System audit \+ scalability assessment (React Native evaluation, SOC 2 gap analysis, Equifax readiness mapping). Analytics instrumentation plan (PostHog \+ Supabase event taxonomy, session replay, feature flags). |
| Week 3High-Fidelity \+ Deck | High-fidelity RECOVER mockups (production-ready mobile screens in PaySitters brand language). Member dashboard showing Beyond Finance deposit alongside utility bills. Generalized agency operations interface. Current vs. proposed pitch deck (market positioning, moat visualization, unit economics, competitive comparison). Vendor onboarding portal spec (all five verticals, CSV \+ API pathways, FCRA white-label config). Competitive intelligence brief (formatted). Top 5 recommendations (ranked by ROI). Mockups available as demo asset for the Beyond Finance COO conversation. |
| Week 4Polish \+ SOW | Final deliverable package (all 7 assets production-ready). Leadership presentation (45 min). Phase 2 SOW: PRD for RECOVER MVP build, sprint roadmap, Excalidraw architecture diagram, React rebuild framework, Supabase \+ PostHog stack. SOW includes explicit Equifax Integration Phase milestone. Budget alignment: product build allocation defined within the $2M bridge round (separate from balance sheet, credit facility, and integration costs). Phase 2 priced to the build allocation, not the total raise. |

**AGENTIC EXECUTION MODEL**

This sprint leverages AI-orchestrated workflows to deliver at a speed and depth that traditional consulting cannot match. Four agent roles run in parallel:

**Live Audit Agent:** Automated site crawl of the current product and Portica demo. Screenshots every screen at mobile viewports. Accessibility scan. Navigation path mapping. Trust signal inventory. Output: annotated screenshot library \+ raw UX data.

**Research Agent:** Parallel web search across App Store reviews, Reddit, Trustpilot, BBB, and competitor product pages. Structured extraction into comparison matrices. Sentiment analysis. Output: competitive intelligence brief \+ market positioning data.

**Document Generation:** Transforms raw audit data \+ research into formatted deliverables. DOCX reports, PPTX decks, branded PDFs. Design system extraction. PaySitters brand language applied throughout. Output: all 7 deliverables in production-ready format.

**Data Pipeline Agent:** PostHog \+ Supabase configuration spec. Event taxonomy for every funnel stage. Session replay setup. Feature flag framework. Dashboard wireframe for key operational metrics. Output: analytics instrumentation plan.

**SPRINT DELIVERABLES (7 INDEPENDENT ASSETS)**

**1\. RECOVER UX Audit \+ Gap Analysis:** Side-by-side analysis of the Portica demo against the current live experience. Severity-rated findings. Annotated screenshots. Deep-link flow evaluation. Mobile-first assessment across the full consumer arrears journey. Equifax Integration Readiness section included.

**2\. RECOVER MVP Wireframes \+ Flow Architecture:** Clean mobile wireframes covering the full five-stage journey: deep-link entry, identity verification, balance display, self-service payment slider, payment confirmation. Beyond Finance escrow deposit journey included. Generalized agency partner portal wireframed. Every screen annotated with behavioral science rationale.

**3\. Current vs. Proposed Pitch Deck:** Visual slide deck. Market positioning, moat visualization (NCTUE \+ Work Number), unit economics ($18.75/mo net margin, 38x LTV/CAC), competitive comparison, RECOVER flow walkthrough, Beyond Finance partnership framing. Built for investor-grade or partner-grade audiences.

**4\. System Audit \+ Scalability Assessment:** Technical audit of existing infrastructure. React Native codebase evaluation. Finicity \+ DEC integration state. Clean-slate vs. refactor recommendation. SOC 2 gap analysis. Equifax Integration Readiness mapping (NCTUE schema, Work Number pay cadence, Financial Durability Score inputs). Scaling requirements from 1K to 100K users.

**5\. Vendor Onboarding Portal Spec:** Architecture spec for vendor-agnostic data ingestion across all five verticals. Same portal, same schema. CSV \+ API pathways. ARM/Collections portfolio file spec (account ID, original creditor, current balance, last payment date, contact permissions, fee share terms). Debt Settlement Program Deposit as explicit biller category. Escrow servicer routing logic. Private-label configuration for FCRA compliance. BYO API approach.

**6\. Analytics \+ Conversion Instrumentation Plan:** PostHog \+ Supabase implementation spec. Event taxonomy for every funnel stage. Session replay configuration. Feature flags for phased rollout. Dashboard mockup: form completion rates, conversion funnel, vendor onboarding pipeline tracking.

**7\. Competitive Intelligence Brief:** YNAB, Monarch, DailyPay, Rocket Money, ARM fintech. Trust signals, UX, value prop comparison. App Store/Play Store review synthesis. Market sentiment. Cross-referenced against live audit findings.

**BUDGET FRAMEWORK**

All scoping is guided by the $2M bridge round as the total capital raise envelope. The round covers balance sheet and Bridge credit facility (\~40%), technical integration including Equifax work (\~35%), operations and compliance (\~15%), and reserve (\~10%). Phase 1 sprint deliverables are priced and committed independently. Phase 2 (RECOVER build) pricing is anchored to the specific product build allocation within the raise, not the total round. A dedicated budget alignment conversation is scheduled before the Phase 2 SOW is finalized.

**IMMEDIATE NEXT STEPS**

**Chris:** Begin RECOVER UX audit and gap analysis this week. Deploy competitive intelligence agents. Deliver Week 1 summary brief by Friday. Prepare Beyond Finance consumer journey screens for Week 2\.

**Matt:** Confirm whether usage analytics are currently active. Facilitate CTO introduction for technical onboarding (repos, AWS access, technical documentation). Provide access to real usage data. Rank vendor vertical priorities across all five verticals.

**PaySitters Team:** Share any pre-existing digital assets, previous FDD/DevOps records, and technical documentation. Share consumer experience flow documentation.

**Joint:** Schedule weekly build cadence (30 min). Align on RECOVER MVP launch target. 90-minute strategic context session before Week 2 wireframes. Budget alignment call (30 min) before Week 4 SOW. Evaluate current state of all integration points.

Looking forward to building this.

**Chris McCarthy**  
GTM Architecture  |  OB.1 AI Solutions  |  chris@ob1ai.co  |  234.602.0500