# Work Wiki

<p align="center">
  <strong>Work Wiki: Turn your AI work traces into growth.</strong>
</p>

<p align="center">
  <a href="https://github.com/bingshuoguo/work-wiki/tree/main">English</a> | 中文
</p>

<p align="center">
  一个本地优先、Markdown-first 的系统，用于生成有证据支撑的日常复盘、沉淀长期工作知识，并改进你与 AI agent 的协作方式。
</p>

Work Wiki 帮你把分散的工作信号整理成一份会持续生长的记录：发生了什么、改变了什么、验证了什么，以及哪些模式正在反复出现。

它面向每天和 Codex、Claude Code、Gemini、Cursor、Antigravity、Copilot Chat 等 agent 一起工作的用户。与其让 agent 写一段模糊的下班总结，不如给它一套结构：先读取证据，再写有依据的复盘，维护长期索引，并把反复出现的模式转化为改进实验。

```text
证据源
  -> 证据源注册表
  -> 每日复盘
  -> 周/月模式沉淀
  -> 长期索引
  -> 成长实验
```

## 为什么需要 Work Wiki

现代工作并不只发生在一个地方。一个任务可能同时跨过 agent session、Git 分支、pull request、ticket、测试运行、日历时间块、设计文档和聊天线程。

这会让普通状态更新变得脆弱：它们依赖记忆，遗漏验证细节，也很少捕捉那些真正解释工作为何顺畅或昂贵的过程模式。

Work Wiki 给 agent 一套复盘协议：

- 先找证据，再写结论。
- 区分已观察事实与推断。
- 记录来源覆盖情况和不确定性。
- 把可复用的决策、经验、工作流和反复问题从一次性总结中提取出来。
- 用日常工作的模式改进你与 agent 的协作方式。

## 它能帮你做什么

| 需求 | Work Wiki 提供 |
| --- | --- |
| 每日复盘 | 按任务、产出、学习、验证和证据缺口组织的结构化复盘。 |
| 周度复盘 | 从多篇日报中挖掘模式，包括反复问题和成长实验。 |
| 月度复盘 | 从更高层面查看产出、技能增长、瓶颈和下一步目标。 |
| 证据追踪 | 私有 `EVIDENCE_SOURCES.md` 注册表，告诉 agent 下次该去哪里找证据。 |
| 长期知识 | 面向项目、决策、经验、技能、工作流、协作和反复问题的长期索引。 |
| 更好的 agent 习惯 | 用实验和 scorecard 改进提示词、验证、上下文加载和复盘质量。 |

## 它如何工作

Work Wiki 不是应用服务器，也不是托管服务。它是一组可移植的 Markdown 协议、模板和工作区约定。

1. **发现来源**  
   先从本地证据开始，例如 agent session 和 Git 仓库。只有显式启用后才加入外部 provider。

2. **维护注册表**  
   把来源元数据保存在私有 `EVIDENCE_SOURCES.md` 中。把注册表变更记录到私有 `EVIDENCE_SOURCES_CHANGELOG.md`。

3. **基于证据写复盘**  
   每日复盘引用轻量级 `EvidenceRef`，而不是复制原始私密内容。

4. **沉淀长期知识**  
   决策、经验、工作流、技能和反复问题会进入 `indexes/`。

5. **闭合成长循环**  
   反复出现的模式会进入 `growth/`，成为实验、scorecard 信号、coaching notes 或工作质量调整。

## 快速开始

1. 把 `workspace-template/` 复制到一个私有工作区。
2. 用你常用的 agent 打开这个工作区。
3. 将 `EVIDENCE_SOURCES.example.md` 复制为 `EVIDENCE_SOURCES.md`。
4. 将 `EVIDENCE_SOURCES_CHANGELOG.example.md` 复制为 `EVIDENCE_SOURCES_CHANGELOG.md`。
5. 对 agent 说：

   ```text
   Initialize my Work Wiki evidence sources. Use local sources first,
   metadata-only mode, and no external provider scans unless already enabled.
   ```

6. 检查生成的 `EVIDENCE_SOURCES.md`。
7. 请求第一次复盘：

   ```text
   Review today's work using Work Wiki.
   ```

8. 周末时请求周度复盘：

   ```text
   Create this week's Work Wiki review.
   ```

## 隐私模型

Work Wiki 默认本地优先，并采取保守策略。

- 真实的 `EVIDENCE_SOURCES.md` 和 `EVIDENCE_SOURCES_CHANGELOG.md` 是私有文件，并被 gitignore 忽略。
- 外部 provider 必须显式 opt-in，默认只读，并优先使用 metadata。
- Gmail、Slack、calendar、docs、monitoring、incident systems 等敏感 provider 需要先在注册表中启用，并在首次扫描前确认。
- 复盘应优先使用别名、链接、计数、时间戳和短摘要。
- 原始邮件正文、私密聊天全文、私有文档正文、大段专有 diff、token、cookie、OAuth secret、API key 和 session material 都不应进入仓库。
- 访问缺失不是失败。把它记录到 `Evidence Integrity`，然后继续使用可用证据。

## 仓库结构

| 路径 | 用途 |
| --- | --- |
| `docs/` | 架构、证据模型、隐私模型、provider 指南、脱敏规则、验证计划和成长循环。 |
| `protocols/` | agent 用于来源维护、每日复盘、周度复盘、月度复盘和索引维护的说明。 |
| `templates/` | 可复用的复盘模板和示例注册表文件。 |
| `workspace-template/` | 可复制的私有工作区骨架，包含 reviews、indexes、growth 文件和被忽略的私有注册表文件。 |
| `examples/` | 面向 solo developer、tech lead 等常见角色的小型示例工作区。 |

## 适合谁

Work Wiki 适合你，如果你：

- 每天使用 coding 或 writing agent；
- 希望复盘基于真实发生的证据；
- 需要一份关于决策、验证和反复阻塞点的私有记录；
- 关心改进 agent 工作流，而不只是记录产出；
- 希望不用每周、每月重新加载上下文也能完成复盘。

它不是托管服务，不是必需 CLI，不是原始数据仓库，不是监控工具，也不是 Git、Jira、Slack、Gmail、日历或文档系统的替代品。

## License

MIT.
