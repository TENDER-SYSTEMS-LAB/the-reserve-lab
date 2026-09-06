# Raw Source Index

This is the single registry of original sources. Hashes use `git hash-object`. Registration and Wiki promotion are separate steps. Preserve registered originals; add corrections as separate sources. A mismatch requires `REVIEW_REQUIRED` on dependent material before further synthesis.

## Registration

When adding a source, append its row and record `git hash-object <path>` once in the `Hash` column. Preserve that hash as provenance.

For a lookup or suspected mismatch, search only the source ID/path and its capture note. Do not load this entire table or compare all hashes for routine tasks. Follow [AGENTS — Verification](../AGENTS.md#verification): inspect changed raw paths with Git; an explicitly requested provenance audit is a separate task.

## Source List

| Source ID | Path | Type | Date | Attribution | Hash | Ingested | Wiki Status |
|---|---|---|---|---|---|---|---|
| `SRC-2026-09-06-wiki-initialization-request` | [raw/conversations/2026-09-06-wiki-initialization-request.md](conversations/2026-09-06-wiki-initialization-request.md) | conversation | 2026-09-06 | user-originated | `2d0f02cbae49f5da300c6f33e51b06d596de3b13` | 2026-09-06 | promoted |
| `SRC-2026-09-06-bank-artwork-interpretation` | [raw/conversations/2026-09-06-bank-artwork-interpretation.md](conversations/2026-09-06-bank-artwork-interpretation.md) | conversation | 2026-09-06 | llm-proposed | `b907053cadbbf9b5f27e62adb76d23265577d8cc` | 2026-09-06 | promoted |
| `SRC-2026-09-06-project-naming-and-public-language` | [raw/conversations/2026-09-06-project-naming-and-public-language.md](conversations/2026-09-06-project-naming-and-public-language.md) | conversation | 2026-09-06 | jointly-developed | `4850e08b17999d7214641ff57069b29e697ff019` | 2026-09-06 | promoted |
| `SRC-2026-09-06-design-audit-and-roadmap-request` | [raw/documents/2026-09-06-design-audit-and-roadmap-request.md](documents/2026-09-06-design-audit-and-roadmap-request.md) | document | 2026-09-06 | user-originated | `8e217bb9765a940add657bce81e336806f56b685` | 2026-09-06 | promoted as audit context and constraints |
| `SRC-2026-09-06-design-audit-and-roadmap` | [raw/documents/2026-09-06-design-audit-and-roadmap.md](documents/2026-09-06-design-audit-and-roadmap.md) | document | 2026-09-06 | llm-synthesis | `d55d47b56f00a0a124234dc7621124dea992d3a0` | 2026-09-06 | promoted; findings and unadopted proposals distinguished |
| `SRC-2026-09-06-design-audit-ingestion-request` | [raw/conversations/2026-09-06-design-audit-ingestion-request.md](conversations/2026-09-06-design-audit-ingestion-request.md) | conversation | 2026-09-06 | user-originated | `7110ce88e363bb0b7cb2586f82103d8532e177dc` | 2026-09-06 | promoted as ingestion authorization only |

## Capture and attribution notes

- `SRC-2026-09-06-wiki-initialization-request`: contains only the user's task message, captured verbatim with a terminal newline; it is not a full conversation export. Promotion supports the initialization request, not any undocumented project concept.
- `SRC-2026-09-06-bank-artwork-interpretation`: the only user turn asks for a Korean answer to an attached prompt. The attachment `붙여넣은 마크다운(1).md` is absent from this repository. The substantive interpretation is ChatGPT's proposal, not a confirmed user brief; statements about the attachment are secondary evidence. Financial explanations have not been independently verified by this ingestion.
- `SRC-2026-09-06-project-naming-and-public-language`: a mixed conversation containing assistant candidates and explicit user decisions. The title and final bio are user-confirmed; the project code, handles, semantic interpretations, and system vocabulary remain assistant proposals. The user reports applying the final bio, but this task did not verify external profiles.
- Both exports retain their original Korean text, metadata, timestamps, and exporter footer byte-for-byte. Only filenames changed at the user's request; mappings are recorded in the Wiki log.
- `SRC-2026-09-06-design-audit-and-roadmap-request`: byte-identical copy of the user's pasted audit brief. It requested a read-only Korean audit and explicitly separated recommendations from decisions. It is not the missing attachment referenced by the earlier bank interpretation.
- `SRC-2026-09-06-design-audit-and-roadmap`: byte-identical copy of the delivered Korean `THE_RESERVE_Design_Audit_and_Roadmap.md`. It combines source-based findings (`llm-synthesis`) with new scope, depth, testing, and roadmap recommendations (`llm-proposed`). Its sibling-repository findings are a dated secondary account, including uncommitted material inspected through 22:39 KST; local links may subsequently change. The report's statements that no Wiki writes were made describe the completed audit, not a permanent prohibition on later authorized ingestion.
- `SRC-2026-09-06-design-audit-ingestion-request`: verbatim capture of the user's follow-up message with one terminal newline, not a full conversation export. It authorizes this ingestion after the read-only audit; it does not explicitly select an institutional type, currency, operating rule, or implementation plan.
