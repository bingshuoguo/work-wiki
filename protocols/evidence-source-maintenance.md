# Evidence Source Maintenance Protocol

Private `EVIDENCE_SOURCES.md` is a self-maintaining registry. Agents may autonomously add, update, degrade, deactivate, or remove sources according to the status state machine.

## Initialization

When initializing Work Wiki:

1. Read `protocols/provider-access-contract.md`.
2. Look for local agent session directories.
3. Look for nearby Git repositories and worktrees.
4. Check available CLIs and MCP connectors only when accessible and enabled in the private registry.
5. Write discovered sources to private `EVIDENCE_SOURCES.md`.
6. Record changes in private `EVIDENCE_SOURCES_CHANGELOG.md`.

## Daily Maintenance

During each review:

1. Verify active sources used for the target date.
2. Increment `failure_count` when a source fails.
3. Set `status: degraded` after two consecutive failures or partial access.
4. Set `status: auth_required` when credentials or connector access are missing.
5. Set `status: inactive` after seven calendar days without successful scan or when the source is no longer relevant.
6. Remove sources only when they are clearly invalid or obsolete.
7. Record all changes in private `EVIDENCE_SOURCES_CHANGELOG.md`.

## Source Status

- `pending`: discovered or configured but not verified.
- `active`: scan normally.
- `degraded`: scan only when relevant or likely fixed.
- `auth_required`: skip until credentials or connector access changes.
- `inactive`: skip unless user asks to retry.
- `removed`: do not keep in the active registry; record in changelog.

## State Machine

| Current | Event | Next |
| --- | --- | --- |
| `pending` | first scan succeeds | `active` |
| `pending` | auth or permission missing | `auth_required` |
| `active` | scan succeeds | `active` |
| `active` | one scan fails | `active` with incremented `failure_count` |
| `active` | two consecutive scans fail | `degraded` |
| `active` or `degraded` | auth expires | `auth_required` |
| `degraded` | two consecutive scans succeed | `active` |
| `degraded` | seven days without success | `inactive` |
| `inactive` | retry succeeds | `active` |
| `inactive` | source is obsolete | `removed` |

`last_verified` means last successful scan date, not last attempted scan.

## Safety

Do not store sensitive raw content in the registry. Store metadata about where and how to look.

