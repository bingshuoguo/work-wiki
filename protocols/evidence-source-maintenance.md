# Evidence Source Maintenance Protocol

私有 `EVIDENCE_SOURCES.md` 是自维护注册表。agent 可以根据状态机自主添加、更新、降级、停用或移除来源。

## Initialization

初始化 Work Wiki 时：

1. 阅读 `protocols/provider-access-contract.md`。
2. 查找本地 agent session 目录。
3. 查找附近的 Git 仓库和 worktree。
4. 只有当私有注册表中可访问且已启用时，才检查可用 CLI 和 MCP connectors。
5. 将发现的来源写入私有 `EVIDENCE_SOURCES.md`。
6. 将变更记录到私有 `EVIDENCE_SOURCES_CHANGELOG.md`。

## Daily Maintenance

每次复盘期间：

1. 验证目标日期使用的 active sources。
2. 当来源失败时递增 `failure_count`。
3. 两次连续失败或部分访问后，将 `status` 设为 `degraded`。
4. 当 credentials 或 connector access 缺失时，将 `status` 设为 `auth_required`。
5. 七个日历日没有成功扫描，或来源不再相关时，将 `status` 设为 `inactive`。
6. 只有在来源明确无效或过时时才移除。
7. 所有变更都记录到私有 `EVIDENCE_SOURCES_CHANGELOG.md`。

## Source Status

- `pending`: 已发现或已配置，但尚未验证。
- `active`: 正常扫描。
- `degraded`: 仅在相关或可能已恢复时扫描。
- `auth_required`: 跳过，直到 credentials 或 connector access 变化。
- `inactive`: 跳过，除非用户要求重试。
- `removed`: 不保留在 active registry 中；记录到 changelog。

## State Machine

| Current | Event | Next |
| --- | --- | --- |
| `pending` | first scan succeeds | `active` |
| `pending` | auth or permission missing | `auth_required` |
| `active` | scan succeeds | `active` |
| `active` | one scan fails | `active` with incremented `failure_count` |
| `active` | two consecutive scans fail | `degraded` |
| `active` or `degraded` | auth expires | `auth_required` |
| `degraded` | two consecutive scans succeed | `active` |
| `degraded` | seven days without success | `inactive` |
| `inactive` | retry succeeds | `active` |
| `inactive` | source is obsolete | `removed` |

`last_verified` 表示上一次成功扫描日期，而不是上一次尝试扫描日期。

## Safety

不要在注册表中存储敏感原始内容。只存储去哪里找、如何查找的 metadata。
