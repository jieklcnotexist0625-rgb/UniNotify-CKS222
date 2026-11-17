# Task 1 — SPEM 2.0 Method Content: Code Review and Static Analysis

Owner: Lim Chin Jiek. Branch: `docs/lcj/spem-method-content`.

## Why SPEM separates method content from process

SPEM 2.0 describes **what** is done (roles, work products, tasks, steps) separately from **when** it is done (the process). This matters because the same method content can be reused in different schedules — for example, a code review gate can run in Scrum sprints or in a V-Model project without changing the roles or work products. Be ready to explain this in the viva.

## Step 1 — Define the three roles

| Role | Why it exists | What it owns | Access needed |
| --- | --- | --- | --- |
| Developer / Author | Ensures end-to-end accountability for a code change from start to finish and cannot approve their own work. | The Change Set | **Read-Write:** Change Set<br>**Read-Only:** Review Findings Log, CI Gate Report |
| Reviewer | Provides an objective evaluation against acceptance criteria, as authors cannot reliably judge their own work. | The Review Findings Log | **Read-Write:** Review Findings Log<br>**Read-Only:** Change Set, CI Gate Report *(No write access to Change Set to prevent becoming a silent co-author)* |
| Static Analysis Gatekeeper | Eliminates human inconsistency by running automated formatting and security checks, with the ability to block merges. | The CI Gate Report | **Write:** CI Gate Report *(Read-only to all humans so results cannot be altered)*<br>**Read-Only:** Change Set |

## Step 2 — Work products and access modes

| Work product | Produced by | Input access | Output access |
| --- | --- | --- | --- |
| Change Set / Pull Request | Developer / Author | read-write by Author | read-only to Reviewer and Gatekeeper |
| Review Findings Log | Reviewer | read-write by Reviewer | read-only to Author |
| CI Gate Report | Static Analysis Gatekeeper | write-only by Gatekeeper | read-only to Author and Reviewer |

## Step 3 — Two tasks broken into sequential steps

Write the steps in the order they actually happen. Each step should name **who acts** and **what work product they touch**.

### Task A — Perform Peer Review

1. Author opens a change set and requests review.
2. Reviewer reads the Change Set to inspect the code against acceptance criteria.
3. Reviewer reads the CI Gate Report to verify that automated checks have passed.
4. Reviewer records findings in the Review Findings Log and approves or rejects the Change Set.
5. Author reads the Review Findings Log and updates the Change Set to fix any issues (or merges the Change Set if approved).

### Task B — Enforce Static Analysis Gate

1. Build is triggered on the change set.
2. Static Analysis Gatekeeper reads the Change Set.
3. Static Analysis Gatekeeper runs automated formatting and security checks and writes the results to the CI Gate Report.
4. Gate result is published and merge is allowed or blocked.

