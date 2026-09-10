---
status: working
attribution: llm-synthesis
updated: 2026-09-10
sources:
  - SRC-2026-09-09-currency-value-supply-and-velocity
  - SRC-2026-09-10-r-token-issuance-and-protocol-drafts
---

# R Monetary Protocol

The user requested an R Monetary Protocol v0.1 draft and then a v0.2 whitepaper. The supplied export contains both. They are **LLM-proposed designs**, not an approved specification, tested contract, issued asset, or production commitment. [[DEC-003-currency-and-circulation-direction]] owns the narrower confirmed world constraints; [[r-whitepaper-development]] owns the later document plan.

## Proposed monetary architecture

The drafts define R as base money, with future deposits, loans, interest-bearing claims, collateral, and credit in a separate banking layer. [[DEC-005-monetary-unit-banking-layer-and-mandate]] later confirms that the separation is between layers, not institutions: THE RESERVE operates the banking layer itself. It also confirms that the base is assumed to exist from the outset rather than created by the institution, and that R is not a liability of THE RESERVE. Genesis issues all base units into the Reserve Treasury at a single past point; release moves existing units into circulation. No post-genesis minting is proposed, including minting to pay token interest. [[DEC-006-burn-mechanism-and-value-preservation]] later establishes **two** supply-reducing channels rather than one: scheduled retirement of treasury-held units, and burn of what a holder spends toward the system. Use between people conserves supply. Elapsed time still reduces no balance, and a burn follows only the holder's own transfer.

The proposed implementation separates `RToken` (ERC-20 balances and supply), `ReserveTreasury` (release, settlement, retirement), and an off-chain `Reserve Observer` (statistics without control of balances). Base Sepolia is the initial network proposal. `RESERVE` / `RSV` / display `R`, 18 decimals, 1,000,000 R genesis supply, 100% initial treasury allocation, zero public circulation, a seven-day v0.1 epoch, and 3% annual contraction are **draft or experimental choices**, not confirmed production parameters. [[DEC-007-burn-accounting-payer-and-genesis-date]] now dates genesis to 17 September 1975 and puts the present at roughly 50% of the initial quantity, which the draft 3% rate contradicts: over 50.98 years it would leave 21.16%. [[DEC-008-contraction-curve-simulation-and-ledger-scope]] then rejects the constant-rate form entirely — the contraction is slow at first and accelerates, and the realized path is noisy. [[DEC-010-non-expansion-restored-and-2026-anchor-withdrawn]] withdraws the 2026 figure, and [[DEC-011-depletion-as-tolerance-band]] unfixes the remaining one: the world states an acceptance criterion, a steady decline to 30 ± 5% remaining at 17 September 2025, and asserts no dated quantity. The manuscript proposes a stretched exponential and records the family of shapes and scales the criterion admits; no functional form, parameter, or rate is confirmed.

## Target supply and executable retirement

The whitepaper proposes

\[
S^*(t)=S_0(1-c)^t
\]

where \(S_0\) is genesis supply, \(c\) an annual contraction parameter, and \(t\) elapsed years. The earlier draft writes \(S_n^*=S_0(1-c)^{n/52}\) for weekly epochs. These are draft schedules; calendar conventions, rounding, and parameter finalization remain unspecified.

A `settle()` call attempts to retire the excess of actual supply over target supply using only available treasury R. The draft's example requires 10,000 R of retirement with only 6,000 R available: retire 6,000 and leave 4,000 as Pending Retirement. Holders are not charged the shortfall. Consequently **a declining target is not a guarantee that actual supply follows it**; reserve depletion and missing calls can leave actual supply above target. The non-expansion invariant \(S_{t+1}\leq S_t\) allows flat supply. [[DEC-009-second-anchor-noise-bounds-and-generator]] briefly withdrew it by permitting intermediate rises; [[DEC-010-non-expansion-restored-and-2026-anchor-withdrawn]] retracts that permission. **Non-expansion holds**, retirement and burn are permanent, no operation restores destroyed R, and \(S(t)\leq S^*(t)\leq S_0\) follows.

