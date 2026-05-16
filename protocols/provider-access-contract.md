# Provider Access Contract

Sensitive providers are disabled by default.

Every provider that can expose private workplace or personal information must follow this contract:

- Explicit opt-in: the source must be listed in private `EVIDENCE_SOURCES.md` before scanning.
- Read-only access: Work Wiki agents may inspect evidence but must not mutate external systems unless a separate user request explicitly asks for that.
- No token storage: tokens, cookies, API keys, OAuth refresh tokens, and session secrets must never be written to the repository.
- Tenant boundary: provider entries must identify the intended account, workspace, organization, or tenant by alias, not by secret or raw token.
- Scope minimization: request or use the smallest practical scope, such as metadata-only email/calendar access when full content is unnecessary.
- Scan confirmation: before first scan of Gmail, Slack, Teams, Feishu, Google Drive, Confluence, Notion, monitoring, incident, or similar sensitive systems, confirm that the source is intentionally enabled in the private registry.
- Publish-safe output: summaries must avoid raw private content unless the user explicitly asks to include it.

