# Corporate visual review — 2026-10-27

| Item | Plan / evidence |
|---|---|
| Authorization | User requests visual/documentation audit and alteration to closely follow https://biofarma.com.ar/. Existing Hospital Screen Build approval remains in effect. This is a refinement of built screens; no new Hospital workflow is added. |
| Reference | Public Biofarma homepage inspected in browser. DM Sans, light heading weight (300), rounded inset header, medical hero image, pill CTA, spacious section hierarchy. |
| Preserved requirements | Dugo+ logo and copy; dark mode; Hospital scope; no role selector; no SMS; partnership inquiry; existing node IDs and routes wherever possible. |
| Reference differences | Dark Dugo+ palette replaces the reference's light palette. Product-specific sections and Hospital workflows remain. Biofarma's brands, claims, geographic coverage and clinical products are not adopted. |
| Landing plan | Inset rounded header, medical hero with dark contrast gradient, large left-aligned DM Sans Light headline, pill Sign In CTA, three capability panels, lighter section headings and consistent spacing. Preserve all source sections/footer and partner entry. |
| Existing screens plan | Unify major titles with DM Sans, improve muted text contrast and panel treatment, retain input positions and state destinations. Restore all Login footers to the full 1400px content height. |
| Visual defect V01 | Seven Emergency Request error text nodes (87:2–87:8) are page children, outside ValidationError. Reparent into 85:250 and position below their corresponding fields. Previous verification claim was incorrect. |
| Visual defect V02 | Login roots have inconsistent 900/1212/1390px heights while their footer extends to y=1400. Standardize content bounds and verify footer visibility. |
| Documentation D01 | Q11 says Sign In is the only active landing route; Q22-A superseded it with Partner Inquiry. Correct current resolution. |
| Documentation D02 | Q20 still says Partner Inquiry is pending Q22, although Q22-A is resolved. Correct current resolution. |
| Documentation D03 | design-tokens.md has malformed table separators. Correct and document reference-driven typography overrides separately from exact source tokens. |
| Documentation D04 | Handoff states every Login frame is 1440×900; live dimensions differ. Record actual full content size and distinguish previous snapshots from current evidence. |
| Documentation D05 | UC-021 explicitly includes already-expired sessions; preserve that alternative and distinguish it from deferred NFR-14 automatic session timeout. |
| Resource discovery | No Code Connect files found; current file has zero components, variable collections, or text styles. No subscribed design library. Existing editable layers will be refined in place to retain prototype IDs; importing unrelated community kits would not match the reference. |
| Verification | After edits: check top-level overlaps, orphan text, text clipping candidates, destination validity, and representative screenshots. A structural route check is not a prototype-mode walkthrough. |
| Status | Refinement and targeted repairs applied. See final evidence below. |

## Final evidence

| Check | Result |
|---|---|
| Visual result | Hero uses the reference medical photograph, dark contrast gradient, inset rounded header, light DM Sans headline, pill CTA and three capability panels. [Saved screenshot](review-assets/corporate-landing-hero.png). |
| Additional repairs | Fixed 16 pre-existing sibling text overlaps; then corrected 9 oversized title boxes introduced during refinement and 1 overflowing button label. |
| Final geometry | 46 frames with zero overlaps; zero orphan text; 2,062 visible text layers checked with zero sibling box collisions and zero parent-bound overflow. This is a geometric audit, not a guarantee against every possible visual issue. |
| Prototype connections | 373 navigation targets resolve; all 4 Loading screens retain timed destinations. No full prototype-mode walkthrough performed in this review. |
| Login | All nine Login states now have 1440×1400 content bounds, including the complete footer. Typography changed to DM Sans; decorative circles removed. |
| Visual comparison | The hero matches Biofarma's main composition and actual medical artwork; Dugo+ dark colors, logo, English product copy, static marketing sections and Hospital dashboard layouts intentionally differ. It is not a pixel-identical clone of the entire site. |
| Resource limitations | Existing screen tree remains editable but predominantly individual layers, without a reusable component library. This review does not claim componentization. |
| Image issue | WebP upload returned success but rendered black. PNG conversion of the same image rendered correctly and is the final fill (hash 0d68806ea804f542d13252025557de45772f08c4). |
| Historical correction | Earlier Emergency validation verification was inaccurate: seven messages were page children. They are now inside the validation frame. Earlier full-footer claims did not match all Login frame bounds; those bounds are now repaired. |
| Documentation corrected | Q11/Q20 current routing; malformed token-table separators; visual overrides; stale Login/Landing dimensions; duplicated Landing node record; approval scope wording; UC-021 versus NFR-14 distinction. |
| Content limitation | Marketing statistics, news examples and illustrative partner names remain source-reference content; this visual review does not establish them as independently verified facts. |
| Next build | Donor Matching remains next; no new screen family was built in this review. |
