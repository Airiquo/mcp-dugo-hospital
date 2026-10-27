# Decisions log
Format: `YYYY-MM-DD | Q-ref | Decision | Decided by`

2026-10-26 | pre | Admin scope limited to hospital account creation and related management (accounts, system params, data requests, audit verify, own profile) | user
2026-10-26 | pre | Existing admin-blood-requests/donor-matching/inventory/donations-rewards/reports HTML pages were candidates for Hospital-dashboard screens; Q1 later confirmed all five | user
2026-10-27 | scope | Finish the Hospital side only (no Admin, Donor, Recipient screens) | user
2026-10-27 | Q1 | Use all five existing pages (blood requests, matching, inventory, donations, reports) as the Hospital dashboard; Q20 later removes Reports from scope because it has no supporting Hospital FR/UC ID | user
2026-10-27 | Q2, Q5, Q8 | Close Admin, Donor, and Recipient questions as OUT OF SCOPE under the Hospital-only scope | user
2026-10-27 | Q3 | Remove every SMS reference from Hospital screens; notifications are in-app and email only | user
2026-10-27 | Q4 | Cover all listed Hospital UCs: UC-002, UC-011 through UC-018, UC-020, UC-021, UC-026, UC-027, UC-031, and UC-034 | user
2026-10-27 | Q6, Q14 | Reuse the landing sign-in panel with role routing for Hospital login | user
2026-10-27 | Q7 | Subscription screen shows plan names and features, with no prices | user
2026-10-27 | Q9 | Use an OSM-styled map mockup | user
2026-10-27 | Q10 | Every Hospital data screen needs default, empty, error, and loading states, plus applicable UC-specific states (validation error, consent missing, access denied, cancel) | user
2026-10-27 | Q11 | Keep the landing page as-is, with the sign-in panel and role routing | user
2026-10-27 | Q12 | Keep manual matching actions per Q16; no-ID pages and features are superseded by Q20 and removed from scope | user
2026-10-27 | Q13 | Ignore the template server row because it is outside UI scope | user
2026-10-27 | Q15 | Initially keep Reports, Donor Registry, and Settings beyond the Facility tab; superseded by Q20 and removed from scope because they lack supporting Hospital FR/UC IDs | user
2026-10-27 | Q16 | Keep all manual matching actions: Pause, Expand radius, Call, and Notify | user
2026-10-27 | matching-radius-controls | Remove the separate “Expand radius” button. Make 5 km, 10 km, 15 km, and 20–25 km direct, selectable search-radius options. This supersedes the Expand radius portion of Q16; Pause, Call, and Notify remain. | user
2026-10-27 | Q17 | Mask donor names in the donations ledger | user
2026-10-27 | Q18 | Build UC-015, UC-014, UC-016, UC-018, and UC-034 as new screens | user
2026-10-27 | Q19 | Use role label “Hospital Staff” and page title “dugo+ hospital” on Hospital pages | user
2026-10-27 | theme | Use dark mode only for the Hospital prototype | user
2026-10-27 | Q20 | Remove Reports, Donor Registry management, Settings tabs beyond Facility, and other no-ID HTML features from Hospital scope | user
2026-10-27 | visual-direction | Remove role selection from the Hospital sign-in UI. Treat HTML as a rough visual reference and allow more polished, original styling across the remaining Hospital screens. Keep the spec and approved scope authoritative for behavior, and retain dark mode, Hospital Staff identity, and all FR/UC requirements. | user
2026-10-27 | landing-reference | Use `/Users/pol/Downloads/landing_1(1).html` as an additional reference for the Hospital landing/sign-in visual system and overall Hospital UI. Use its embedded Dugo+ logo. Its dark palette is the preferred visual reference; keep non-ID marketing content out of the Hospital scope. | user
2026-10-27 | login-reference | Use the live login at `https://dugo-plus.web.app/login` and `/Users/pol/Documents/dugo_mobile_web/web/src/pages/public/Login.jsx` plus `web/src/layout/AuthLayout.jsx` as the Hospital login layout reference. Keep the no-role-selector decision and Hospital-only UC-002 scope; omit donor Google login, self-registration, and password recovery. | user
2026-10-27 | prototype-interactions | Wire the Figma screens so the clickable prototype mimics the approved Hospital user flows, including navigation and state transitions; do not leave live-looking controls static. | user
2026-10-27 | landing-flow-override | Include the supplied landing page as the first Hospital prototype page and entry shell, styled in dark mode from its dark theme and Dugo+ logo. Its only functional path is Sign In → Hospital Login; no role selection or Donor/Recipient journeys. This overrides Q20 only for the landing entry page; no-ID Reports, Registry management, and extra Settings content remain removed. | user
2026-10-27 | landing-refinement | Center the Landing headline, supporting copy, and Hospital sign-in CTA within the hero text column; follow the supplied dark-mode landing composition more closely, including its large right-side gradient blood drop, while preserving Hospital-only prototype routing. | user
2026-10-27 | landing-full-page-override | Include the supplied landing HTML’s remaining content sections and full footer as a static, dark-mode Landing page, close to the reference. Keep Hospital Sign In as the only active journey out of public marketing content; static donor/recipient copy and decorative controls do not route to Donor/Recipient screens. Restore the shared landing footer on all Hospital Login states, without Admin-only links. Continue honoring the no-SMS rule. | user
2026-10-27 | Q6-clarification | Hospital sign-in is a direct Hospital-specific login with no role-selection UI; this supersedes the earlier “role routing” wording in Q6/Q14. | user |
2026-10-27 | partnership-model | Remove Hospital subscription management (FR-018/UC-015) from the prototype despite the earlier Q4/Q7/Q18 scope answers. Add an active “Become a Partner” CTA in the Landing Partners section, leading to a form for Hospital email, contact, and location; Send leads to a “request received / we’ll get back to you” confirmation screen. This also supersedes the landing rule that Hospital Sign In is the only active public route. The partner flow is flagged pending Q22's requirement-ID resolution. | user |
2026-10-27 | Q22 | Choose C: defer the public Partner Inquiry form and confirmation flow because the approved spec has no matching FR/UC ID. Keep the Landing “Become a Partner” CTA visible but static/inert until an applicable requirement ID is approved. This supersedes the active-route portion of `partnership-model`; the subscription screen remains removed. | user |
2026-10-27 | Q22-revision | Supersede the earlier Q22-C deferral with Q22-A: build the Partner Inquiry as a public intake step supporting FR-040. It only collects a request for Dugo+ follow-up; Hospital account creation, suspension, and removal remain System Admin actions under FR-040. Keep dark mode and the previously specified facility, hospital email, contact, location fields, and received/follow-up confirmation. | user |
2026-10-27 | prototype-realistic-flows | Make the prototype demonstrate the user journey, not just display screens: clicking form fields reveals sample entered values or selections; empty/partial submissions show the specific validation error; completed forms move through Loading to their correct confirmation/result; and every Loading state has a verified next step. Audit every built screen's primary and recovery interactions. Figma Design free-text entry must not be claimed unless verified; use visible click-to-fill demo values when needed. Remove accidental translucent overlays, including the washed-out Hospital Login frame. | user |

