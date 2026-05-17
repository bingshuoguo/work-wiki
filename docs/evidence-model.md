# Evidence Model

Work Wiki 区分证据类型、置信度、来源覆盖情况和证据引用。

## Evidence Types

- Agent session evidence: prompts、tool calls、commands、file references、decisions 和 review loops。
- Git evidence: branches、commits、diffs、changed files、stash 和 untracked files。
- Delivery evidence: pull requests、reviews、CI checks、merge status 和 deployments。
- Requirement evidence: tickets、issues、acceptance criteria、status changes 和 blockers。
- Communication evidence: email、chat、meeting notes 和 review threads。
- Calendar evidence: meetings、planning blocks、interviews、reviews 和 focus time。
- Documentation evidence: design docs、runbooks、notes、decisions 和 comments。
- Quality evidence: test reports、coverage、traces、screenshots、benchmarks 和 failure logs。
- Operational evidence: alerts、dashboards、incidents、releases、rollbacks 和 feature flags。

## Source Status

- `pending`: 已发现或已配置，但尚未验证。
- `active`: 正常扫描。
- `degraded`: 仅在相关或可能已恢复时扫描。
- `auth_required`: 跳过，直到凭证或 connector 访问发生变化。
- `inactive`: 跳过，除非用户要求重试。
- `removed`: 不再使用；只保留在 changelog 或历史说明中。

## EvidenceRef

使用轻量级证据引用，而不是复制原始证据：

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

复盘和索引应引用 `EvidenceRef` ID、alias、claim 和 confidence。默认不应包含原始私密内容。

## Confidence

- High: 来自 commit、PR、test report、ticket 或 session transcript 等持久 artifact 的直接证据。
- Medium: 来自 summary、metadata、referenced link 或间接 artifact 的部分证据。
- Low: 证据较弱、访问不完整、时间戳含糊或上下文需要推断。

## Fact Language

- Observed: 由证据直接支持。
- Inferred: 基于多个信号很可能成立，但并非直接陈述。
- Uncertain: 可能成立，但支持不足。

## Evidence Integrity

每篇复盘都应包含 AI sessions、Git、PR/CI、requirements、communication、calendar、documentation、test artifacts、operations、registry changes 和 uncertain items 的覆盖情况。
