# Provider Guide

Evidence provider 是 agent 可以检查的任何来源，用于支持工作复盘。

Provider entries 位于私有 `EVIDENCE_SOURCES.md` 文件中，使用 Markdown section 和 YAML fenced metadata。公开示例必须使用 `EVIDENCE_SOURCES.example.md` 和 aliases。

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

agent 可以自主添加、更新、降级、停用或移除来源。每一次来源变更都必须记录在私有 `EVIDENCE_SOURCES_CHANGELOG.md` 中。复盘可以链接 changelog entries，但不能把复盘当作唯一审计记录。
