# Raw

This directory is the Source of Truth. It preserves originals unchanged: conversation exports, documents, surveys, and unclassified material.

## Source Types

- `conversations/` — exported conversation transcripts
- `documents/` — standalone documents
- `surveys/` — survey or evaluation outputs collected from multiple models
- `inbox/` — material that has arrived but has not been classified yet

Create directories only when material arrives; empty source directories are not required.

## Adding a Source

1. Place the original, unchanged, under the directory matching its type. Use the filename form `YYYY-MM-DD-short-slug.md`.
2. Compute its hash:

   ```bash
   git hash-object raw/<type>/YYYY-MM-DD-short-slug.md
   ```

3. Append one row to [`sources.md`](sources.md) with the source ID `SRC-YYYY-MM-DD-short-slug`, the path, the type, the date, the attribution, the hash, and the ingestion status.

## Rules

- Never edit or delete a registered source. If a correction is needed, register the corrected version as a separate source.

- Registered sources keep their original language. The repository's English-default policy applies to the Wiki, not to evidence.
- Registration is not promotion. A source enters the Wiki only when the promotion rules in [`../schema.md`](../schema.md) are satisfied.
