---
status: working
attribution: llm-synthesis
updated: 2026-09-10
sources:
  - SRC-2026-09-10-depletion-as-tolerance-band
  - SRC-2026-09-10-non-expansion-restored-and-2026-anchor-withdrawn
  - SRC-2026-09-10-second-anchor-noise-bounds-and-generator
  - SRC-2026-09-10-contraction-curve-simulation-and-ledger-scope
  - SRC-2026-09-10-burn-accounting-payer-and-genesis-date
  - SRC-2026-09-10-burn-mechanism-and-value-preservation
  - SRC-2026-09-10-initial-issuance-clarification
  - SRC-2026-09-10-monetary-unit-banking-layer-and-mandate
  - SRC-2026-09-10-whitepaper-sections-1-4-decisions
  - SRC-2026-09-10-r-whitepaper-structure-comparison
  - SRC-2026-09-10-r-token-issuance-and-protocol-drafts
  - SRC-2026-09-09-currency-value-supply-and-velocity
  - SRC-2026-09-07-the-reserve-identifier-confirmation
  - SRC-2026-09-06-wiki-initialization-request
  - SRC-2026-09-06-project-naming-and-public-language
  - SRC-2026-09-06-bank-artwork-interpretation
  - SRC-2026-09-06-design-audit-and-roadmap-request
  - SRC-2026-09-06-design-audit-and-roadmap
  - SRC-2026-09-06-design-audit-ingestion-request
---

# Current State

A snapshot of what is decided, what is being written, and what is still open. Chronology lives in
[[log]]; each decision's exact wording and limits live in its own page.

## Identity

- The project is named **THE RESERVE**, with the user-confirmed identifier **RS-001** (2026-09-07). See
  [[DEC-001-project-name]].
- Its public bio is **“A place for what remains.”** The user approved it and reported applying it. See
  [[DEC-002-public-language]].
- The user asked for a shared world with independent public wording: neither “other” nor “changing values”
  should be reused in the bio.
- The social handle `@thereserve.rs001` remains an unconfirmed assistant recommendation.

## Confirmed — the monetary world

Nine decision pages, [[DEC-003-currency-and-circulation-direction]] through
[[DEC-011-depletion-as-tolerance-band]], now define R. Consolidated:

**The institution.** THE RESERVE is the world's **central bank and issuing authority** of R, and it
operates the **banking layer itself** — no separate bank is chartered, under a stated principle of not
expanding the world unnecessarily. Its **mandate is RESERVE**: to keep. That is its whole monetary
objective and the reason no ordinary central-bank instrument appears.

**The unit.** R is the monetary unit of the world. A **fixed quantity was issued once**, on
**17 September 1975**, and none has been issued since. R is **not a liability** of THE RESERVE, carries no
redemption and no claim, and **cannot be held by an actual person** — it exists only within the world, so
no external market for it is possible. `1R = 1R` holds **because** destruction offsets a value that would
otherwise fall; the fixed unit is the result of the mechanism, not an axiom above it.

**Destruction.** R's value is falling in the world, and **destruction is how that value is preserved** —
reducing the quantity is the act of keeping, not its opposite. Two channels reduce supply: **scheduled
retirement** of treasury-held units, and **burn**, when a holder spends toward the system. Use between
people destroys nothing. Burn **counts toward** the contraction target. **Non-expansion holds**: supply
never rises, and retirement and burn are permanent.

**The schedule.** The contraction is **not** a constant rate. It is slow at first and accelerates, and the
realized path is noisy — one-sided beneath the schedule, monotone, so noise varies the *speed* of decline
only. The world asserts **no dated quantity**. It states one **acceptance criterion**: a steady decline
from 1975 to **17 September 2025**, with **30 ± 5%** remaining on that date. The curve is therefore a
family, not a fitted line.

**Observation.** There are **no real participants**, so no divergence between world record and observation
can arise. The flows are **simulated**, produced by a **generator** that will be built and **published on
GitHub but not disclosed within the work**. The Reserve Observer publishes a generated series, labeled as
such; it measures nothing.

**Deployment.** Any deployment is **both** a public ledger of the world's monetary history **and** a rule
implementation whose accounts exist only within the world. It distributes to no one. The elapsed decline
since 1975 sits **before the record**, so the ledger opens with supply already reduced and at roughly
epoch 2,660 rather than epoch 0.

**Language.** Audience-facing terms must not explicitly name AI; the protocol term is *System Payment*.

