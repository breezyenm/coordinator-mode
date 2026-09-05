# Task Board Format

The task board is a markdown file at `TASK_BOARD.md` in the project root. It is the single source of truth for coordinated work.

## Template

```markdown
# Task Board

> Last updated: [timestamp]

## Active Tasks

| ID | Task | Phase | Started | Updated |
|----|------|-------|---------|---------|
| T-001 | [Task name] | RESEARCHING | [time] | [time] |

---

## T-001: [Task Name]

**Requested by:** [user or context]
**Phase:** RESEARCHING | SYNTHESIZED | IMPLEMENTING | VERIFYING | COMPLETE | BLOCKED
**Pipeline breaks:** [none, or reason for skipping a phase]

### Research Log
[Populated during Phase 1 — include the Mermaid dependency-map diagram]

### Synthesized Spec
[Populated during Phase 2 — include the Mermaid change-order diagram]

### Implementation Notes
[Populated during Phase 3 — files changed, decisions made]

### Verification Report
[Populated during Phase 4]

---

## Completed Tasks

| ID | Task | Completed | Files Changed |
|----|------|-----------|---------------|
| | | | |

---

## Change History

| Time | Task | Action |
|------|------|--------|
| | T-001 | Created, status: RESEARCHING |
| | T-001 | Research complete, 5 files examined |
| | T-001 | Spec produced, awaiting review |
```

## Rules

1. Every status transition gets a change history entry
2. Never delete a completed task — move it to the Completed section
3. If a task is BLOCKED, note the blocker in the Implementation Notes
4. The task board is append-only during a session — never rewrite history
5. Task IDs are sequential: T-001, T-002, etc.
6. Keep the Active Tasks table as the first thing after the header — it's the dashboard view
