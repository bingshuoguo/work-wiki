# Evidence Sources

This example shows the structure of a private `EVIDENCE_SOURCES.md` registry.

Maintenance mode: autonomous.

Public examples must use aliases instead of real local paths, account names, tenants, ticket keys, repositories, or provider identifiers.

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

- Agents may add, update, degrade, deactivate, or remove sources.
- Record every source mutation in private `EVIDENCE_SOURCES_CHANGELOG.md`.
- Reviews may reference changelog entries but must not be the only audit trail.
- Do not store sensitive raw content here.

