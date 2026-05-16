# Evidence Integrity Protocol

Evidence integrity explains how trustworthy a review is.

Every review must state what was checked, what was missing, what failed, and what remains uncertain.

## Coverage Categories

- AI session coverage
- Git coverage
- PR / CI coverage
- Requirement coverage
- Communication coverage
- Calendar coverage
- Documentation coverage
- Test artifact coverage
- Operational coverage
- Evidence source registry changes
- Uncertain items

## Conflict Handling

If sources conflict, report the conflict instead of forcing a conclusion.

Examples:

- Session says tests passed, but CI failed.
- Git shows no commit, but session describes implementation.
- Ticket status is done, but PR is unmerged.
- Email mentions approval, but deployment evidence is missing.

## Confidence

Use high, medium, or low confidence language. Avoid false precision.

## EvidenceRef

Use lightweight evidence references instead of copying raw evidence:

```yaml
id: ev-2026-05-16-001
source_id: codex-local
source_alias: primary-agent-session-store
type: agent_session
date: 2026-05-16
time_range: 09:30-10:20
locator_alias: codex-session-2026-05-16-a
artifact_kind: session_metadata
confidence: high
privacy: metadata_only
claim: Agent ran verification command for the reviewed task.
```

Rules:

- `source_id` must match a private registry entry.
- `locator_alias` must be publish-safe or private to the workspace.
- Do not include secret URLs, raw tokens, private message bodies, or large code excerpts.