## In progress — White Paper v0.2

[whitepaper/R-white-paper-v0.2.md](../whitepaper/R-white-paper-v0.2.md) holds Sections 1–10 as whitepaper
prose — Abstract, Introduction, Design Principles and Non-Goals, Definitions and System Model, The
Monetary Unit, Monetary State, Issuance and Supply, Transactions and State Transitions, Monetary Dynamics,
and Monetary Policy. Sections 11–22 remain outline, each annotated with the gap blocking it. The method is
to write until a rule would have to be invented, then record the gap instead: the manuscript's register
holds **forty-one** items with **twenty-eight resolved**. See [[r-whitepaper-development]] for the drafting
chronology and [[r-monetary-protocol]] for the underlying draft mechanisms.

The manuscript is drafting work. Document Version 0.2 / Protocol Version 0.1 / Status Draft. No parameter
is confirmed, and no code, deployment, test evidence, security review, or economic validation exists.

## Open — what must still be decided

Ordered by how much later work each unblocks. Full statements in
[[Q-001-institutional-scope]]; the manuscript carries them as `OPEN-nn`.

| Priority | Decision | Why it blocks |
|---|---|---|
| 1 | **Release eligibility, purpose, and amount** (`OPEN-13`) — who receives R, on what ground, and what receiving it enables | Release is the only door by which R enters the world. Without it there is no circulation, no System Payment, no burn through use, and no velocity. Blocks §10 as a policy, §13, §14 |
| 2 | **May the institution pay the system directly?** (`OPEN-41`) | The manuscript admits only a participant as payer, but the initial payer is confirmed to be THE RESERVE. Decides whether release is the sole outflow; gates priority 1 |
| 3 | **Curve parameters and noise amplitude** (`OPEN-37`, `OPEN-36`) | The criterion admits a family. Shape, scale, and noise are constrained jointly by one test, and every figure the work displays waits on them |
| 4 | **What a payer receives for a System Payment** (`OPEN-29`) | A payment that obtains nothing is a donation. This is the part an in-world participant experiences |
| 5 | **The permission model** (`OPEN-05`) — release keys, custody, rotation, bounds | §14 Governance, §15 Security |
| 6 | **Treasury partition** (`OPEN-12`) — release capacity against retirement capacity | Release policy otherwise decides the schedule's achievability silently |
| 7 | **May the banking layer create claims exceeding the base?** (`OPEN-25`) | One institution guarantees the base and would create the claims above it. The banking layer entirely |

Structural items awaiting resolution: classification mutability (`OPEN-09`), Pending Retirement semantics
(`OPEN-16`), calendar and rounding conventions (`OPEN-11`), settlement's repeat-call and caller-incentive
behavior (`OPEN-17`), remaining velocity eligibility rules (`OPEN-19`), and whether release can ever be
obligatory (`OPEN-26`).

Boundary items that limit what the document may claim: protocol immutability (`OPEN-07`), the definitive
name and on-chain code (`OPEN-08`), what a holder can do that a non-holder cannot (`OPEN-10`), a terminal
supply floor (`OPEN-15`), whether the world record carries values or only a direction (`OPEN-24`).

## Withdrawn and superseded

Track these so they do not reappear as facts.

- **50% remaining at 10 September 2026** — withdrawn. Not a fact of the world, and it survives nowhere as
  a value. See [[DEC-010-non-expansion-restored-and-2026-anchor-withdrawn]].
- **30% remaining at 17 September 2025** — unfixed into a criterion with a ±5-point tolerance. The world
  asserts no dated quantity. See [[DEC-011-depletion-as-tolerance-band]].
- **Permission for intermediate supply rises** — retracted; non-expansion holds. See
  [[DEC-010-non-expansion-restored-and-2026-anchor-withdrawn]].
- **Real on-chain participation and the divergence rule** — superseded by simulation. The first half of
  [[DEC-004-monetary-authority-and-authored-decline]] stands; its expectation of real participants does
  not.
- **The assistant reading that retirement removes only the undistributed remainder** — corrected by the
  user. See [[DEC-006-burn-mechanism-and-value-preservation]].
- **3% annual contraction, and any constant-rate schedule** — inapplicable in shape as well as magnitude.
- Draft-only and unconfirmed: 1,000,000 R genesis supply, 18 decimals, seven-day epoch, Base Sepolia, the
  `RSV` symbol.

