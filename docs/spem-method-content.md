# Task 1 — SPEM 2.0 Method Content: Code Review and Static Analysis

Owner: Lim Chin Jiek · Branch: `docs/lcj/spem-method-content` · Updated: 26 November 2026

## 1. Why SPEM separates method content from process

SPEM 2.0 describes **what** is done — roles, work products, tasks and steps — separately from **when** it is done (the process that sequences them). The separation is what makes the method content reusable: the same review gate can run inside a Scrum increment or a V-Model stage without changing a single role or work product. In this assignment the method content is fixed here and published to Notion; the process that enacts it is described in Task 5.

## 2. Roles

| Role | Owns | Responsibility | Competence | Access mode |
|---|---|---|---|---|
| **Developer / Author** | Change Set / Pull Request | Ensures end-to-end accountability for a code change and cannot approve their own work. | Module implementation and test writing. | Read-write: Change Set. Read-only: Review Findings Log, CI Gate Report. |
| **Reviewer** | Review Findings Log | Provides an objective evaluation against the acceptance criteria and no write access to the Change Set, so the role cannot become a silent co-author. | Evaluation of code against written acceptance criteria. | Read-write: Review Findings Log. Read-only: Change Set, CI Gate Report. |
| **Static Analysis Gatekeeper** | CI Gate Report | Runs the automated formatting and security checks and can block a merge. | Analyser ruleset configuration (ESLint, SonarQube) and secure coding rules. | Write: CI Gate Report, read-only to all humans. Read-only: Change Set. |

The three roles are separated so that the author of a change is never its sole approver. That is the control which removes the craft-based pattern in which a developer merges code simply because it compiles on their own machine.

## 3. Work products

| Work product | Producer | Produced from (input) | Output | Access mode |
|---|---|---|---|---|
| **Change Set / Pull Request** | Developer / Author | Committed source diff, linked user story and GWT acceptance criteria. | A review-ready change set with context, risk tag and reviewers assigned. | Read-write by the Author; read-only to the Reviewer and the Static Analysis Gatekeeper. |
| **Review Findings Log** | Reviewer | The Change Set and the acceptance criteria it has to satisfy. | Ranked findings with severity, file location and the approve or reject decision. | Read-write by the Reviewer; read-only to the Author; no write access to the Change Set. |
| **CI Gate Report** | Static Analysis Gatekeeper | The build triggered on the Change Set and the configured ruleset. | Pass or fail per rule, with blocking defects identified. | Written by the Gatekeeper; read-only to the Author and the Reviewer. |

The explicit input and output access modes are the part most students omit, and they are the part that carries the argument. A work product that only one role can write and every role can read gives a single source of truth for each review decision. Retyping the same fact into three places is exactly the duplicate-entry waste the Lean audit identifies in Vialing's admissions workflow.

## 4. Tasks and sequential steps

### Task A — Perform peer review

**Purpose:**&#8203; ensure a change is evaluated by someone other than its author, against written acceptance criteria.
**Trigger:**&#8203; a change set is opened and review is requested.

| Step | Instruction | Exit condition |
|---|---|---|
| A1 | Author opens a change set and requests review. | Change set exists and a reviewer is requested. |
| A2 | Reviewer reads the Change Set and checks the code against the acceptance criteria. | Every acceptance criterion marked met or not met. |
| A3 | Reviewer reads the CI Gate Report to confirm the automated checks passed. | Gate result known: pass or fail. |
| A4 | Reviewer records findings in the Review Findings Log and approves or rejects the Change Set. | Decision recorded with its rationale. |
| A5 | Author fixes the issues and updates the Change Set, or merges it if approved. | Change merged, or returned to step A2. |

### Task B — Enforce the static analysis gate

**Purpose:**&#8203; apply formatting and security checks consistently, without relying on reviewer memory.
**Trigger:**&#8203; a build is triggered on a change set.

| Step | Instruction | Exit condition |
|---|---|---|
| B1 | A build is triggered on the change set. | Build completes and the artefact is available. |
| B2 | Gatekeeper reads the Change Set. | Scope of the change understood. |
| B3 | Gatekeeper runs the formatting and security checks and writes the CI Gate Report. | Report shows pass or fail per rule. |
| B4 | Gate result is published and the merge is allowed or blocked. | Merge state set; blocking findings raised to the author. |

The two tasks are interlocked rather than parallel: Task B step 4 decides whether a merge is possible at all, and Task A step 3 is where the Reviewer checks that outcome before approving. Because both records are work products rather than chat messages, the evidence for a change sits in one place instead of being scattered across conversations.
