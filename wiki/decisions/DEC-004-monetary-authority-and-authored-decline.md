---
status: confirmed
attribution: user-confirmed
updated: 2026-09-10
sources:
  - SRC-2026-09-10-whitepaper-sections-1-4-decisions
---

# Monetary Authority and Authored Decline

Two blocking questions raised by the drafted whitepaper Sections 1–4 are now decided by the user. They
resolve `OPEN-02` and `OPEN-03` in [whitepaper/R-white-paper-v0.2.md](../../whitepaper/R-white-paper-v0.2.md)
and narrow the first priority in [[Q-001-institutional-scope]].

## Confirmed — THE RESERVE is the central bank and issuing authority

Within the world, THE RESERVE is a **central bank and the issuing authority of R**. It is not a commercial
bank layer, and the base-layer role is not shared with another institution.

This settles the institutional question for the monetary base only. It does not by itself state whether
the same institution later operates deposit-taking, lending, or other banking functions denominated in R;
[[DEC-005-monetary-unit-banking-layer-and-mandate]] subsequently confirms that it does, and also supplies
the mandate that the consequences below record as missing.

## Confirmed — declining velocity is authored world history

Declining velocity is **a defined result within the worldview**, stated as the world's own history. The
user accepts explicitly that velocity **cannot be controlled by the protocol**.

The two halves must be held together. The decline is a fact of the world, not a protocol guarantee, not a
prediction about the public chain, and not a claim that observation will confirm it. Actual on-chain
velocity may rise.

**Superseded in part.** [[DEC-007-burn-accounting-payer-and-genesis-date]] states that R exists only within
the world and cannot be held by an actual person, so there are no real participants and the divergence this
decision accepts cannot arise. [[DEC-008-contraction-curve-simulation-and-ledger-scope]] then settles what
replaces it: the flows are **simulated**, and the Reserve Observer publishes a generated series rather than
an independent measurement. The first half of this decision stands — the declining velocity is authored
world history, and the protocol cannot control velocity. The expectation of real on-chain participation
does not. That divergence is a known and accepted condition of the design, not a defect and not
something the record should conceal.

This resolves the design tension recorded in [[r-monetary-protocol]] between the world's declining
velocity and the drafts' intent to record real behavior. The resolution is a boundary, not a mechanism:
world history is authored, chain observation is measured, and the two are reported as separate things.

## Consequences the decisions carry

- Decentralization is not a goal of R. A central bank issuing base money and authorizing release is the
  intended structure, so permissioned release is the normal case rather than an unresolved compromise.
  The exact permission model, key custody, and upgrade authority remain undecided.
- The contraction schedule is fixed and blind to markets by prior design, so the authority's remaining
  discretion sits almost entirely in release. What the mandate of a central bank with one instrument
  actually is has not been stated.
- Whether R is a liability of THE RESERVE, given that no redemption is offered, is now a live question
  that the central-bank role raises and does not answer.

## Boundaries

These are world and design decisions. They confirm no parameter, approve no release, and establish no
legal entity, regulatory classification, or actual central-banking function outside the work. The prior
limits in [[DEC-003-currency-and-circulation-direction]] remain in force, including the fixed-unit premise
as an artwork premise rather than a purchasing-power guarantee.

## Sources

- [[SRC-2026-09-10-whitepaper-sections-1-4-decisions]] — [raw/conversations/2026-09-10-whitepaper-sections-1-4-decisions.md](../../raw/conversations/2026-09-10-whitepaper-sections-1-4-decisions.md)
