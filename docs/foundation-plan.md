# Dugo+ Foundation — 2026-10-27

| Scope | Decision / acceptance |
|---|---|
| Product | Real-time blood donor matching and request coordination for Hospital Staff. |
| Platform | Desktop web, 1440px screens; sidebar navigation. |
| This step | One Foundation page containing variables/styles, main components, and a compact specimen of instances. No app screens created or migrated. |
| Visual direction | Corporate, rounded, spacious; DM Sans and Biofarma-inspired typography; Dugo+ dark palette and logo. |
| Theme | Dark only, retaining the explicit prior user decision. The new prompt contains generic light/dark placeholders rather than an explicit request to replace that decision. |
| Palette | Primary #C8283C; secondary/accent #FF8F94; background #0E0A0A; surface #1A1413; raised #221A18; field #170F0E; primary text #F3EFEC; secondary text #BCAEA2; success #8FD4A6; warning #E9BB5A; error #FF9C94. |
| Added state colors | Pressed primary #B01F33; disabled surface #2B211E and text #A59D96; border #FFFFFF26; focus #FF8F94; on-primary #FFFFFF. Values reused from existing source tokens where available. |
| Typography | DM Sans: Display 64/72 Light; H1 48/56 Light; H2 32/40 Regular; H3 24/32 Medium; Body 16/24 Regular; Body Small 14/20 Regular; Caption 12/16 Medium; Button 14/20 Medium. |
| Spacing | 0, 4, 8, 12, 16, 24, 32, 48; 4px base. Sidebar items are 44px tall with 4px gaps, inside a vertical auto-layout stack. |
| Radii | 0, 8, 12, 16, 22, full (999); 22 retained for source-compatible cards. |
| Elevation | Level 1: 0 4px 12px rgba(0,0,0,.24). Level 2: 0 12px 32px rgba(0,0,0,.40). New values chosen under the user's permission to complete unspecified tokens. |
| Button | Primary/Secondary/Ghost × Default/Pressed/Disabled × Small/Medium = 18 variants. Editable label. |
| Text input | Default/Focused/Error/Disabled = 4 variants. Label, value and helper text properties; helper never overlaps the field. |
| Supporting components | Card (2 elevations), Header, Sidebar item (default/selected/disabled), Sidebar, List item (default/selected/disabled), Avatar (3 sizes), Badge (neutral/success/warning/error), Request status (active/emergency/no match). |
| Traceability | Form/actions: FR-012, FR-016, FR-021, FR-040; UC-002, UC-013, UC-020. Navigation/card/list: UC-011–014, UC-017–018, UC-026–027, UC-031, UC-034. Request status: FR-021, FR-037; UC-020. Foundation components are not additional screens or features. |
| Resource discovery | No local component sets, components, variables, text styles or effect styles. Dugo Button/Input/Sidebar library searches returned no matches. Existing community kits have a different product/token model; create native Dugo+ components. |
| Bindings | Color semantic aliases reference primitives. All component solid paints, strokes, gaps, padding, radii and dimensions bind to tokens; every text node uses a shared token-bound text style. Image logo fill is an asset, not a color token. |
| Verification | Variant counts, component properties, token aliases/scopes/code syntax, auto-layout, bindings, equal sidebar spacing, instance specimen, screenshot. |
| Existing gap | Emergency Default inspected: Inventory and Donations have a 5px gap; a 46px gap appears between Audit Log and Hospital Profile. User reports inconsistent gaps on some screens. Record for screen migration; current request explicitly limits this step to foundations. |
| Migration boundary | New foundation does not automatically repair existing one-off screen layers. Replace those sidebars with instances during the next requested screen integration; preserve and revalidate prototype links. |
