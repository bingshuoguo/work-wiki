# Work Wiki Agent Instructions

将本仓库作为一个 Markdown-first 的框架，用于进行证据驱动的工作复盘。

当用户输入 `/init` 或要求初始化 Work Wiki 时：

1. 阅读 `protocols/evidence-source-maintenance.md`。
2. 阅读 `protocols/provider-access-contract.md`。
3. 阅读 `templates/EVIDENCE_SOURCES.example.md` 和 `templates/EVIDENCE_SOURCES_CHANGELOG.example.md`。
4. 优先发现本地来源。
5. 创建或更新私有 `EVIDENCE_SOURCES.md`。
6. 在私有 `EVIDENCE_SOURCES_CHANGELOG.md` 中记录注册表变更。
7. 总结新增、更新、跳过和不确定的来源。

当用户要求每日复盘时：

1. 阅读私有 `EVIDENCE_SOURCES.md`。
2. 遵循 `protocols/daily-review.md`。
3. 在 `Evidence Integrity` 下记录来源覆盖情况和不确定性。
4. 当复盘产生长期知识时，更新长期索引。
5. 当模式显示出有用实验时，更新 growth artifacts。

当用户要求周度或月度复盘时：

1. 优先使用已有每日复盘。
2. 遵循 `protocols/weekly-review.md` 或 `protocols/monthly-review.md`。
3. 更新 `indexes/` 和 `growth/` artifacts。

默认安全规则：

- Gmail、Slack、calendar、docs、monitoring、incident systems 等敏感 provider 必须先在私有 `EVIDENCE_SOURCES.md` 中显式启用，才能扫描。
- 首次扫描任何敏感 provider 前必须确认。
- 外部 provider 默认只读，并优先使用 metadata。
- 绝不存储 token、cookie、OAuth secret、API key 或 session material。
- 除非用户明确要求，否则不要存储敏感的原始邮件、聊天、文档或代码内容。
- 优先使用 metadata、链接、计数、时间戳和短摘要。
- 区分已观察证据与推断。
- 如果某个来源无法读取，继续使用可用证据，并记录缺口。
