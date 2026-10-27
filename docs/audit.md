# Audit: Hospital side only (scope set by user 2026-10-27)
Source: docs/dugo-spec.md (UC-011..018, 020, 026, 027, 031, 034, plus UC-002/021 login/logout) vs /html.
Not covered here: Admin, Donor, Recipient. Phase 3 token extraction is recorded in [design-tokens.md](design-tokens.md).

## (a) HTML files vs hospital role
| HTML file | Page purpose (as built) | Hospital UC covered | Notes |
|---|---|---|---|
| landing.html | Marketing + sign-in panel; "Hospital / Blood Bank -> Dashboard" card | UC-002 (partial) | Single sign-in, email + password. No role selector seen. Q6 |
| admin-dashboard.html | KPI cards, urgent requests, inventory snapshot, donation trend, donor coverage map | UC-011 (partial), UC-013 (partial), UC-017 (partial) | Trend toggle weekly/monthly; totals by donation type, not blood type |
| admin-blood-requests.html | Request list, filters, New request modal, emergency-release confirm | UC-012, UC-013, UC-020 (partial) | Extras: component, ward, contact, "Reserve from inventory", uncrossmatched release, Match/Cancel actions |
| admin-donor-matching.html | Matching for one request: waves, radius, donor list, Notify/Call | UC-012 step 6-7, UC-020 step 6-7 (partial) | Extras: Pause matching, Call, manual Notify, fallback tier |
| admin-inventory.html | Stock by type/component, batches, Add/Issue/Discard | UC-017, UC-026 | Extras: Quarantine/Reserved/Issued/Expired, Broadcast campaign, Discard |
| admin-donations-rewards.html | Donation ledger, 4-step Confirm donation, Rewards tab | UC-027 (partial), UC-014 (partial) | Step names: Donor / Screening / Donation / Confirm. Cleared/Deferred/Rejected labels not seen in extracted text: verify |
| admin-donor-registry.html | Donor list, Add donor, Import CSV, Edit, Notify | UC-014/016 (partial) | Contact masked; names and points shown |
| admin-audit-trail.html | Filterable log, entry detail panel, Export log, RA 10173 notes | UC-031, UC-016 (access logging) | Sensitive entries; reveal-with-reason flow |
| admin-reports.html | Report builder, KPIs, charts, export table | none | No hospital UC |
| admin-settings.html | Tabs: Facility, Staff & access, Compatibility, Eligibility, Inventory rules, Matching rules, Templates, Rewards, Privacy, Staff alerts | UC-018 (Facility tab only) | Most tabs have no hospital UC; matching rules overlap Admin UC-028 |

## (b) Hospital UCs with NO screen in /html
| UC | Name | Gap |
|---|---|---|
| UC-015 | Manage Subscription Plan | Removed from prototype by the partnership-model decision; Q7/Q21 are superseded. |
| UC-034 | View Hospital Location on Map | No screen. Dashboard map shows donors, not the hospital's saved location |
| UC-014 | View Blood Donation History | No per-donor history view with access/consent check |
| UC-016 | Secure Donor Information | No consent-missing / access-denied state |
| UC-021 | Logout | Only a "$ exit" sidebar link |
| UC-018 | Edit Hospital Profile | Facility tab exists, but not as a profile screen with confirm/cancel states |

## (c) HTML features with NO hospital UC/FR
Reports & Analytics page; Donor Registry add/import/edit; Rewards tab; Settings tabs other than Facility; Broadcast campaign; Discard stock; uncrossmatched emergency release; Cancel request. Pause matching / direct radius selection / Call donor / Notify also lack direct Hospital FR/UC support, but remain included by the explicit Q16 user decision and its latest radius-control override.

## (d) Spec vs HTML contradictions
| Spec | HTML |
|---|---|
| Roles: Hospital vs System Admin (AGENTS scope) | Title "dugo+ admin", user label "Blood Bank Admin" on hospital pages |
| UC-016: donor info only with recorded consent | Donations table shows full donor names; matching/registry mask them |
| Admin owns matching radius tiers and retry (UC-028) | Hospital settings has "Matching rules" tab; matching page previously had Expand radius; latest user direction replaces it with direct radius-tier selection |
| Matching is system-initiated (UC-012, UC-020) | Manual Notify/Call per donor |
| No real personal data in prototype (prompt 07) | Realistic full names and donor IDs |

## (e) Tokens
| Status | Result |
|---|---|
| Phase 3 | Extracted exact shared CSS custom-property values for the dark theme only: colors, typography, spacing, sizing, radii, shadows, and role aliases from all 10 HTML files. |
| Token reference | [design-tokens.md](design-tokens.md) |
| Phase 4 | Hospital screen plan is drafted in [screen-plan.md](screen-plan.md); Q20 resolved the no-ID scope conflict by removing those pages and features from Hospital scope. |

## (f) Partnership intake request

