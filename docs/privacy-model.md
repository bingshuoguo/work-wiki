# Privacy Model

Work Wiki is local-first and privacy-aware by default.

## Default Rules

- Do not store raw email bodies.
- Do not store private chat transcripts.
- Do not store private document bodies.
- Do not store large proprietary code diffs.
- Prefer metadata, links, counts, timestamps, aliases, and short summaries.
- Keep real `EVIDENCE_SOURCES.md` and `EVIDENCE_SOURCES_CHANGELOG.md` private and gitignored.
- Keep local caches out of version control.
- Record missing permissions without forcing access.

## Sensitive Sources

Mark sensitive providers in private `EVIDENCE_SOURCES.md`:

```yaml
privacy: sensitive_metadata_only
```

For sensitive sources, agents should summarize only the minimum context needed for work review.

## Local Cache Policy

The following paths should remain untracked:

```text
.cache/
.local/
raw/
EVIDENCE_SOURCES.md
EVIDENCE_SOURCES_CHANGELOG.md
```

## Redaction

- Replace people, organizations, projects, tenants, local paths, provider domains, and private repositories with aliases in publish-safe output.
- Avoid copying private messages.
- Summarize decisions and blockers without quoting sensitive content.
- Never write token, cookie, OAuth, API key, SSH key, or session material.

