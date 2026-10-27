# Phase 4 — Hospital screen plan

| Plan basis | Value |
|---|---|
| Product scope | Hospital Staff only; Donor, Recipient, and System Admin screens excluded |
| Theme and visual direction | Dark mode only. Use Biofarma (https://biofarma.com.ar/) as the latest corporate composition and typography reference; retain the supplied Dugo+ logo and dark palette. HTML remains a content reference; corporate overrides are recorded in design-tokens.md. The spec and approved decisions govern behavior and scope. |
| Web viewport | 1440px for Hospital and landing screens |
| Notification channels | In-app and email only |
| Map treatment | OSM-styled mockup |
| Global data-screen states | Default, empty, error, and loading on every data screen, plus the applicable UC-specific states below |
| Prototype interaction | Wire relevant controls to valid screen/state destinations to demonstrate the Hospital flows. Keep destinations pending when their planned screens have not yet been built. |
| Realistic input and submission | Clicking a form field reveals an entered example value or selected option. Blank or partial submission routes to matching field-level validation. A completed form proceeds through Loading to the correct outcome. Verify the primary and recovery path on every built screen. If arbitrary text entry is unavailable in Figma Design, use click-to-fill examples and state that limitation. |
| Opacity and overlays | Keep each screen frame at 100% opacity unless its plan documents a translucent treatment. Inspect screenshots for accidental washout or opaque overlays. |
| Figma layer names | `Hospital/<ScreenName>/<State>`; components use `Cmp/<Name>` |
| Build gate | A screen or feature without an applicable FR/UC ID is flagged and not built until resolved |
| Pre-Figma gate | Verify each screen's FR/UC flow, required states, source and exact tokens, privacy rules, visual hierarchy, and control destinations before writing to Figma. Block an affected screen while a required content/scope decision is open. |
| Figma call budget | After the required session and targeted file inspection, compose one complete screen/state family in one safe-to-retry write; take one screenshot and make only a targeted repair if needed. Do not build another screen in the same build session. |

## Primary user journey

| Step | Destination | Prototype path | IDs |
|---:|---|---|---|
| 1 | Dugo+ landing | Entry screen; Hospital Sign In → Login; Become a Partner → Partner Inquiry → request received | FR-012; UC-002 entry shell; FR-040 supporting intake per Q22-A |
| 2 | Hospital Login | Credential demo → Dashboard; validation/error states remain available | FR-012; UC-002 |
| 3 | Dashboard → Blood Requests | Review summary, open or create a request | FR-014, FR-016, FR-017, FR-020; UC-011–013, UC-017 |
| 4 | Matching / Emergency Request → Donation Verification | Continue a request through match or emergency handling and donor screening | FR-017, FR-021, FR-031–033, FR-036, FR-042; UC-012, UC-020, UC-027 |
| 5 | Hospital tools | Branch to Inventory, Donor History, Secure Donor Info, Profile, Location Map, and Audit Log | IDs listed per screen below |
| 6 | Logout | Sign Out → Hospital Login | FR-012; UC-021 |

Wire the controls on each built screen to valid destinations. Document future screen destinations as pending and finish their links when those screens are built.

## Planned screens and flows

| # | Planned screen / flow | Layer name base | Viewport | Source HTML | FR / UC IDs | Planned scope and states |
|---:|---|---|---:|---|---|---|
| 1 | Dugo+ landing entry | `Hospital/Landing` | 1440px | `/Users/pol/Downloads/landing_1(1).html` | FR-012; UC-002 (entry shell); FR-040 supporting intake per Q22-A | First user-journey page. Retain all sections and footer in dark mode; use the Biofarma-inspired corporate hero and typography per the latest visual decision. No role chooser. Hospital Sign In routes to Login; Partners CTA routes to Partner Inquiry. Other donor/recipient marketing copy and decorative controls have no destination. |
| 2 | Hospital sign-in | `Hospital/Login` | 1440px | Live `https://dugo-plus.web.app/login`; React `web/src/pages/public/Login.jsx` and `web/src/layout/AuthLayout.jsx` | FR-012; UC-002 | Follow the live page's header, two-column sign-in band, card, and shared footer below the fold. Hospital-specific sign-in with no role-selection control. Include required-field validation, invalid credentials/account unavailable, suspended/removed account denial, connection error, and Hospital dashboard route. Do not include donor Google login, self-registration, or password recovery. Post-logout return uses this screen (UC-021). |
| 3 | Hospital dashboard | `Hospital/Dashboard` | 1440px | `admin-dashboard.html` | FR-014, FR-016, FR-020; UC-011, UC-013, UC-017; NFR-023 | Use existing KPI, active-request, inventory, donation, and map areas where they support these IDs. Add an obvious collected-units selector with This month, Past 6 months, and Past year states, each displaying clearly labeled illustrative demo totals. Include zero/no records, no active requests, retrieval error, loading, and the UC-011 invalid-period outcome. Map is an OSM-styled mockup. |
| 4 | Blood requests | `Hospital/BloodRequests` | 1440px | `html/admin-blood-requests.html` | FR-016, FR-017, FR-037; UC-012, UC-013 | Active request list, create-request flow, and request detail. Order requests by urgency per FR-037. Include default, empty/no active requests, loading, retrieval error/retry, missing or invalid fields, failed validation, no compatible eligible donors with request retained as active where applicable, and notification delivery issue/retry. Do not add request cancellation: no Hospital cancellation UC/FR supports it. BUILT in Figma (`54:2`–`54:1186`, nine state frames). |
| 5 | Emergency request | `Hospital/EmergencyRequest` | 1440px | `html/admin-blood-requests.html`; reuse the existing Blood Requests create-form structure | FR-021; UC-020; NFR-02, NFR-05, NFR-07 | BUILT in Figma: ten states `85:2`, `85:89`, `85:145`, `85:198`, `85:250`, `85:336`, `85:423`, `85:510`, `85:597`, `85:671`. Dark-mode emergency form uses patient initials, blood type, component, quantity, urgency, required-by time, ward, hospital location, contact, notes, and the request-form authorization. Blank submit → field validation; field click → fixed demo values; authorization → Loading → Active/Matching confirmation; confirmation branches to Empty/no-match or NotificationIssue; notification retry returns through Loading. NFR-05 tiers shown as 5 km → 10 km → 15 km → capped 20–25 km with the under-five-second target; NFR-02 in-app/email only. No SMS or uncrossmatched-release action. Reuses the existing Hospital shell and exact CSS tokens; no library components or variables are available in the file. |
| 6 | Donor matching | `Hospital/DonorMatching` | 1440px | `admin-donor-matching.html` | FR-017, FR-021; UC-012, UC-020; NFR-05 | BUILT: Matching states in Figma. Three donor choices write the selected masked donor variable, carried through notification/call and into Donation Verification. Pause, Call, Notify, Refresh, retry and recovery routes are wired. Direct radius tiers (5 km, 10 km, 15 km, 20–25 km) update the selected highlight and summary, then search through Loading → RadiusSelected; while Paused, the new tier is applied when staff resume. Radius controls are dimmed during loading and contact-confirmation states. The OSM-styled map remains illustrative. |
| 7 | Blood inventory and updates | `Hospital/Inventory` | 1440px | `admin-inventory.html` | FR-020, FR-034; UC-017, UC-026 | View inventory and add/update records. Include empty inventory, missing/invalid fields, validation failure, update/audit failure without success indication, retryable retrieval error, and loading. |
| 8 | Donation verification | `Hospital/DonationVerification` | 1440px | `admin-donations-rewards.html` (screen structure reference only) | FR-031, FR-032, FR-033, FR-036, FR-042; UC-016, UC-027; NFR-11, NFR-16 | PARTIALLY BUILT: 21 states in Figma. The Default screen has the expanded identity, donor-reported answers (02–08), staff screening/documentation (01, 09), aftercare (10), donation history, and clinician-review summary. Added status-preserving Saving/SavingDecision, donation-confirmation Loading, donor-record lookup Loading, Empty, consent gate/Loading/missing, and access-denied states. Matching selections bind fictional donor identity fields to the screening profile. Dashboard sidebar links to its existing frame; unbuilt sidebar destinations are dimmed. Structural route checks and screenshots are recorded in audit (h); prototype-mode walkthrough remains outstanding. Rewards remain excluded. |
| 9 | Donor donation history | `Hospital/DonorHistory` | 1440px | New screen; enter from an authorized donor record in Requests/Matching | FR-020, FR-038; UC-014; NFR-11, NFR-16 | Check authorization and consent before displaying history. Include default, empty/no history, loading, retrieval error/retry, consent missing, and access denied without exposing history. Do not link to the excluded Donor Registry management page. |
| 10 | Secure donor information | `Hospital/SecureDonorInfo` | 1440px | New screen; enter from an authorized donor record in Requests/Matching | FR-019, FR-038; UC-016; NFR-11, NFR-16 | Display only permitted information after role and consent checks; record access in the audit trail. Include default, empty/no authorized details available, loading, consent missing, access denied, and retrieval error without disclosing protected data. Do not link to the excluded Donor Registry management page. |
| 11 | Hospital partnership inquiry | `Hospital/PartnerInquiry` | 1440px | React reference: `/Users/pol/Documents/dugo_mobile_web/web/src/pages/public/Partner.jsx`; visual shell `/Users/pol/Documents/dugo_mobile_web/web/src/layout/AuthLayout.jsx` | FR-040 (supporting public intake step per Q22-A; no account administration) | Collect facility name, hospital email, contact, and location. Send leads to a request-received/follow-up confirmation. Provide default, validation error, sending/loading, submission error retaining entries, and confirmation states. Do not claim an account was created or a live submission was sent by the prototype. Dark mode only. |
| 11 | Hospital profile | `Hospital/Profile` | 1440px | New screen; `admin-settings.html` Facility tab is the visual reference | FR-013; UC-018 | Show current facility name, contact information, and location as specified by UC-018. Include default, empty/optional profile details not set, loading, retrieval/save error retaining prior values, cancel/discard, required-field validation, and save confirmation. |
| 12 | Hospital location map | `Hospital/LocationMap` | 1440px | New screen | FR-015; UC-034; NFR-09 | Show the saved Hospital location on an OSM-styled mockup. Include default, empty/location unavailable when profile has no saved location, loading, and map-service error with retry. Do not introduce live map dependencies. |
| 13 | Audit log | `Hospital/AuditLog` | 1440px | `admin-audit-trail.html` | FR-035; UC-031; NFR-15 | Authorized Hospital view of donation, inventory, and data-access records with event type, timestamp, and non-identifying references where applicable. Include default, empty/no records, loading, retrieval error/retry, and access denied. Admin-only integrity verification is excluded. |
| 14 | Logout action | `Hospital/Logout` | 1440px | Existing sidebar action | FR-012; UC-021 | Treat as a Dashboard action/state, not a new standalone page. Invalidate session, then return to `Hospital/Login/Default`, as UC-021 specifies. Include the UC-021 already-expired-session alternative and connection failure (this is distinct from automatic NFR-14 timeout); do not show logout success until invalidation is confirmed. NFR-14 remains deferred and is not designed. |

## Removed from Hospital scope by Q20

| Existing page or feature | HTML source | IDs found in the specification | Scope decision |
|---|---|---|---|
| Reports and analytics | `admin-reports.html` | None for Hospital | Removed from scope; no applicable Hospital FR/UC ID. |
| Donor Registry add/import/edit/notify page | `admin-donor-registry.html` | None for these registry-management actions | Removed from scope; UC-014 and UC-016 are covered by the separate history/security screens. |
| Settings tabs beyond Facility | `admin-settings.html` | None for the extra tabs; matching-rule ownership is Admin UC-028 | Removed from scope; only the Hospital profile flow (UC-018) remains planned. |
| Uncrossmatched emergency release, discard stock, broadcast campaign, and other unmatched extras | Existing request/inventory HTML | No applicable Hospital FR/UC ID found in the audit | Removed from scope. |
| Rewards tab and Hospital request cancellation | `admin-donations-rewards.html`; `admin-blood-requests.html` | No Hospital FR/UC supports these controls in the approved scope | Removed from scope; retain the latest Q16-approved Pause/Call/Notify actions and direct radius-tier selection in Matching. |
| Audit-log export | `admin-audit-trail.html` | UC-031 specifies viewing records and details, not export | Exclude export controls unless a supporting Hospital requirement is approved. |
| Subscription management screen | UC-015; FR-018 | User's partnership-based model removes subscription management | Removed from prototype per latest user decision. |
| Landing-page content and features | `landing_1(1).html` | No separate Hospital FR/UC IDs; full page remains a static entry/marketing surface associated with FR-012 / UC-002 | Include static sections/footer. Hospital Sign In and Become a Partner → Partner Inquiry are active public routes. No role chooser, SMS references, or Donor/Recipient routes. |
| Public partner intake | Existing React `/partner` reference | FR-040 is System Admin account creation; Q22-A approves this screen only as the preceding public intake step | Build the intake and confirmation; do not show account creation, suspension, or removal as Hospital actions. |

## Approved scope decisions applied

| Decision | Applied to this plan |
|---|---|
| Q1, Q20 | Requests, matching, inventory, and donations pages remain references for applicable screens. Reports was later removed from scope because no Hospital FR/UC ID supports it. |
| Q3 | No SMS references; in-app and email only. |
| Q7, Q21 | Subscription page/content removed; no plan catalog needed. |
| Q9 | OSM-styled map mockups. |
| Q10 | Common data-screen states plus applicable use-case-specific states. |
| Q15, Q20, landing-flow-override, landing-full-page-override, partnership-model, Q22-A | Reports, Registry management, extra Settings, and Subscription remain removed. Landing sections/footer remain static; Hospital Sign In and the Become a Partner intake flow are active public flows. |
| Q16 + latest radius override | Keep Pause, Call, and Notify; remove the separate Expand radius button; make 5 km, 10 km, 15 km, and 20–25 km directly selectable. |
| Q17–Q19 | Mask donor names in the ledger; build applicable newly requested screens except removed UC-015; use “Hospital Staff” and “dugo+ hospital.” |
| Theme | Dark mode only. |

## Pre-Figma state and visual acceptance matrix

| Screen | State coverage to verify before build | Visual/flow acceptance criteria |
|---|---|---|
| Landing | Static content; no data states | Dark mode, Dugo+ mark, complete sections/footer, and vertical scroll; Hospital Sign In → Login; Partners CTA → Partner Inquiry; no role chooser, SMS, or Donor/Recipient destinations |
| Login | Default, validation, credential demo, authentication error, access denied, connection error | Sign-in form remains the visual focus; shared footer scrolls below the fold; Home returns to Landing; successful demo reaches Dashboard; no role selector or Admin-only footer link |
| Dashboard | Default, Empty, Error, Loading, invalid period | Request status, inventory, collected units, and donor matches are scannable under time pressure (NFR-023); urgency is visible (FR-037); unbuilt routes remain identified as pending |
| Blood Requests | Default, Empty/no active requests, Error, Loading, field validation, click-to-fill demo, consent missing/confirmed, no eligible match, notification issue/retry | Blank submit shows required-field errors; clicking a field reveals fictional sample values; consent must be explicitly checked; completed request moves through Loading to RequestDetail; urgent requests are easy to distinguish; no unsupported cancel control; no-match request retained as active where applicable. Figma uses fixed demo values, not arbitrary keyboard text entry. |
| Emergency Request | Default, Empty/no eligible match, Error, Loading, validation, click-to-fill, authorization, Active/Matching, notification failure/retry | Emergency urgency is prominent; blank submit shows specific validation; field click reveals fictional demo values; authorization must be confirmed; completed submit moves through Loading to Active/Matching; no match retains Active status; retry preserves the request; in-app/email only; no SMS or unsupported emergency release |
| Matching | Default, Empty/no match, Error, Loading, pause/radius/action outcomes | OSM-style mockup balanced with donor results; eligibility and outcomes are legible; Pause, Call, and Notify remain; radius tiers 5, 10, 15, and 20–25 km are direct choices; show NFR-05 under-five-second target without implying real GPS data |
| Inventory | Default, Empty, Error, Loading, validation, update/audit failure | Stock is easy to compare by type; quantity and expiration are visible; add/update is tied to a completed donation or issued transfusion; no discard/broadcast controls |
| Donation Verification | Default, Empty/no donor ready, Error, Loading, screening/outcome/confirmation states; consent missing and access denied | Matching selection carries its fictional profile through screening. Consent gate precedes protected details. Save retry preserves the selected outcome through Loading to the matching Saved state; retrieval retry and completed-donation confirmation pass through Loading. Empty is reachable from Matching/Empty. Donor history changes only after completed-donation confirmation; clinical flags remain review-only; no Rewards tab. Prototype-mode primary/recovery walkthrough is still required. |
| Donor History | Default, Empty/no history, Error, Loading, consent/access states | History is readable only after authorization and consent; denied/error states reveal no history; enter from Requests/Matching, never the removed Registry page |
| Secure Donor Info | Default, Empty/no authorized details, Error, Loading, consent/access states | Access checks are visually clear; show only permitted fields and log access; denied/error states disclose no protected data |
| Partner Inquiry | Default, ValidationError, Loading/Sending, SubmissionError (retain entries), Confirmation | Dark public shell; fields are facility, hospital email, contact, and location; confirmation says the inquiry was received and Dugo+ will follow up; no account-creation claim or fabricated live delivery. |
| Hospital Profile | Default, Empty/optional details absent, Error, Loading, validation/cancel/save states | Present only UC-018 facility name, contact, and location fields; make edit/cancel/save result clear; failed save retains prior values |
| Location Map | Default, Empty/location unavailable, Error, Loading | Saved facility location is prominent on OSM-style mockup; missing location and map failure have distinct messages; retry is clear |
| Audit Log | Default, Empty/no records, Error, Loading, access denied | Event type, timestamp, and non-identifying references are scannable; only authorized Hospital records appear; no Admin-only integrity verification |

## Figma call efficiency and review gate

| Gate | Pass condition before the write |
|---|---|
| Scope | The screen has FR/UC IDs; its role and entry route match the approved Hospital-only scope; no unresolved question affects its content or behavior. |
| Evidence | Spec flows and alternate paths are checked against the source HTML/React reference; only fields and sample data supported by those sources are used. |
| States | Required Default, Empty, Error, Loading and applicable UC-specific states are listed for the screen. |
| Visual plan | Dark-only palette uses exact source CSS tokens; intended hierarchy and layout goal are written; no placeholder, clipped text, overlap, or unreadable contrast is accepted in screenshot review. |
| Prototype | Every live-looking control has a valid interaction or documented future destination; Landing Become a Partner routes to Partner Inquiry; fields populate on click; blank/partial submits validate; complete submits progress through Loading to outcome; primary and recovery paths are click-tested. |
| API use | State the Figma tool and inputs before the call. Reuse the active file/session where appropriate; inspect only the relevant nodes; build one screen/state family in one safe-to-retry composition call; capture one screenshot; make one targeted correction pass only when needed. |
| Stop | Do not proceed to the next screen without the user's next instruction. Report differences from both plan and reference HTML, and record IDs/screenshot/status in the handoff checklist. |
