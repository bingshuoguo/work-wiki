# Work Wiki

<h2 align="center">Work Wiki: Turn your AI work traces into growth.</h2>

<p align="center"><strong>An evidence-backed work review system for AI-assisted work.</strong></p>

Work Wiki is a local-first, evidence-driven review framework for AI-augmented workers.

It helps people who work with agents such as Codex, Claude Code, Gemini, Cursor, Antigravity, Copilot Chat, and similar tools turn daily work traces into reviews, durable knowledge, and personal growth.

## Why

AI-assisted work leaves traces across agent sessions, Git repositories, pull requests, tickets, emails, calendars, chat, documents, tests, and deployment systems. Most daily summaries ignore that evidence and become vague status updates.

Work Wiki gives agents a shared framework for finding evidence, writing grounded reviews, maintaining long-lived indexes, and converting repeated patterns into improvement experiments.

## What It Is

- A Markdown-first framework.
- A set of portable agent instructions.
- A self-maintaining private evidence source registry.
- Daily, weekly, and monthly review protocols.
- Long-lived indexes for projects, decisions, learnings, skills, workflows, recurring problems, and collaboration.
- A growth loop for scorecards, experiments, coaching notes, and sustainable work quality.

## What It Is Not

- Not a hosted service.
- Not a required CLI.
- Not a raw data warehouse.
- Not a surveillance tool.
- Not a replacement for Git, Jira, Slack, Gmail, or your calendar.

## Quickstart

1. Copy `workspace-template/` into a private workspace.
2. Open the workspace with your preferred agent.
3. Copy `EVIDENCE_SOURCES.example.md` to private `EVIDENCE_SOURCES.md`.
4. Copy `EVIDENCE_SOURCES_CHANGELOG.example.md` to private `EVIDENCE_SOURCES_CHANGELOG.md`.
5. Ask: `Initialize my Work Wiki evidence sources. Use local sources first, metadata-only mode, and no external provider scans unless already enabled.`
6. Review and edit `EVIDENCE_SOURCES.md` if needed.
7. Ask: `Review today's work using Work Wiki.`
8. At the end of the week, ask: `Create this week's Work Wiki review.`

## Core Flow

```text
Source Discovery
  -> Evidence Sources Registry
  -> Daily Evidence Scan
  -> Review Artifacts
  -> Knowledge Indexes
  -> Growth Loop
```

## Privacy Defaults

- Real `EVIDENCE_SOURCES.md` and `EVIDENCE_SOURCES_CHANGELOG.md` are private and gitignored by default.
- External providers are explicit opt-in, read-only, metadata-first, and must never store tokens in the repository.
- Do not copy email bodies, private chat transcripts, private documents, or large code diffs into the workspace by default.
- Prefer metadata, aliases, links, counts, timestamps, and short summaries.
- Record missing access and uncertainty under `Evidence Integrity`.

## Repository Map

- `docs/`: concepts, architecture, evidence model, privacy model, provider safety, and growth loop.
- `protocols/`: instructions agents follow for reviews and maintenance.
- `templates/`: reusable Markdown and YAML templates.
- `workspace-template/`: copyable private Work Wiki workspace.
- `examples/`: workspace-shaped examples for common roles.

## License

MIT.
