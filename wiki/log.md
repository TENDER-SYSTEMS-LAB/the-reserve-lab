# Wiki Log

Append new entries after all existing entries. Do not rewrite past entries.

## [2026-09-06] maintenance | Initialize THE RESERVE Wiki

- Created the repository entry point, agent instructions, schema, raw-source workflow and registry, Wiki index, and current-state snapshot.
- Registered `SRC-2026-09-06-wiki-initialization-request` as a verbatim capture of the user's task message and promoted its explicit initialization request into current state.
- Adapted operational documentation from the local OTHER GOODS and LONGING checkouts. Reference HEADs at inspection: OTHER GOODS `817e88f0a150c2ebc1508d1233297abc052bf3a2`; LONGING `7408711818174acabc05795ae88d9c472745de14`. These identify the inspected checkouts; no project source corpus was imported.
- Preserved English maintained documentation, original-language raw evidence, source hashes, explicit attribution and status, and append-only history. Kept raw capture corrections as separate sources consistently across the rules.
- Selected `the-reserve-lab` to match the local directory and public visibility to match the two reference repositories. These are initialization choices, not creative project decisions.
- The project's concept and scope remain undocumented. No placeholder concept, decision, or question pages were created.

## [2026-09-06] maintenance | Align README with OTHER GOODS

- Applied the user-provided OTHER GOODS README structure: project title, short introduction, divider, institutional credit, and Archive link.
- Removed repository-operation details from the entry point. Kept the introduction limited to the documented project affiliation and development state; no concept tagline or project identifier was invented.

## [2026-09-06] ingest | Register bank interpretation and naming conversations

- Renamed the two user-supplied exports at the user's request, preserving their complete contents byte-for-byte:
  - `ChatGPT-은행 작품 해석-20260906-1957.md` → `2026-09-06-bank-artwork-interpretation.md`; Git blob hash `b907053cadbbf9b5f27e62adb76d23265577d8cc`.
  - `ChatGPT-작품 이름 논의-20260906-1957.md` → `2026-09-06-project-naming-and-public-language.md`; Git blob hash `4850e08b17999d7214641ff57069b29e697ff019`.
- Registered both sources and their hashes. Promoted five institutional alternatives and the recommended future-claims mechanism as `llm-proposed`; recorded the missing source attachment and unverified financial explanations.
- Recorded THE RESERVE and “A place for what remains.” as explicit user decisions. Kept project codes, handles, mechanisms, and worldbuilding suggestions unconfirmed.
- Added an overview, two concept pages, two decision pages, and one consolidated question page; updated current state and index while preserving the earlier initialization history.
- Rewrote the README using the confirmed title and bio, with Overview and Archive navigation. Removed TENDER SYSTEMS from README at the user's request. The removal applies to README, not to immutable sources or institutional Git rules.

## [2026-09-06] ingest | Preserve the design audit and proposed worldbuilding roadmap

- Registered the user's audit brief and the delivered Korean design audit as byte-identical standalone originals, plus the follow-up ingestion request as a verbatim message capture with a terminal newline. The source registry records their hashes, distinct attribution, and promotion roles.
- Preserved the audit's readiness findings and its 2026-09-06 22:39 KST related-repository snapshot, including uncommitted-source, access, and secondary-evidence limits. The audit request does not replace the earlier missing bank-interpretation attachment.
- Added one independently developing concept, worldbuilding-roadmap, for the proposed scope/depth framework, six completion gates, reopening triggers, A–F dependencies, and five assignable review tasks. Reused institutional-directions for candidate and cross-work comparisons, future-claims for the unresolved benefit and five test cases, and Q-001 for prioritized user choices.
- Updated overview, current state, and the index together. Ingestion authorization is recorded separately from adopting an institution, scope, currency, rule, or implementation plan. Existing name and bio decisions remain unchanged; no candidate was selected or rejected by this ingestion.
- Verified all three previously registered source hashes before writes and all six registered hashes after synthesis. Both copied files remain byte-identical to their supplied originals. Checked Wiki/source links, one index entry per Wiki page, attribution, and Git whitespace; no findings. The earlier LONGING CSV normalization signal remains a caveat in the report, not a new THE RESERVE source mismatch.
- Appended this entry without altering prior log content. No artwork implementation, issue creation, commit, or push was performed.

## [2026-09-06] lint | Align source and index links with LONGING

- Wiki `## Sources` entries used per-page relative Markdown links to the raw files. Rewrote them as `[[SRC-...]] — raw/<type>/<file>.md`, the form `schema.md` documents and LONGING uses, so pages resting on the same original share a link.
- `wiki/index.md`: added the standard page frontmatter it was missing and converted its internal page links to `[[wikilink]]` form. Repository-control links to `../README.md`, `../AGENTS.md`, `../schema.md`, and the raw files remain Markdown links, as in LONGING.
- No claim, attribution, status, or hash changed.

## [2026-09-06] lint | Link source files from every Sources entry

- Following the alignment entry above, the 25 `## Sources` entries across 8 pages now read `[[SRC-...]] — [raw/<type>/<file>.md](<relative path>)`. The wikilink is the shared source identifier; the Markdown link restores the direct route to the file that the earlier per-page links provided.
- `schema.md`: the Provenance example now shows both links and states the relative-path rule — `../raw/...` from a page directly under `wiki/`, `../../raw/...` from a page in a subdirectory.
- No claim, attribution, status, or hash changed. This is a link-format correction only.

## [2026-09-07] lint | Verify provenance links and synchronize maintenance dates

- Reviewed the pending documentation changes and synchronized the eight edited subject pages, index, and corresponding catalog dates for this maintenance. Project claims, statuses, attribution, and source registrations remain unchanged.
- Corrected the count in the preceding entry by addition: there are 23 `## Sources` entries across 8 pages, not 25. The earlier entry remains intact as part of the append-only history.
- Verified one catalog entry for each of the nine Wiki pages other than the index, matching page statuses and dates, registered source identifiers, and existing local link targets. `git diff --check` passed, and `git status --porcelain raw/` was empty; registered originals were not changed or rehashed.