2026-10-27 | corporate-reference | Audit visual and documentation errors and refine the existing design to closely follow https://biofarma.com.ar/. User permits visual changes needed for a corporate appearance; retain Dugo+ identity, dark mode and approved behavior. Reference-driven typography and composition supersede earlier exact visual-matching instructions where they conflict. | user

2026-10-27 | foundation-first | Build a design foundation only on a page named Foundation: token variables/styles, typography scale, 4px spacing, two elevations, and reusable auto-layout component variants. Choose and report unspecified token values. No new app screens in this step. Existing screen spacing issue is recorded for later component migration. | user

2026-10-27 | emergency-sidebar-integration | Apply the consistent Foundation sidebar to the existing Emergency Request state family, preserving navigation and request content. | user

2026-10-27 | Q23 | Apply the consistent Foundation sidebar to all remaining existing Hospital screens; do not build Donor Matching in this pass. | user
2026-10-27 | matching-scaffold | Continue with the Donor Matching screen scaffold after the sidebar pass. Build the Matching states and wire the Hospital user flow under FR-017, FR-021, FR-031, UC-012, UC-020, UC-027, NFR-05, and Q16. | user
2026-10-27 | matching-identity-screening-patch | Preserve the selected masked donor through matching, notification, call, and screening states; add the UC-027 status-recording and donation-confirmation flow. | user
2026-10-27 | sign-out-color | Use the light-red Foundation accent token (#FF8F94) for Sign out labels across Hospital sidebar instances. | user
2026-10-27 | donation-screening-details | Redesign the UC-027 screening workspace to show donor identity details and valid-ID status, consent/access status, donor-submitted questionnaire answers numbered from 1, prior donation history below, and a right-side summary of potentially relevant answers. Until the facility supplies approved eligibility rules, those answers are clinician-review flags only; do not label donors ineligible automatically. Keep donor identity separate from eligibility status and use fictional prototype records. | user
2026-10-27 | Q24 | Keep potential deferral answers as clinician-review flags until facility-approved criteria are supplied; do not automatically classify a donor as ineligible. | user
2026-10-27 | Q25 | Separate donor self-reported answers, staff screening/documentation, and aftercare into distinct sections. | user
2026-10-27 | Q26 | Dashboard collected-unit period selector should offer This month, Past 6 months, and Past year. Use clearly labeled illustrative demo totals because the source supplies no values for these ranges. | user
