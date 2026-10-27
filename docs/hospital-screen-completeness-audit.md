# Hospital screen completeness audit — 2026-10-27

| Area | Status | Evidence / remaining work |
|---|---|---|
| Figma inventory | 69 top-level frames; zero top-level overlaps | Families: Landing 1, Login 9, Dashboard 5, Partner Inquiry 9, Blood Requests 12, Emergency Request 10, Donor Matching 11, Donation Verification 12. |
| Landing, Login, Dashboard, Partner Inquiry | BUILT | All approved entry, sign-in, dashboard and partner intake families are present. |
| Blood Requests, Emergency Request | BUILT | Form, validation, loading, empty/error and confirmation states are present. |
| Donor Matching | BUILT | 11 states; three masked donor choices set the selectedDonor prototype variable and carry it through notification, call and screening. Q16 actions remain. |
| Donation Verification | PARTIAL | 12 UC-027 states under Hospital/DonationVerification: Cleared/Deferred/Rejected, validation, missing record, save failure/retry, and cleared-only completed-donation confirmation. Q10 Empty and Loading states are missing; the save path currently skips a loading state. |
| Inventory and updates | MISSING | FR-020/FR-034; UC-017/UC-026. The Inventory sidebar item currently has no destination. |
| Donor donation history | MISSING | FR-020/FR-038; UC-014; NFR-11/NFR-16. Needs consent/authorization checks, empty/loading/error states, and protected-data denial. |
| Secure donor information | MISSING | FR-019/FR-038; UC-016; NFR-11/NFR-16. Needs consent-missing, access-denied, retrieval-error and authorized-data states. |
| Hospital profile | MISSING | FR-013; UC-018. The Hospital Profile sidebar item currently has no destination. |
| Hospital location map | MISSING | FR-015; UC-034; NFR-09. The Location sidebar item currently has no destination. |
| Audit log | MISSING | FR-035; UC-031; NFR-15. The Audit Log sidebar item currently has no destination. |
| Donations navigation | PENDING | The Donations sidebar item has no destination; route it when the approved donation/history destination is built. |
| Logout | PARTIALLY BUILT | All 50 Sign out labels use the Foundation light-red accent #FF8F94, and all 50 label ancestors route to Hospital Login. UC-021 already-expired-session and connection-failure alternatives are still pending. NFR-14 timeout remains deferred. |
| Data-screen states | PARTIAL | Matching, Dashboard, Blood Requests, Emergency Request, and Partner Inquiry have their planned state families. Donation Verification still needs Empty and Loading; unfinished screen families need their planned Default/Empty/Error/Loading and UC-specific states when built. |
| Other no-ID features | OUT OF SCOPE | Reports, Donor Registry management, subscription management, extra Settings tabs, SMS, and unsupported fallback release remain excluded under the recorded decisions. |
| Prototype-mode walkthrough | PENDING | Structural destinations were inspected; browser control is disabled in this session, so actual clicks and timed transitions were not witnessed. |
