# V0 Validation Plan

Run these checks before publishing a Work Wiki release.

## Required Checks

1. File presence: all required docs, protocols, templates, examples, and workspace-template files exist.
2. Privacy defaults: `.gitignore` and `workspace-template/.gitignore` ignore real `EVIDENCE_SOURCES.md`, `EVIDENCE_SOURCES_CHANGELOG.md`, `.cache/`, `.local/`, and `raw/`.
3. Example-only registry: public templates use `EVIDENCE_SOURCES.example.md` and alias fields instead of real local paths.
4. Provider safety: docs include opt-in, read-only, no-token-storage, tenant-boundary, and metadata-first rules.
5. Registry audit: all source mutation rules require changelog entries.
6. State machine: source statuses and transition rules are documented.
7. EvidenceRef: docs define how reviews and indexes cite evidence without copying raw evidence.
8. Review templates: daily, weekly, and monthly templates include `Evidence Integrity`.
9. Index/growth templates: workspace template includes skills, recurring problems, workflows, experiments, scorecard, and quality-of-life files.
10. Publish-safety scan: repository contains no real secrets, local user paths, private provider identifiers, or raw evidence samples.
11. Adoption smoke test: copy `workspace-template/` into a temporary private workspace, create private registry/changelog from examples, create daily/weekly/monthly review artifacts from templates, and verify `Evidence Integrity`, index files, and growth files exist.

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

For negative `rg` scans, exit code 1 with no output means the scan is clean.

## Release Gate

Public release must stop for explicit confirmation before pushing:

- host
- namespace / owner
- repository name
- visibility
- license holder
- security contact path
- validation status
- publish-safety scan status

Do not publish if any item is unknown or validation is not clean.

