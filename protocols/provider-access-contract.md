# Provider Access Contract

敏感 provider 默认禁用。

任何可能暴露私密工作或个人信息的 provider 都必须遵守以下 contract：

- Explicit opt-in: 扫描前，来源必须列在私有 `EVIDENCE_SOURCES.md` 中。
- Read-only access: Work Wiki agent 可以检查证据，但除非用户提出单独请求，否则不得修改外部系统。
- No token storage: token、cookie、API key、OAuth refresh token 和 session secret 绝不能写入仓库。
- Tenant boundary: provider entries 必须用 alias 标识目标账号、workspace、organization 或 tenant，而不是 secret 或 raw token。
- Scope minimization: 请求或使用实际需要的最小 scope，例如 full content 不必要时使用 metadata-only email/calendar access。
- Scan confirmation: 首次扫描 Gmail、Slack、Teams、Feishu、Google Drive、Confluence、Notion、monitoring、incident 或类似敏感系统前，确认该来源已在私有注册表中有意启用。
- Publish-safe output: 除非用户明确要求包含原始私密内容，否则 summary 必须避免这些内容。
