# R — A Contracting Monetary Base for THE RESERVE

**Document Version** 0.2 · **Protocol Version** 0.1 · **Status** Draft
**Institution** THE RESERVE (RS-001) · **Date** 2026-09-10

---

## Status of this draft

This manuscript is written against the 22-section outline recorded in
[r-whitepaper-development](../wiki/concepts/r-whitepaper-development.md). Sections 1–4 are drafted
first, deliberately, because they are the sections that cannot be written without deciding what R is.
Sections 5–10 follow from them and are now drafted; Sections 11–22 remain outline.

Two rules govern the prose:

1. **Nothing is asserted as settled unless a user decision supports it.** The confirmed constraints are
   recorded in [DEC-003](../wiki/decisions/DEC-003-currency-and-circulation-direction.md): a bank-like
   institution with a currency; a unit whose value does not change inside the work; a total supply that
   declines; declining velocity; retention rather than circulation between people; and audience-facing
   language that does not explicitly name AI. [DEC-004](../wiki/decisions/DEC-004-monetary-authority-and-authored-decline.md)
   adds two: THE RESERVE is the central bank and issuing authority of R, and the declining velocity is
   authored world history that the protocol cannot control.
   [DEC-005](../wiki/decisions/DEC-005-monetary-unit-banking-layer-and-mandate.md) adds three: a quantity
   of R is assumed to have existed from the outset, the same institution operates the banking layer, and
   the institution's mandate is RESERVE.
   [DEC-006](../wiki/decisions/DEC-006-burn-mechanism-and-value-preservation.md) adds two: R's value is
   falling in the world and destruction exists to preserve it, and R is burned when used toward the system
   while use between people leaves supply unchanged.
   [DEC-007](../wiki/decisions/DEC-007-burn-accounting-payer-and-genesis-date.md) adds five: burn counts
   toward the contraction target, THE RESERVE designates system accounts, THE RESERVE is the initial payer
   and R cannot be held outside the world, the fixed unit is the result of the burn mechanism, and genesis
   is 17 September 1975 (its depletion figure since withdrawn; see DEC-010).
   [DEC-008](../wiki/decisions/DEC-008-contraction-curve-simulation-and-ledger-scope.md) adds four: the
   contraction accelerates and is noisy rather than running at a constant rate, the velocity flow runs on
   simulated data because there are no real participants, the deployment is both a public ledger of the
   world's history and a rule implementation with in-world accounts only, and the elapsed decline since
   1975 sits before the record.
   [DEC-009](../wiki/decisions/DEC-009-second-anchor-noise-bounds-and-generator.md) adds three: a depletion
   figure for 17 September 2025 (since unfixed, below), a noise that runs on one side beneath the schedule,
   and a generator published on GitHub but not shown in the work.
   [DEC-010](../wiki/decisions/DEC-010-non-expansion-restored-and-2026-anchor-withdrawn.md) then withdraws
   the earlier 50%-at-2026 figure and restores strict non-expansion, retracting the permission for
   intermediate rises.
   [DEC-011](../wiki/decisions/DEC-011-depletion-as-tolerance-band.md) unfixes the remaining figure: the
   world states an acceptance criterion — a steady decline to 30 ± 5% remaining at 17 September 2025 — and
   asserts no dated quantity. Everything else in this document is a draft proposal.
