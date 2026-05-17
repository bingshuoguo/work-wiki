# Redaction Taxonomy

Metadata 和 summaries 也可能泄露敏感信息。Work Wiki 使用以下分类：

- Public-safe: 通用 provider type、source alias、evidence type、confidence 和 date。
- Internal metadata: 本地路径、仓库名、ticket key、PR URL、sender 或 attendee 名称、组织名。
- Sensitive content: 邮件正文、聊天消息、文档正文、事故细节、客户数据、secrets、专有代码、私有 dashboard。
- Secret material: tokens、cookies、API keys、OAuth refresh tokens、SSH keys 和 session identifiers。

## Default Handling

- Public-safe data 可以出现在示例和公开文档中。
- Internal metadata 只能出现在私有工作区中。
- Sensitive content 需要用户明确批准后才能包含。
- Secret material 绝不能写入。

## Publish-Safe Mode

Publish-safe mode 会用别名替换路径、provider identifiers、人员、组织、项目和 tenants。
