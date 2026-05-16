# Evidence Model

Work Wiki distinguishes evidence type, confidence, source coverage, and evidence references.

## Evidence Types

- Agent session evidence: prompts, tool calls, commands, file references, decisions, and review loops.
- Git evidence: branches, commits, diffs, changed files, stash, and untracked files.
- Delivery evidence: pull requests, reviews, CI checks, merge status, deployments.
- Requirement evidence: tickets, issues, acceptance criteria, status changes, blockers.
- Communication evidence: email, chat, meeting notes, and review threads.
- Calendar evidence: meetings, planning blocks, interviews, reviews, and focus time.
- Documentation evidence: design docs, runbooks, notes, decisions, and comments.
- Quality evidence: test reports, coverage, traces, screenshots, benchmarks, failure logs.
- Operational evidence: alerts, dashboards, incidents, releases, rollbacks, feature flags.

## Source Status

- `pending`: discovered or configured but not verified.
- `active`: scan normally.
- `degraded`: scan only when relevant or likely fixed.
- `auth_required`: skip until credentials or connector access changes.
- `inactive`: skip unless the user asks to retry.
- `removed`: no longer used; keep only in changelog or historical notes.

## EvidenceRef

Use lightweight evidence references instead of raw copied evidence:

```yaml
id: ev-2026-05-16-001
source_id: codex-local
source_alias: primary-agent-session-store
type: agent_session
date: 2026-05-16
locator_alias: codex-session-2026-05-16-a
confidence: high
privacy: metadata_only
claim: Agent ran verification command for the reviewed task.
```

Reviews and indexes should cite `EvidenceRef` IDs, aliases, claims, and confidence. They should not include raw private content by default.

## Confidence

- High: direct evidence from durable artifacts such as commits, PRs, test reports, tickets, or session transcripts.
- Medium: partial evidence from summaries, metadata, referenced links, or indirect artifacts.
- Low: weak evidence, incomplete access, ambiguous timestamps, or inferred context.

## Fact Language

- Observed: directly supported by evidence.
- Inferred: likely based on multiple signals, but not directly stated.
- Uncertain: possible but not well supported.

## Evidence Integrity

Every review should include coverage for AI sessions, Git, PR/CI, requirements, communication, calendar, documentation, test artifacts, operations, registry changes, and uncertain items.

