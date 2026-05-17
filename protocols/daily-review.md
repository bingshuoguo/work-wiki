# Daily Review Protocol

当用户要求每日复盘时，为请求日期创建复盘。如果没有指定日期，使用今天的本地日期。

## Workflow

1. 阅读私有 `EVIDENCE_SOURCES.md`。
2. 扫描目标日期的 active sources。
3. 按 task 或 project 分组工作，而不是按 transcript 分组。
4. 将 session intent 与 output、delivery、requirement、communication 和 quality evidence 对齐。
5. 如果发现、降级、停用或移除了来源，更新私有 `EVIDENCE_SOURCES.md`。
6. 将每个来源变更写入私有 `EVIDENCE_SOURCES_CHANGELOG.md`。
7. 将复盘写到 `reviews/daily/YYYY-MM/YYYY-MM-DD.md`。
8. 在 `Evidence Integrity` 中引用相关 changelog entries。
9. 只在出现长期决策、经验、工作流、反复问题或技能证据时更新 indexes。
10. 只有当出现明确模式或 active experiment 时，才更新 growth artifacts。

## Date Rules

- 除非 workspace config 指定其他 timezone，否则使用用户本地 timezone。
- 每日复盘覆盖 `00:00:00` 到 `23:59:59`。
- 跨午夜 session 按主要活跃工作时间归属。
- 如果主要时间不明确，按 session start date 归属，并记录不确定性。

## Output Format

```markdown
# Daily Work Review - YYYY-MM-DD

## 1. Today Summary
- Main thread:
- Visible output:
- Key learning:
- Main efficiency issue:
- Growth signal:

## 2. Work Threads

### Thread: <task or project name>
- Time range:
- Tools:
- Related directories:
- EvidenceRefs:
- Output:
- Status: done / partial / blocked / exploration
- Value: high / medium / low
- Notes:

## 3. Visible Output
- Code:
- Docs:
- Tests:
- Decisions:
- Communication:
- Verification commands:
- Test artifacts:

## 4. Learning
- Technical knowledge:
- Engineering method:
- AI collaboration:
- Domain/context:

## 5. Reusable Methods
- Effective prompts:
- Debugging paths:
- Task decomposition:
- Review patterns:

## 6. Efficiency Loss
- Repeated context:
- Unclear goals:
- Missing verification:
- Tool-switching cost:
- Over-exploration:
- Collaboration overhead:

## 7. Growth Loop
- Active experiment:
- Evidence observed:
- Suggested adjustment:

## 8. Tomorrow Actions
1.
2.
3.

## 9. Evidence Integrity
- AI session coverage:
- Git coverage:
- PR / CI coverage:
- Requirement coverage:
- Communication coverage:
- Calendar coverage:
- Documentation coverage:
- Test artifact coverage:
- Operational coverage:
- Evidence source registry changes:
- Uncertain items:
```

## Rules

- 优先使用具体证据，而不是宽泛总结。
- 使用 `EvidenceRefs:` 表示证据。只包含 reference IDs、aliases、short claims 和 confidence。默认不包含原始摘录。
- 只有在有证据时才标记 low value。
- 不要编造外部状态。
- 记录缺失来源，而不是假设状态。
- Tomorrow actions 最多三项。
- 避免说教；将流程问题描述为可改进的模式。
