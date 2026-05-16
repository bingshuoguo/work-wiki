# Provider Guide

An evidence provider is any source an agent can inspect to support a work review.

Provider entries live in private `EVIDENCE_SOURCES.md` files as Markdown sections with YAML fenced metadata. Public examples must use `EVIDENCE_SOURCES.example.md` and aliases.

## Provider Entry

```yaml
id: unique-provider-id
alias: publish-safe-source-alias
status: pending
type: agent_session
access: local_path
locator_alias: SOURCE_HOME
scope:
  - metadata
privacy: local_only
last_verified:
failure_count: 0
```

## Status Values

- `pending`
- `active`
- `degraded`
- `auth_required`
- `inactive`
- `removed`

## Access Values

- `local_path`
- `git`
- `cli`
- `mcp`
- `browser`
- `api`
- `manual`

## Privacy Values

- `local_only`
- `metadata_only`
- `sensitive_metadata_only`
- `user_approved_content`

## Maintenance

Agents may autonomously add, update, degrade, deactivate, or remove sources. Every source mutation must be recorded in private `EVIDENCE_SOURCES_CHANGELOG.md`. Reviews may link to changelog entries but must not be the only audit trail.

