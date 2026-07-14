# Timeline

Phased delivery, sequenced by risk and dependency as described in our technical
approach. Total duration is approximately 12 weeks, comfortably ahead of Meridian's
Q4 restocking season.

| Phase | Weeks | Scope |
|---|---|---|
| 1. Architecture review | 1–2 | Audit stack, data flow, API surface. Produce current-state documentation (R4). Flag findings (CORS, data storage) for Meridian IT. |
| 2. Reports remediation | 3–4 | Full defect audit and fix: API/Options-API migration, i18n, logging cleanup, filter behavior (R1). Browser tests for Reports flows (R3, partial). Backlog i18n fix folded in. |
| 3. Restocking build | 5–9 | Design and build the Restocking view: stock, demand, and budget-ceiling inputs; PO recommendation output; backend endpoint (R2). Browser tests for Restocking flows (R3, partial). |
| 4. Test coverage close-out | 10 | Fill any remaining gaps in browser coverage across critical flows, informed by what phases 1–3 surfaced (R3, complete). |
| 5. Desired items (time-permitting) | 11–12 | UI refresh against Meridian's reference (D1), remaining i18n modules (D2), dark mode prototype (D3), in that order, as time allows. |

Phases 1–4 (R1–R4) are the committed scope and represent our not-to-exceed price.
Phase 5 (D1–D3) is scoped and priced separately in the pricing section below, and is
delivered within the same 12-week window only if capacity allows; it does not extend
the Q4 deadline for required items.

We'd confirm this schedule against an actual start date once the engagement is
awarded, and would flag immediately if anything discovered during the architecture
review (Phase 1) changes our estimate for later phases.
