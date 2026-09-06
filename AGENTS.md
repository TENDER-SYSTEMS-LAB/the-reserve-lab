# THE RESERVE Wiki — Agent Instructions

This is THE RESERVE's long-term project memory. Shared conventions originate in [TENDER SYSTEMS](https://github.com/TENDER-SYSTEMS-LAB/tender-systems); these local instructions are sufficient for routine work. Consult the institutional repository only when shared rules or cross-project scope are at issue.

## Task-Sized Reading

- Read these instructions once when entering this repository; reuse unchanged material already in context. Do not reread a whole file just to verify one fact.
- Locate the editing destination in `wiki/index.md` with a focused search; read the full catalog only when the destination is unclear. Read the relevant page or section next.
- Consult the relevant `wiki/current-state.md` section for current decisions, priorities, conflicts, or a change to project state. It is not required reading for a link, formatting, or Git-only task.
- `schema.md` is an on-demand reference: read the applicable section for unfamiliar structure, metadata, attribution, provenance, or promotion rules. Do not load it in full at every task.
- Read only the needed source row, capture note, and original when evidence matters. For example: `rg -n -F 'SRC-YYYY-MM-DD-slug' raw/sources.md`. Do not load the registry table or scan raw originals for routine verification.
- Search `wiki/log.md` by topic/date for history; inspect its tail when appending. Keep the full log out of context. Earlier verification entries describe past work, not instructions to repeat it.
- For edits, inspect `git status --short` to identify existing work and use a scoped diff. For read-only questions, skip unrelated Git, authentication, hash, and lint checks.
- Delegate only useful independent work with the relevant paths and a bounded result; avoid duplicating a complete audit in parent and child agents.

## Conversation Ingestion Workflow

1. **Register** — Preserve the new original and record its Git blob hash once in `raw/sources.md`; inspect only the applicable registry rows and notes.
2. **Locate** — Use the catalog and relevant existing pages; consult current state where the new material affects it.
3. **Analyze** — Distinguish ideas, decisions, hypotheses, questions, rejection, rationale, and uncertainty.
4. **Compare** — Identify new, reinforcing, conflicting, or superseding information.
5. **Promote selectively** — Leave one-off or unsupported material in raw.
6. **Update first** — Extend an existing page when it owns the material.
7. **Create only if needed** — Add a page for an independent entity likely to develop further.
8. **Cross-link** — Link related pages and the supporting source ID and original file.
9. **Check state** — Update `wiki/current-state.md` only when current decisions, scope, priorities, or questions changed.
10. **Synchronize the index** — For each created, moved, deleted, or edited page, update only affected catalog entries when their summary, status, or updated date changed. Register every Wiki page except the index exactly once with a link, one-line summary, status if present, and date.
11. **Append the result** — Add one concise `## [YYYY-MM-DD] <type> | <title>` entry after all existing log content for meaningful ingestion, decisions, durable queries, or maintenance. Prefer `ingest`, `query`, `decision`, `lint`, or `maintenance`. Do not log routine reads or clean checks without a durable result.

## Preservation and Scope

- Maintain documentation in English; preserve raw originals, proper names, source IDs, paths, and intentional quotations. Public translations are derivatives of canonical English; see `schema.md`.
- Never edit/delete a registered original, including a defective capture; register a separate correction. The source registry and raw README are maintained control documents, not originals.
- Never replace raw evidence with Wiki synthesis, invent facts, promote an LLM proposal to a user decision, or present rejected material as current. Preserve uncertainty, attribution, and consequential evolution.
- Never modify existing log entries, including uncommitted entries from earlier work. Correct them by appending. No silent overwrites or empty placeholder pages; add taxonomy and metadata only for a real need.
- Write institutional records without the operator's personal identity. Keep project detail canonical in its owning Lab; institution-level shared rules belong in TENDER SYSTEMS.
- Keep `README.md` a public entry point, the index a catalog, current state a snapshot, `raw/sources.md` the sole source registry, and the log the history. Do not duplicate source tables or ingestion chronology in guides.
- Preserve concurrent work. Never use directory-wide checkout/restore, `git reset --hard`, `git add --renormalize .`, or `git checkout-index -f -a`. Stage explicit reviewed paths, not `git add -A`; recheck status before committing.

## Verification

- After edits, check `git status --porcelain raw/` once and inspect only changed paths. Registry/guide edits and new files are not evidence that an existing original changed.
- If a registered original changed, stop synthesis based on it, inspect that path's diff and registry row, and report the affected material as `REVIEW_REQUIRED`. Preserve the worktree; do not restore files blindly.
- **Never compare all registered hashes as a routine task.** Hash only a new source at registration; rehash an existing source only for a concrete mismatch investigation. A complete provenance audit requires an explicit request. Git status detects working-tree changes; it does not prove historical registry accuracy.
- Validate changed pages, affected catalog entries, local links and provenance, and `git diff --check`. Check old-log preservation mechanically without printing its contents. Skip content checks for a Git-only task whose reviewed files are unchanged.
- Run a wider lint only for an explicit audit, a structural migration, or a finding whose impact extends beyond the changed pages. Report actionable findings or a brief pass summary; do not enumerate every healthy link/hash or regenerate checks after they pass without a new reason.

## Git Identity and Push Policy

Only for a commit/push task, verify the remote belongs to `TENDER-SYSTEMS-LAB`. Every new author and committer must be `TENDER SYSTEMS <code@tender.systems>`, the verified institutional identity. Configure it locally if needed; never guess an address, use personal attribution, or change global identity.

Before every commit, check local `user.name`/`user.email`, `git var GIT_AUTHOR_IDENT`, and `git var GIT_COMMITTER_IDENT`. Afterward inspect `git log -1 --format=fuller`. Stop if either identity is wrong.

Push only when requested. Before each push verify the actual authentication account and the author/committer of every outgoing commit. Prefer dedicated institutional credentials; if explicitly required, never fall back to personal authentication. An Organization is not a Git authentication identity, and commit attribution is separate from the push actor. Keep institutional credentials isolated where configured.

Never expose tokens, helper secrets, or private keys. Never rewrite existing history or force-push to change attribution.

### Standing authorization

Standing user authorization (2026-09-06): The user permits the operator's personal GitHub account to authenticate pushes for this repository and accepts that the authenticating account may remain visible in GitHub audit logs or other non-commit activity surfaces. Do not request this permission again unless the user revokes it or the task explicitly requires a dedicated institutional push identity. This authorization does not change the commit identity requirement: every new commit must retain TENDER SYSTEMS as both author and committer, using the verified institutional email. Verify the actual authentication account and the identities of all outgoing commits before each push.
