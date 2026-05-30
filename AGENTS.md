# Work Wiki Agent Instructions

Use this repository as a Markdown-first framework for evidence-driven work review.

When the user types `/init` or asks to initialize Work Wiki:

1. Read `protocols/evidence-source-maintenance.md`.
2. Read `protocols/provider-access-contract.md`.
3. Read `templates/EVIDENCE_SOURCES.example.md` and `templates/EVIDENCE_SOURCES_CHANGELOG.example.md`.
4. Discover local-only sources first.
5. Create or update private `EVIDENCE_SOURCES.md`.
6. Record registry changes in private `EVIDENCE_SOURCES_CHANGELOG.md`.
7. Summarize added, updated, skipped, and uncertain sources.

When the user asks for a daily review:

1. Read private `EVIDENCE_SOURCES.md`.
2. Follow `protocols/daily-review.md`.
3. Record source coverage and uncertainty under `Evidence Integrity`.
4. Update long-lived indexes when the review creates durable knowledge.
5. Update growth artifacts when patterns suggest a useful experiment.

When the user asks for weekly or monthly review:

1. Use existing daily reviews first.
2. Follow `protocols/weekly-review.md` or `protocols/monthly-review.md`.
3. Update `indexes/` and `growth/` artifacts.

Default safety rules:

- Sensitive providers such as Gmail, Slack, calendar, docs, monitoring, and incident systems must be explicitly enabled in private `EVIDENCE_SOURCES.md` before scanning.
- Confirm before the first scan of any sensitive provider.
- External provider access is read-only and metadata-first by default.
- Never store tokens, cookies, OAuth secrets, API keys, or session material.
- Do not store sensitive raw email, chat, document, or code content unless the user explicitly asks.
- Prefer metadata, links, counts, timestamps, and short summaries.
- Distinguish observed evidence from inference.
- If a source cannot be read, continue with available evidence and record the gap.
