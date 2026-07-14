# Technical Approach

This section addresses each item in RFP §3, in the sequence we'd deliver it. That
sequence is organized around risk and dependency, not strictly Meridian's stated
priority order. We start with an architecture review because it de-risks everything
that follows. We tackle Reports remediation next because it is contained and
high-visibility, and rebuilds confidence with the operations team early. We build the
Restocking view once the ground is stable underneath it. Automated testing is not a
final phase, it is threaded through all of the above, so IT sees continuous progress
rather than a single deliverable at the end.

## R4 — Architecture documentation

Before changing anything, we will audit the current system: the Vue 3 / FastAPI
stack, the data flow from filters through the API client to the backend, and the full
API surface. We will document this as a current-state overview suitable for handoff
to Meridian IT. This review is also where we expect to surface a few items worth
flagging early, for example the backend's CORS configuration currently accepts
requests from any origin, and there is no database, only in-memory JSON. Neither is
necessarily wrong for a system this size, but both are worth Meridian IT knowing about
explicitly rather than discovering later.

## R1 — Reports module remediation

The Reports page is the one part of the dashboard that never finished its migration
to the patterns used everywhere else. Where every other view has moved to Vue's
Composition API and a shared API client, Reports still runs on the older Options API
and calls a hardcoded backend URL directly. That alone explains several of the
symptoms Meridian's team has logged: filters that behave inconsistently with the rest
of the app, and formatting that doesn't match. Reports also has no internationalization
support, while five of the app's other views already use the dashboard's existing i18n
system, so currency and labels are hardcoded in English regardless of locale. We also
expect to find leftover debug logging in the browser console, based on our initial
review. We will treat Meridian's list of eight logged issues as a floor, not a
ceiling, and perform a full audit of the page before remediation. As a related, smaller
finding, the Backlog view shares the same i18n gap and we'll fold its fix into this
phase rather than opening a separate one.

## R2 — Restocking recommendations

This is the centerpiece of the engagement, and the feature we understand matters most
to the operations team day to day. The view will take three inputs, current stock
levels by warehouse, the existing demand forecast, and an operator-supplied budget
ceiling, and produce a recommended purchase order list that respects that ceiling. The
backend already exposes the stock and demand data this feature needs, and we found
that the previous vendor had already defined (but never wired up) a data model for
creating purchase orders. That's a useful head start, not a concern, and we'll build
on it rather than starting from nothing.

## R3 — Automated browser testing

There is currently no automated test coverage of any kind, which is what's made
Meridian's IT team unwilling to approve changes. Rather than deliver a single test
suite at the end of the engagement, we will add browser-based coverage as we touch
each flow, so Reports gets tests as part of its remediation, Restocking gets tests as
it's built, and IT sees the safety net grow with every phase rather than waiting on
one at the finish line. We will select which flows to cover based on risk, informed by
what the architecture review surfaces, rather than working from a fixed list decided
before we've looked at the system.

## D1 — UI modernization

We understand Meridian has a specific visual reference in mind for what "current
standards" means here. Once that reference is shared, we'll scope the refresh against
it directly rather than applying a generic redesign. This work is scheduled after the
required items and will proceed as time allows within the Q4 window.

## D2 — Internationalization

The dashboard already has a working i18n system, a composable and locale dictionaries
for English and Japanese, used by five of its seven views. Extending it to the
remaining modules is a matter of applying an existing pattern consistently rather than
introducing new infrastructure, which keeps this item lower-risk and lower-cost than
it might otherwise be.

## D3 — Dark mode

The application already defines a consistent set of design tokens, a slate and gray
color palette with status colors for green, blue, yellow, and red. Dark mode is best
delivered as a theme layer on top of those existing tokens rather than a rewrite of
component styling, and we'd plan to prototype it on a separate branch so it doesn't
put the primary work at risk.

## Assumptions

- Meridian will provide a specific visual reference for D1's "current standards."
- Budget for this engagement falls in the $70K to $120K range.
- Critical flows for R3 will be selected based on risk, informed by our architecture
  review, rather than a predetermined list.
- The previous vendor's handoff documentation is adequate but outdated; we expect to
  verify it against the codebase rather than reconstruct it from scratch.
- Delivery of the required items (R1–R4) is targeted ahead of Meridian's Q4
  restocking season, with desired items (D1–D3) addressed as time allows within
  that window.
