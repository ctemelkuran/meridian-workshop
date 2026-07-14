# Executive Summary

**In response to RFP MC-2026-0417 — Inventory Dashboard Modernization**

Meridian Components' operations team depends on its inventory dashboard every day to
track stock, orders, and spend across three warehouses. That system is functional but
unfinished: the Reports module has known defects, there's no way to turn stock and
demand data into a purchasing decision, and, critically, the lack of automated test
coverage has left IT unwilling to approve further changes. The result is a dashboard
that can't safely evolve, at the exact moment Meridian's operations team needs it to.

We propose a focused, four-phase engagement that closes out the required scope (R1–R4)
ahead of Meridian's Q4 restocking season, with UI, i18n, and dark-mode improvements
(D1–D3) layered in as time allows within that window.

Our approach is sequenced around risk, not just Meridian's stated priority order. We
start with an architecture review (R4), not as a documentation exercise, but as the
foundation that makes every other phase faster and safer. Reports remediation (R1)
comes next: it's contained, high-visibility, and rebuilds confidence with the operations
team early. We then build the Restocking view (R2), the feature Meridian's VP of
Operations has specifically requested and the centerpiece of this engagement.
Automated browser test coverage (R3) is woven in throughout rather than bolted on at
the end — each phase ships with tests for the flows it touches, so IT has a
continuously growing safety net instead of a one-time deliverable.

We've reviewed the previous vendor's handoff notes and the existing codebase closely
enough to scope this confidently. The stack (Vue 3 / FastAPI) is straightforward, the
data model is simple, and the incomplete work (partial Reports filters, an Options API
migration left half-done) is well within normal handoff variance — not a sign of
deeper trouble. We're proposing a fixed-fee engagement in the $70K–$120K range,
detailed in the pricing section, with the Restocking feature and Q4 deadline treated
as the schedule's anchor.
