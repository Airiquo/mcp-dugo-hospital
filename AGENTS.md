# Dugo+ UI Prototype: Working Rules (non-negotiable)

Project: Dugo+, a real-time blood donor matching system (BulSU IT303).
Goal: finish a Figma UI prototype that follows the documentation and reuses the design of the HTML files in /html.

## Source of truth (in this order)
1. docs/dugo-spec.md (FR, NFR, UC, ERD, DFD). docs/dugo-spec.pdf is the original.
2. /html files (visual design, layout, copy, tokens)
3. My answers in chat, recorded in docs/decisions.md

## Anti-default rules
1. Never fill a gap with "common practice", "typically", "by default", or "assuming". If something is unspecified, contradictory, or has more than one reasonable reading, DO NOT choose. Add it to docs/open-questions.md and ask me.
2. Ask in ONE numbered batch, max 8 questions. Each has 2-4 labeled options (A/B/C) plus "Other". Then STOP and wait for my reply.
3. Every decision I give goes into docs/decisions.md with the date. Read docs/decisions.md and docs/open-questions.md at the start of every session.
4. Every planned screen must cite FR/UC IDs. A screen with no ID gets flagged, not built.
5. Design tokens (colors, fonts, spacing, radii, shadows) must be copied exactly from the HTML CSS. Never describe or approximate a value. If a token is missing, ask.
6. Do not call any Figma write/create tool until I type exactly: APPROVED: <phase name>.
7. Before any Figma call, state the tool name and its inputs. After building, screenshot and list differences vs. the plan and the source HTML.
8. One screen (or one component set) per session in the build phase. Do not continue to the next on your own.
9. Report facts, not reassurance. If a step failed or is incomplete, say so.
10. **Realistic prototype flows:** Every form field must respond to interaction by showing a value or selected option. Empty and partially completed submissions must route to the matching field-level validation state; completed submissions must pass through Loading and then reach the correct success/detail state. Every Loading state must have a verified next destination or explicit retry path. Test every built screen's primary path and recovery path in prototype mode before calling the flow complete. If Figma Design cannot accept arbitrary typed text, use clearly labeled, click-to-fill example values and do not claim free-text entry. Login must demonstrate email-only/password-missing validation and a complete credential path. Keep top-level screen opacity at 100% unless a documented visual treatment requires otherwise; inspect screenshots for unintended overlays or washout.

## Role scope (from the spec)
- Admin: create hospital accounts; suspend/remove hospital and donor/recipient accounts; configure matching radius tiers and notification retry; process data-subject requests; view audit log and verify record integrity; login/logout; view own profile (FR-040, 041, 035, 039, 044, 046, 047; UC-028 to 033).
- Admin does NOT handle blood requests, matching, inventory, screening, or donation confirmation.
- Hospital staff: requests, emergency requests, screening, inventory, donation history, subscription, profile, location (UC-011 to 018, 020, 026, 027, 034), plus audit log view (UC-031).
- Donor / Recipient: mobile web app (390px). Hospital / Admin: web dashboard (1440px).
- Notifications are in-app and email only (no SMS).
- NFR-14 (session timeout) is DEFERRED: do not design it.

## Output conventions
- Plans and audits are written to files in /docs, in tables, not prose.
- Figma layer names: `<Role>/<ScreenName>/<State>`; components: `Cmp/<Name>`.

## Recorded user overrides (latest decisions take precedence where they conflict)
- The 2026-10-27 visual-direction and corporate-reference decisions allow redesign of HTML styling. Use Biofarma as the latest corporate visual reference while retaining dark mode and the supplied Dugo+ logo. See docs/design-tokens.md for exact applied values.
- Subscription management (FR-018/UC-015) is removed from prototype scope. Public Partner Inquiry is approved as supporting FR-040 intake under revised Q22-A; it does not create an account.
- The 2026-10-27 visual/documentation review covers existing screens. New screen construction still follows the one-screen-per-request rule.
- Distinguish structural route checks from prototype-mode walkthroughs. Record exactly which was performed; never infer that valid destination IDs establish full journey correctness.
