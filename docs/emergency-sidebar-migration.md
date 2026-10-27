# Emergency Request sidebar migration

| Plan | Acceptance |
|---|---|
| Authorization | User: “apply the consistent sidebar”; continues approved Hospital Screen Build. |
| Scope | Ten existing Emergency Request states; FR-021 / UC-020. |
| Component | Foundation Sidebar `106:131`, set `106:158`; linked instances, no detachment. |
| Layout | Fit existing 220px rail; 44px rows, 4px uniform gaps; preserve body layout and 1440×1000 frames. |
| Behavior | Preserve Dashboard, Blood Requests and Sign out destinations; leave unbuilt destinations explicitly pending. Preserve request forms and timed Loading route. |
| Verification | Instance geometry and route comparison; screenshot; attempt prototype-mode walkthrough. Record structural and runtime evidence separately. |

| Result | Evidence |
|---|---|
| Migration | All ten Emergency Request states now contain linked sidebar instances. Instance/frame IDs and original layer inventory are in [state ledger](emergency-sidebar-state.json). |
| Geometry | 220×1000 rail, 188×44 menu rows, seven 4px gaps per state. No sidebar text overflow; DM Sans throughout; screen opacity 100%. |
| Content preservation | Before/after body geometry and reactions matched in all ten states. Loading still has its timed destination to Confirmation `85:597`. |
| Routes | Dashboard→`16:2`, Blood Requests→`54:2`, Sign out→`4:2`; all inspected destination IDs exist. Sign out is attached only to its button, not the sidebar root. |
| Prototype-mode verification | Browser click walkthrough from Emergency Default passed Dashboard, Blood Requests and Sign out; observed destination URLs match the recorded IDs. Restart returned to Emergency Default between cases. |
| Limits | Full form primary/validation/recovery journey was not retested. Matching, Inventory, Donations, Audit Log, Hospital Profile and Location destinations remain pending their screens; they were not invented. |
| Screenshot review | Full 1440×1000 Emergency Default screenshot inspected after composition; no sidebar overlap, clipping or accidental washout. Final Sign out correction changed behavior only. |
| Differences vs plan/source | Plan met. Original 36px manually positioned rows replaced by 44px auto-layout rows with uniform 4px gaps. Foundation master remains 240px wide; instances fit the source 220px rail. Original logo retained; old small brand subtitle and footer rule replaced by the Foundation composition. No request content changed. |
| API calls | Six Figma calls: one session and five use_figma calls, including one oversized read response that made no changes. Screenshot was returned within an audit call. |
| Remaining | Other screen families retain their existing sidebars. Migrate one requested family at a time; preserve routes and test them after integration. |
