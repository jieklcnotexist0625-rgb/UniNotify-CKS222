# Task 1 — SPEM 2.0 Method Content: Code Review and Static Analysis

Owner: Lim Chin Jiek. This file is a skeleton. Write the analysis yourself; the short notes below are prompts, not answers.

## Three roles

1. Developer / Author — [describe responsibilities and access rights]
2. Reviewer — [describe responsibilities and access rights]
3. Static Analysis Gatekeeper — [describe responsibilities and access rights]

## Three work products (state input and output access modes for each)

| Work product | Produced by | Input access | Output access |
| --- | --- | --- | --- |
| Change Set / Pull Request | Developer / Author | read-write by Author | read-only to Reviewer and Gatekeeper |
| Review Findings Log | Reviewer | [fill in] | [fill in] |
| CI Gate Report | Static Analysis Gatekeeper | [fill in] | [fill in] |

## Two tasks with sequential steps

### Task A — Perform Peer Review

1. Author opens a change set and requests review.
2. [add steps]
3. [add steps]
4. Reviewer records findings and approves or rejects.
5. [add steps]

### Task B — Enforce Static Analysis Gate

1. Build is triggered on the change set.
2. [add steps]
3. [add steps]
4. Gate result is published and merge is allowed or blocked.

## Notion EPG checklist

- [ ] Relational database with linked Roles, Work Products, Tasks and Steps tables
- [ ] Share link enabled
- [ ] Collaborative updates panel shows individual matric logs for all five members
- [ ] Screenshot saved to `evidence/`

## Reference

SPEM 2.0 separates **method content** (the what: roles, work products, tasks, steps) from **process** (the when and in what order). Be ready to explain this in the viva.
