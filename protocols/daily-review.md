# Daily Review Protocol

When the user asks for a daily review, create a review for the requested date. If no date is given, use today's local date.

## Workflow

1. Read private `EVIDENCE_SOURCES.md`.
2. Scan active sources for the target date.
3. Group work by task or project, not by transcript.
4. Align session intent with output, delivery, requirement, communication, and quality evidence.
5. Update private `EVIDENCE_SOURCES.md` if sources are discovered, degraded, inactive, or removed.
6. Write every source mutation to private `EVIDENCE_SOURCES_CHANGELOG.md`.
7. Write the review under `reviews/daily/YYYY-MM/YYYY-MM-DD.md`.
8. Reference relevant changelog entries in `Evidence Integrity`.
9. Update indexes only for durable decisions, learnings, workflows, recurring problems, or skill evidence.
10. Update growth artifacts only when there is a clear pattern or active experiment.

## Date Rules

- Use the user's local timezone unless workspace config specifies another timezone.
- Daily reviews cover `00:00:00` through `23:59:59`.
- Assign cross-midnight sessions by majority active work time.
- If majority time is unclear, assign by session start date and record uncertainty.

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

- Prefer concrete evidence over broad summary.
- Use `EvidenceRefs:` for evidence. Include only reference IDs, aliases, short claims, and confidence. Do not include raw excerpts by default.
- Mark low value only with evidence.
- Do not invent external state.
- Record missing sources instead of assuming status.
- Keep tomorrow actions to at most three items.
- Avoid moralizing; describe process issues as improvable patterns.

