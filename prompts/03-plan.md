(Use Plan mode.)
Using ONLY docs/dugo-spec.md, /html, and docs/decisions.md, write:
1. docs/tokens.md: exact values copied from the HTML CSS (colors, fonts, sizes, spacing, radii, shadows). Missing token? Ask, don't invent.
2. docs/components.md: shared components (buttons, inputs, badges, tables, cards, sidebar, topbar, modals, urgency and blood-type badges) with variants, derived from the HTML.
3. docs/build-plan.md: ordered table of every screen: # | Role | Viewport (1440/390) | UC IDs | FR IDs | Source (html file or NEW) | Components | States | Next screen (prototype link).
4. docs/flows.md: each prototype flow as a numbered screen chain.
5. docs/traceability.md: every FR and UC -> screen #. Flag any with no screen.
Finally run the rejection check: list every item in these files that is not in the spec, HTML, or decisions.md and label it ASSUMPTION. If any exist, convert them to questions and stop.
