---
name: init-workwiki
description: Use when the user types /init or asks to initialize a Work Wiki workspace by discovering useful local evidence sources, creating or updating private EVIDENCE_SOURCES.md, and recording changes in EVIDENCE_SOURCES_CHANGELOG.md.
---

# Init Work Wiki

Initialize a Work Wiki workspace from local evidence first, then optionally registered external providers.

## Required Reading

Before scanning or writing registry files:

1. Read `protocols/evidence-source-maintenance.md`.
2. Read `protocols/provider-access-contract.md`.
3. Read `templates/EVIDENCE_SOURCES.example.md`.
4. Read `templates/EVIDENCE_SOURCES_CHANGELOG.example.md`.

## Safety Rules

- Never store tokens, cookies, OAuth secrets, API keys, SSH keys, or session material.
- Do not scan sensitive providers unless they are explicitly enabled in private `EVIDENCE_SOURCES.md`.
- Confirm before the first scan of Gmail, Slack, Teams, Feishu, calendar, docs, monitoring, incident, or similar sensitive systems.
- Prefer aliases, counts, timestamps, paths expressed as locator aliases, and short metadata summaries.
- Do not copy raw private email, chat, document, or code content into registry files.
- If a source cannot be read, continue with available evidence and record the gap.

## Workflow

1. Check whether private `EVIDENCE_SOURCES.md` and `EVIDENCE_SOURCES_CHANGELOG.md` exist.
2. If either file is missing, create it from the matching template.
3. Discover local-only sources first:
   - current Git repository and nearby worktrees;
   - visible agent configuration in `.codex/`, `.claude/`, `.cursor/`, `AGENTS.md`, `CLAUDE.md`, and `GEMINI.md`;
   - local review artifacts under `reviews/`, `indexes/`, and `growth/`;
   - local caches only as metadata locations, never raw copied content.
4. Add or update provider entries with stable `id`, publish-safe `alias`, `status`, `type`, `access`, `locator_alias`, `scope`, `privacy`, `last_verified`, and `failure_count`.
5. Record every registry mutation in `EVIDENCE_SOURCES_CHANGELOG.md` under today's local date.
6. Report:
   - sources added or updated;
   - sources skipped and why;
   - sensitive providers that still require explicit opt-in;
   - the next recommended command, usually a daily review.

## Source Defaults

- Current repository: `type: git`, `access: local_path`, `privacy: local_only`.
- Agent instruction files: `type: documentation`, `access: local_path`, `privacy: local_only`.
- Work Wiki artifacts: `type: documentation`, `access: local_path`, `privacy: local_only`.
- External services: leave `inactive` or `auth_required` unless private registry opt-in and confirmation are present.

## Output Discipline

Use observed/inferred/uncertain language. Do not claim a source is active unless it was successfully checked during this init run.
