# Architecture

Work Wiki 使用 Markdown-first 架构：

```text
Source Discovery
  -> Evidence Sources Registry
  -> Daily Evidence Scan
  -> Review Artifacts
  -> Knowledge Indexes
  -> Growth Loop
```

## Source Discovery

来源发现发生在初始化期间，也会在复盘过程中按需发生。agent 会寻找可用来源，例如本地 agent session、Git 仓库、PR 系统、ticket 系统、email、calendar、chat、documentation、test artifacts、deployment systems 和 monitoring systems。

## Evidence Sources Registry

私有 `EVIDENCE_SOURCES.md` 是来源注册表。它记录 agent 下次应该去哪里找证据。公开仓库只应提供 `EVIDENCE_SOURCES.example.md`。

## Review Artifacts

复盘是主要面向用户的 artifacts：

```text
reviews/
  daily/
  weekly/
  monthly/
```

每日复盘捕捉有证据支撑的工作线程。周度和月度复盘从累积的每日复盘中挖掘模式。

## Knowledge Indexes

索引是受 wiki 启发的知识层：

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

索引存放长期综合，而不是原始数据。

## Growth Loop

Growth artifacts 将模式转化为行为改变：

```text
growth/
  goals.md
  experiments.md
  scorecard.md
  coaching-notes.md
  quality-of-life.md
```
