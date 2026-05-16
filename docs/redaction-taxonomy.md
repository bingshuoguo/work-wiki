# Redaction Taxonomy

Metadata and summaries can leak sensitive information. Work Wiki uses these categories:

- Public-safe: generic provider type, source alias, evidence type, confidence, and date.
- Internal metadata: local paths, repository names, ticket keys, PR URLs, sender or attendee names, organization names.
- Sensitive content: email bodies, chat messages, document bodies, incident details, customer data, secrets, proprietary code, private dashboards.
- Secret material: tokens, cookies, API keys, OAuth refresh tokens, SSH keys, and session identifiers.

## Default Handling

- Public-safe data may appear in examples and public docs.
- Internal metadata may appear only in private workspaces.
- Sensitive content requires explicit user approval before inclusion.
- Secret material must never be written.

## Publish-Safe Mode

Publish-safe mode replaces paths, provider identifiers, people, organizations, projects, and tenants with aliases.

