---
status: confirmed
attribution: user-confirmed
updated: 2026-09-10
sources:
  - SRC-2026-09-10-second-anchor-noise-bounds-and-generator
---

# Second Anchor, Noise Bounds, and the Generator

Three decisions follow [[DEC-008-contraction-curve-simulation-and-ledger-scope]]. They supply a second
point on the contraction history, bound the noise, and settle how the simulated data is produced and
disclosed. One of them removes an invariant the whole monetary model has rested on; that consequence is
recorded here rather than resolved.

## Confirmed — a depletion figure for 17 September 2025, since unfixed

At **17 September 2025** — exactly 50 years after genesis — **30% of the original quantity remains**.

**The user subsequently unfixed this value**; see [[DEC-011-depletion-as-tolerance-band]]. It is now an
acceptance criterion with a ±5-point tolerance rather than a figure the world asserts. The date and the
approximate magnitude stand; the exactness does not.

### Superseded framing — the impossible pair is gone

The reconciliation below was written while the 50%-at-2026 figure still stood.
[[DEC-010-non-expansion-restored-and-2026-anchor-withdrawn]] withdraws that figure, so the two-point
conflict no longer exists and the schedule-versus-path reading it forced is moot. The 30% figure now stands
alone. Retained as the question's history.

### This point is not on the schedule

The previously confirmed figure in [[DEC-007-burn-accounting-payer-and-genesis-date]] is about **50%
remaining at 10 September 2026**, which is *later*. Taken as two points on one falling curve they are
impossible: supply would have to rise from 30% to 50% over the intervening year.

The same turn authorizes exactly that (below), so the two are read together as follows, and the manuscript
is written on this reading:

- **50% at 2026** pins the **schedule** `S*` — the ceiling.
- **30% at 2025** is a point on the **realized path**, which runs below the ceiling.

Under the manuscript's draft curve the schedule stands at about 51.3% in September 2025, so a realized path
at 30% sits roughly 21 percentage points beneath it and then returns to touch the ceiling within a year.
That is a very large excursion to call noise; the reading is recorded as the manuscript's working
interpretation and **needs confirmation**.

A consequence for [[r-whitepaper-development]]: a second point on the *path* does not fix the schedule's
shape parameter. The earlier expectation that one more dated figure would pin `k` does not hold, and
`OPEN-37` remains open.

## Confirmed — noise is one-sided below the schedule, and may rise

Noise stays on **one side only, beneath the schedule**. Within that band the realized path **may rise
during intermediate periods**, provided it never breaches the **original quantity**.

This settles the structural half of `OPEN-36`: the schedule remains a ceiling
([[DEC-007-burn-accounting-payer-and-genesis-date]]), and the noisy path lives under it rather than
straddling it. `OPEN-18` is not reopened.

### It removed non-expansion — since retracted

**The user retracted this permission**; see
[[DEC-010-non-expansion-restored-and-2026-anchor-withdrawn]]. Non-expansion holds, retirement and burn are
permanent, and no operation restores destroyed R. The analysis below is retained as the question's history,
and the manuscript's `OPEN-39` is closed by the retraction rather than by an answer.

### It removes non-expansion

Permitting intermediate rises contradicts the invariant that total supply never increases. That invariant
has been present since the earliest drafts in [[r-monetary-protocol]] — no post-genesis creation, permanent
retirement, permanent burn — and the manuscript states it as `I1` and as design principle `P3`.

Two readings are possible and the turn does not choose between them.

- **The history rises, the rules do not.** The realized series is generated data
  ([[DEC-008-contraction-curve-simulation-and-ledger-scope]]), so it can move in ways the protocol's own
  operations cannot produce. The ledger would then display a history its rule implementation could not
  have generated — and the deployment is confirmed to be both of those things at once.
- **An operation restores supply.** Some act returns R that had been retired or burned, bounded by the
  original quantity. No such operation exists in the specification, and "permanent" destruction would have
  to be withdrawn from §7.5 and §7.7.

Recorded in the manuscript as `OPEN-39`, and it now blocks Sections 7, 8, and 17.

## Confirmed — the generator is built and published, but not shown in the work

The simulated data is produced by a **generator that will be built**. It is **published on GitHub**, and it
is **not disclosed within the artwork**.

This resolves `OPEN-38` and splits the disclosure question cleanly. The method is auditable by anyone who
looks for it; the work itself stays quiet about it. It is consistent with the quiet, static presentation
recorded in [[DEC-003-currency-and-circulation-direction]] and with the audience-language limits there.

It also narrows the manuscript's honesty requirement to a workable rule: the whitepaper states that the
series is generated and where the generator lives; the work shows the series without explaining it.

## Boundaries

These are world and design decisions. They confirm no shape parameter, no noise distribution, no
repository, and no implementation. The generator does not yet exist. That the realized path may rise is a
stated property of the world's history; the mechanism, if any, is undecided.

## Sources

- [[SRC-2026-09-10-second-anchor-noise-bounds-and-generator]] — [raw/conversations/2026-09-10-second-anchor-noise-bounds-and-generator.md](../../raw/conversations/2026-09-10-second-anchor-noise-bounds-and-generator.md)
