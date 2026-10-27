# Remaining Hospital sidebar migration — 2026-10-27

| Plan | Acceptance |
|---|---|
| Authorization | Q23-A explicitly covers all remaining existing Hospital sidebars. |
| Scope | Five Dashboard states (UC-011) and twelve Blood Requests states (FR-016/017/037, UC-012/013). |
| Layout | Linked Foundation Sidebar `106:131`; existing 220px rail; 44px rows separated by 4px; correct selected item. |
| Preservation | Retain all existing navigation reactions and body geometry/content/routes. Keep Sign out on its button only. |
| Exclusions | Public Landing/Login/Partner Inquiry have no Hospital sidebar. Emergency Request already migrated. No new screen construction. |
| Verification | Structural comparisons across all states; representative full screenshots; runtime sidebar navigation checks. Full form walkthrough is a separate unfinished item. |

| Result | Evidence |
|---|---|
| Completed | Five Dashboard and twelve Blood Requests states migrated. Together with ten Emergency Request states, all 27 existing authenticated sidebar states now use Foundation `106:131`. No legacy Hospital sidebar rectangles remain. |
| State ledger | [Exact created/removed IDs and per-state checks](remaining-sidebar-state.json). |
| Structural checks | All 17 bodies unchanged (content, geometry and reactions); seven 4px gaps per sidebar; no sidebar text overflow; 100% frame opacity; correct selected item; root reactions empty. All sidebar destination IDs resolve. |
| Visual checks | Full Dashboard and Blood Requests composition screenshots inspected in the Figma tool response. Dark palette and supplied logo retained; DM Sans confirmed. No sidebar overlap or clipping. |
| Prototype-mode checks | Passed Dashboard→Blood Requests (`54:2`), Blood Requests→Dashboard (`16:2`), Dashboard Sign out→Login (`4:2`), and Blood Requests Sign out→Login (`4:2`) through actual browser clicks. |
| Scope of testing | Runtime tests cover Default-state sidebar actions. Other state routes checked structurally; full form primary/recovery journeys were not retested or declared complete. |
| Plan / HTML differences | Plan met. Manual 36px source rows replaced by Foundation 44px rows with 4px gaps. Instances retain the original 220px rail rather than master 240px width. Foundation brand and staff footer composition replaces the old subtitle/footer rule. |
| Pending destinations | Matching, Inventory, Donations, Audit Log, Hospital Profile and Location remain unbuilt destinations; migration does not create them. |
| Figma efficiency | Three use_figma calls in this continuation: scoped inspection, batched migration, and audit with two composition screenshots. Existing session reused. |
