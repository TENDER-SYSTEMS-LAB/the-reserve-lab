---
status: confirmed
attribution: user-confirmed
updated: 2026-09-10
sources:
  - SRC-2026-09-10-non-expansion-restored-and-2026-anchor-withdrawn
---

# Non-Expansion Restored and the 2026 Figure Withdrawn

The user withdraws one confirmed figure and retracts one confirmed permission. Both corrections narrow the
model rather than extend it, and together they resolve the largest open item the manuscript held.

## Withdrawn — 50% remaining at 10 September 2026

The figure confirmed in [[DEC-007-burn-accounting-payer-and-genesis-date]] — approximately 50% of the
original quantity remaining at 10 September 2026 — is **withdrawn**. It is no longer a fact of the world
and must not be used as an anchor, a published value, or a premise anywhere.

The remaining dated figure is the one confirmed in
[[DEC-009-second-anchor-noise-bounds-and-generator]]: **30% remains at 17 September 2025**, fifty years
after genesis.

The impossible pair that forced the schedule-versus-path reading is therefore gone. That reading was
recorded as an interpretation needing confirmation and is now moot; the manuscript no longer carries it.

## Confirmed — non-expansion holds

The user retracts the permission for intermediate rises, stating directly that it conflicts with the
non-expansion invariant and that the invariant is what the design should keep.

**Total supply never increases.** `S_{t+1} ≤ S_t` at every transition, without exception and without an
emergency override. Retirement and burn are permanent, no operation restores retired or burned R, and
nothing creates a base unit after genesis.

This restores `I1` and design principle `P3` to their earlier form, and it resolves `OPEN-39` — the
manuscript's most consequential open item — by removing the condition that created it. The two readings it
held open, a generated history the rules could not produce and an operation that returns destroyed R, are
both closed: neither is needed and neither exists.

The bound `S(t) ≤ S*(t) ≤ S₀` still holds and is now implied rather than load-bearing. The schedule remains
a **ceiling** ([[DEC-007-burn-accounting-payer-and-genesis-date]]), and the noise remains one-sided beneath
it ([[DEC-009-second-anchor-noise-bounds-and-generator]]) — with the realized path now monotone, so noise
appears only as variation in the **speed** of decline.

## Consequence — the schedule has no confirmed anchor

With the 2026 figure withdrawn, one dated figure remains, and what it pins is not settled.

"30% remains" is a statement about the quantity that actually remains — a point on the **realized path**.
The schedule `S*` sits at or above the path, so unless the path happens to meet the ceiling on that date,
the 30% figure constrains the schedule only as a lower bound and fixes neither `λ` nor `k`.

The manuscript proceeded on the reading that the path **meets the ceiling** at 17 September 2025, recorded
as `OPEN-40`. [[DEC-011-depletion-as-tolerance-band]] then made that question moot by replacing the figure
with a tolerance band, which a path running below its schedule can satisfy either way. What survives from
`OPEN-40` is the narrower question of how far below — the noise amplitude.

## Boundaries

These corrections confirm no shape parameter and no new figure. The withdrawn 50% must not survive anywhere
as a value. The surviving 30% was a fact of the world's history rather than a measurement, and
[[DEC-011-depletion-as-tolerance-band]] has since unfixed it into a criterion with a tolerance.

## Sources

- [[SRC-2026-09-10-non-expansion-restored-and-2026-anchor-withdrawn]] — [raw/conversations/2026-09-10-non-expansion-restored-and-2026-anchor-withdrawn.md](../../raw/conversations/2026-09-10-non-expansion-restored-and-2026-anchor-withdrawn.md)