## Earlier institutional field — still unselected

[[overview]] introduces the bank-artwork research field. All five [[institutional-directions]] remain
assistant proposals, and [[future-claims]] remains a recommendation the user has not selected. The
monetary decisions above define the base layer; they do not choose an operating contract for the
visitor's relationship with the institution, which is why `OPEN-10` and `OPEN-13` are still open.

## September 6 design audit and proposed scope

The audit found enough material to compare institutional alternatives, but no selected operating contract or executable artwork in the inspected THE RESERVE commit (`e2aa812754892db5f3399f3d53aa7041d2faff96`). Document detail, user approval, and implementation remain separate measures. This is a bounded audit finding, not a claim about all possible external work.

[[worldbuilding-roadmap]] proposes an institution-centered scope: define the institution and object to D2, and the consequential contract, time, state, and audience path to D3. Shared references start at D1; common money, settlement, macroeconomics, and additional products wait for an operational reason. These are planning recommendations, not adopted project deferrals or an approved implementation plan.

The first proposed test compares the visitor's meaningful present benefit, future obligation, and the institution's own responsibility. [[future-claims]] remains a test candidate; custody remains an alternative. The present benefit and observable performance rule are still undefined, so five paper cases reveal gaps rather than demonstrate working credit.

The audit's sibling comparison shows that OTHER GOODS also explores transactions and post-purchase state, while a dated, uncommitted LONGING draft compares forecast claims and support rights. Independence must be tested through parties, obligations, and effects, not account screens, time, or the word “claim.” No shared currency, account, or settlement contract was established by that audit. See [[institutional-directions]] for attribution and snapshot limits. The user envisages denominating LONGING assets in Reserve; that is an intention, not an accepting party, exchange rule, or settlement contract.

## Evidence limits

The September 9–10 exports contain ambiguous transcription and unsupported assistant summary additions (water parity, salary, cRES, and institutions); these are not adopted facts. Technical and legal references remain secondary citations. Protocol and document version labels conflict across the two later exports; preserve their chronology rather than invent an approved release.

The nine decision captures from the working conversation are selected turns, not full exports. Their headings are capture scaffolding. Arithmetic recorded alongside them — elapsed intervals, implied rates, admissible parameter ranges — is computed by this repository from the confirmed dates and criteria, and is not supplied by the user.

The interpretation export refers to a missing attachment. Its substantive contents are assistant proposals and its financial explanations have not been independently verified. The older naming decisions rest on their cited conversations; a reported bio update is not a live profile check.

The later audit brief is not that missing attachment. Sibling findings are secondary evidence in this repository, based on the report's 2026-09-06 investigation through 22:39 KST, including uncommitted material and an inaccessible institution-repository remote. Recheck the relevant originals before making a consequential cross-work decision. A reported LONGING CSV normalization discrepancy is a limitation of that earlier investigation, not a changed THE RESERVE source.

That destruction preserves value, that the decline accelerates, and that the path is noisy are **premises of the world**, not measured or validated monetary results.

## Evolution

Initialization recorded only the project name and repository request, so concept and scope were described as undocumented. The two supplied earlier conversations established naming decisions and a body of proposed institutional interpretations. The subsequent read-only audit evaluated readiness and proposed target depth, scope boundaries, and a dependent roadmap; the user then requested its ingestion, which did not itself select an institutional type or its rules.

The September 9–10 conversations established a bank/currency direction, and the drafting of White Paper v0.2 turned that direction into a specified monetary system by writing until a rule was missing and then asking. Nine decisions followed in one working session, two of them corrections of the assistant's own readings. The institution, the unit, the destruction mechanism, the schedule's shape, the status of observation, and the deployment's purpose are now settled; the visitor's relationship to the institution is not.

## Earlier audit next-work proposal

The audit proposed **TR-A01**, a concrete comparison of the relationship created by future claims and custody, alongside **TR-A02**, a check of actual cross-work dependencies. That comparison remains useful for institutional responsibility and cross-work dependencies, but it is no longer the documented development path: the whitepaper's open register is. See [[worldbuilding-roadmap]] for the five assignable cards and completion gates. No sketch, implementation, issue, or release has been executed.

## Sources

