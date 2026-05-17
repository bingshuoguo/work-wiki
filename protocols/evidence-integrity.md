# Evidence Integrity Protocol

Evidence integrity 解释一篇复盘的可信程度。

每篇复盘都必须说明检查了什么、缺失了什么、什么失败了，以及什么仍不确定。

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

如果来源之间冲突，报告冲突，而不是强行得出结论。

示例：

- Session 显示 tests passed，但 CI failed。
- Git 没有 commit，但 session 描述了 implementation。
- Ticket status 是 done，但 PR 未合并。
- Email 提到 approval，但缺少 deployment evidence。

## Confidence

使用 high、medium 或 low 置信度语言。避免虚假的精确性。

## EvidenceRef

使用轻量级证据引用，而不是复制原始证据：

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

规则：

- `source_id` 必须匹配私有注册表 entry。
- `locator_alias` 必须 publish-safe，或仅在私有 workspace 内可见。
- 不要包含 secret URL、raw token、private message bodies 或 large code excerpts。
