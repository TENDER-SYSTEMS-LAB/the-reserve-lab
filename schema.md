# THE RESERVE Wiki Schema

This document defines how to manage the Wiki; it is not part of the Wiki's subject matter. A new agent or person beginning work in this repository should be able to understand the entire operating system by reading only `schema.md`, `wiki/index.md`, and `wiki/current-state.md`.

This schema adapts the operating conventions of [other-goods-lab](https://github.com/TENDER-SYSTEMS-LAB/other-goods-lab) and [longing-lab](https://github.com/TENDER-SYSTEMS-LAB/longing-lab).

## Layers

This repository has three layers:

- **`raw/`** — The Source of Truth. This layer preserves originals unchanged: conversation exports, documents, and unclassified material. Never replace or delete a file under `raw/`. If a correction is needed, add a new revision as a separate source instead of editing the existing file.
- **`wiki/`** — The LLM-maintained synthesis layer. It does not summarize one source in isolation; it combines multiple sources to maintain the best current model of the project. The Wiki never replaces raw material. However well organized a Wiki page may be, the raw original remains the final evidence.
- **`schema.md`** — This document. It governs how the Wiki is managed rather than describing the project itself.

## Language and Localization

English is the canonical language for all maintained documentation. This includes the root README, repository rules, Wiki pages, source-registry prose, headings, summaries, and log entries.

Registered raw sources are evidence and retain their original language. The English-default rule never permits rewriting a file under `raw/documents/`, `raw/conversations/`, or `raw/surveys/`. Promote its meaning into the Wiki in English, or register a translation as a separate derivative source when a full translation is genuinely required.

## Navigation and History

Four documents that may appear similar serve different audiences and positions in time:

- **`README.md`** — The repository's entry point. It explains what the project is, what is currently being researched, why the repository exists, and where to begin reading. Do not include a complete file tree or agent editing instructions.
- **`wiki/index.md`** — A content-oriented catalog for agents and Wiki editors. Excluding the index itself, register every Wiki page exactly once under its type using `link + one-line summary + updated date`; include status when the page has one. It also routes new information to the proper page. Do not remove an entry unless the page is deleted.
- **`wiki/current-state.md`** — A snapshot of currently valid decisions, scope, priorities, and unresolved questions. It does not replace the full page catalog or work history.
- **`wiki/log.md`** — An append-only history of ingestion, meaningful queries, decisions, linting, and maintenance in the order they occurred. Do not edit an existing entry except during an explicitly authorized repository-wide migration that preserves its meaning.

Use `## [YYYY-MM-DD] <type> | <title>` for new log entry headings. Prefer `ingest`, `query`, `decision`, `lint`, or `maintenance` as the type. Do not record every ordinary conversation or read-only action when it leaves no result in the Wiki.

## Taxonomy

The current page types are:

- **index** — The working catalog for finding every Wiki page and editing destination by type.
- **overview** — A page explaining the overall concept of the project.
- **current-state** — A page showing where the project stands now.
- **concept** — A page for an idea that crosses several areas.
- **decision** — A page recording a decision that affected project direction.
- **question** — A page for a central unresolved question.
- **log** — The append-only work history.

Add a taxonomy only when real material requires that page type; do not create directories or placeholders in advance.

## Status

A page or section may use one of eight status values:

- `confirmed` — Material confirmed by the user.
- `working` — A direction currently being developed.
- `hypothesis` — An idea not yet verified.
- `speculation` — A weakly supported conjecture.
- `deferred` — Material intentionally postponed.
- `rejected` — Material discarded after review.
- `deprecated` — Material that was once valid but is no longer valid.
- `unknown` — Material for which there is not yet enough evidence to judge.

Do not attach a status to every sentence. Use status only at page or section level.

## Attribution

Use five values to distinguish where information came from:

- `user-originated` — An idea first introduced by the user.
- `llm-proposed` — An idea proposed by an LLM.
- `jointly-developed` — An idea developed together through conversation.
- `user-confirmed` — Material explicitly accepted or decided by the user.
- `llm-synthesis` — A later LLM interpretation combining several sources.

The most important rule is: **Never transform an LLM proposal into a user decision in the record.** Material attributed as `llm-proposed` does not become `user-confirmed` until the user actually confirms or accepts it.

## Provenance

Every important claim must be traceable to a source ID through a `## Sources` section. For example:

```markdown
## Sources

- [[SRC-2026-09-04-example-document]] — raw/documents/2026-09-04-example-document.md
```

When provenance is a secondary citation — that is, when the original conversation or material behind a claim is absent from the repository and appears only indirectly through another source — state that limit.

Keep provenance useful without making pages unmanageably metadata-heavy. Do not attach a citation to every sentence; collect sources at page level or by major claim.

## Promotion

Not every raw source becomes a Wiki page automatically. Information promoted to the Wiki should be worth consulting repeatedly, meaningful to the understanding of the project, and supported by verifiable provenance.

- **Strong promotion** — Material directly confirmed or decided by the user. Record it in the Wiki with `user-confirmed` attribution.
- **Working promotion** — Material not yet confirmed but worth consulting throughout the project's development. Record it with a status such as `hypothesis` or `working`.
- **Do not promote** — One-off chatter, meaningless LLM variants, duplicate phrasing, unsupported conjecture, or material that makes a discarded idea appear current. Leave it in raw.

Attribution and status must make the promotion level visible at all times.

## Page Frontmatter

Pages use minimal YAML frontmatter containing only these four fields. Do not add fields before a real need emerges.

- `status` — One of the eight values above.
- `attribution` — One of the five values above.
- `updated` — The date on which the page was last updated.
- `sources` — A list of source IDs supporting the page.

Example:

```yaml
---
status: hypothesis
attribution: llm-synthesis
updated: 2026-09-04
sources:
  - SRC-2026-09-04-example-document
---
```

## File Naming

- Decisions: `wiki/decisions/DEC-NNN-short-slug.md`
- Questions: `wiki/questions/Q-NNN-short-slug.md`
- Concepts: `wiki/concepts/short-slug.md`
- Raw sources: `raw/<type>/YYYY-MM-DD-short-slug.md`, registered with the source ID `SRC-YYYY-MM-DD-short-slug`

Cross-link pages with `[[wikilink]]` syntax.

## Updates

When a new source arrives, check whether an existing page can be updated before creating a new page. Classify the relationship to existing knowledge as one of:

- **Correction** — Existing information was wrong.
- **Evolution** — Project thinking changed over time.
- **Alternative** — Different ideas coexist without conflict.
- **Unresolved contradiction** — There is not enough evidence to decide which side is right.

For an Evolution, add a `## Evolution` section that preserves the sequence from previous state → transition → current state. Never silently overwrite existing knowledge. A page must always show what changed and why.

## Deprecation and Rejection

Do not delete discarded ideas. Change the relevant page or section status to `rejected` or `deferred` and explain the reason under `## Why rejected`. Take care that rejected material does not appear current in the index, current state, or elsewhere.

## Deletion

Even when an original source is deleted or invalidated, do not remove its row from `raw/sources.md`. Change its `Wiki Status` to `invalidated` and record the reason. Do not delete Wiki material that depended only on that source; mark the relevant page or section `REVIEW_REQUIRED`.

## Output Rules

When answering from the Wiki:

- Identify the source supporting the answer.
- Distinguish confirmed material (`confirmed`, `user-confirmed`) from hypotheses or speculation.
- Say when something is unknown. Never fabricate a plausible answer without evidence.
- Do not mix a user decision with an LLM interpretation; always distinguish where the judgment came from.

## Maintenance

Continuously watch for two conditions:

**(A) Single-source dependency** — Mark a review signal when an important conclusion depends on only one source.

**(B) Source-Wiki mismatch** — Periodically check whether original files have changed since registration. Compare `git hash-object <source path>` with the `Hash` column in `raw/sources.md`. If a value differs, do not update the Wiki automatically. Mark the relevant page `REVIEW_REQUIRED` for human review.

## Wiki Lint

As the Wiki grows, manually check:

- broken Wiki links
- orphan pages that nothing links to
- duplicate concepts
- pages that are excessively large or small
- stale pages that have not been updated for a long time
- missing provenance
- source hash mismatches
- rejected ideas presented as current
- mismatches between the index and current state
- single-source dependencies
- maintained documentation written in a language other than English

Lint should produce a report before making changes. Do not automatically repair findings at scale.

## Not in Scope

The following are intentionally absent:

- **A giant taxonomy** — Add page types only when several real pages need them.
- **Empty placeholder pages** — Create a page only when there is content to hold.
- **An automated lint script** — Create it only when the page count exceeds what the manual checklist can handle.
- **RAG** — Introduce a vector database or embeddings only when keyword search and the index stop being sufficient. Even then, keep raw retrieval distinct from Wiki knowledge retrieval.
