---
status: confirmed
attribution: user-confirmed
updated: 2026-09-10
sources:
  - SRC-2026-09-10-contraction-curve-simulation-and-ledger-scope
---

# Contraction Curve, Simulation, and Ledger Scope

Four decisions resolve `OPEN-33`, `OPEN-34`, and `OPEN-35` in
[whitepaper/R-white-paper-v0.2.md](../../whitepaper/R-white-paper-v0.2.md) and settle where the world's
elapsed history sits relative to the record. They follow
[[DEC-007-burn-accounting-payer-and-genesis-date]] and supersede part of
[[DEC-004-monetary-authority-and-authored-decline]].

## Confirmed — the contraction is not a constant exponential

The schedule is **not** a constant-rate exponential across the whole interval. The user gives the reason
directly: what the work is about does not fall in a straight line. It falls **with noise**, and it falls
**slowly at first and then faster** — accelerating.

Two properties are therefore confirmed for the curve:

- **Accelerating.** The rate of decline increases with elapsed time. Early loss is slight; later loss is
  steep.
- **Noisy.** The realized path is not smooth.

The confirmed anchor from [[DEC-007-burn-accounting-payer-and-genesis-date]] still holds: about 50%
remains at 50.98 years. The earlier draft parameter of 3% annually is now doubly inapplicable — it is both
the wrong magnitude and the wrong shape.

No functional form or parameter is confirmed by this turn. The manuscript proposes a stretched-exponential
schedule with a shape parameter, fitted to the 50% anchor, and marks the form and its parameters as
unconfirmed.

**One constraint the noise cannot break.** Total supply never rises — that invariant is not negotiable and
predates this decision. Noise therefore appears as **variation in the speed of decline**, never as a
fluctuation upward. Recorded in the manuscript as a rule rather than left implicit.

## Confirmed — there are no real participants, and the data is simulated

There are no real participants and the divergence between world record and observation **cannot arise**.
That much confirms the conflict recorded as `OPEN-35`.

The user adds the part that resolves it rather than merely closing it: the system exists within the world,
and although there are no actual users, **it can be simulated**. The declining velocity is a flow that
**runs on simulated data**.

This supersedes the second half of [[DEC-004-monetary-authority-and-authored-decline]]. That decision
accepted that a public chain would record whatever velocity real participants produced, including a rising
one, and the manuscript's divergence rule existed to handle exactly that case. There are no such
participants, so:

- The Reserve Observer does not observe independent behavior. It publishes a **simulated** series.
- Measurement is no longer a check on the world record. Both are authored; they differ in how they are
  produced, not in whether they are.
- The declining velocity remains authored world history — the confirmed position in
  [[DEC-004-monetary-authority-and-authored-decline]] — and simulation is how that history is expressed as
  data rather than as a claim.

The honesty requirement moves rather than disappears: the document and anything the audience sees must say
that the series is simulated, instead of implying an independent measurement it does not have.

## Confirmed — what the deployment is

The deployment is **both** things the manuscript listed as alternatives, not one of them:

- a **public ledger that displays the world's monetary history**, and
- a **rule implementation whose accounts exist only within the world**.

There is no distribution to actual persons, consistent with
[[DEC-007-burn-accounting-payer-and-genesis-date]].

## Confirmed — the elapsed history sits before the record

The decline from 1975 to the present — the interval over which about 50% was lost — is placed **before the
record**.

The ledger therefore opens with supply already reduced, not at the original quantity. Genesis and the
original quantity remain facts of the world's history and are documented as such; they are not the
ledger's opening state. The epoch index continues to count from 1975, so the record opens at roughly epoch
2,660 rather than at epoch 0.

## Boundaries

These are world and design decisions. They confirm no curve parameter, no quantity, and no deployment
target, and they establish no implementation, audit, or economic validation. That the schedule
accelerates and the path is noisy are properties of the world's history, not measurements.

## Sources

- [[SRC-2026-09-10-contraction-curve-simulation-and-ledger-scope]] — [raw/conversations/2026-09-10-contraction-curve-simulation-and-ledger-scope.md](../../raw/conversations/2026-09-10-contraction-curve-simulation-and-ledger-scope.md)
