# V0 Validation Plan

发布 Work Wiki release 前运行这些检查。

## Required Checks

1. File presence: 所需 docs、protocols、templates、examples 和 workspace-template 文件都存在。
2. Privacy defaults: `.gitignore` 和 `workspace-template/.gitignore` 忽略真实 `EVIDENCE_SOURCES.md`、`EVIDENCE_SOURCES_CHANGELOG.md`、`.cache/`、`.local/` 和 `raw/`。
3. Example-only registry: 公开模板使用 `EVIDENCE_SOURCES.example.md` 和 alias 字段，而不是真实本地路径。
4. Provider safety: 文档包含 opt-in、read-only、no-token-storage、tenant-boundary 和 metadata-first 规则。
5. Registry audit: 所有来源变更规则都要求写入 changelog。
6. State machine: 来源状态和转换规则已文档化。
7. EvidenceRef: 文档定义了复盘和索引如何引用证据，而不复制原始证据。
8. Review templates: daily、weekly 和 monthly 模板包含 `Evidence Integrity`。
9. Index/growth templates: workspace template 包含 skills、recurring problems、workflows、experiments、scorecard 和 quality-of-life 文件。
10. Publish-safety scan: 仓库不包含真实 secret、本地用户路径、私有 provider 标识符或原始证据样例。
11. Adoption smoke test: 将 `workspace-template/` 复制到临时私有工作区，从 examples 创建私有 registry/changelog，创建 daily/weekly/monthly review artifacts，并确认 `Evidence Integrity`、index files 和 growth files 存在。

## Commands

```bash
find . -type f | sort
rg -n "EVIDENCE_SOURCES.md|EVIDENCE_SOURCES_CHANGELOG.md" .gitignore workspace-template/.gitignore
rg -n "token|secret|cookie|OAuth|read-only|opt-in|tenant" docs protocols README.md
rg -n "EvidenceRef|Evidence Integrity|auth_required|pending|degraded|inactive|removed" docs protocols templates
find . -type f -not -path './.git/*' -not -path './docs/validation-plan.md' -print0 | xargs -0 rg -n --pcre2 "(BEGIN (RSA|DSA|EC|OPENSSH) PRIVATE KEY|AKIA[0-9A-Z]{16}|ghp_[A-Za-z0-9_]{20,}|glpat-[A-Za-z0-9_-]{20,}|sk-[A-Za-z0-9_-]{20,}|xox[baprs]-[A-Za-z0-9-]{20,}|access_token\\s*[:=]|refresh_token\\s*[:=]|client_secret\\s*[:=]|api_key\\s*[:=]|[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,})"
find . -type f -not -path './.git/*' -not -path './docs/validation-plan.md' -print0 | xargs -0 rg -n --pcre2 "(/Users/|~/.codex|~/.claude|gmail\\.com|slack\\.com)"
git check-ignore EVIDENCE_SOURCES.md EVIDENCE_SOURCES_CHANGELOG.md .cache/x .local/x raw/x
```

对于 negative `rg` scans，exit code 1 且无输出表示扫描干净。

## Release Gate

公开发布前必须停下来明确确认：

- host
- namespace / owner
- repository name
- visibility
- license holder
- security contact path
- validation status
- publish-safety scan status

如果任何项目未知，或验证不干净，不要发布。
