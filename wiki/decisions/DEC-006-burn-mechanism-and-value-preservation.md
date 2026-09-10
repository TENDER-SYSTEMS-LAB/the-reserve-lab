---
status: confirmed
attribution: user-confirmed
updated: 2026-09-10
sources:
  - SRC-2026-09-10-burn-mechanism-and-value-preservation
---

# Burn Mechanism and Value Preservation

The user corrects the assistant's proposed reading of `OPEN-27` and supplies the mechanism it was missing.
This supersedes the reading recorded in [[DEC-005-monetary-unit-banking-layer-and-mandate]] and changes
the monetary model's central rule.

## Confirmed — why R is destroyed

R's value **is falling in the general world**. Destruction exists **to preserve that value**.

The mandate to keep (`RESERVE`, [[DEC-005-monetary-unit-banking-layer-and-mandate]]) and the mechanism that
destroys money are therefore not in tension at all. Burning *is* the act of keeping: supply is reduced so
that the value of what remains is preserved.

The assistant's earlier reading — that retirement removes only the institution's undistributed remainder,
so that what is preserved is what people hold — was **wrong** and is superseded. It described a boundary,
not a purpose, and the purpose is value preservation.

## Confirmed — how R is destroyed

Two kinds of use are distinguished by their effect on total supply.

- **Between people.** When holders use R with one another, total supply **does not fall**. The units move;
  nothing is destroyed.
- **Toward the system.** When a holder uses R toward the system — machines and automated counterparties —
  the R is **burned** and leaves the supply permanently.

Destruction is therefore driven by how R is used, not only by an institutional schedule. It reduces a
holder's balance, but only through that holder's own act, so the prior guarantee that no balance is
reduced without its holder's own transfer still stands. Nothing decays, expires, or is seized.

[[DEC-003-currency-and-circulation-direction]]'s confirmed behavioral direction now has a mechanism behind
it: people store rather than spend between one another, and spend toward the system. The falling velocity
and the falling supply are the same story observed at two points — person-to-person use falling is the
velocity, system-directed use burning is the contraction.

Note the audience-language limit in [[DEC-003-currency-and-circulation-direction]]: the audience-facing
term for this category must not explicitly name AI.

## Consequences

- The base layer now has **two channels** that reduce supply: scheduled retirement from the treasury, and
  burn on use toward the system. The whitepaper's earlier invariant that settlement is the only operation
  reducing supply is false and has been corrected.
- Contraction is no longer purely deterministic. One channel follows a fixed schedule; the other follows
  behavior the protocol does not control. Non-expansion still holds unconditionally.
- Account classification becomes load-bearing rather than bookkeeping. Whether an account is a system
  counterparty now determines whether R is destroyed, not merely how a statistic is computed.
- Observed velocity gains a natural definition: person-to-person transfer volume, with system-directed use
  excluded because it is the other phenomenon rather than a form of circulation.

## Open — the fixed-unit premise

[[DEC-003-currency-and-circulation-direction]] confirms that **the value of one unit does not change**
within the artwork. This decision states that R's value **is falling** in the world and that burning
preserves it.

The reading that holds both together is that the fixed value is the **result** of the burn mechanism
rather than an independent axiom: `1R = 1R` holds *because* supply is destroyed as the value would
otherwise fall. **That reading is an inference and needs the user's confirmation**, since the alternative
is that the earlier fixed-value premise has been revised. Recorded here rather than resolved, and marked
in the manuscript as `OPEN-31`.

## Boundaries

This is a world and design decision. It confirms no parameter, approves no release, and establishes no
implementation, deployment, or economic validation. Whether burning actually preserves value is a premise
of the world, not a demonstrated monetary result.

## Sources

- [[SRC-2026-09-10-burn-mechanism-and-value-preservation]] — [raw/conversations/2026-09-10-burn-mechanism-and-value-preservation.md](../../raw/conversations/2026-09-10-burn-mechanism-and-value-preservation.md)