- [[SRC-2026-09-06-wiki-initialization-request]] — [raw/conversations/2026-09-06-wiki-initialization-request.md](../raw/conversations/2026-09-06-wiki-initialization-request.md)
- [[SRC-2026-09-06-project-naming-and-public-language]] — [raw/conversations/2026-09-06-project-naming-and-public-language.md](../raw/conversations/2026-09-06-project-naming-and-public-language.md)
- [[SRC-2026-09-06-bank-artwork-interpretation]] — [raw/conversations/2026-09-06-bank-artwork-interpretation.md](../raw/conversations/2026-09-06-bank-artwork-interpretation.md)
- [[SRC-2026-09-06-design-audit-and-roadmap-request]] — [raw/documents/2026-09-06-design-audit-and-roadmap-request.md](../raw/documents/2026-09-06-design-audit-and-roadmap-request.md)
- [[SRC-2026-09-06-design-audit-and-roadmap]] — [raw/documents/2026-09-06-design-audit-and-roadmap.md](../raw/documents/2026-09-06-design-audit-and-roadmap.md)
- [[SRC-2026-09-06-design-audit-ingestion-request]] — [raw/conversations/2026-09-06-design-audit-ingestion-request.md](../raw/conversations/2026-09-06-design-audit-ingestion-request.md)
- [[SRC-2026-09-07-the-reserve-identifier-confirmation]] — [raw/conversations/2026-09-07-the-reserve-identifier-confirmation.md](../raw/conversations/2026-09-07-the-reserve-identifier-confirmation.md)

- [[SRC-2026-09-09-currency-value-supply-and-velocity]] — [raw/conversations/2026-09-09-currency-value-supply-and-velocity.md](../raw/conversations/2026-09-09-currency-value-supply-and-velocity.md)
- [[SRC-2026-09-10-r-token-issuance-and-protocol-drafts]] — [raw/conversations/2026-09-10-r-token-issuance-and-protocol-drafts.md](../raw/conversations/2026-09-10-r-token-issuance-and-protocol-drafts.md)
- [[SRC-2026-09-10-r-whitepaper-structure-comparison]] — [raw/conversations/2026-09-10-r-whitepaper-structure-comparison.md](../raw/conversations/2026-09-10-r-whitepaper-structure-comparison.md)

- [[SRC-2026-09-10-whitepaper-sections-1-4-decisions]] — [raw/conversations/2026-09-10-whitepaper-sections-1-4-decisions.md](../raw/conversations/2026-09-10-whitepaper-sections-1-4-decisions.md)
- [[SRC-2026-09-10-monetary-unit-banking-layer-and-mandate]] — [raw/conversations/2026-09-10-monetary-unit-banking-layer-and-mandate.md](../raw/conversations/2026-09-10-monetary-unit-banking-layer-and-mandate.md)
- [[SRC-2026-09-10-initial-issuance-clarification]] — [raw/conversations/2026-09-10-initial-issuance-clarification.md](../raw/conversations/2026-09-10-initial-issuance-clarification.md)
- [[SRC-2026-09-10-burn-mechanism-and-value-preservation]] — [raw/conversations/2026-09-10-burn-mechanism-and-value-preservation.md](../raw/conversations/2026-09-10-burn-mechanism-and-value-preservation.md)
- [[SRC-2026-09-10-burn-accounting-payer-and-genesis-date]] — [raw/conversations/2026-09-10-burn-accounting-payer-and-genesis-date.md](../raw/conversations/2026-09-10-burn-accounting-payer-and-genesis-date.md)
- [[SRC-2026-09-10-contraction-curve-simulation-and-ledger-scope]] — [raw/conversations/2026-09-10-contraction-curve-simulation-and-ledger-scope.md](../raw/conversations/2026-09-10-contraction-curve-simulation-and-ledger-scope.md)
- [[SRC-2026-09-10-second-anchor-noise-bounds-and-generator]] — [raw/conversations/2026-09-10-second-anchor-noise-bounds-and-generator.md](../raw/conversations/2026-09-10-second-anchor-noise-bounds-and-generator.md)
- [[SRC-2026-09-10-non-expansion-restored-and-2026-anchor-withdrawn]] — [raw/conversations/2026-09-10-non-expansion-restored-and-2026-anchor-withdrawn.md](../raw/conversations/2026-09-10-non-expansion-restored-and-2026-anchor-withdrawn.md)
- [[SRC-2026-09-10-depletion-as-tolerance-band]] — [raw/conversations/2026-09-10-depletion-as-tolerance-band.md](../raw/conversations/2026-09-10-depletion-as-tolerance-band.md)