The drafts propose permissionless settlement with formula-determined amounts and institution-authorized release. They do not finish shortfall accounting, repeat-call behavior, return/replenishment policy, a terminal supply floor, or the tradeoff between release and future retirement capacity.

## Circulation and observation

The v0.1 draft defines \(C_t=S_t-T_t-X_t\): circulating supply equals total supply less Treasury and other excluded protocol balances. The whitepaper abbreviates this to reserve plus circulation, subject to classified protocol balances. Exclusions must be explicit and non-overlapping before implementation.

The proposed observational measure is

\[
V_{30}=Q_{30}/\overline C_{30},
\]

with eligible transfer volume \(Q_{30}\) and average circulating supply \(\overline C_{30}\) over 30 days. Initial releases, treasury returns, retirement, and internal protocol transfers are excluded in the draft. Address classification, repeated/self transfers, averaging, and the zero-circulation case still need rules; the formula is not a validated human-to-human activity measure.

The world direction calls for decreasing velocity, but the protocol draft proposes recording actual public-chain behavior even if it rises. [[DEC-004-monetary-authority-and-authored-decline]] first resolved this as a reporting boundary. [[DEC-008-contraction-curve-simulation-and-ledger-scope]] then removed the premise it rested on: there are no real participants, so no divergence can arise, and the velocity flow runs on **simulated data**. The Reserve Observer publishes a generated series rather than an independent measurement, and the honesty requirement becomes disclosure of the simulation rather than separation of two records. Simulated/historical world data and observed transactions must remain distinguishable. System-directed spending and longer retention are proposed mechanisms, not an automatic consequence of spending toward AI.

## Authority, value, and banking boundaries

The drafts propose no fiat peg, guaranteed redemption, official liquidity support, native token yield, or external-price oracle for monetary policy. They separate the internal unit from any third-party market price. These are proposed constraints, not a legal classification or evidence that external trading can be prevented.

Transferability without arbitrary seizure, reversal, transfer taxes, balance decay, or post-genesis minting is proposed. Production immutability, release keys, upgradeability during experiments, and classification authority still need an exact permission model. The whitepaper itself also leaves unrestricted transferability as an open question; it is not finally resolved merely by the preceding design prose.

A separate Reserve Rate could affect later banking claims. The earlier currency discussion proposes interest as the cost of using R over time, responding to scarcity and borrowing demand rather than directly measuring trust. The later drafts return to a schematic trust/velocity decline → rate rise. **No final rate equation or monotonic rate rule is confirmed**; preserve this tension for review rather than treating either diagram as a calibrated model.

## Evolution and next decisions

The September 6 [[future-claims]] proposal left issuance largely in the background. R drafting brings the monetary base forward while keeping credit and its visitor consequences unresolved. It does not select Future Claims Bank or define a working banking service.

The supplied drafts identify release eligibility and purpose as a major next decision: who receives R, why, and what receiving it enables. Other gaps include treasury partition/returns, final supply parameters, holder rights, custody/wallet experience, observer methodology, authority, and the boundary between fictional decline and open-chain observations. [[Q-001-institutional-scope]] consolidates these choices.

Technical/security and jurisdiction-specific claims in the export remain attributed source material, not independently verified guidance. The source supplies no contract code, deployment address, test evidence, or completed security review.

## Sources

- [[SRC-2026-09-09-currency-value-supply-and-velocity]] — [raw/conversations/2026-09-09-currency-value-supply-and-velocity.md](../../raw/conversations/2026-09-09-currency-value-supply-and-velocity.md)
- [[SRC-2026-09-10-r-token-issuance-and-protocol-drafts]] — [raw/conversations/2026-09-10-r-token-issuance-and-protocol-drafts.md](../../raw/conversations/2026-09-10-r-token-issuance-and-protocol-drafts.md)
