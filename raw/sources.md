# Raw Source Index

This is the single registry of original sources. Hashes use `git hash-object`. Registration and Wiki promotion are separate steps. Preserve registered originals; add corrections as separate sources. A mismatch requires `REVIEW_REQUIRED` on dependent material before further synthesis.

| ID | Path | Type | Date | Attribution | Hash | Ingested | Wiki Status |
|---|---|---|---|---|---|---|---|
| `SRC-2026-09-06-wiki-initialization-request` | [raw/conversations/2026-09-06-wiki-initialization-request.md](conversations/2026-09-06-wiki-initialization-request.md) | conversation | 2026-09-06 | user-originated | `2d0f02cbae49f5da300c6f33e51b06d596de3b13` | 2026-09-06 | promoted |

| `SRC-2026-09-06-bank-artwork-interpretation` | [raw/conversations/2026-09-06-bank-artwork-interpretation.md](conversations/2026-09-06-bank-artwork-interpretation.md) | conversation | 2026-09-06 | llm-proposed | `b907053cadbbf9b5f27e62adb76d23265577d8cc` | 2026-09-06 | promoted |
| `SRC-2026-09-06-project-naming-and-public-language` | [raw/conversations/2026-09-06-project-naming-and-public-language.md](conversations/2026-09-06-project-naming-and-public-language.md) | conversation | 2026-09-06 | jointly-developed | `4850e08b17999d7214641ff57069b29e697ff019` | 2026-09-06 | promoted |

The initial source contains only the user's task message, captured verbatim with a terminal newline; it is not a full conversation export. Promotion supports the initialization request, not any undocumented project concept.

## Capture and attribution notes

- `SRC-2026-09-06-bank-artwork-interpretation`: the only user turn asks for a Korean answer to an attached prompt. The attachment `붙여넣은 마크다운(1).md` is absent from this repository. The substantive interpretation is ChatGPT's proposal, not a confirmed user brief; statements about the attachment are secondary evidence. Financial explanations have not been independently verified by this ingestion.
- `SRC-2026-09-06-project-naming-and-public-language`: a mixed conversation containing assistant candidates and explicit user decisions. The title and final bio are user-confirmed; the project code, handles, semantic interpretations, and system vocabulary remain assistant proposals. The user reports applying the final bio, but this task did not verify external profiles.
- Both exports retain their original Korean text, metadata, timestamps, and exporter footer byte-for-byte. Only filenames changed at the user's request; mappings are recorded in the Wiki log.
