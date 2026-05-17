# Privacy Model

Work Wiki 默认本地优先，并关注隐私。

## Default Rules

- 不存储原始邮件正文。
- 不存储私密聊天全文。
- 不存储私有文档正文。
- 不存储大段专有代码 diff。
- 优先使用 metadata、links、counts、timestamps、aliases 和 short summaries。
- 真实 `EVIDENCE_SOURCES.md` 和 `EVIDENCE_SOURCES_CHANGELOG.md` 保持私有，并被 gitignore 忽略。
- 本地缓存不进入版本控制。
- 记录缺失权限，但不强迫访问。

## Sensitive Sources

在私有 `EVIDENCE_SOURCES.md` 中标记敏感 provider：

```yaml
privacy: sensitive_metadata_only
```

对于敏感来源，agent 只应总结工作复盘所需的最小上下文。

## Local Cache Policy

以下路径应保持未跟踪：

```text
.cache/
.local/
raw/
EVIDENCE_SOURCES.md
EVIDENCE_SOURCES_CHANGELOG.md
```

## Redaction

- 在 publish-safe output 中，用别名替换人员、组织、项目、tenant、本地路径、provider 域名和私有仓库。
- 避免复制私密消息。
- 总结决策和阻塞点时不要引用敏感内容。
- 绝不写入 token、cookie、OAuth、API key、SSH key 或 session material。
