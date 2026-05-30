# /init

Initialize this Work Wiki workspace.

Follow the Work Wiki initialization workflow:

1. Read `protocols/evidence-source-maintenance.md`.
2. Read `protocols/provider-access-contract.md`.
3. Read `templates/EVIDENCE_SOURCES.example.md`.
4. Read `templates/EVIDENCE_SOURCES_CHANGELOG.example.md`.
5. Discover local-only evidence sources first.
6. Create or update private `EVIDENCE_SOURCES.md`.
7. Record every registry mutation in private `EVIDENCE_SOURCES_CHANGELOG.md`.

Safety constraints:

- Do not store tokens, cookies, OAuth secrets, API keys, SSH keys, or session material.
- Do not scan sensitive providers unless they are explicitly enabled in private `EVIDENCE_SOURCES.md`.
- Confirm before the first scan of Gmail, Slack, Teams, Feishu, calendar, docs, monitoring, incident, or similar sensitive systems.
- Prefer aliases, counts, timestamps, locator aliases, and short metadata summaries.
- Do not copy raw private email, chat, document, or code content into registry files.

Finish by reporting sources added, updated, skipped, and uncertain.
