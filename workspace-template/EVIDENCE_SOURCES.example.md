# Evidence Sources

This example shows the structure of a private `EVIDENCE_SOURCES.md` registry.

Maintenance mode: autonomous.

Public examples must use aliases instead of real local paths, account names, tenants, ticket keys, repositories, or provider identifiers.

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

