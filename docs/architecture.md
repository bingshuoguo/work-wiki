# Architecture

Work Wiki uses a Markdown-first architecture:

```text
Source Discovery
  -> Evidence Sources Registry
  -> Daily Evidence Scan
  -> Review Artifacts
  -> Knowledge Indexes
  -> Growth Loop
```

## Source Discovery

Source discovery happens during initialization and opportunistically during reviews. Agents look for available sources such as local agent sessions, Git repositories, PR systems, ticket systems, email, calendar, chat, documentation, test artifacts, deployment systems, and monitoring systems.

## Evidence Sources Registry

Private `EVIDENCE_SOURCES.md` is the source registry. It records where agents should look next time. Public repositories should ship only `EVIDENCE_SOURCES.example.md`.

## Review Artifacts

Reviews are the main user-facing artifacts:

```text
reviews/
  daily/
  weekly/
  monthly/
```

Daily reviews capture evidence-backed work threads. Weekly and monthly reviews mine patterns from accumulated daily reviews.

## Knowledge Indexes

Indexes are the wiki-inspired layer:

```text
indexes/
  projects.md
  decisions.md
  learnings.md
  skills.md
  workflows.md
  recurring-problems.md
  people-and-collaboration.md
```

Indexes store durable synthesis, not raw data.

## Growth Loop

Growth artifacts convert patterns into behavior change:

```text
growth/
  goals.md
  experiments.md
  scorecard.md
  coaching-notes.md
  quality-of-life.md
```