2. **Every gap this drafting exposes is marked, not smoothed over.** Where the text would otherwise have
   to invent a rule, it stops and records an `OPEN-nn` marker instead. Those markers are collected in
   [Open definitions](#open-definitions), at the end of the document and are the intended input to the
   next decision pass. A section that reads as incomplete is reporting a real state of the design.

Notation in this document departs from the source drafts in one place, deliberately. The earlier drafts
used `S` for total supply while the later outline used `S` for whole protocol state. This manuscript
reserves `S` for supply and writes protocol state as `Σ`. See §4.9.

---

# 1. Abstract

R is the monetary unit of THE RESERVE, the central bank and issuing authority of this monetary system.

R is defined by a single monetary premise: the unit does not change, and the quantity of units does not
grow. A fixed quantity of R was issued once, at a point in the past, and has only decreased since. That
issuance is a premise of this world rather than a recurring instrument, and no further R has been or can
be issued. There is no issuance schedule, no mining
reward, no staking yield, and no mechanism by which a new base unit can come into existence.

The institution's mandate is **reserve**: to keep. In the world of THE RESERVE the value of R is falling,
and destruction is how that value is preserved. Reducing the quantity is not the opposite of keeping — it
is the act of keeping.

The system distinguishes four monetary events that are ordinarily confused with one another:

1. **Genesis** — a single issuance, at a defined point in the past, of the whole fixed quantity into the
   Reserve Treasury. Nothing has been issued since.
2. **Release** — the movement of already-existing units from the Reserve Treasury into circulation.
   Release does not change the base.
3. **Retirement** — the scheduled, permanent removal of units the institution holds, against a
   deterministic target.
4. **Burn** — the permanent removal of units a holder uses toward the system.

The two reduction channels differ in what drives them. Retirement follows a schedule. Burn follows use:

- **Use between people leaves the supply unchanged.** When holders transact with one another, units move
  and nothing is destroyed.
- **Use toward the system destroys the units spent.** R directed to a system counterparty leaves the
  supply permanently.

A holder's balance is therefore reduced only by that holder's own act. Nothing decays, expires, rebases,
or is seized, and no schedule reaches a holder's balance. A holder of 100 R holds 100 R until they spend
it.

Retirement operates against a deterministic target. At any time `t`, the protocol defines a target supply
`S*(t)` declining at a fixed rate, and a settlement operation that retires the excess of actual supply
over that target — **using only units the institution itself holds.**

That constraint has a consequence the system accepts rather than hides: if the treasury is exhausted,
scheduled retirement stops, and only burn continues to reduce supply. `S*(t)` is therefore a *ceiling*, not
a promise about where supply sits beneath it:

$$
S_{t+1} \leq S_t, \qquad S(t) \leq S^*(t) \leq S_0
$$

Supply never increases, never exceeds the schedule, and never exceeds the quantity issued at genesis.
Retirement and burn are permanent: nothing restores a destroyed unit, and no operation creates one.

R states no exchange rate. It is not pegged, not redeemable, and carries no promise of purchasing power
against any external currency, commodity, or asset. Its identity is `1R = 1R`, and that identity is a
*result*: the unit holds because destruction offsets a value that would otherwise fall. Constancy is what
the mechanism produces, not an axiom the mechanism serves.

R exists only within the world of THE RESERVE. No person outside it holds R, and no external market for it
exists or can. The audience observes this monetary system; it does not participate in it. Every holder,
account, and participant named below is an entity within the world.

R is a base layer only. Deposits, lending, interest-bearing claims, collateral, and credit are separated
into a distinct banking layer, not specified here.

**OPEN-02 — resolved.** At the base layer THE RESERVE is the central bank and issuing authority of R; no
other institution issues the base. The same institution also operates the banking layer above it (§2.4,
OPEN-22). See §5.2 and
[DEC-004](../wiki/decisions/DEC-004-monetary-authority-and-authored-decline.md).

**OPEN-01 and OPEN-23 — resolved.** The institution's purpose and its monetary mandate are the same word:
**reserve**. R exists so that what is held can be kept. §10 develops what that mandate does and does not
authorize.

---

# 2. Introduction

## 2.1 The observed condition

Contemporary monetary systems are built to expand. Commercial banks create deposit money by lending
against it. Central banks alter monetary conditions through balance-sheet operations and policy rates.
Cryptoasset systems have largely reproduced the same instinct in a different form: block rewards,
staking emissions, inflation schedules, governance-authorized mints. The mechanisms differ; the default
direction does not. More money is the normal case, and its absence is treated as a malfunction.

Expansion is not a neutral default. It sets the terms on which holding is understood. Where the base
grows, holding is a decision that loses by waiting, and the system's ordinary advice is to move value on
— to spend it, lend it, deploy it, or convert it into something that grows faster than the unit decays.
Circulation becomes the measure of health.

## 2.2 The premise of R

R begins from the opposite premise. The monetary base of THE RESERVE is designed to become smaller, and
contraction is not an exceptional event within it. Contraction is the normal monetary condition.

This inverts what the system asks of a holder. Where the base contracts and the unit is constant, holding
is not a failure to act. Keeping is the ordinary behavior, and the system does not need to argue for it.

Two properties must hold simultaneously for that to be true, and separating them is the central
distinction of this document:

- **The aggregate declines.** Total supply falls over time, on a deterministic schedule.
- **The unit is untouched.** No individual balance is reduced by the passage of time. There is no
  demurrage, no rebasing, no negative interest on the base unit, and no expiry.

Stated plainly: **the quantity of money may decline while the integrity of each individual unit remains
unchanged.** Systems that contract by shrinking every balance proportionally do not satisfy this. R
contracts through the institution's own scheduled retirement and through what holders themselves spend
toward the system — never through a reduction imposed on a balance from outside it.

This is also where the two directions of the world meet. Use between people preserves the supply; use
toward the system destroys it. As a world spends less with one another and more toward the system, both
things follow at once: circulation between people falls, and the money supply falls. They are one
behavior seen at two points.

## 2.3 Why a separate protocol

The premise cannot be expressed as a parameter of an existing system. A fixed cap is not contraction —
Bitcoin's terminal supply is an asymptote approached from below, not a base that declines from a
completed genesis. A burn mechanism tied to usage is not contraction either — it makes the money supply a
function of activity, and R's world is one where activity itself declines. A demurrage currency contracts
the holder rather than the base, which is the exact property R rejects.

What R requires is a base that is complete at genesis, an institution that holds the undistributed
remainder, and a rule that destroys part of that remainder on a schedule that does not depend on anyone's
behavior. That combination needs its own specification.

**OPEN-03 — resolved.** The declining velocity of THE RESERVE is **authored world history**: a defined
result within the world, stated by the institution as its own record. It is explicitly *not* a protocol
guarantee. The protocol cannot control velocity, and the public chain will record whatever velocity real
participants produce, including a rising one. Both halves are held together deliberately; §9 develops the
consequence and §4.8 keeps the two records separable. See
[DEC-004](../wiki/decisions/DEC-004-monetary-authority-and-authored-decline.md).

## 2.4 Scope of this document

**In scope.** The monetary unit; the monetary state and its variables; genesis; the release of reserve
units into circulation; the contraction target and the settlement operation that pursues it; the protocol
state transition; the observational measures the institution publishes.

**Out of scope.** Deposits, lending, credit, collateral, interest-bearing claims, default and repayment,
and any product denominated in R but not identical to R. These belong to a banking layer that this
document deliberately does not specify. THE RESERVE operates that layer itself — there is no second
institution and no separately chartered bank — so the separation between *money* and *claims denominated
in money* is a separation of layers within one institution, not a separation of parties. It is a design
principle, not an omission (§3.2).

**Also out of scope.** Any statement about the value of R against an external currency or asset, any
statement about legal or regulatory classification, and any claim that an implementation exists, has been
audited, or has been deployed. No contract code, deployment, security review, or economic validation
supports this draft.

**OPEN-04 — resolved by OPEN-03.** The boundary is drawn by enforceability, not by section number.
A **protocol fact** is a rule the implementation enforces and anyone can verify against the record. A
**world record** is a statement THE RESERVE makes about its own history, which the protocol does not
enforce and observation may contradict. Both appear below §4, and every world record is labeled as one
where it appears. Supply contraction is a protocol fact; declining velocity is a world record.

---

# 3. Design Principles and Non-Goals

## 3.1 What R preserves

**P1 — Unit constancy.** One R is one R. The unit is never redenominated, split, merged, or rebased.
Every balance is expressed in the same unit at every point in the system's life, so an amount recorded at
genesis remains legible without conversion at any later date.

**P2 — Holder integrity.** No mechanism reduces a holder's balance without that holder's own transfer.
This excludes demurrage, expiry, negative interest on the base unit, balance decay, involuntary
confiscation, and transfer taxes. A burn (§7.7) reduces a balance, but only as the effect of a transfer
the holder themselves made; no schedule, elapsed time, or authority reaches a balance. It is the
constraint that makes contraction bearable: what a holder keeps, they keep.

**P3 — Non-expansion.** `S_{t+1} ≤ S_t` at every transition, without exception and without an emergency
override. There is no authority — including THE RESERVE — that can create a base unit after genesis or
restore one that has been retired or burned. It follows that `S(t) ≤ S*(t) ≤ S₀` at all times.

**P4 — Determinism of the schedule.** The contraction target is a closed-form function of elapsed time
and fixed parameters. It does not respond to price, demand, activity, governance vote, or discretion.
Anyone can compute the target for any date.

**P5 — Separation of layers.** Base money is specified independently of any claim denominated in it.
A failure in the banking layer must not be able to alter the base.

**P6 — Legibility of state.** Total supply, treasury holdings, circulating supply, and retirement history
are publicly derivable from the record at all times. The institution's own position is not privileged
information.

**P7 — No unnecessary expansion.** The system does not add an institution, role, instrument, or mechanism
that the design does not require. Where a function is needed, THE RESERVE performs it rather than a new
party being introduced to perform it. This is why one institution holds the base and operates the banking
layer, and why the non-goals in §3.3 are stated as decisions rather than as work deferred.

## 3.2 What R optimizes for

R optimizes for **durability of the unit as a store of account** and for **legibility of the monetary
state**, in that order.

It does not optimize for liquidity, throughput, or transactional efficiency. These are not treated as
defects to be minimized; they are simply not the axis along which the system is designed. A monetary base
whose intended behavior is retention has no reason to compete on velocity.

**Decentralization is not a goal.** R is base money issued by a central bank, and the asymmetry in the
design is the intended structure rather than an unresolved compromise: **release is authorized by the
institution**, while **settlement is permissionless** — anyone may call it, and the retired amount is
determined by formula, so a caller has no discretion over it. The institution decides what enters
circulation; no one, including the institution, decides what contraction does. What the system
decentralizes is verification and enforcement of the schedule, not issuance.

> **OPEN-05 — narrowed: the permission model itself.**
> The location of authority is settled (`OPEN-02`), but its mechanics are not. Undecided: which keys
> authorize release, how they are held and rotated, whether any release is rate-limited or bounded by the
> protocol rather than by policy, and what a release looks like in the public record. Section 14 can now
> be structured, but not completed.

> **OPEN-23 — What is the mandate of a central bank with one instrument?**
> The contraction schedule is fixed and blind by design (P4), so it is not an instrument the authority
> operates. Retirement is formula-determined and permissionless. That leaves **release** as effectively the
> institution's only monetary act. A central bank normally has an objective against which its acts are
> judged; R's authority currently has none stated. Undecided, and closely coupled to OPEN-01 and OPEN-13.

## 3.3 Non-goals

The following are explicit non-goals. Each is a decision, not an unfinished feature.

**N1 — No peg.** R maintains no parity with any fiat currency, commodity, or cryptoasset.

**N2 — No redemption.** THE RESERVE does not promise to exchange R for anything. There is no reserve of
external assets backing R and no redemption window.

**N3 — No purchasing-power guarantee.** `1R = 1R` is a statement about the unit's constancy within THE
RESERVE. It is not a claim that R buys a constant quantity of anything, at any time, anywhere.

**N4 — No price oracle in monetary policy.** No external price feeds into issuance, release, retirement,
or any protocol decision. The contraction schedule is blind to markets by construction.

**N5 — No native yield.** Holding R does not generate R. There is no interest, no staking reward, and no
rebase that increases balances. The system has no mechanism to pay yield in base units, because paying it
would require minting, which P3 forbids.

**N6 — No market operations.** THE RESERVE does not provide liquidity, act as buyer or seller of last
resort, or intervene in any external market where R may trade. Contraction is *intended* to preserve
value (§10.1), but it is not an operation conducted against a market: the schedule is blind (P4, N4), and
the burn channel is driven by holders' own use rather than by the institution.

**N7 — No involuntary balance adjustment.** Restated from P2 because it is the non-goal most often
assumed away in contracting-supply designs: the contraction target is never met by reducing holders.

## 3.4 What the system does not attempt to prevent

Stating a non-goal is not the same as having control. Three limits follow honestly from the above.

- The contraction target may be undershot. Because burn counts toward it (§7.7), holders' own use can
  carry supply below `S*(t)`, at which point scheduled retirement does nothing. The institution neither
  causes nor prevents this.
- The contraction target may also be missed from above, if the treasury is exhausted and burn is slow.
  See §7.6.
- The institution cannot compel use, and therefore cannot compel the burn channel to run at any rate.

> **OPEN-06 — Is transferability unrestricted?**
> P2 and N7 establish that transfers cannot be *forced*. They do not establish whether every transfer is
> *permitted*. The drafts propose free transferability while simultaneously listing unrestricted
> transferability as an open question. Both cannot stand. This decision determines whether an external
> market is possible at all, which in turn determines whether §3.4's first limit is a concession or a
> design choice.

> **OPEN-07 — Is the deployed protocol immutable?**
> The drafts propose immutability in production while retaining upgradeability during experiments. The
> boundary between "experiment" and "production," who declares the crossing, and what upgrade powers exist
> before it, are unspecified. An upgradeable contract makes P3 a promise of intent rather than a property
> of the system, and the document must say which one it is offering.

---

# 4. Definitions and System Model

From this section onward the document proceeds as **Definition → Rule → Condition → Consequence.**
Narrative claims do not appear below this line.

## 4.1 Base unit and denomination

**Definition.** `R` is the monetary unit of THE RESERVE. All amounts in this document are expressed in R.

**Rule.** R is divisible into `10^d` indivisible base units, where `d` is the decimals parameter. The
draft value is `d = 18`. Every quantity in the protocol — balance, supply, target, retirement amount — is
an integer number of indivisible base units. No protocol operation produces a fractional base unit.

**Consequence.** Every rounding decision in the system is a decision about integers, and must be
specified rather than left to floating-point convention. See OPEN-11.

**Definition.** R is fungible. Two amounts of equal integer value are indistinguishable, and no unit
carries history, origin, restriction, or tier.

> **OPEN-08 — Definitive name, notation, and on-chain code.**
> `R` is supported as the currency notation. The three-letter code is not settled: the source record
> contains an ambiguous transcription, an `RES` interpretation, and a later `RSV` insertion, none of which
> is a clear user selection. The drafts also propose a deliberate split between the presented notation
> `R` and a machine-readable token symbol. That split may be right, but it is currently a proposal resting
> on an unsettled code. Section 5 (The Monetary Unit) cannot be drafted until this is fixed.

## 4.2 Account

**Definition.** An **account** is an addressable holder of a balance.

**Rule.** Every account has exactly one balance, which is a non-negative integer of base units. An account
exists implicitly; there is no registration, approval, or account-creation operation.

**Definition.** Accounts are classified into three disjoint kinds:

| Kind | Meaning |
|---|---|
| **Institutional** | Controlled by THE RESERVE. The Reserve Treasury is the principal institutional account. |
| **System** | Operated by the system rather than by a person. R sent to a system account is destroyed rather than credited (§7.7), so a system account holds no balance. |
| **Excluded** | Protocol-operated accounts whose balances are held by the system rather than by a participant. |
| **Participant** | Every other account. |

**Condition.** The classification must be total (every account has exactly one kind), disjoint (no account
has two), and publicly derivable.

**Consequence.** Because a system account destroys what it receives, the supply identity in §4.4 is
unaffected by System Payments other than through the reduction of `S` itself.

**Rule.** THE RESERVE designates system accounts, and classifies accounts generally.

**Consequence.** Because a transfer to a system account is destroyed (§7.7), classification is a monetary
power and not bookkeeping: the institution defines the boundary of the destruction channel. It is the
second thing the institution decides, alongside release, and §10.2 is qualified accordingly.

> **OPEN-09 — narrowed: may a designation change?**
> The authority is settled. Undecided: whether a classification can be changed after it is set, by what
> procedure, and what becomes of a balance held by an account that is later designated a system account. A
> mutable designation makes circulating supply — and therefore the settlement amount — partly
> discretionary, which sits against P4.

> **OPEN-10 — What does a participant account hold, as a right?**
> The protocol defines a balance. It does not define what holding R entitles a participant to, what THE
> RESERVE owes a holder, or what a holder can do that a non-holder cannot. Under N2 there is no redemption
> claim, so the answer is not "a claim on the institution" — but no alternative answer is recorded. This
> is OPEN-01 restated at the level of the individual account, and Section 5's "what R does not represent"
> depends on it.

## 4.3 Time and epoch

**Definition.** `t` denotes elapsed time since genesis, measured in **epochs**. The draft epoch length is
seven days.

**Rule.** Genesis occurs at epoch `t = 0`. Epoch boundaries are fixed at genesis and do not shift.

**Condition.** All time-dependent quantities in this document are functions of the integer epoch index,
not of wall-clock instants.

> **OPEN-11 — Calendar convention and rounding.**
> The source drafts state the contraction schedule in two incompatible forms — annually as `S_0(1-c)^t`
> and weekly as `S_0(1-c)^{n/52}`. Neither fixes the reconciliation. Undecided: whether `c` is an annual
> or per-epoch rate; how a 52-epoch year reconciles with a 365-day calendar; how the fractional exponent
> is evaluated in integer arithmetic; and the rounding direction at each step. Since the target determines
> the retirement amount, rounding is not cosmetic — a rounding rule that rounds the target down is a
> slightly faster contraction than one that rounds up, permanently.

## 4.4 Supply, treasury, and excluded balances

**Definition.**

| Symbol | Name | Meaning |
|---|---|---|
| `S(t)` | Total supply | Sum of all balances across all accounts at epoch `t`. |
| `S₀` | Genesis supply | `S(0)`. Draft value: 1,000,000 R. |
| `T(t)` | Treasury | Sum of balances of institutional accounts. |
| `X(t)` | Excluded | Sum of balances of excluded accounts. |
| `C(t)` | Circulating supply | Balance held by participant accounts. |

**Rule.** By construction of the classification in §4.2:

$$
S(t) = C(t) + T(t) + X(t)
$$

and therefore

$$
C(t) = S(t) - T(t) - X(t)
$$

**Condition.** The identity holds only if the account classification is total and disjoint (§4.2). If it
is not, `C(t)` is undefined rather than merely inaccurate.

**Rule (genesis).** At `t = 0`: `S(0) = S₀`, `T(0) = S₀`, `X(0) = 0`, `C(0) = 0`. The entire base is
created once and assigned to the Reserve Treasury. No operation creates a base unit at any `t > 0`.

> **OPEN-12 — Treasury partition.**
> `T(t)` is treated as a single quantity, but it is used for two competing purposes: release into
> circulation, and retirement to meet the target. Every unit released is a unit unavailable to retire.
> The drafts do not partition the treasury, do not state a reserve floor held back for retirement, and do
> not state a policy for returns into the treasury. Without a partition, release policy silently
> determines whether the contraction schedule is achievable — see §4.7.

## 4.5 Transaction and transfer

**Definition.** A **transaction** is an authorized instruction that moves an integer amount from one
account to another.

**Rule.** A transfer of `a` from account `i` to account `j` is valid if and only if `a ≥ 0` and
`balance(i) ≥ a`. It decreases `balance(i)` by `a` and increases `balance(j)` by `a`.

**Consequence.** A transfer between two accounts that both retain what they receive conserves total supply.
The exception is a System Payment, whose recipient destroys rather than retains it (§7.7).

**Definition.** A **release** is a transfer from an institutional account to a participant account.
A **return** is a transfer from a participant account to an institutional account.

**Definition.** A **System Payment** is a transfer from a participant account to a **system account** — an
account operated by the system rather than by a person. A System Payment is the only transfer that
destroys R (§7.7).

**Definition.** A **person-to-person transfer** is a transfer between two participant accounts that are
not system accounts. It conserves supply.

**Rule.** Release requires institutional authorization. It increases `C(t)` and decreases `T(t)`, and
leaves `S(t)` unchanged.

> **OPEN-13 — Release eligibility and purpose.**
> Who receives R, on what basis, in what amount, and what receiving it enables are entirely undefined.
> This is identified in the source material as the major next decision, and it is load-bearing for at
> least four later sections: monetary policy (Section 10), governance (Section 14), economic incentives
> (Section 13), and the participant's actual experience. It also interacts with OPEN-12 — an unbounded
> release policy can exhaust the retirement reserve.

**OPEN-14 — resolved.** System Payments exist in the protocol and are the mechanism by which supply
falls through use. They do not count as circulation between people: they are the other phenomenon, and
§4.8 excludes them from the velocity measure for that reason. The audience-facing term is *System
Payment*, which names the counterparty's role without naming what operates it.

> **OPEN-29 — Is the whole amount burned, and what returns to the payer?**
> §7.7 destroys the amount transferred. Undecided: whether the entire amount is always destroyed or a
> portion is retained by a system account; and what the payer receives in exchange, since a payment that
> obtains nothing is a donation rather than a use. The exchange is the part of the mechanism a
> participant would actually experience, and it is unspecified.

> **OPEN-41 — Can the institution make a System Payment?**
> The definition above admits only a participant account as payer, but the initial payer is confirmed to be
> THE RESERVE
> ([DEC-007](../wiki/decisions/DEC-007-burn-accounting-payer-and-genesis-date.md)). Either institutional
> accounts may also pay the system — in which case R can leave the treasury and be destroyed without ever
> being released, and release is not the only outflow — or "initial payer" means something narrower. This
> bears directly on OPEN-13: it decides whether release is the sole route by which R leaves the
> institution.

## 4.6 Target supply

**Definition.** The **target supply** `S*(t)` is the supply the protocol schedules for epoch `t`.

**Rule.**

$$
S^*(t) = S_0 (1 - c)^{t}
$$

where `c` is the contraction parameter. The draft value is 3% annual.

**Condition.** `c` is fixed at genesis and is not adjustable by governance, vote, or discretion (P4).

**Consequence.** `S*(t)` is strictly decreasing and asymptotically approaches zero. It never reaches zero
in finite time under continuous evaluation, but under integer arithmetic (§4.1) it reaches the smallest
representable amount in finite time.

> **OPEN-15 — Terminal floor.**
> The schedule has no stated floor. Whether contraction continues to the last indivisible base unit, halts
> at a defined minimum supply, or halts when the treasury is exhausted is undecided. The consequence above
> makes this a real endpoint, not a theoretical one, and Section 17 (Failure Modes) requires an answer.

## 4.7 Settlement

**Definition.** **Settlement** is the operation that attempts to bring actual supply to target supply by
permanently retiring institutionally held units.

**Rule.** At settlement in epoch `t`:

1. Compute the required retirement `r = max(0, S(t) − S*(t))`.
2. Compute the available amount `v = min(r, T(t))`.
3. Permanently destroy `v` units from the treasury: `S(t) ← S(t) − v`, `T(t) ← T(t) − v`.
4. Record the shortfall `p = r − v` as **Pending Retirement**.

**Condition.** Settlement never reads or reduces a participant balance. If `T(t) = 0`, settlement retires
nothing and the entire required amount becomes pending.

**Consequence — the central caveat of this system.** Actual supply follows the target only while the
treasury holds enough to retire. Where it does not, `S(t) > S*(t)` persists. The protocol's guarantee is
non-expansion, `S_{t+1} ≤ S_t`, which permits flat supply indefinitely. **A declining target is not a
guarantee of declining supply**, and this document does not present it as one.

> **OPEN-16 — Pending Retirement has no defined semantics.**
> The quantity `p` is recorded, but the drafts do not say what it does. Undecided: whether pending amounts
> accumulate across epochs or are recomputed from scratch each settlement; whether a later treasury
> replenishment must first discharge the backlog; whether the backlog is capped; and whether it is
> merely published or actually constrains anything. If `r` is recomputed each epoch from `S(t) − S*(t)`,
> the backlog is implicit in the gap and the separate record is decorative — which may be the right answer,
> but it has not been chosen.

> **OPEN-17 — Repeat and timing behavior.**
> Settlement is proposed as permissionless. Undecided: whether it may be called more than once per epoch;
> what happens when it is not called for many epochs; whether the caller is compensated; and whether an
> uncalled epoch is skipped or accrued. A permissionless operation with no caller incentive may simply not
> be called, which is a failure mode with no current mitigation.

**OPEN-18 — resolved.** `S*(t)` is a **ceiling**, not a floor. Supply may be below it, and often will be:
burn counts toward the target (§7.7), so holders' own use can carry `S` under `S*`, at which point
`r = max(0, S − S*)` is zero and settlement retires nothing. The schedule states the most R that may exist
at epoch `t`, not the amount that must.

## 4.8 Observation

**Definition.** The **Reserve Observer** is an off-chain process that computes and publishes statistics
about the monetary state. It holds no balance and controls no account.

**Condition.** The Observer does not observe independent behavior. R exists only within the world and no
actual person holds it (§1), so there is no external population whose activity could be measured. The
series the Observer publishes is **simulated**: it runs on data generated for the world, not collected
from it.

**Rule.** Every series the Observer publishes is labeled as simulated wherever it appears. The document,
and anything an audience sees, must not present it as an independent measurement.

**Definition.** Observed velocity over a 30-day window:

$$
V_{30} = \frac{Q_{30}}{\overline{C}_{30}}
$$

where `Q₃₀` is eligible transfer volume over the window and `C̄₃₀` is average circulating supply over the
same window.

**Rule.** `Q₃₀` counts person-to-person transfers only. It excludes releases, returns, retirements,
transfers between excluded accounts, and System Payments — the last because a System Payment is the
destruction channel (§7.7), not a form of circulation between people.

**Consequence.** With System Payments excluded, `V₃₀` measures exactly the phenomenon the world's velocity
record is about: how often R moves between people.

**Condition.** `V₃₀` is undefined when `C̄₃₀ = 0`, which is the state of the system immediately after
genesis.

> **OPEN-19 — Velocity is not yet a measure of anything.**
> Eligibility for `Q₃₀` is defined only by exclusion, and the exclusions depend on the unresolved account
> classification (OPEN-09). Also undecided: whether self-transfers and round-trips between accounts under
> one controller are excluded, how the average `C̄₃₀` is computed, and the zero-circulation case. Until
> these are fixed, `V₃₀` measures on-chain transfer activity, not the human behavior the world direction
> describes, and the document must not present it as the latter.

**Rule (what separates the two records).** The world's declining velocity is a **world record** (§9.2): a
statement the institution makes. The Observer's series is a **simulated series**: data generated to express
that history in numbers. Both are authored. They differ in how they are produced, not in whether they are,
and neither is evidence for the other.

> **OPEN-20 — narrowed: how the simulation is disclosed.**
> The boundary is decided; its presentation is not. Undecided: what label the audience sees, whether the
> generating assumptions are published alongside the series, and whether the world record and the simulated
> series are shown together at all. What is settled is that nothing may be presented as measurement of
> real activity. See also OPEN-24, OPEN-38.

## 4.9 Protocol state

**Definition.** The **protocol state** at epoch `t` is

$$
\Sigma(t) = \big(\, B(t),\; K(t),\; t,\; p(t),\; \Pi \,\big)
$$

where `B(t)` is the mapping from accounts to balances, `K(t)` is the account classification (§4.2), `p(t)`
is Pending Retirement (§4.7), and `Π` is the fixed parameter set `(S₀, c, d, epoch length)`.

**Rule.** State advances by a transition function `τ` applied to a state and an operation:

$$
\Sigma(t+1) = \tau\big(\Sigma(t),\, \text{op}(t)\big)
$$

where `op` is one of *transfer*, *release*, *return*, *systemPayment*, *settle*, or *classify*.

**Note on notation.** The source outline wrote this relation with `S` for whole protocol state, while the
monetary drafts use `S` for total supply and `T` for the treasury balance. This manuscript resolves that
collision by reserving `S` and `T` for the monetary quantities and writing protocol state as `Σ` and the
transition as `τ`. The derived quantities `S(t)`, `T(t)`, `X(t)`, `C(t)` are all functions of `Σ(t)`; they
are not independent state.

**Invariants.** For every transition:

- **I1** — `S(t+1) ≤ S(t)`. No operation increases total supply, and it follows that
  `S(t) ≤ S*(t) ≤ S₀`.
- **I2** — `S` decreases by exactly two operations: *settle*, which retires treasury units on a schedule,
  and *systemPayment*, which burns the amount a holder spends toward the system. *transfer*, *release*,
  and *return* conserve it.
- **I3** — For every participant account `i`, `balance(i)` changes only by a transfer that `i` authorized.
- **I4** — `S(t) = C(t) + T(t) + X(t)` holds after every transition.
- **I5** — Every balance is a non-negative integer of base units.

## 4.10 Symbols

| Symbol | Meaning | Status |
|---|---|---|
| `R` | The monetary unit | Notation supported |
| `d` | Decimals | Draft: 18 |
| `t` | Epoch index since genesis | Draft epoch: 7 days |
| `S(t)` | Total supply | Defined |
| `S₀` | Genesis supply | Draft: 1,000,000 R |
| `S*(t)` | Target supply | Defined; see OPEN-11, OPEN-15, OPEN-18 |
| `c` | Contraction parameter | Draft: 3% annual; annual-vs-epoch unresolved |
| `T(t)` | Treasury balance | Defined; partition unresolved (OPEN-12) |
| `X(t)` | Excluded balances | Defined; membership unresolved (OPEN-09) |
| `C(t)` | Circulating supply | Derived |
| `r`, `v`, `p` | Required, actual, pending retirement | Defined; `p` semantics unresolved (OPEN-16) |
| `Q₃₀`, `C̄₃₀`, `V₃₀` | Observed volume, average circulation, velocity | Draft; eligibility unresolved (OPEN-19) |
| `Σ(t)` | Protocol state | Defined here; resolves source notation collision |
| `τ` | State transition function | Defined here |
| `Π` | Fixed parameter set | Values not confirmed |

---

---

# 5. The Monetary Unit: R

## 5.1 The unit

**Definition.** One R is one unit of account of THE RESERVE. It is defined by its position in the system,
not by any quantity of an external thing.

**Condition.** The unit's constancy is produced, not assumed. `1R = 1R` holds because destruction offsets a
value that would otherwise fall (§7.7, §10.4). Remove the mechanism and the premise does not survive.

**Rule.** The unit is invariant. R is never redenominated, split, merged, rebased, revalued, or replaced
by a successor unit. An amount recorded at genesis denotes the same unit at every later epoch.

**Condition.** Invariance of the unit is independent of the quantity of units. §7 reduces the aggregate;
nothing in §7 touches the definition of the unit itself.

**Rule (divisibility).** R is divisible into `10^d` indivisible base units and every protocol quantity is
an integer number of them (§4.1). Divisibility is a property of the notation, not of value: subdividing
100 R into smaller amounts creates no additional R.

**Rule (fungibility).** Units are indistinguishable. No unit carries origin, history, tier, restriction,
or provenance. A unit released last epoch and a unit released at genesis are the same unit.

**Consequence.** Because the unit is invariant and fungible, the only monetary variable in the system is
*how many* units exist and *who holds them*. R has no second dimension for policy to act on. This is what
makes the design small enough to specify, and also what leaves the institution with a single instrument
(OPEN-23).

## 5.2 The issuer

**Definition.** THE RESERVE is the central bank and issuing authority of R. A quantity of R is assumed to
have existed from the outset; the institution records that quantity into the Reserve Treasury at genesis,
holds the undistributed remainder, authorizes release into circulation, and publishes the monetary state.

**Condition.** "Issuing authority" means that no other party may bring R into existence. It does not mean
the institution performed an act of creation: the base is a premise of the world, not something the
institution made.

**Rule.** No other institution issues R. There is no second issuer, no delegated issuance, and no
mechanism by which a participant, a bank, or a contract can bring a base unit into existence.

**Rule (mandate).** The institution's mandate is **RESERVE**: to keep what is held. This is its whole
stated monetary objective, and every discretionary act is judged against it (§10).

**Condition.** *This document* is confined to the base layer. The banking layer above it is operated by
the same institution (§2.4, P7); it is unspecified here, not assigned elsewhere.

**Consequence.** The authority's powers are narrower than a conventional central bank's in every respect
except issuance. It sets no policy rate on the base unit (N5), conducts no market operations (N6), holds
no external reserves against R (N2), and cannot expand the base under any condition (P3). The contraction
schedule is fixed and blind (P4), and settlement is permissionless (§3.2). **Release is therefore the
institution's only discretionary monetary act.**

**OPEN-21 — resolved.** R is not a liability of THE RESERVE. It is issued against nothing, redeemable for
nothing, and represents no obligation of the institution. The treasury is a balance of undistributed money,
not an asset held against a liability, and the institution has no balance sheet in which R appears as an
obligation. Section 6 therefore models the treasury correctly as a balance.

**OPEN-22 — resolved.** The same institution operates the banking layer, under P7. No separate bank is
chartered or licensed.

> **OPEN-25 — May the banking layer create claims exceeding the base?**
> One institution now holds the base and would also create claims denominated in it. Whether deposit or
> credit claims may in aggregate exceed the R that backs them — the ordinary condition of banking, and the
> mechanism by which money is elsewhere created — is unspecified. P3 protects the *base* from expansion; it
> says nothing about claims above it. This is the banking layer's central question and it sits with the
> same institution that guarantees the base's non-expansion.

## 5.3 What R does not represent

**Rule.** R is not a claim and not a liability of anyone. Holding R does not entitle the holder to
redemption, to an external asset, to a payment from THE RESERVE, or to a share of anything the institution
holds.

**Rule.** R is not a security, a share, a debt instrument, or a certificate of participation, and this
document makes no statement about how any jurisdiction would classify it.

**Rule.** R is not a measure of purchasing power. `1R = 1R` states that the unit is constant as a unit of
account (§5.1); it makes no claim about what R buys, at any time, anywhere (N3).

**Consequence.** What remains, once those are excluded, is the plain positive statement: R is the object
in which balances within THE RESERVE are denominated and settled. What the institution owes a holder is
not a payment but the preservation of the conditions under which the unit can be kept — which is the
mandate (§10.1). What a holder can *do* that a non-holder cannot is still unstated (OPEN-10).

## 5.4 Relationship to external currency

**Rule.** The protocol defines no exchange rate, publishes no reference rate, and reads no external price
(N1, N4).

**OPEN-06 — resolved.** R exists only within the world and cannot be held by anyone outside it. There is
therefore no party who could trade it, and no external market, actual or potential. The absence of an
exchange rate is not a refusal to acknowledge a price; there is no price.

**Consequence.** Arguments elsewhere about an internal unit coexisting with an external market do not
apply here. The unit is the only price R has.

---

# 6. Monetary State

## 6.1 The state

**Definition.** The monetary state at epoch `t` is the tuple `(B(t), K(t), t, p(t), Π)` written `Σ(t)` in
§4.9: balances, account classification, epoch, Pending Retirement, and the fixed parameter set.

**Rule.** `S(t)`, `T(t)`, `X(t)`, and `C(t)` are **derived**, not stored: each is a sum over `B(t)`
restricted by `K(t)`. The protocol maintains no independent counter that could disagree with the balances.

**Condition.** The identity `S(t) = C(t) + T(t) + X(t)` (I4) holds by construction of the classification,
and fails to be meaningful the moment the classification stops being total and disjoint (OPEN-09).

**Consequence.** There is no privileged internal record. Anyone reconstructing balances from the public
record derives the same monetary aggregates the institution publishes.

## 6.2 Published state

**Rule.** The institution publishes, at every epoch: total supply `S(t)`; treasury `T(t)`; excluded
balances `X(t)`; circulating supply `C(t)`; target supply `S*(t)`; cumulative retirement `S₀ − S(t)`; and
Pending Retirement `p(t)`.

**Condition.** Each published quantity is derivable from the record by a third party. Nothing in the
published set depends on information only the institution holds (P6).

**Consequence.** The institution's own monetary position is public. A holder can always determine how much
R the issuer still controls, and therefore how much retirement capacity remains — which is the quantity
that determines whether the contraction schedule can actually be met (§7.6).

---

# 7. Issuance and Supply

## 7.1 Genesis

**Definition.** Genesis is the single issuance, at a defined point in the past, of the fixed quantity `S₀`.
It is the only issuance in this world's history.

**Rule.** At `t = 0`, `S₀` units are issued in full to the Reserve Treasury: `S(0) = T(0) = S₀`,
`X(0) = 0`, `C(0) = 0`.

**Condition.** Genesis occurs exactly once and cannot be repeated, re-run, or supplemented.

**Rule (genesis date).** Genesis is **17 September 1975**. That date is Epoch 0.

**Rule (the criterion).** From genesis to **17 September 2025** the quantity declines steadily. At that
date, **30 ± 5% of `S₀`** remaining — a band of 25% to 35% — meets the criterion.

**Condition.** This is the world's only dated statement about quantity, and it is a **criterion, not a
value**. No figure is asserted for that date or any other. Every quantity in the world's history is
whatever the schedule and the realized path produce, subject to this one test.

**Rule (the record begins after the decline).** The interval from genesis to the present sits **before the
record**. The ledger opens with supply already reduced to roughly a quarter to a third of `S₀`; it does not
open at `S₀`.
Genesis and the original quantity are documented facts of the world's history, not the ledger's opening
state.

**Condition.** The epoch index continues to count from 1975, so the record opens at approximately epoch
2,660 rather than at epoch 0. `S*(t)` is evaluated on that same index, which is what makes the opening
balance and the schedule agree.

**Condition.** `t = 0` is a past moment in the world, not the moment a reader arrives. Over fifty years —
18,263 days, or 2,609 seven-day epochs, to the date the criterion names — separate genesis from the
present, and `S` has been falling throughout. A reader meets the system with most of it already gone.

**Consequence.** Every R that will ever exist existed at `t = 0`. The system's entire subsequent monetary
history is a redistribution and a reduction of that one quantity, and the institution never adds to it.

**OPEN-32 — resolved.** Genesis is 17 September 1975, Epoch 0. The world's only dated statement about
quantity is the criterion above, and it names a band rather than a value. An earlier figure putting the
present at about 50% is withdrawn and appears nowhere in this document.

**OPEN-34 — resolved.** The schedule is not a constant-rate exponential. It accelerates (§7.4), which is
also why the drafts' 3% annual parameter is inapplicable in shape as well as in magnitude.

**OPEN-33 — resolved.** The deployment is **both** a public ledger that displays the world's monetary
history and a rule implementation whose accounts exist only within the world. It distributes to no one.
Its own genesis is the moment of deployment, which is why the elapsed history sits before the record.

## 7.2 No issuance after genesis

**Rule.** Genesis is the only issuance (§7.1). No operation in §8.1 creates a base unit, and `S₀` is never
exceeded.

**Rule.** Of the operations specified, none increases `S`: transfers conserve it, and settlement (§7.5) and
burn (§7.7) reduce it.

**Consequence.** Invariant I1 (`S_{t+1} ≤ S_t`) holds unconditionally. There is no emergency issuance, no
governance mint, no yield, no restoration of destroyed units, and no minting to pay obligations —
including obligations the banking layer may later create, which is precisely why P5 exists.

## 7.3 Release

**Definition.** A **release** transfers units from the treasury to a participant account (§4.5).

**Rule.** Release requires institutional authorization. It decreases `T(t)`, increases `C(t)`, and leaves
`S(t)` unchanged.

**Condition.** Release is bounded by `T(t)`. The institution cannot release what it does not hold, and
cannot create what it needs.

**Consequence.** Release and retirement draw on the same finite pool. Every unit released is a unit no
longer available to retire. Release policy therefore silently determines the achievability of the
contraction schedule, and there is currently no partition, floor, or bound that prevents release from
exhausting retirement capacity — see OPEN-12 and OPEN-13, which §7.6 depends on.

## 7.4 Target supply

**Condition (shape).** The contraction does not run at a constant rate. It is **slow at first and
accelerates**: early loss is slight, later loss is steep. A constant-rate exponential is the wrong shape
for this world, not merely the wrong magnitude.

**Rule (draft form).** The schedule is a stretched exponential in elapsed years `y`:

$$
S^*(y) = S_0 \exp\left[-\left(\frac{y}{\lambda}\right)^{k}\right], \qquad k > 1
$$

`k` is the shape parameter that produces acceleration; `λ` is the scale. `k = 1` recovers the constant-rate
case and is excluded. The instantaneous annual rate of decline is `(k/λ)(y/λ)^{k−1}`, which rises with `y`
— the property that makes the curve accelerate.

**Condition (the criterion, not an anchor).** The world fixes no point on this curve. It states one test
(§7.1): the realized quantity at `y = 50.00` — 17 September 2025 — lies between **25% and 35%** of `S₀`.
A test with a tolerance does not determine `λ` from `k`; it admits a **family** of curves.

**Admissible parameters.** For the draft shape `k = 2`, any `λ` between **42.47 and 48.80** years satisfies
the criterion. Other shapes have their own ranges — roughly 40.22–48.41 for `k = 1.5`, and 44.84–49.20 for
`k = 3`.

**Consequence.** A ten-point band at one date is a band everywhere. With `k = 2` the admissible history
spans:

| Year from genesis | Calendar | Remaining |
|---|---|---|
| 10 | 1985 | 94.6% – 95.9% |
| 25 | 2000 | 70.7% – 76.9% |
| 40 | 2015 | 41.2% – 51.1% |
| 50.00 | **2025** | **25.0% – 35.0%** |
| 50.98 | 2026 | 23.7% – 33.6% |
| 60 | 2035 | 13.6% – 22.1% |
| 75 | 2050 | 4.4% – 9.4% |

The band is widest in the middle decades and narrows toward the ends, because a curve pinned loosely at one
late date is least constrained where it is furthest from that date in proportion.

**Consequence — this is what the generator must satisfy.** The flows are generated (§9.3), so a criterion
rather than a value gives the generator a test to pass. Shape, scale, and noise process are jointly
constrained by one condition at one date, and by nothing else. Any combination whose realized path lands in
the band qualifies.

**No parameter is confirmed.** The values above are computed from the criterion; the world states only the
criterion.

**Condition.** The target is a function of elapsed time and fixed parameters only. It does not read `S`,
`T`, price, activity, or any external input (P4).

**Consequence.** The schedule remains computable by anyone for any date. Acceleration changes the curve's
shape, not its determinism.

## 7.4a The realized path and its noise

**Definition.** The **realized path** `S(t)` is the world's actual monetary history. The schedule `S*(t)` is
its ceiling. They are different objects and only the schedule is smooth.

**Rule (one-sided).** Noise lies on one side only: the realized path runs **beneath** the schedule. It
never straddles it, so the ceiling in §4.6 is never breached and `S*` remains a bound rather than a central
tendency.

**Rule (bounded above by the original quantity).** `S(t) ≤ S₀` at every point in the world's history,
without exception.

**Rule (monotone).** The realized path never rises. Supply is non-increasing at every step (I1, P3), so
noise appears only as **variation in the speed of decline** — periods of faster and slower loss — and never
as a fluctuation upward. A noise model that can increase supply is not admissible in this system.

**Condition (what the criterion constrains).** The criterion in §7.1 applies to the **realized quantity**
— what actually remains — and therefore to the path, not to the schedule. The schedule need only sit at or
above it. Because the criterion carries a tolerance, a path running below its schedule can satisfy it
without the two meeting, so nothing here forces them together.

**OPEN-40 — resolved by the tolerance.** Whether the path meets the ceiling on that date no longer
determines whether anything is anchored: the band accommodates either. What remains is how far below the
schedule the path runs, which is the noise amplitude in `OPEN-36`.

> **OPEN-36 — narrowed: the noise's own specification.**
> The structural questions are settled: one-sided, beneath the schedule, monotone. Undecided: the
> distribution, amplitude, and time scale of the deviation, and whether it is generated once as the world's
> fixed history or produced continuously. Since the path cannot rise, the noise is a process on the
> *rate* — specifying it means saying how much the rate may vary and over what horizon. Its amplitude and
> the curve's parameters are constrained jointly, by the single test at 2025 and nothing else.

> **OPEN-37 — Which `k`, and which `λ` within its admissible range?**
> The criterion admits a family (§7.4), so neither parameter is determined. Because the curve is the world's
> entire monetary history, the choice decides how much was lost in the decades the work refers to: at 2000
> the admissible range alone spans 70.7%–76.9% for `k = 2`, and a different shape moves it further. Fixing
> it needs either a second criterion at another date or a direct choice of parameters.

## 7.5 Retirement

**Rule.** Settlement retires `v = min(max(0, S(t) − S*(t)), T(t))` units from the treasury, permanently,
and records the shortfall as Pending Retirement (§4.7).

**Condition.** Retirement acts on the treasury only. No participant balance is read, reduced, or required
(P2, N7, I3).

**Consequence.** Retirement reduces `S` on a schedule and can only ever reduce it. It is not the only
channel that reduces `S`; §7.7 is the other.

## 7.6 What the supply schedule does not guarantee

**Condition.** Retirement is capped by `T(t)`.

**Consequence.** If the treasury is exhausted, scheduled retirement stops. `S(t)` then falls only as
holders spend toward the system (§7.7), at whatever rate they do — which may be slower than the schedule,
faster than it, or not at all. The protocol's guarantee is non-expansion, which is satisfied by a
permanently flat supply.

**Rule (statement of limits).** This document states, and the institution must not contradict elsewhere:
the target is a schedule, not a promise; supply may lag the target without any rule having been broken;
and the gap `S(t) − S*(t)` is itself published (§6.2) rather than concealed.

**Consequence.** A reader can judge the system's actual contraction from the record instead of from the
schedule. Whether the gap is intended to be closable at all — that is, whether the institution holds back
retirement capacity as a matter of policy — is OPEN-12.

## 7.7 Burn

**Definition.** A **burn** is the permanent destruction of the amount transferred in a System Payment
(§4.5).

**Rule.** A System Payment of `a` from participant account `i` to a system account decreases
`balance(i)` by `a` and decreases `S(t)` by `a`. No account's balance increases.

**Condition.** Burn occurs only through a transfer the holder themselves authorized. No schedule, elapsed
time, institutional act, or third party can burn a holder's R (P2, N7, I3).

**Rule (use between people is not a burn).** A person-to-person transfer conserves supply exactly. Two
holders may pass the same R between them without limit and destroy nothing.

**Consequence — why the mandate and the mechanism agree.** In this world the value of R is falling.
Destruction is how that value is preserved: as units leave the supply, what remains is preserved rather
than diluted. Reducing the quantity is not the opposite of keeping; it is the instrument of keeping. That
is the whole of the apparent contradiction between a mandate to reserve and a mechanism that destroys
money, and it dissolves once the purpose is stated.

**Consequence — contraction is partly behavioral.** One reduction channel follows a fixed schedule and one
follows what holders do. The protocol therefore does not determine the path of `S(t)`, only that it never
rises.

**Rule (burn counts toward the target).** Burned units count toward the contraction target. The formula
needs no special case: `r = max(0, S − S*)` reads whatever `S` has become, so every unit a holder destroys
is a unit the treasury need not retire.

**Consequence.** The two channels are not independent. Use toward the system relieves the institution of
retirement, and where use is heavy enough, supply falls below `S*(t)` and scheduled retirement stops
entirely (§4.6, `OPEN-18`). Holders' behavior can therefore carry the whole of contraction, and the
institution's schedule becomes a ceiling that behavior has already satisfied.

**OPEN-28 — resolved** by the rule above. **OPEN-30 — resolved:** THE RESERVE designates system accounts
(§4.2).

**Consequence — the institution shapes the burn channel without operating it.** It cannot make a holder
spend, but by designating which accounts destroy what they receive, it defines where destruction is
possible at all.

> **OPEN-29 — narrowed: what does a payer receive?**
> The initial payer is THE RESERVE. What any payer receives in exchange for a System Payment is still
> unstated, and a payment that obtains nothing is a donation rather than a use. This is the part of the
> mechanism an in-world participant would actually experience.

---

# 8. Transactions and State Transitions

## 8.1 Operations

**Definition.** The protocol admits exactly six operations: *transfer*, *release*, *return*,
*systemPayment*, *settle*, and *classify*.

| Operation | Authorized by | Effect on `S` | Effect on `C` | Effect on `T` |
|---|---|---|---|---|
| transfer | the sending account | unchanged | unchanged | unchanged |
| release | the institution | unchanged | increases | decreases |
| return | the sending participant | unchanged | decreases | increases |
| systemPayment | the sending participant | decreases | decreases | unchanged |
| settle | anyone (permissionless) | decreases | unchanged | decreases |
| classify | undecided (OPEN-09, OPEN-30) | unchanged | changes | may change |

**Condition.** *transfer* between two participant accounts is the only operation that changes no aggregate
at all. It moves R without changing what the monetary state says about the system.

**Consequence.** The two supply-reducing operations are authorized by different parties and follow
different logics: *settle* by anyone against a formula, *systemPayment* by a holder against their own
intent. Neither is executed by the institution — though the institution decides, through *classify*, which
accounts destroy what they receive (§4.2).

## 8.2 Validity

**Rule.** A transfer of `a` from `i` to `j` is valid if and only if `a ≥ 0`, `a` is an integer of base
units, and `balance(i) ≥ a` (§4.5). There is no other precondition — no whitelist, no minimum, no fee
requirement stated at this layer, and no time lock.

**Condition.** Authorization is the sending account's alone. Neither the institution nor any third party
can move a participant's balance (I3).

## 8.3 Transition

**Rule.** `Σ(t+1) = τ(Σ(t), op(t))`, where `τ` is total over valid operations and undefined over invalid
ones — an invalid operation is rejected, never partially applied.

**Condition.** Every transition preserves I1–I5 (§4.9). A proposed extension to the protocol that cannot
preserve them is out of scope of this base layer by definition, not by policy.

**Consequence.** The invariants, not the operation list, are the specification. Any implementation that
preserves I1–I5 and the published derivations of §6 implements this monetary model, whatever its
mechanics.

## 8.4 Fees

**Condition.** Fees paid to a network for including a transaction are not a monetary operation of this
protocol: they are denominated in whatever the underlying network requires and do not move, create, or
destroy R.

> **OPEN-17 — restated here because §8 makes it structural.**
> Settlement is permissionless and carries no stated reward, so no participant has a reason to pay a
> network fee to call it. A contraction schedule that depends on an uncompensated voluntary call is a
> schedule that may simply not be executed. Repeat-call behavior within an epoch and the treatment of
> skipped epochs are undecided alongside it.

---

# 9. Monetary Dynamics

Section 9 contains the document's only **world records**. They are labeled as such at each occurrence, per
the boundary in §2.4.

## 9.1 What the protocol determines

**Rule.** The protocol determines the aggregate's direction: `S` is non-increasing, `S*` declines
deterministically, and no balance changes without its holder's authorization. These are enforceable and
verifiable.

**Condition.** The protocol does not determine the aggregate's *path*. One reduction channel is scheduled
and one is behavioral (§7.7), so how fast `S` actually falls depends on how holders use R.

**Condition.** The protocol determines nothing about behavior. It does not know why a transfer occurred,
whether two accounts share a controller, or whether a holder intends to keep or to spend. It observes only
where a payment went.

**Consequence.** Velocity is not a protocol variable. Nothing in §§5–8 constrains it, and no rule in this
document can make it rise or fall. What the protocol does establish is that the two behaviors have
different monetary consequences — use between people preserves the supply, use toward the system reduces
it — so the world's behavioral direction and its monetary direction are linked by mechanism rather than by
assertion.

## 9.2 The world record

**World record.** In the world of THE RESERVE, velocity declines. Money moves between people less often
over time; holding lengthens; accumulation replaces circulation. This is the institution's account of its
own monetary history and it is a defined result within that world.

**World record.** The value of R is falling in this world. The contraction of the supply is what preserves
it (§7.7).

**World record.** The two directions are stated together: the base contracts, and the money that remains
moves less between people. Together they describe a monetary system settling rather than accelerating —
which is the condition the design exists to express (§2.2).

**Condition.** These are one behavior, not two coincidences. A world that spends toward the system rather
than with one another produces both a falling person-to-person velocity and a falling supply, because the
same act that removes a payment from circulation between people is the act that burns it.

**Condition.** A world record is not enforced, not guaranteed, and not derived from the ledger. It is what
the institution states, and it is the only category of statement in this document with that status.

> **OPEN-24 — Does the world record carry values, or only a direction?**
> "Velocity declines" is a direction. Whether the institution's history states specific values over
> specific periods — a series an audience could read — or asserts only the direction, is undecided. A
> stated series is authored data and must be labeled as such wherever it appears; a direction alone cannot
> be plotted. This determines what the quiet interface can actually show.

## 9.3 Simulation

**OPEN-35 — resolved.** There are no real participants, and no divergence between world record and
observation can arise. There is no external population holding R (§1), so nothing independent exists to
diverge. What replaces observation is **simulation**: the system exists within the world, and although no
actual person uses it, its use can be simulated. The declining velocity is a flow that runs on simulated
data. See
[DEC-008](../wiki/decisions/DEC-008-contraction-curve-simulation-and-ledger-scope.md).

**Rule.** The Reserve Observer publishes a simulated series, labeled as such (§4.8). It measures no real
activity and offers no independent confirmation of anything.

**Condition.** This removes a check the earlier design assumed it had. A published number here is not
evidence; it is the world's history expressed as data. The document's honesty requirement therefore moves
rather than disappears — from *keep the measurement separate from the claim* to **say plainly that the
series is generated**.

**Consequence.** `V₃₀` and the other published series remain useful as the form in which the world's
monetary history becomes legible, and they remain worth defining precisely (§4.8) so that what is
generated is generated consistently. They are not, and must never be presented as, observations.

**OPEN-38 — resolved.** A **generator** produces the simulated data. It is **published on GitHub**, and it
is **not disclosed within the work**.

**Rule (disclosure).** This document states that the series is generated and where the generator lives. The
work itself shows the series without explaining it. The method is auditable by anyone who looks for it; the
work stays quiet.

**Consequence.** The audience is not asked to accept numbers on the institution's word, but neither is it
told. Verification is available and unadvertised — which is the same posture the institution takes toward
its own monetary state (§6.2), where everything is derivable and nothing is announced.

**Condition.** The generator does not yet exist, and no repository is named.

## 9.4 What this section does not claim

- It does not claim that a contracting base causes velocity to decline. The mechanism runs the other way:
  a behavior that lowers person-to-person velocity is the same behavior that contracts the base (§7.7).
  Neither aggregate is asserted to cause the other.
- It does not demonstrate that contraction preserves value. That destruction preserves value is a premise
  of this world (§9.2), not a validated monetary result, and no model, simulation, or evidence in this
  document supports it.
- It does not claim that the world's decline has been observed or validated. It is simulated, which is
  a way of expressing the world's history in data and not a way of testing it.
- It does not claim that R's holders will behave in any particular way, since no actual person holds R.

---

# 10. Monetary Policy

## 10.1 The objective

**Definition.** The mandate of THE RESERVE is **RESERVE**: to keep what is held.

**Rule.** The institution has no other stated monetary objective. It does not target a price level, an
exchange rate, an activity level, a velocity, a rate of return, or a distribution of holdings.

**Condition.** The mandate is about *keeping*, not about *quantity in itself*. In this world the value of R
is falling, and reducing the quantity is how that value is preserved (§7.7). Scarcity is therefore not a
separate objective the institution pursues alongside keeping; it is the form keeping takes.

**Condition.** `1R = 1R` is the mandate's result, not its premise. The unit holds because destruction
offsets a value that would otherwise fall; an institution that stopped destroying would not preserve a
constant unit, it would lose one.

**Condition.** The mandate does not oblige the institution to make R available, and it does not authorize
it to take anything from a holder. What it obliges is the preservation of the conditions under which what
a holder holds remains worth holding.

**Consequence.** Most of what a central bank ordinarily does is not merely unavailable to THE RESERVE
(§5.2) but outside its objective. There is nothing for open-market operations, a policy rate, or a
liquidity facility to serve here, which is why their absence in §3.3 is stated as a set of decisions
rather than as capability the institution lacks.

## 10.2 The single instrument

**Rule.** The institution has two discretionary acts: **release**, which puts R into circulation (§7.3),
and **classification**, which designates the system accounts that destroy what they receive (§4.2). Genesis
is complete (§7.1), the contraction schedule is fixed and blind (P4), settlement is permissionless and
formula-determined (§3.2), and a burn is initiated by the holder who spends (§7.7).

**Consequence.** The institution decides what enters circulation, and where destruction is possible. It
decides neither how much is destroyed nor when — that follows from use.

**Condition.** Every release is judged against the mandate: whether it serves the keeping of what is held.

**Consequence.** Monetary policy here is a policy about two acts, evaluated against one criterion. It has
no dials, no stance, no tightening or loosening, and no reaction function. The institution can decide
whether, to whom, and how much to release, and which counterparties destroy what they are paid — and the
answer to *why* is always the same word.

> **OPEN-13 — Release eligibility, purpose, and amount.**
> The mandate now supplies the criterion but not the rule. Undecided: who is eligible to receive R, on
> what basis, in what amount, at what frequency, and what receiving it makes possible for the recipient.
> This is the last of the original blocking gaps and it is what §10 needs in order to become a policy
> rather than a principle.

> **OPEN-26 — Is release ever obligatory?**
> §10.2 treats release as discretionary throughout. Whether the mandate can ever *require* a release —
> whether some condition obliges the institution to act rather than permitting it — is unspecified. The
> answer determines whether a holder or applicant has any standing at all, and it is closely coupled to
> OPEN-10.

## 10.3 What policy does not do

**Rule.** Policy does not expand the base under any condition (P3), does not adjust `c` or the schedule
(P4), does not reduce any holder's balance (P2, N7), does not intervene in a market (N6), and does not read
an external price (N4). It also does not cause a burn: only a holder's own System Payment does (§7.7).

**Consequence.** A reader can verify from the record that policy did none of these things, because none
of them is expressible as an operation in §8.1.

## 10.4 The mandate and destruction

**Condition.** A mandate to keep sits against a mechanism whose central act is destroying money. Stated
without qualification the two appear to contradict.

**Rule.** They do not. In this world the value of R is falling, and destruction is how that value is
preserved. What the mandate keeps is not the *number of units* but the *worth of what is held*, and
reducing the quantity is the instrument by which that is done. Contraction is the mandate carried out, not
a departure from it.

**Consequence.** This settles what the institution is for, and it is the reason none of the ordinary
central-bank instruments appear here. An institution that preserved value by defending a price would need
markets, reserves, and a rate. This one preserves it by taking units out of existence — on a schedule for
what it holds, and through holders' own use for what they hold.

**OPEN-27 — resolved.** Destruction preserves a falling value; the mandate and the mechanism are the same
purpose. An earlier draft of this section proposed instead that retirement removes only the institution's
undistributed remainder, so that what is preserved is what people hold. That reading was wrong: it
described a boundary rather than a purpose, and it could not account for burn, which reaches exactly the
units holders spend. See
[DEC-006](../wiki/decisions/DEC-006-burn-mechanism-and-value-preservation.md).

**OPEN-31 — resolved.** The fixed unit and the falling value are not in conflict: `1R = 1R` holds
*because* supply is destroyed as the value would otherwise fall. The confirmed premise that the unit's
value does not change is not revised by the falling value — it is explained by it. §5.1 records the same
statement as a condition on the unit.

## 10.5 The banking layer

**Condition.** The same institution operates the banking layer (§2.4, P7). A mandate to keep therefore
governs an institution that would also create claims denominated in what it keeps.

**Consequence.** The mandate does not stop at the base. Whether it constrains the banking layer, and how,
is not specified here — see OPEN-25, which asks the sharper form of the same question.

---

# Sections 11–22 — outline

Retained from the proposed 22-section outline in
[r-whitepaper-development](../wiki/concepts/r-whitepaper-development.md).

11. **Protocol Architecture** — *structurable now: unit contract, treasury, observer (§4.8). Blocked on
    OPEN-07 for the upgradeability statement.*
12. **Network and Transaction Lifecycle** — *blocked on the network decision; Base Sepolia is a draft
    choice, not a confirmed target.*
13. **Economic Incentives and Fees** — *blocked on OPEN-17. §8.4 states the problem: an uncompensated
    permissionless settlement call.*
14. **Governance** — *structurable now that authority is settled (§3.2, §5.2); blocked on OPEN-05 for the
    permission model, keys, and release bounds.*
15. **Security Model** — *blocked on OPEN-05 and OPEN-07.*
16. **Privacy and Transparency** — *unblocked in substance by §6.2 and §9.3; blocked on OPEN-20 and
    OPEN-38 for how the simulation and its generator are disclosed.*
17. **Failure Modes** — *partially drafted in substance at §7.6 and §8.4; blocked on OPEN-15 (terminal
    floor) and OPEN-16 (Pending Retirement semantics).*
18. **Risks and Limitations**
19. **Implementation and Deployment** — *structurable now that the deployment's purpose is settled (§7.1):
    a public ledger of the world's history and a rule implementation with in-world accounts only, opening
    after the elapsed decline. No implementation exists; blocked on OPEN-38 and OPEN-07.*
20. **Conclusion**
21. **References**
22. **Appendices** — Formal Protocol Specification; Monetary Model and Equations; Protocol Parameter
    Registry; Threat Model; Disclosure Matrix; Reference Implementation Specification

---

# Open definitions

Forty-one gaps have been exposed by drafting Sections 1–10. Twenty-eight are resolved; the rest are ordered by
how much later drafting they block.

## Resolved

| ID | Question | Resolution |
|---|---|---|
| OPEN-01 | Why the institution issues money at all | To keep. Same word as the mandate. §10.1 |
| OPEN-02 | What is THE RESERVE, institutionally? | Central bank and issuing authority of R. §5.2 |
| OPEN-03 | Is the decline authored, modeled, or emergent? | Authored world history, expressed as simulated data. §9.2, §9.3 |
| OPEN-04 | Where does artwork narrative end and protocol fact begin? | By enforceability, not by section. World records are labeled. §2.4 |
| OPEN-05 *(partly)* | Where does authority sit? | Decentralization is not a goal; release is authorized, settlement is permissionless. §3.2 |
| OPEN-06 | Can an external market exist? | No. R exists only within the world and cannot be held outside it. §5.4 |
| OPEN-14 | Do System Payments exist, and what are they called? | Yes; they are the burn channel, and the term is *System Payment*. §4.5, §7.7 |
| OPEN-18 | Is the target a floor or a ceiling? | A ceiling, and the monotone path stays beneath it. §4.6, §7.4a |
| OPEN-21 | Is R a liability of THE RESERVE? | No. Issued against nothing; no balance sheet in which R is an obligation. §5.3 |
| OPEN-22 | Does the same institution operate the banking layer? | Yes. No separate bank is chartered. §2.4, P7 |
| OPEN-23 | The mandate of a central bank whose only instrument is release | RESERVE — to keep. §10.1 |
| OPEN-27 | How can a mandate to keep destroy money? | The value is falling; destruction is how it is preserved. §10.4 |
| OPEN-28 | Does burn count toward the contraction target? | Yes. The formula needs no special case. §7.7 |
| OPEN-30 | Who designates a system account? | THE RESERVE. It is a monetary power, not bookkeeping. §4.2 |
| OPEN-31 | The fixed unit against the falling value | The unit holds *because* destruction offsets the fall. §10.4 |
| OPEN-32 | When was genesis, and what is the present? | Genesis 17 September 1975, Epoch 0; the present is governed by a criterion, not a stated value. §7.1 |
| OPEN-33 | What is a deployment for? | Both a public ledger of the world's history and a rule implementation with in-world accounts only. §7.1 |
| OPEN-34 | The depletion against a constant-rate schedule | The schedule is not constant-rate. It accelerates. §7.4 |
| OPEN-35 | Whose behavior does the Observer measure? | No one's. The series is simulated. §9.3 |
| OPEN-38 | What generates the simulated data, and is it published? | A generator, published on GitHub, not disclosed within the work. §9.3 |
| OPEN-39 | Non-expansion withdrawn, with nothing producing an increase | Withdrawn in turn. Non-expansion holds; destruction is permanent. §3.1, §7.2 |
| *(reframed)* | Genesis as an institutional act | A fixed quantity was issued once at a past point. §7.1 |
| OPEN-40 | Does the realized path meet the ceiling in 2025? | Moot. The tolerance accommodates either; what remains is the noise amplitude. §7.4a |
| *(withdrawn)* | 50% remaining at 10 September 2026 | No longer a fact of the world. §7.1 |
| *(unfixed)* | 30% remaining at 17 September 2025 | Now a criterion with a ±5-point tolerance, not a value. §7.1, §7.4 |
| *(narrowed)* | OPEN-09 — classifying authority | THE RESERVE classifies; mutability of a designation is still open. §4.2 |
| *(narrowed)* | OPEN-29 — the payer | The initial payer is THE RESERVE; what a payer receives is still open. §7.7 |
| *(narrowed)* | OPEN-36 — noise structure | One-sided beneath the schedule and monotone; it varies the rate only. §7.4a |
| *(narrowed)* | OPEN-20 — disclosure | Stated in the whitepaper, not in the work. §9.3 |

## Blocking — later sections cannot be written without these

| ID | Question | Blocks |
|---|---|---|
| OPEN-37 | Which `k`, and which `λ` in its admissible range? The criterion admits a family | §7.4, §6.2, the parameter registry, every figure the work displays |
| OPEN-36 | The noise's distribution, amplitude, and time scale as a process on the rate | §7.4a, §9, §17; constrained jointly with OPEN-37 |
| OPEN-13 | Release eligibility, purpose, and amount — who receives R and why | §10 as an actual policy, §13, §14, OPEN-12 |
| OPEN-41 | May the institution make a System Payment, so that R can be destroyed without being released? | §4.5, §7.3, §7.7; gates OPEN-13 |
| OPEN-29 | What the payer receives for a System Payment | §7.7, §13, the in-world participant's experience |
| OPEN-05 | The permission model: release keys, custody, rotation, bounds | §14, §15 |
| OPEN-12 | Treasury partition between release capacity and retirement capacity | §7.6, §10, §17 |
| OPEN-25 | May the banking layer create claims exceeding the base? | The banking layer entirely; §18 |

## Structural — required before the model is internally consistent

| ID | Question |
|---|---|
| OPEN-09 | May a classification change after it is set, and what becomes of a balance if it does? |
| OPEN-16 | Semantics of Pending Retirement — accumulate, recompute, cap, or discharge |
| OPEN-11 | Calendar convention, epoch-to-year conversion, and integer rounding direction |
| OPEN-17 | Repeat calls, missed epochs, and caller incentive for settlement |
| OPEN-19 | Remaining eligibility rules for `Q₃₀` — self-transfers, common controllers, averaging, zero circulation |
| OPEN-26 | Is release ever obligatory, or always discretionary? |

## Boundary — determines what the document may claim

| ID | Question |
|---|---|
| OPEN-07 | Is the deployed protocol immutable, and who declares the experiment over? |
| OPEN-08 | Definitive name, display notation, and on-chain code |
| OPEN-10 | What a holder can do that a non-holder cannot |
| OPEN-15 | Terminal floor of the contraction schedule |
| OPEN-24 | Does the world record carry values, or only a direction? |

---

## Provenance and limits

This manuscript is drafting work, not an approved release. The confirmed constraints it rests on are in
[DEC-003](../wiki/decisions/DEC-003-currency-and-circulation-direction.md),
[DEC-004](../wiki/decisions/DEC-004-monetary-authority-and-authored-decline.md), and
[DEC-005](../wiki/decisions/DEC-005-monetary-unit-banking-layer-and-mandate.md), and
[DEC-006](../wiki/decisions/DEC-006-burn-mechanism-and-value-preservation.md), and
[DEC-007](../wiki/decisions/DEC-007-burn-accounting-payer-and-genesis-date.md), and
[DEC-008](../wiki/decisions/DEC-008-contraction-curve-simulation-and-ledger-scope.md), and
[DEC-009](../wiki/decisions/DEC-009-second-anchor-noise-bounds-and-generator.md), and
[DEC-010](../wiki/decisions/DEC-010-non-expansion-restored-and-2026-anchor-withdrawn.md), and
[DEC-011](../wiki/decisions/DEC-011-depletion-as-tolerance-band.md). The draft mechanisms it
formalizes are LLM proposals preserved in
[r-monetary-protocol](../wiki/concepts/r-monetary-protocol.md); the drafting chronology and version-label
conflict are in [r-whitepaper-development](../wiki/concepts/r-whitepaper-development.md); the open
decisions are consolidated in [Q-001](../wiki/questions/Q-001-institutional-scope.md).

No parameter in this document is confirmed. No contract code, deployment, test evidence, security review,
or economic validation exists. Nothing here constitutes an offer, an issuance, or a statement about legal
or regulatory classification.
