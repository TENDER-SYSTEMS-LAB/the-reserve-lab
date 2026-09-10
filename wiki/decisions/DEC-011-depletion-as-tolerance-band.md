---
status: confirmed
attribution: user-confirmed
updated: 2026-09-10
sources:
  - SRC-2026-09-10-depletion-as-tolerance-band
---

# Depletion as a Tolerance Band

The 30% figure confirmed in [[DEC-009-second-anchor-noise-bounds-and-generator]] is **not fixed**. It
becomes an acceptance criterion with a tolerance rather than a value the world asserts.

## Confirmed — the criterion

From **17 September 1975 to 17 September 2025** the quantity declines **steadily**. At 17 September 2025,
**30 ± 5%** remaining — a band of **25% to 35%** — meets the criterion.

Two things change from the prior record.

- **No dated quantity is asserted.** The world states a criterion the history must satisfy, not a number it
  must hit. Nothing in the work publishes "30%" as a fact.
- **The steady decline over the whole interval is reaffirmed**, consistent with the non-expansion invariant
  restored in [[DEC-010-non-expansion-restored-and-2026-anchor-withdrawn]].

The criterion is read as applying to the **quantity that actually remains** — the realized path — since
that is what "remains" denotes. The schedule sits at or above the path.

## Consequence — the curve is a family, not a fitted line

A point fixes `λ` once `k` is chosen. A band does not: it admits a **family** of curves. For the
manuscript's draft shape `k = 2`, the admissible scale is `λ` between **42.47 and 48.80** years, and the
same band admits other shapes with their own ranges — roughly 40.22–48.41 for `k = 1.5` and 44.84–49.20 for
`k = 3`.

The band at one date widens elsewhere, which is what makes this a real choice rather than a formality. With
`k = 2`, the admissible history spans:

| Year | Remaining |
|---|---|
| 1985 | 94.6% – 95.9% |
| 2000 | 70.7% – 76.9% |
| 2015 | 41.2% – 51.1% |
| **2025** | **25.0% – 35.0%** |
| 2035 | 13.6% – 22.1% |
| 2050 | 4.4% – 9.4% |

A ten-point band in 2025 is a ten-point band in 2015 and a five-point band in 2050. The criterion
constrains the world's history loosely, not tightly.

## Consequence — this is the generator's acceptance test

Because the flows are generated ([[DEC-008-contraction-curve-simulation-and-ledger-scope]]), a criterion
rather than a value gives the generator something to satisfy. Any shape, scale, and noise process whose
realized path lands inside the band on that date qualifies. The three are jointly constrained by one test
at one date, and nothing else in the world's history is pinned.

This also weakens the question recorded as `OPEN-40`: whether the realized path meets the ceiling in 2025
no longer determines whether anything is anchored, since the band accommodates a path running below its
schedule. What replaces it is narrower — how far below, which is the noise amplitude in `OPEN-36`.

## Boundaries

This confirms no shape parameter, no scale, and no noise process. It sets one test, at one date, with a
tolerance. The parameter ranges above are computed from the criterion, not supplied by the user, and the
generator does not yet exist.

## Sources

- [[SRC-2026-09-10-depletion-as-tolerance-band]] — [raw/conversations/2026-09-10-depletion-as-tolerance-band.md](../../raw/conversations/2026-09-10-depletion-as-tolerance-band.md)
