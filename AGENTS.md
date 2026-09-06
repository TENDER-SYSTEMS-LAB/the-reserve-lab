# THE RESERVE Wiki — Agent Instructions

This repository is THE RESERVE's long-term memory. Agents working here read before they write. Before adding anything new, check what has already been recorded and build on it.

This repository follows the same operating convention as [other-goods-lab](https://github.com/TENDER-SYSTEMS-LAB/other-goods-lab). When the two diverge without reason, prefer the established convention there.

## What to Read First

Read these files in order:

1. `wiki/index.md`
2. `wiki/current-state.md`
3. `schema.md`
4. The concept, decision, or question pages relevant to the task

Do not begin by scanning the entire raw layer. Start with the synthesis already maintained in the Wiki, then consult only the raw sources that are necessary.

## Repository Language

- English is the canonical and default language for all maintained repository documentation, including `README.md`, `AGENTS.md`, `schema.md`, `wiki/**`, `raw/README.md`, and `raw/sources.md`.
- Write all new pages, edits, headings, summaries, metadata prose, and log entries in English, even when the user's working language is not English.
- Preserve proper names, source identifiers, file paths, code, and intentionally quoted source text when translating them would change their identity or evidentiary meaning.
- Registered files under `raw/documents/`, `raw/conversations/`, and `raw/surveys/` are immutable source records and retain their original language. Never rewrite a raw source to satisfy the English-default policy; synthesize or explain it in English in the Wiki instead.

## Document Roles

- `README.md` is the entry point through which readers understand the project and the repository. Do not put the complete file list or agent instructions there.
- `wiki/index.md` is the working catalog for finding every Wiki page and its editing destination. Excluding the index itself, register each page exactly once under its type with `link + one-line summary + updated date`; include status when the page has one.
- `wiki/current-state.md` is a snapshot of currently valid decisions, scope, priorities, and unresolved questions.
- `wiki/log.md` is an append-only chronological history of meaningful ingestion, queries, decisions, linting, and maintenance.
- `raw/sources.md` is the single registry for every original source's path, hash, and ingestion status. Do not duplicate the raw source list in the index.

## Query Workflow

When the user asks a question, find the answer in this order:

```text
index
  ↓
current-state
  ↓
relevant concept / decision / question
  ↓
raw source only when necessary
```

Consult raw sources only for consequential judgments or when the original evidence must be checked directly.

## Conversation Ingestion Workflow

When ingesting a new conversation or document, follow this sequence:

1. **Register the source** — Preserve the original unchanged under `raw/` and register it in `raw/sources.md` with its hash.
2. **Explore the existing Wiki** — Read the index, current state, and relevant pages first.
3. **Analyze the conversation** — Extract ideas, decisions, hypotheses, open questions, rejected or deferred ideas, rationale, tensions, and emerging concepts.
4. **Compare with existing knowledge** — Decide whether the information is new, reinforces existing material, conflicts with it, or supersedes an earlier decision.
5. **Decide whether to promote** — Keep the material only in raw or promote it into the Wiki.
6. **Prefer updating existing pages** — Before creating a page, check whether an existing page can be updated.
7. **Create a new page** — Do so only for a genuinely new, independent entity.
8. **Cross-link** — Link related concepts, decisions, and questions.
9. **Check current state** — Determine whether the project's current state changed and update it when needed.
10. **Synchronize the index** — In the same task, update the catalog entry when a page is created, moved, or deleted, or when its summary, status, or updated date changes.
11. **Append to `log.md`** — Add the work after all existing entries using `## [YYYY-MM-DD] <type> | <title>`. Prefer `ingest`, `query`, `decision`, `lint`, or `maintenance` as the type.

## Never Do These Things

- Delete or modify a raw source.
- Replace raw material with the Wiki.
- Promote every source automatically.
- Record an LLM proposal as a user decision.
- Present a rejected idea as current.
- Invent facts without a source.
- Hide uncertainty.
- Silently overwrite older knowledge.
- Modify past entries in `log.md` outside an explicitly authorized repository-wide migration.
- Create many empty placeholder pages.
- Add metadata fields that are not needed.
- Treat Wiki size, page count, or document length as a success metric.

## When to Create a New Page

Create a page only when a meaningful unit has emerged that cannot be captured by one line in `current-state.md` and is likely to develop independently over time.

## Git Identity and Push Policy

All Git commits created for this repository must use the institutional TENDER SYSTEMS identity rather than the personal identity of the operator.

### Commit identity

Before creating any commit, verify the repository-local Git identity.

Required identity:

- `user.name`: `TENDER SYSTEMS`
- `user.email`: the verified email address assigned to the dedicated TENDER SYSTEMS GitHub identity

Use repository-local configuration:

```bash
git config --local user.name "TENDER SYSTEMS"
git config --local user.email "<VERIFIED_TENDER_SYSTEMS_EMAIL>"
```

Do not modify the operator's global Git identity unless explicitly requested. Never fall back to the operator's personal name or personal email address.

If the TENDER SYSTEMS email address cannot be verified from the existing environment or GitHub configuration, do not invent one and do not use a personal email address. In particular, do not guess a Gmail address, a `tendersystems` domain address, or a `noreply` address. Stop before committing and report that the institutional email must be configured.

Before every commit, verify:

```bash
git var GIT_AUTHOR_IDENT
git var GIT_COMMITTER_IDENT
```

Both identities must resolve to the TENDER SYSTEMS institutional identity.

After creating a commit, verify with:

```bash
git log -1 --format=fuller
```

The author and committer must not contain the operator's personal identity.

### Push authentication

Commit identity and GitHub push authentication are separate concerns. Setting `git config user.name` or `user.email` does not determine which GitHub account performs the push.

Before pushing, identify which GitHub account or automation identity will authenticate the operation. A dedicated institutional identity remains preferred. Acceptable institutional mechanisms include:

- a dedicated TENDER SYSTEMS GitHub user or machine account with its own SSH key;
- a dedicated TENDER SYSTEMS GitHub credential or token;
- a GitHub App or another explicitly configured institutional automation identity.

Do not assume that membership in the `TENDER-SYSTEMS-LAB` GitHub Organization makes the Organization itself a Git authentication identity.

The public commit history derives author and committer attribution from the commit object, not from the account that authenticated a later push. When the user explicitly authorizes personal push authentication on that basis, the agent may use it only after confirming that the public commit record contains the institutional author and committer identity. Do not describe personal authentication as institutional authentication, and do not promise that the push actor is anonymous: GitHub organization audit logs or other non-commit activity surfaces may retain the authenticating account.

Push only when requested by the user. Identify the authenticated GitHub account and keep both commit identities institutional. Authorization recorded in a sibling repository does not constitute standing authorization for this repository.

If a dedicated TENDER SYSTEMS push identity is required for the task, do not fall back to the operator's personal credentials.

Where SSH is used, prefer a dedicated SSH host alias and key configuration that isolates TENDER SYSTEMS authentication from the operator's personal GitHub identity. Where HTTPS is used, keep TENDER SYSTEMS credentials isolated from personal GitHub credentials.

Never expose, print, commit, or document secrets such as:

- personal access tokens;
- OAuth tokens;
- private SSH keys;
- credential-helper secrets.

### Pre-commit and pre-push safety rule

Before any `git commit`, the agent must verify:

1. The repository is a TENDER SYSTEMS repository.
2. `user.name` resolves to `TENDER SYSTEMS`.
3. `user.email` resolves to the verified TENDER SYSTEMS email.
4. The author and committer identities do not contain the operator's personal identity.

Before any `git push`, the agent must additionally verify the actual authentication identity. Prefer a dedicated TENDER SYSTEMS identity. For a user-requested push, identify the actual authentication account and disclose that the actor may remain visible in audit logs or other non-commit activity surfaces. In either case, verify that the commits being pushed retain the institutional author and committer identity.

If the applicable conditions cannot be verified, do not commit or push. Report the unresolved configuration instead.

### Existing history

Do not rewrite existing Git history merely because older commits contain a personal identity. Unless explicitly instructed otherwise, do not use:

- `git filter-repo`;
- history-rewriting rebase operations;
- force push;
- author rewriting of existing commits.

This policy applies to new commits from this point forward.

## Verification

At the beginning and end of a task, verify that source originals have not changed since registration:

```bash
git hash-object <each registered source path from raw/sources.md>
```

Compare the results with the `Hash` column in `raw/sources.md`. If any value differs, the original changed. Do not update the Wiki automatically; mark the relevant page `REVIEW_REQUIRED`.