| Source / request | Current flow in React reference | Spec alignment | Plan disposition |
|---|---|---|---|
| User requests a “Become a Partner” CTA, Hospital email/contact/location form, and confirmation after Send | `/Users/pol/Documents/dugo_mobile_web/web/src/pages/public/Partner.jsx` has `/partner` intake and confirmation; project `docs/REQUIREMENTS.md` D21 associates it with FR-012/FR-040 | `dugo-spec.md` FR-040 assigns Hospital account creation to System Admin; Q22-A clarifies the public intake is only a supporting request step | Built as `Hospital/PartnerInquiry` under FR-040 per revised Q22-A and linked from Landing Partners section/footer. It collects a follow-up request only; no account creation or Admin actions. |

## (g) Donation verification refresh

| Review area | Result | Evidence / remaining work |
|---|---|---|
| Donor identity and access | Added fictional full name, date of birth, sex, masked phone/email, masked valid-ID reference, separate “ID verified” and “Consent recorded” pills, and access-logged note. | UC-016; NFR-11/NFR-16. Do not use real donor data in this prototype. |
| Questionnaire | Added ten numbered sections covering vitals/physical check, interval, health history, medicines/vaccines, procedures/exposures, risk behavior, women-specific questions, day readiness, decision documentation, and aftercare. | UC-027. Donor-submitted responses are displayed; facility staff still complete checks and determine the final result. |
| Eligibility summary | Right rail lists recent travel, vaccine, and tattoo/piercing as potential review flags. | User selected clinician-review flags until approved hospital criteria are supplied. The prototype does not mark a donor ineligible automatically. |
| Donation history and decision | Added three fictional completed-donation rows below the questionnaire; polished Cleared/Deferred/Rejected selection and their saved confirmations with status pills and outcome-specific next-step copy. The 2026-10-27 patch adds status persistence through Loading and retry. | Structural routes and selected-outcome variable are verified. Prototype-mode walkthrough has not been completed. |
| Visual review | Screenshot reviewed at 1440×1000; dark-mode Foundation colors, persistent sidebar/header, consent/ID pills, scroll viewport, right review rail, and separation between profile and decision are visible. | The details/history/decision continue below the initial viewport by vertical scroll. Questionnaire values are editable text layers. |
| Plan and HTML differences | The screen plan previously described outcome states but not the full screening review workspace. | Compared with `admin-donations-rewards.html`, the updated screen adds identity details with consent/access indicators, submitted health answers, a right-side review summary, and donor history; it keeps the existing Cleared/Deferred/Rejected decisions and completion confirmation. The HTML ledger/rewards layout is only a structure reference; Rewards remain excluded. |
| Remaining verification | The 2026-10-27 patch adds DonationVerification Empty, Saving, SavingDecision, DonationConfirmLoading, RecordLookupLoading, ConsentLoading, ConsentGate, ConsentMissing, and AccessDenied states. | Empty has an entry from Matching/Empty; Loading destinations are structurally wired. Q10's named states are represented; prototype-mode primary/recovery walkthrough remains unverified. |
| Clinical criteria references | WHO states donor-selection criteria differ by country and directs services to national/local criteria; DOH-CAR publishes locally varying values. | [WHO donor eligibility guidance](https://www.who.int/campaigns/world-blood-donor-day/who-can-give-blood); [DOH-CAR donor guidance](https://caro.doh.gov.ph/world-blood-donor-day-5/). Neither was applied as automatic hospital policy. |

## (h) Donation Verification flow audit — 2026-10-27

| Finding | Evidence | User-flow impact / next step |
|---|---|---|
| Primary destination IDs resolve | Matching `Begin final screening` now routes to `ConsentGate`; the recorded-consent action routes through `ConsentLoading` to Default. Cleared/Deferred/Rejected lead to their result states and save through Saving, with a second Loading decision for the non-Cleared outcomes. | Patched and structurally verified. This does not verify interaction behavior in prototype mode. |
| Retry save drops the selected result | A `screeningStatus` string variable is set by each outcome choice and checked by two supported binary conditionals: Saving routes Cleared to its Saved state and other outcomes to SavingDecision; SavingDecision routes Deferred to its Saved state and the fallback to RejectedSaved. SaveError → Retry save returns through Saving. | Patched structurally; all three branches preserve their selected status. Prototype-mode retry has not been clicked through. |
| Retry screening does not retry retrieval | `RecordNotFound/Retry screening` routes to `RecordLookupLoading`, which returns to Default after its timeout. | Patched structurally; the screen represents a re-fetch attempt and preserves the selected donor through the `selectedDonor` binding. |
| Selected donor identity is not carried into the expanded profile | The three Matching choices set the selected masked donor and fictional full name, DOB, sex, contact, email, and ID-reference variables. The Default profile text is bound to these variables. | Patched structurally for N*** O., M*** R., and J*** A.; sample records are fictional. |
| Sidebar items look active but have no reaction | Dashboard now links to `Hospital/Dashboard/Default`; Blood Requests, Matching, and Sign out remain linked. Inventory, Donations, Audit Log, Hospital Profile, and Location are visually dimmed in all Donation Verification states because those target screen families are not built. | Patched for the reviewed flow. Do not treat the dimmed entries as completed destinations. |
| Save and completion skip Loading | Result Save routes through `Saving` and, for Deferred/Rejected, `SavingDecision`; Confirm donation routes through `DonationConfirmLoading` to DonationCompleted. `Empty` is reached from a new secondary action on Matching/Empty. | Patched structurally. Screenshots reviewed; no prototype-mode walkthrough yet. |
| Consent is displayed but not gated in this route | Matching’s Begin final screening now opens a no-PII ConsentGate. Consent recorded routes through ConsentLoading before Default; ConsentMissing and AccessDenied show no donor identity/health details and provide recovery routes. | Patched structurally. The gate models a staff-confirmed consent record; it does not establish live consent or backend authorization. |
| Deferral details are guidance-only | Deferred copy tells staff to explain the reason and facility-approved return timing, but there is no reason/duration capture. | If the facility needs those details recorded in Dugo+, add a policy-backed field/state; do not invent deferral intervals. |
| Clinical checklist grouping | The screen now separates donor-reported answers (02–08), staff screening/documentation (01, 09), and aftercare (10). | Q25 resolved. Screenshot review confirms the three section cards and their rows are visually distinct. |
| Patched state node IDs | Saving `186:1848`; DonationConfirmLoading `186:1874`; RecordLookupLoading `186:1900`; ConsentGate `186:1926`; ConsentMissing `186:1952`; AccessDenied `186:1978`; Empty `186:2004`; ConsentLoading `186:2030`; SavingDecision `189:1593`; Matching/Empty secondary route `187:1595`. | Figma file key `ai01prc8DzRT7NVCcwwVto`. Existing Verification states remain listed in the screen-plan history. |
| Prototype walkthrough not completed | Figma destinations, bindings, route targets, and screenshots were structurally inspected. CUA reported “Local browser use is disabled in Work settings,” and no browser surface was available. | Primary and recovery paths still need a prototype-mode click-through when browser use is enabled. Do not report the flow as fully tested. |

## (i) Matching radius controls — 2026-10-27

| Review area | Result | Evidence / remaining work |
|---|---|---|
| Radius choice | Removed the separate Expand Radius button. Added direct 5 km, 10 km, 15 km, and 20–25 km choices. | Supersedes the Expand Radius portion of Q16. Pause, Call, and Notify remain. |
| Selection behavior | The 24 chips in Default, Empty, Error, RadiusSelected, and DonorsSelected set the matching mode and route through Loading. Loading goes to RadiusSelected. In Paused, choosing a tier changes the selection only; Resume starts Loading. | Structurally verified. The four modes update the selected-chip fill and radius summary together. |
| Disabled states | Loading, NotifyConfirmation, NotificationSent, CallConfirmation, and CallPlaced show radius chips dimmed with no click actions. | Avoids interrupting a pending search, notification, or call flow. |
| State and visual review | Renamed RadiusExpanded to RadiusSelected; removed Expand Radius controls and stale “widened/expanded” copy. Matching/Empty still has Retry Search and now has the secondary View Empty Screening route from the prior patch. | Screenshots reviewed at 1440×1000. Default shows only 5 km selected; the selected-radius state keeps the same tier controls and summary. |
| Figma identifiers | Radius mode collection `VariableCollectionId:197:1621`; modes `197:0` (5 km), `197:1` (10 km), `197:2` (15 km), `197:3` (20–25 km). | Matching Default `126:713`; Loading `126:899`; Empty `126:979`; Error `126:1059`; Paused `126:1139`; RadiusSelected `126:1219`; DonorsSelected `126:1299`. |
| Prototype walkthrough | Route IDs and all four tier-to-mode mappings were inspected. Browser use remains disabled in Work settings. | Prototype-mode selection of 10/15/20–25 km has not been clicked through. |

## (j) Dashboard collected-unit periods — 2026-10-27

| Review area | Result | Evidence / remaining work |
|---|---|---|
| Screen location | The period selector is on Dashboard; Blood Requests has no collected-unit-period screen. | Matches FR-014 / UC-011, which place viewing collected units on the dashboard. |
| Visible control | Replaced the misleading “This week” text/validation-error route with a three-option selector labeled “UNITS COLLECTED · ILLUSTRATIVE DEMO VALUES.” | Screenshot: [Dashboard with period selector](https://www.figma.com/api/mcp/asset/1cfe00ec-26d1-4692-a1c9-b2bd912e3f28.png). Dark mode retained. |
| Period destinations and values | This month → Dashboard Default `16:2`, 286; Past 6 months → `209:2193`, 1,482; Past year → `209:2308`, 2,936. Every state shows its active option and a range-specific illustrative note. | Values are explicitly illustrative demo totals because the HTML source only contains weekly chart points and does not supply totals for these ranges. User approved illustrative totals (Q26). No calendar or rolling date boundaries are asserted. |
| Structural route check | Each inactive period option has an ON_CLICK route to the matching frame; each state offers routes to both other periods. The selected option is intentionally inert. | Verified frame IDs, labels, totals, notes, and destinations in Figma. |
| Source difference and prototype walkthrough | The HTML offers weekly/monthly donation-trend tabs, but has no past-six-month or past-year dataset. The new selector changes the collected-units KPI; the separate Donation activity chart retains its weekly context. | Only structural routes and screenshots were checked; prototype-mode interaction verification was not performed. |
