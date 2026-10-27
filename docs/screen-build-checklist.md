# Hospital screen build — handoff checklist

## Handoff status

| Item | Current status |
|---|---|
| Project scope | Hospital Staff screens plus public Landing/Login and Partner Inquiry; Donor, Recipient, and System Admin screens are out of scope. Partner Inquiry is a public intake supporting FR-040 per revised Q22-A. |
| Decisions and questions | Decisions recorded in [decisions.md](decisions.md). Q7/Q21 subscription work is superseded and removed; Q22-A is resolved. See [open-questions.md](open-questions.md). |
| Visual direction | Dark mode only. Use Biofarma (https://biofarma.com.ar/) as the latest corporate composition/typography reference, with the supplied Dugo+ logo and retained dark palette. HTML remains a content/layout reference; see [corporate-visual-review.md](corporate-visual-review.md). The spec and approved decisions govern behavior. |
| Screen plan | The spec crosswalk and pre-Figma state/visual acceptance matrix are documented in [screen-plan.md](screen-plan.md). Partner Inquiry is planned under FR-040 as a request intake only. |
| Figma work | Landing, Login, Dashboard, Partner Inquiry, Blood Requests, Emergency Request, and Donor Matching are built. Donation Verification has 12 UC-027 states, but still needs the global Empty and Loading states. Matching preserves a selected masked donor through notification, call, and screening states. |
| Canvas layout | 69 top-level Hospital frames. Current bounding-box check returned zero overlaps. Landing stays in its separate column; later screen families occupy distinct rows. |
| Figma target | [Dugo+ Hospital UI Prototype](https://www.figma.com/design/ai01prc8DzRT7NVCcwwVto) — file key `ai01prc8DzRT7NVCcwwVto`. |
| Current next step | Add Donation Verification Empty and Loading states first, then build Inventory. Other missing planned families are Donor History, Secure Donor Info, Hospital Profile, Location Map, and Audit Log. Twenty-seven original authenticated sidebar frames have Foundation navigation; Matching and Donation Verification retain the same sidebar. Full prototype-player walkthrough remains pending. |
| Approval | Received: `APPROVED: Hospital Screen Build, create new file yourself`. Follow-up user requests authorized the subsequent built screens and this visual/documentation refinement. Do not start another unrequested screen. |
| Resume condition | Landing, Login (including all Login state footers), Dashboard, Partner Inquiry, Blood Requests, Emergency Request, Donor Matching, and Donation Verification are built. Donor identity and UC-027 flows are structurally wired. Full prototype-mode walkthrough remains pending. Build Inventory next, then the other unbuilt approved Hospital screen families. |

## Before every Figma write

| Done | Action |
|---|---|
| [ ] | Confirm the existing approved phase covers the screen; if it does not, stop until the exact phase approval is provided. |
| [ ] | Identify the intended existing Figma file and reuse its key/session. Create a session only when starting a distinct screen task, per the Figma tool instructions. |
| [ ] | State the Figma tool name and exact inputs before calling it. |
| [ ] | Load required Figma guidance before `use_figma`; load design-generation guidance for a full screen. |
| [ ] | Inspect only the relevant existing frame/components/variables and naming needed for this screen; avoid whole-file scans when an existing convention is documented. |
| [ ] | Verify screen FR/UC flow, states, privacy, source HTML/React behavior, exact CSS tokens, layout hierarchy, and all control destinations against the matrix in [screen-plan.md](screen-plan.md). |
| [ ] | Confirm no open question affects this screen. Q22-A approves Partner Inquiry as intake only; subscription management is removed from scope. |
| [ ] | Prepare all state frames and route destinations before the composition call so one screen/state family can be written as one safe-to-retry batch. |
| [ ] | Capture one screenshot after composition; make a targeted repair only when a visible defect exists; restore the intended viewport/scroll settings before closing the screen. |

## Per-screen build checklist

| Done | Requirement |
|---|---|
| [x] | Build one screen only in the session. Do not proceed to the next screen without the user's next instruction. |
| [ ] | Use the screen's exact FR/UC IDs and scope from [screen-plan.md](screen-plan.md). If a screen/feature has no applicable ID, stop and flag it; do not build it. |
| [ ] | Use a 1440px web viewport for the Landing entry and Hospital dashboard screens. |
| [ ] | Use dark mode and the values in [design-tokens.md](design-tokens.md), including the latest user-authorized corporate reference overrides. |
| [ ] | Include Default, Empty, Error, and Loading on every data screen, plus its applicable use-case-specific states from the screen plan. |
| [ ] | Keep the role label “Hospital Staff” and page title “dugo+ hospital” on authenticated Hospital pages; Landing uses the Dugo+ brand and no role chooser. |
| [ ] | Use `Hospital/<ScreenName>/<State>` for Figma layer names and `Cmp/<Name>` for components. |
| [ ] | Wire interactive controls to valid screen/state destinations so the prototype mirrors the approved user flow. Record pending destinations for screens not yet built; finish those connections as their screens are added. |
| [ ] | Keep notifications in-app and email only; do not include SMS. Use OSM-styled mockups where the screen plan calls for a map. |
| [ ] | Preserve the approved privacy and feature decisions, including masked donor names in the donations ledger and all four matching actions. |
| [x] | Return all created/mutated node IDs and structural evidence from every `use_figma` write. |
| [x] | Capture a screenshot after composition. Report differences against both the screen plan and source HTML. |
| [ ] | Stop after this one screen and report completion or any blocker; do not begin another screen autonomously. |

## Screen sequence

| Order | Screen | FR / UC IDs | Source | Status |
|---:|---|---|---|---|
| 1 | Dugo+ full landing page | FR-012; UC-002 (entry shell) | `/Users/pol/Downloads/landing_1(1).html` | COMPLETE — `Hospital/Landing/Default` `21:16` contains the hero, all 12 marketing sections, and 500px footer; dark-only; Sign In routes to Login (`4:2`); Partners section CTA `51:3` and footer link `32:332` route to Partner Inquiry (`44:2`). |
| 2 | Hospital sign-in | FR-012; UC-002 | Live `/login`; React `web/src/pages/public/Login.jsx`, `web/src/layout/AuthLayout.jsx` | INTERACTION FIXED — existing six states plus `EmailEntered` `66:2`, `PasswordEntered` `66:56`, `PasswordVisible` `66:110`; all nine frames at 100% opacity. Empty submit validates; email-only shows password-required; password-only shows email-required; second field completes demo credentials; complete sign-in routes Dashboard. |
| 3 | Hospital dashboard | FR-014, FR-016, FR-020; UC-011, UC-013, UC-017; NFR-023 | `/Users/pol/Documents/dugo_mobile_web/dark/admin-dashboard.html` | COMPLETE — `Hospital/Dashboard/Default` `16:2`; `Empty` `16:152`; `Error` `16:259`; `Loading` `16:365`; `ValidationError` `16:471`. Screenshot captured from Default after visual fixes. |
| 4 | Blood requests | FR-016, FR-017, FR-037; UC-012, UC-013 | `html/admin-blood-requests.html` | BUILT + INTERACTION FIXED — nine existing states plus `RequestDraft` `71:263`, `ConsentMissing` `71:350`, and `RequestComplete` `71:437`; empty submit validates, field click shows filled demo values, consent is required, completed submit routes through Loading to RequestDetail. |
| 5 | Emergency request | FR-021; UC-020; NFR-02, NFR-05, NFR-07 | `html/admin-blood-requests.html` | COMPLETE — ten states `85:2`, `85:89`, `85:145`, `85:198`, `85:250`, `85:336`, `85:423`, `85:510`, `85:597`, `85:671`; eight existing Blood Requests emergency entry actions route to the Emergency form. |
| 6 | Donor matching | FR-017, FR-021, FR-031; UC-012, UC-020; NFR-05 | `html/admin-donor-matching.html` | BUILT — 11 states in `Hospital/DonorMatching`; three donor choices write the selected masked donor variable, which carries through notify/call actions. Pause, radius expansion, refresh, retry, and sidebar routes are structurally wired. |
| 7 | Blood inventory and updates | FR-020, FR-034; UC-017, UC-026 | `html/admin-inventory.html` | NOT STARTED |
| 8 | Donation verification | FR-031, FR-032, FR-033, FR-036, FR-042; UC-027 | `html/admin-donations-rewards.html` | PARTIAL — 12 states in `Hospital/DonationVerification`; Cleared/Deferred/Rejected, validation, missing record, save failure, and completed-donation confirmation after Cleared. Add Q10 Empty and Loading states; wire Loading to a verified next state. |
| 9 | Donor donation history | FR-020, FR-038; UC-014; NFR-11, NFR-16 | New screen | NOT STARTED |
| 10 | Secure donor information | FR-019, FR-038; UC-016; NFR-11, NFR-16 | New screen | NOT STARTED |
| 11 | Hospital partnership inquiry | FR-040 (supporting public intake only per Q22-A) | React `/Users/pol/Documents/dugo_mobile_web/web/src/pages/public/Partner.jsx`; public shell in `AuthLayout.jsx` | INTERACTION FIXED — original five states plus `FacilityEntered` `68:2`, `EmailEntered` `68:85`, `ContactEntered` `68:168`, `LocationEntered` `68:251`; empty submit validates; completed Send → Loading → Confirmation; Landing CTA and footer route to `44:2`. |
| 12 | Hospital profile | FR-013; UC-018 | New screen; use `html/admin-settings.html` Facility tab as reference | NOT STARTED |
| 13 | Hospital location map | FR-015; UC-034; NFR-09 | New screen | NOT STARTED |
| 14 | Audit log | FR-035; UC-031; NFR-15 | `html/admin-audit-trail.html` | NOT STARTED |
| 15 | Logout action/state | FR-012; UC-021 | Existing Hospital sidebar action; return to `Hospital/Login/Default` | SIGN OUT LABEL LIGHT RED across 50 instances; all 50 label ancestors route to Login. UC-021 connection-failure and already-expired alternatives pending; automatic NFR-14 timeout remains deferred. |

## Hospital Login build record

| Check | Result |
|---|---|
| Figma frames | `4:2`, `19:53`, `4:34`, `4:67`, `4:100`, `4:133`; all nine current Login states are 1440×1400 full content frames, including the footer. Earlier captures had inconsistent heights; corrected in the corporate visual review. |
| Screenshot | Captured from `Hospital/Login/CredentialsEntered` after wiring, showing the fictional prefilled credential state. [Shared Login footer screenshot](https://www.figma.com/api/mcp/asset/f158e46a-37e5-4915-b3b0-37e2ff309823.png). |
| Plan comparison | UC-002 Hospital sign-in, required-field validation, incorrect/unusable account, suspended/removed account, and connection failure are represented. No role chooser is present. No data-screen loading state is applicable to this login screen. |
| Source comparison | Matches the live React login's top header, Dugo+ mark, two-column sign-in layout, card, password reveal control, and dark palette. Includes `Hospital Staff` and `dugo+ hospital` labels. |
| Differences / limitations | Hospital copy is specific to assigned staff credentials, and the card states that Hospital accounts are provided by Dugo+. Role selection, donor Google login, self-registration, password recovery, and the redundant footer sign-in button are omitted. Footer email input and newsletter Subscribe button are visual prototype content, not live integrations. Login frames now contain the full 1440×1400 content, including the entire footer. Prototype viewport/scroll behavior still requires a browser walkthrough. |
| Figma node IDs | State frames: `4:2`, `4:34`, `4:67`, `4:100`, `4:133`, `19:53`; footer frames: `35:2`, `35:26`, `35:50`, `35:74`, `35:98`, `35:122`; logo nodes: `7:2`–`7:11`; login layout additions: `9:2`–`9:36`; page title additions `9:37`–`9:41`; removed unsupported recovery links `9:3`, `9:10`, `9:17`, `9:24`, `9:31`. |

## Prototype interaction record

| Flow / control | Connection |
|---|---|
| Login with empty fields | `Hospital/Login/Default` Sign In → `ValidationError` |
| Simulated credential entry | Clicking Email or Password from Default, ValidationError, AuthenticationError, or ConnectionError → `CredentialsEntered` (`19:53`) with fictional `hospital.staff@example.org`; Sign In → `Hospital/Dashboard/Default` |
| Login error recovery | Authentication/connection error Sign In → `CredentialsEntered`; Access Denied Sign In → `Default` |
| Dashboard period | Replace the invalid-period detour with an obvious, working period selector for This month, Past 6 months, and Past year. Clearly label displayed values as illustrative demo totals; each option updates the selected range and its associated total/chart state. Keep period selection on Dashboard, not Blood Requests. |
| Dashboard retrieval retry | Error Retry → Loading → Default after 900ms |
| Dashboard navigation | Blood Requests nav from Dashboard Default, Empty, Error, Loading, and ValidationError → `Hospital/BloodRequests/Default` (`54:2`); Dashboard nav from Blood Requests states → Dashboard Default (`16:2`). |
| Dashboard return | Sign out → Login Default; Dashboard nav from Empty, Error, Loading, or ValidationError → Dashboard Default |
| Error recovery audit repairs | AccessDenied email/password fields (`4:125`, `4:128`) → Login Default (`4:2`); Dashboard Empty/Error/Loading/ValidationError Sign Out (`16:188`, `16:295`, `16:401`, `16:507`) → Login Default; Dashboard Loading (`16:365`) → Default after 900ms. |
| Emergency Request entry and submit | Emergency Request actions in all eight Blood Requests states → Emergency Request Default (`85:2`); blank submit → ValidationError (`85:250`); field click → RequestDraft (`85:336`); submit without authorization → ConsentMissing (`85:423`); checkbox → RequestReady (`85:510`); send → Loading (`85:198`) → Confirmation (`85:597`) after 1.1 seconds. |
| Emergency Request alternate outcomes | Confirmation → Empty/no eligible donors (`85:89`) or NotificationIssue (`85:671`); request remains Active; notification retry → Loading → Confirmation; Error retry → Emergency Request Default. |
| Flow entry points | 12 named Figma prototype starting points now place Dugo+ Landing first, followed by Login, the credential demo, all login outcomes, and Dashboard Default/Empty/Error/Loading/ValidationError. |
| Interaction limits | Figma does not accept real text entry in these static form layers; Login, Partner Inquiry, Blood Requests, and Emergency Request demonstrate entry using fictional click-to-fill values. Partner form submission, Blood Request creation, Emergency Request matching, and notification delivery are simulated; no live request is sent. Footer newsletter controls and marketing sections are static by instruction. Dashboard nav controls to Matching, Inventory, Donations, Audit Log, Hospital Profile, and Location remain future destinations until those screens are built. Subscription is removed; do not restore its nav item. |

## Hospital Dashboard build record

| Check | Result |
|---|---|
| Figma frames | `16:2`, `16:152`, `16:259`, `16:365`, `16:471`; each 1440×1000. |
| Screenshot | Captured from `Hospital/Dashboard/Default` after visual fixes and Blood Requests route wiring. [Dashboard Default](https://www.figma.com/api/mcp/asset/646fee8e-733d-450c-b71b-6d0fe778a0e6.png). |
| Plan comparison | Includes active requests, collected-unit total with period selection, inventory snapshot, and required default/empty/error/loading states plus invalid-period validation. |
| Source comparison | Uses the dashboard HTML's masked request initials, active-request status, four KPI values, blood-type inventory counts, and weekly collection context. Includes Hospital role identity and the Dugo+ logo. The map is rendered as an OSM-style mockup. |
| Differences / limitations | No Reports, Donor Registry, or extra Settings navigation. The source's geographic dot graphic was replaced with an OSM-style street-grid mockup. Dashboard values are illustrative prototype data, not live records. Built routes are wired; destinations whose screens are not built remain pending, as listed in the interaction record. |
| Figma node IDs | Main creation returned `16:2`–`16:622`. Logo tiles added `16:623`–`16:627`; inventory row fill fixes `16:106`, `16:450`, `16:577`; logo tile layer-order fixes include `16:623`–`16:627` and logo marks `16:4`, `16:154`, `16:261`, `16:367`, `16:473`. |

## Out of scope

| Excluded content | Reason |
|---|---|
| Reports and analytics | Q20 removed it; no applicable Hospital FR/UC ID. |
| Subscription management | Q7/Q21 are superseded by the partnership-based model; UC-015 / FR-018 screen removed. |
| Donor Registry add/import/edit/notify management | Q20 removed it; UC-014 and UC-016 have separate planned screens. |
| Settings tabs beyond Facility | Q20 removed them; matching-rule ownership belongs to Admin UC-028. |
| Uncrossmatched emergency release, discard stock, broadcast campaign, and other unmatched HTML extras | Q20 removed no-ID features from scope. |
| Landing Donor/Recipient routes (static marketing remains included) | Include all supplied sections/footer as static landing content. Hospital Sign In and Become a Partner → Partner Inquiry are active public routes. Omit role selection, Donor/Recipient routes, and SMS references. |
| NFR-14 session timeout | Deferred by project instruction; do not design. |

## Flow-first construction sequence

| Order | Build/wiring step | Acceptance check |
|---:|---|---|
| 1 | Keep `Hospital/Landing/Default` before existing Login and Dashboard frames in the user journey. | Dugo+ mark and dark-mode hero are present; no role chooser. |
| 2 | Wire Landing Sign In → `Hospital/Login/Default`; wire Login Home → Landing from each applicable Login state. Wire Become a Partner to Partner Inquiry after that separate screen session. | A user can enter/return from Hospital login and open the inquiry flow. |
| 3 | Blood Requests is built after Landing, Login, Dashboard, and Partner Inquiry. | The urgency-sorted list, create flow, detail, empty/error/loading, validation, no-eligible-donors, and notification-retry states are present and wired. |
| 4 | Follow the primary path: Landing → Login → Dashboard → Blood Requests → Matching/Emergency Request → Donation Verification; retain navigation branches to other planned Hospital tools. | No live-looking in-scope control is left without an interaction or documented pending destination. |
| 5 | Stop after one screen per session. | Do not build the next screen until the user asks to continue. |

## Landing entry build record

| Check | Result |
|---|---|
| Figma frame | `Hospital/Landing/Default` `21:16`, 1440×11860 full content frame after corporate refinement. Hero plus 12 static section frames; footer `32:322` is 1440×500. |
| Screenshot | [Landing hero](https://www.figma.com/api/mcp/asset/cb84bee1-d83c-4f9b-9e60-f385ccb6544b.png); [Stories section](https://www.figma.com/api/mcp/asset/ed57ba4e-3660-4f64-8dae-7a2d6f4480c8.png); [Contact section](https://www.figma.com/api/mcp/asset/4c47b71c-bf7b-49e5-b2f0-438c2f558595.png); [Landing footer](https://www.figma.com/api/mcp/asset/0edef098-64a1-4105-8a01-aea1ce65ff2e.png). These are historical screenshots from the earlier design. The current full-content Landing frame is 1440×11860; current hero evidence is linked in the latest corporate review. |
| Prototype wiring | Recorded route configuration (not a new prototype-mode walkthrough): Landing Sign In → Login Default (`4:2`) → click Email/Password → CredentialsEntered (`19:53`) → Sign In → Dashboard (`16:2`) → Sign Out → Login. Login Home returns to Landing (`21:16`) on Default, ValidationError, AuthenticationError, AccessDenied, ConnectionError, and CredentialsEntered. Landing Sign In routes to Login; Become a Partner CTA `51:3` and footer link `32:332` route to Partner Inquiry `44:2`. Landing is the first prototype start; 11 prior starts remain available. |
| Plan comparison | Landing is the first entry. Hospital Sign In routes to Login; Partners section and footer route to the FR-040 supporting intake. No role selector or Donor/Recipient destinations. Other donor/recipient marketing copy remains static. This is the UC-002 entry shell. |
| Source comparison | Current refinement reuses the source Dugo+ logo and dark palette; the old blood-drop hero is hidden and replaced with Biofarma-inspired medical photography and DM Sans Light headings. Earlier source treatment used the dark palette (`#0e0a0a`, `#f3efec`, `#a59d96`, `#1a1413`, `#ff3a4a`, `#ff8f94`, `#f3d2ce`), and DM Sans/Newsreader/Space Mono. Twelve static sections reproduce marketing story, process, features, compatibility, impact, partners, insights, FAQ, contact, and footer. The Compatibility section `32:208` was corrected from cream/white to the dark tokens after the full-canvas audit. SMS copy is absent per Q3. |
| Differences / limitations | Hospital Sign In routes to Login; Partner CTA and footer link route to Partner Inquiry. Remaining marketing copy is static. Theme/X-ray controls are omitted. Figma simulates sign-in with a prefilled credential state and does not perform real authentication. |
| Figma node IDs | Frame `21:16`; logo `21:17`–`21:18`; hero text/buttons `21:19`–`21:31`; source SVG frame `29:2` with vector layers `29:3`–`29:4`. Sections: Why `32:11`; Stories `32:43`; Duel `32:69`; Platform `32:101`; About `32:136`; Features `32:156`; Compatibility `32:208`; Numbers `32:235`; Partners `32:260`; Insights `32:282`; FAQ `32:298`; Contact `32:313`; Footer `32:322`. Login Home reactions on `9:2`, `9:9`, `9:16`, `9:23`, `9:30`, `19:77` return to Landing. |

## Hospital Partner Inquiry build record

| Check | Result |
|---|---|
| Figma states | Nine top-level 1440×1400 frames: existing `44:2`, `49:84`, `49:171`, `49:256`, `49:341`; progressive entry `68:2`, `68:85`, `68:168`, `68:251`. |
| Screenshots | [Partner Inquiry empty form](https://www.figma.com/api/mcp/asset/9479ad81-732f-435f-848a-148b61f74933.png); [Partner Inquiry completed form](https://www.figma.com/api/mcp/asset/02f463fd-397d-4838-8364-7180192bea26.png); [Partner Inquiry confirmation](https://www.figma.com/api/mcp/asset/8b328981-afab-4692-ae41-ba2f8c1e04bb.png). |
| Prototype wiring | Blank Send → ValidationError; clicking fields in Default/ValidationError reveals the entered example values in progressive states; Facility → Email → Contact → Location; completed Send → Loading → Confirmation after 1.1 seconds. Validation recovery returns to Default; SubmissionError Retry → Loading; Home/Back to Dugo+ → Landing; Sign in → Hospital Login. Landing CTA and footer route to Default (`44:2`). |
| Plan comparison | Includes the facility name, Hospital email, contact person, optional phone, and facility location; the confirmation says Dugo+ will follow up within 2–3 business days. It does not create an account or perform System Admin actions. |
| Source comparison | Reuses the Dugo+ logo and public auth shell direction, dark styling, header, form card, and footer. React reference has contact person, email, phone, partnership type, and message; the approved Hospital design uses the requested location field and omits partnership type/message. |
| Differences / limitations | Example form data includes a `.example` email; Figma uses fixed click-to-fill demo values rather than arbitrary keyboard text entry and sends no live inquiry. Landing CTA wiring and Subscription navigation removal are complete. |

## Emergency Request build record

| Check | Result |
|---|---|
| Figma states | Ten top-level 1440×1000 frames: `Default` `85:2`; `Empty` / no eligible donors `85:89`; `Error` `85:145`; `Loading` `85:198`; `ValidationError` `85:250`; `RequestDraft` `85:336`; `ConsentMissing` `85:423`; `RequestReady` `85:510`; `Confirmation` `85:597`; `NotificationIssue` `85:671`. All are in their own row at y=5270. |
| Screenshots | [Emergency Request blank form](https://www.figma.com/api/mcp/asset/cfb5c3d8-8402-4345-8426-0724283fd00e.png); [Emergency Request validation errors](https://www.figma.com/api/mcp/asset/4b6e922d-e746-450d-9b66-93eb8bd5fdf0.png); [Emergency Request authorized form](https://www.figma.com/api/mcp/asset/11c3234c-25d1-45bb-b14f-b6930cef85ab.png); [Emergency request confirmation](https://www.figma.com/api/mcp/asset/9d177449-c881-499f-83da-2f68e7b0d60a.png); [Full canvas overview](https://www.figma.com/api/mcp/asset/dde411ec-d62c-44be-a775-8ee4c535c5dc.png). |
| Prototype wiring | All eight existing Blood Requests “Emergency request” actions (`54:38`, `54:186`, `54:334`, `54:482`, `54:778`, `54:926`, `54:1074`, `54:1222`) route to Emergency Request Default. Blank submit → ValidationError with inline messages on all required fields; field click reveals fixed sample values; request submit without authorization → ConsentMissing; explicit checkbox → RequestReady; send → Loading → Confirmation after 1.1 seconds. Confirmation branches to Empty/no match or NotificationIssue. No-match keeps the request Active; notification retry returns through Loading to Confirmation. Error retry returns to the emergency form. |
| Plan comparison | Implements FR-021 and UC-020 with required blood type, quantity, urgency, location, supporting request information, validation, active status, tiered matching, no-match retention, and notification retry. Search tiers show 5 km → 10 km → 15 km → capped 20–25 km and the under-five-second target. Donor alerts are in-app and email only. |
| Source comparison | Reuses the editable Hospital shell and request fields from `html/admin-blood-requests.html`; the dark theme and form hierarchy match the existing Blood Requests screen. The emergency screen emphasizes the Emergency flow, priority search, active status, and delivery retry. |
| Differences / limitations | Figma uses fixed fictional values rather than real text entry, location lookup, donor matching, or live notification delivery. Error is a separately inspectable alternative state with a working retry action. Uncrossmatched emergency release, SMS, and other unsupported HTML actions are excluded. |
| Figma node IDs | State frames `85:2`, `85:89`, `85:145`, `85:198`, `85:250`, `85:336`, `85:423`, `85:510`, `85:597`, `85:671`. Existing emergency entry controls updated: `54:38`, `54:186`, `54:334`, `54:482`, `54:778`, `54:926`, `54:1074`, `54:1222`. |

## Blood Requests build record

| Check | Result |
|---|---|
| Figma states | Existing `Default` `54:2`; `Empty` `54:150`; `Error` `54:298`; `Loading` `54:446`; `CreateRequest` `54:594`; `ValidationError` `54:742`; `RequestDetail` `54:890`; `NoEligibleDonors` `54:1038`; `NotificationIssue` `54:1186`. Added `RequestDraft` `71:263`; `ConsentMissing` `71:350`; `RequestComplete` `71:437`. All are top-level 1440×1000 frames; Blood Requests row overlap check returned zero. |
| Screenshots | [Blood Requests default](https://www.figma.com/api/mcp/asset/76b8672b-d0f9-46b9-b809-17f3d3d6f3de.png); [Create Request form](https://www.figma.com/api/mcp/asset/6d79590a-9887-49d4-870a-7c29d6733943.png); [Request detail](https://www.figma.com/api/mcp/asset/bf0a927f-24d7-42e8-a76c-3f085996991d.png); [Completed request form with consent](https://www.figma.com/api/mcp/asset/716e127f-e3f3-4f22-8486-bac96ab4f2be.png). |
| Prototype wiring | New request → CreateRequest; empty submit → ValidationError; clicking a form field in CreateRequest/ValidationError shows the fictional populated RequestDraft; Draft submit → ConsentMissing; checking consent from Draft/ConsentMissing → RequestComplete; Complete submit → Loading → RequestDetail after the existing 1.1-second timeout. Request rows → RequestDetail; detail → NoEligibleDonors or NotificationIssue; retry → Loading; Empty create → CreateRequest; Error retry → Default; back/edit actions return to list or form. Verified destination IDs and no row overlap in Figma. |
| Plan comparison | Implements FR-016/017/037 and UC-012/013 with urgency-first active list, create flow, validation, active request confirmation, no eligible donor state retaining active status, and in-app/email notification retry. Patient names are represented by initials. |
| Source comparison | Reuses the dark Dashboard shell, Dugo+ identity, Hospital Staff label, and native editable shapes/text. Source request fields are adapted to the approved create flow. SMS, request cancellation, uncrossmatched emergency release, and other unsupported HTML extras are omitted. |
| Differences / limitations | Data is illustrative, and form entry, matching, and notification delivery are simulated rather than live. Figma demonstrates fixed values rather than arbitrary keyboard text entry. RequestDetail reuses the same request example (A.B., A−, Red cells, 4 units, Urgent, Today · 18:00, Emergency, Malolos, Bulacan); contact and notes remain visible in the form but are not repeated in the detail summary. Screen visual direction is polished from the HTML reference. The list includes 4 fictional urgency-sorted examples and masked initials. |
| Figma node IDs | Existing state frames `54:2`, `54:150`, `54:298`, `54:446`, `54:594`, `54:742`, `54:890`, `54:1038`, `54:1186`; new state frames `71:263`, `71:350`, `71:437`; Consent checkmark `71:591`. |

## Latest corporate visual review — 2026-10-27

| Check | Result |
|---|---|
| Current visual evidence | [Saved hero screenshot](review-assets/corporate-landing-hero.png); [review and change record](corporate-visual-review.md). Earlier screenshot links document earlier versions and may expire. |
| Landing | Existing root 21:16 retained. New editable hero 97:2, photograph fill 97:3, header 97:5, hero Sign In wrapper 97:11, header Sign In wrapper 97:8. Existing Sign In label destinations retained and copied onto wrappers. All sections/footer retained. |
| Repairs | Seven Emergency error text layers 87:2–87:8 reparented into 85:250; full Login footer bounds restored; Login role/title, Dashboard title/subtitle, Landing statistic/title and Blood Request hint/error overlap fixed; Blood Request validation button label fitted. |
| Structural verification | 69 top-level Hospital frames; 0 frame overlaps. All 50 Sign out labels bind to the light-red Foundation accent token and route to Login. |
| Route verification | Matching and Donation Verification routes and selected-donor variable bindings were structurally checked. Prototype-mode clicks and timed transitions have not been witnessed. |
| Remaining work | Build Inventory, Donor History, Secure Donor Info, Hospital Profile, Location Map, and Audit Log. UC-021 expired-session/connection-failure alternatives remain pending. Perform a full prototype-mode journey walkthrough before calling the prototype interaction-tested. |
| API usage for this review | 16 Figma connector calls: 1 session, 11 use_figma, 1 libraries, 2 asset-upload requests, 1 screenshot. Two early read calls exceeded response limits; no canvas changes occurred in those failed reads. Two asset POSTs followed upload requests; the initial WebP rendered black and was replaced with PNG. |
