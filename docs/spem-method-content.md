# Task 1 — SPEM 2.0 Method Content: Code Review and Static Analysis

Owner: Lim Chin Jiek. Branch: `docs/lcj/spem-method-content`.

**Academic integrity note:** the brief restricts direct AI generation of the report. The prompts below are questions to guide your own analysis. Write the answers in your own words — you must be able to defend them in the Week 9 viva.

## Why SPEM separates method content from process

SPEM 2.0 describes **what** is done (roles, work products, tasks, steps) separately from **when** it is done (the process). This matters because the same method content can be reused in different schedules — for example, a code review gate can run in Scrum sprints or in a V-Model project without changing the roles or work products. Be ready to explain this in the viva.

## Step 1 — Define the three roles

For each role, answer three questions in 2–3 sentences:

1. **Why must this role exist?** What problem does it solve that the other two roles cannot?
2. **What does it own?** Which work product does it create or approve?
3. **What access does it need?** Read, write, or approve — and on which work products?

| Role | Why it exists | What it owns | Access needed |
| --- | --- | --- | --- |
| Developer / Author | [write your answer] | [write your answer] | [write your answer] |
| Reviewer | [write your answer] | [write your answer] | [write your answer] |
| Static Analysis Gatekeeper | [write your answer] | [write your answer] | [write your answer] |

**Reasoning hint:** separate the person who *produces* a change from the person who *judges* it, and from the *automated check* that no human should override casually. That separation is the point of having three roles instead of one.

## Step 2 — Work products and access modes

State, for each work product, who can read it and who can change it. Think about why a reviewer should not be able to silently edit the author's change, and why a CI report must not be editable by the author.

| Work product | Produced by | Input access | Output access |
| --- | --- | --- | --- |
| Change Set / Pull Request | Developer / Author | read-write by Author | read-only to Reviewer and Gatekeeper |
| Review Findings Log | Reviewer | [fill in] | [fill in] |
| CI Gate Report | Static Analysis Gatekeeper | [fill in] | [fill in] |

## Step 3 — Two tasks broken into sequential steps

Write the steps in the order they actually happen. Each step should name **who acts** and **what work product they touch**.

### Task A — Perform Peer Review

1. Author opens a change set and requests review.
2. [add step — who acts, what artifact]
3. [add step]
4. Reviewer records findings and approves or rejects.
5. [add step]

### Task B — Enforce Static Analysis Gate

1. Build is triggered on the change set.
2. [add step]
3. [add step]
4. Gate result is published and merge is allowed or blocked.

## Checkpoint before you commit

- [ ] I wrote all three role descriptions in my own words
- [ ] Every work product has an explicit input access and output access mode
- [ ] Each task has numbered steps in chronological order, naming the actor
- [ ] I can explain why method content is separate from process

## Notion EPG checklist (next commit, not this one)

- [ ] Relational database with linked Roles, Work Products, Tasks and Steps tables
- [ ] Share link enabled
- [ ] Collaborative updates panel shows individual matric logs for all five members
- [ ] Screenshot saved to `evidence/`
