# Evidence Sources

这个示例展示私有 `EVIDENCE_SOURCES.md` 注册表的结构。

Maintenance mode: autonomous.

公开示例必须使用 aliases，而不是使用真实本地路径、账号名、tenant、ticket key、仓库或 provider identifiers。

## Agent Sessions

### Codex Sessions

```yaml
id: codex-local
alias: primary-agent-session-store
status: pending
type: agent_session
access: local_path
locator_alias: CODEX_HOME
scope:
  - session metadata
  - prompts
  - tool calls
  - commands
privacy: local_only
last_verified:
failure_count: 0
```

### Claude Code Sessions

```yaml
id: claude-local
alias: secondary-agent-session-store
status: pending
type: agent_session
access: local_path
locator_alias: CLAUDE_HOME
scope:
  - session metadata
  - transcripts
  - tool calls
privacy: local_only
last_verified:
failure_count: 0
```

## Code Repositories

```yaml
id: example-repo
alias: main-work-repo
status: inactive
type: git
access: local_path
locator_alias: MAIN_WORK_REPO
scope:
  - branches
  - commits
  - diffs
  - changed files
  - verification commands
privacy: local_only
last_verified:
failure_count: 0
```

## Communication

```yaml
id: gmail-metadata
alias: work-email-metadata
status: inactive
type: communication
access: mcp
provider_alias: work-email
scope:
  - sender alias
  - subject summary
  - timestamp
  - thread metadata
privacy: sensitive_metadata_only
last_verified:
failure_count: 0
```

## Calendar

```yaml
id: google-calendar
alias: work-calendar-metadata
status: inactive
type: calendar
access: mcp
provider_alias: work-calendar
scope:
  - event title alias
  - time range
  - attendee aliases
  - meeting metadata
privacy: sensitive_metadata_only
last_verified:
failure_count: 0
```

## Registry Notes

- agent 可以添加、更新、降级、停用或移除来源。
- 每次来源变更都记录到私有 `EVIDENCE_SOURCES_CHANGELOG.md`。
- 复盘可以引用 changelog entries，但不能把复盘当作唯一审计记录。
- 不要在这里存储敏感原始内容。
