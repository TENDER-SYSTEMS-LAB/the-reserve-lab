---
status: confirmed
attribution: user-confirmed
updated: 2026-09-10
sources:
  - SRC-2026-09-10-burn-accounting-payer-and-genesis-date
---

# Burn Accounting, Payer, Fixed Value, and Genesis Date

Five questions raised by the drafted manuscript are decided. They resolve `OPEN-28`, `OPEN-29` in part,
`OPEN-30`, `OPEN-31`, and `OPEN-32` in
[whitepaper/R-white-paper-v0.2.md](../../whitepaper/R-white-paper-v0.2.md), and follow
[[DEC-006-burn-mechanism-and-value-preservation]]. Two of them have arithmetic and scope consequences that
the deciding turn did not address; those are recorded below rather than resolved.

## Confirmed — burn counts toward the contraction target

R burned through use toward the system counts toward the contraction target. The two reduction channels
are not independent: what holders destroy reduces the retirement the treasury must perform.

The consequence follows mechanically from the settlement formula, which retires
`max(0, S − S*)`. When burn has already carried actual supply below target, the required retirement is
zero and settlement does nothing. **Supply may therefore fall below the target and stay there**, which
settles `OPEN-18`: the target is a ceiling that supply must not exceed, not a floor it descends toward.

## Confirmed — THE RESERVE designates system accounts

THE RESERVE designates which accounts are system accounts.

Because a transfer to a system account destroys the amount sent
([[DEC-006-burn-mechanism-and-value-preservation]]), this is a monetary power rather than bookkeeping: the
institution defines the boundary of the destruction channel. It also settles the classifying authority
left open as `OPEN-09`; whether a designation can later change, and by what procedure, is still unstated.

## Confirmed — the initial payer, and that R cannot be held outside the world

The initial payer is **THE RESERVE**. R exists **only within the world**, and an actual person cannot hold
it.

This is the most consequential statement in the turn, and it reaches beyond the question it answers.

- There is no external market for R and none is possible, since no one outside the world can hold it.
  This settles `OPEN-06`.
- Holders, participants, and accounts in the whitepaper are entities within the world. The audience
  observes the monetary system; it does not participate in it.
- It **conflicts with a prior confirmed statement.** [[DEC-004-monetary-authority-and-authored-decline]]
  accepts that a public chain would record whatever velocity *real participants* produce, including a
  rising one. If no real person can hold R, there are no real participants and no such divergence can
  arise. One of the two must give. Recorded as `OPEN-35`, unresolved.
- What a payer receives in exchange for a System Payment is still unstated, so `OPEN-29` is only partly
  answered.

## Confirmed — the fixed unit is the result of the mechanism

`1R = 1R` holds **because** supply destruction offsets a value that would otherwise fall. The fixed unit is
the result of the burn mechanism, not an independent axiom.

This settles `OPEN-31` and reconciles [[DEC-003-currency-and-circulation-direction]]'s fixed-value premise
with [[DEC-006-burn-mechanism-and-value-preservation]]'s falling value. The earlier premise is not revised;
it is explained.

## Confirmed — genesis date; the depletion figure since withdrawn

Genesis is **17 September 1975**, which is Epoch 0. That stands.

The present supply was defined here as approximately **50% of the initial quantity**. **The user
subsequently withdrew that figure**; see
[[DEC-010-non-expansion-restored-and-2026-anchor-withdrawn]]. It is no longer a fact of the world and must
not be used as an anchor or a published value. The section below is retained as the question's history —
its arithmetic is no longer live.

### The stated depletion contradicts the draft contraction rate

From 17 September 1975 to 10 September 2026 is 18,621 days — 50.98 years, or 2,660 seven-day epochs.

| Contraction rate | Remaining after 50.98 years |
|---|---|
| 3% annually — the draft parameter in [[r-monetary-protocol]] | **21.16%** |
| **1.35% annually** (0.026% per 7-day epoch) | **50%** — the stated present |

The 3% figure was never a confirmed parameter, but the two cannot both stand. Either the rate becomes
roughly 1.35% annually, or the present depletion is not 50%, or the schedule is not a constant-rate
exponential over the whole interval. Recorded as `OPEN-34`; nothing here selects an answer.

Note also that the stated 50% is the outcome of **both** channels together, since burn now counts toward
the target. A rate chosen to produce 50% by scheduled retirement alone would overshoot once burn is
included.

## Boundaries

These are world and design decisions. They confirm no on-chain parameter, approve no release, and
establish no implementation, deployment, or economic validation. The genesis date and the 50% figure are
facts of the world's history, not measurements. That destruction preserves value remains a premise, not a
demonstrated result.

## Sources

- [[SRC-2026-09-10-burn-accounting-payer-and-genesis-date]] — [raw/conversations/2026-09-10-burn-accounting-payer-and-genesis-date.md](../../raw/conversations/2026-09-10-burn-accounting-payer-and-genesis-date.md)
