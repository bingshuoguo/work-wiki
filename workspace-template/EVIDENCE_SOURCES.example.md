# Evidence Sources

这个示例展示私有 `EVIDENCE_SOURCES.md` 注册表的结构。

Maintenance mode: autonomous.

公开示例必须使用 aliases，而不是使用真实本地路径、账号名、tenant、ticket key、仓库或 provider identifiers。

## Agent Sessions

```yaml
id: local-agent-sessions
alias: primary-agent-session-store
status: pending
type: agent_session
access: local_path
locator_alias: AGENT_SESSION_HOME
privacy: local_only
last_verified:
failure_count: 0
```

## Code Repositories

```yaml
id: main-work-repo
alias: main-work-repo
status: inactive
type: git
access: local_path
locator_alias: MAIN_WORK_REPO
privacy: local_only
last_verified:
failure_count: 0
```
