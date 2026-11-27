# Task 5: Process Tailoring and Human Factors Governance

**Owner:** Muhammad Yusri Bin Epiyusra (`myusri06@student.usm.my`) — Governance Lead & Report Integrator  
**Context:** CKS222 Group Coursework (Semester I, 2026/2027) — Comparing **Vialing (SkyCMS)** with **CCA103 UniNotify (Group 36, Semester II 2025/2026)**

---

## 6.1 Münch's 4 Ps Tailoring Analysis

Process tailoring adapts a software development process to the situational context of the product, project, people, and problem rather than forcing a rigid, one-size-fits-all standard (Armbrust et al., 2008; Münch et al., 2012). Because the CKS222 coursework compares a commercial Malaysian campus-management SaaS (**Vialing / SkyCMS**) with an expanded university coursework baseline (**CCA103 UniNotify**), the 4 Ps analysis accounts for both perspectives:

| P Factor | Audited Organisation (Vialing / SkyCMS) & University Baseline (CCA103 UniNotify) | Tailoring Implication for the Process |
| :--- | :--- | :--- |
| **Problem** | Vialing's operational reality highlights data silos across admissions, registry, and finance, duplicate data entry, slow reconciliation between academic eligibility and fee balances, reliance on offline spreadsheets, and staff-memory governance (Vialing, n.d.-a). In UniNotify, missed deadlines and manual tracking motivated automated reminders (Group 36, 2026a). | Enforce a single source of truth for records/decisions, automate validation and reminder workflows, and replace ad-hoc chat/spreadsheet tracking with formal process records and review gates. |
| **Project** | SkyCMS is a multi-module campus SaaS spanning admissions, PTPTN/MARA/FPX billing, examinations, MQA compliance, and HR/payroll across institutions (Vialing, n.d.-a). UniNotify was a four-module, one-semester student project delivered across five iterations (Group 36, 2026a, 2026b). For CKS222, the group is executing a compressed 12-day report and evidence cycle (16–27 Nov 2026). | Combine short iterative cycles for rapid drafting and feedback with strict milestone/gate checks so integration, evidence gathering, and compliance checks happen continuously rather than at the very end. |
| **People** | Vialing serves diverse institutional roles (admissions, registry, finance, academic faculty, students, parents, executives) (Vialing, n.d.-a). In our CKS222 group of five members, only Lim Chin Jiek and Gabriel Gan Heng Qing built the original CCA103 system, while Chiew Yee Fan, Aly Irwanshah Bin Azman, and Muhammad Yusri Bin Epiyusra contribute through audit, analysis, and integration. | Assign clear RACI accountability across five roles, use Notion EPG documentation so context is shared transparently, and pair experienced members with newer/non-CCA103 members to prevent knowledge silos. |
| **Product** | SkyCMS manages high-stakes student records, financial transactions, and MQA audit trails alongside scheduling and notifications (Vialing, n.d.-a). UniNotify consists of four modules (*User Management System*, *Reminder & Notification*, *Assignment Management System*, and *User Dashboard and Calendar*) on a client-server stack (Group 36, 2026a, 2026b). | Apply heavy, symmetrical V-Model verification and validation gates to high-criticality data (student records, fee/payment flows, MQA audit trails), while using lightweight agile checks for lower-risk UI/documentation updates. |

---

## 6.2 Justification of the Hybrid Prescriptive Approach

Neither a pure ad-hoc agile process nor a rigid waterfall model fits this context:
- **Why not pure ad-hoc agile?** Relying purely on informal iteration risks missing audit trails, skipping verification on sensitive student/payment records, and letting requirements drift without documented sign-off.
- **Why not pure waterfall?** Freezing everything upfront and deferring integration/testing until the end creates late bottlenecks and high rework cost—as seen in UniNotify's late integration/testing pattern and Vialing's reconciliation delays (Group 36, 2026a; Vialing, n.d.-a).

Instead, we adopt a **hybrid prescriptive approach** combining four mechanisms (Münch et al., 2012):
1. **Scrum-like short iterations:** Backlog-driven increments, frequent progress check-ins, and reviewable deliverables so team work adapts smoothly within the tight schedule.
2. **V-Model gate checks:** Symmetrical verification and validation gates for high-risk data (student records, payment flows, MQA compliance), requiring clear evidence and review sign-off before acceptance.
3. **XP engineering/quality practices:** Pair programming for knowledge transfer and defect prevention, test-first/TDD thinking for verifiable acceptance criteria, and continuous integration (CI) for early defect detection.
4. **SPEM 2.0 / Notion EPG & RACI governance:** Explicit roles, work products, access modes, and single-Accountable ownership per deliverable so process rules are prescriptive and review logs provide descriptive traceability.

---

## 6.3 Tuckman Team Dynamics

### 6.3.1 Current Team Stage with Evidence

Using Tuckman's four-stage model (**Forming, Storming, Norming, Performing**; Tuckman, 1965), the team has progressed through **Forming** and **Storming**, established **Norming**, and is moving into **Performing** as deliverables and submission gates are finalized:

| Tuckman Stage | Evidence from This Project |
| :--- | :--- |
| **Forming** | Team roster, role allocations, and repository/governance responsibilities were established at the start of the coursework. |
| **Storming** | Differences emerged around group composition/prior CCA103 familiarity and how far to expand a student coursework baseline to full-project and multi-module SaaS scale; resolved by agreeing on transparent scope disclosure and full-scale expansion. |
| **Norming** | Shared working norms were put in place through the Notion EPG, RACI matrix, Git branching/PR rules, Given-When-Then criteria, and Definition of Done. |
| **Performing** | Team members execute their assigned tasks and peer reviews, coordinate evidence for submission gates, and resolve decisions collectively via group consensus polls. |

> **Evidence Note (Appendix / Chat Extracts):** Attach unedited chat screenshots showing (a) initial role/task setup, (b) the scope-expansion and cut-scope agreement, and (c) the group consensus polls, with visible dates and participant names (no edited or backdated images).

### 6.3.2 Conflict and Resolution

A key structural risk in the team was **asymmetric prior system familiarity**: two members (Lim Chin Jiek and Gabriel Gan Heng Qing) participated in the original CCA103 UniNotify project, whereas the other three members joined without prior UniNotify build context. Left unmanaged, this could cause informal decisions among those familiar with the baseline and leave others behind.

We addressed this through three governance controls:
1. **Centralized, visible documentation in the Notion EPG and repository** so rationale and decisions are recorded rather than kept in private side-chats.
2. **Balanced RACI ownership** so accountability is distributed across tasks and every deliverable has clear Responsible and Accountable owners.
3. **Pair/collaborative walkthroughs and peer reviews** so CCA103 context and technical/process details are actively shared across the group.

---

## 6.4 Fist-of-Five Consensus Decision

### 6.4.1 Decision Context

The group tested alignment on scope and process adoption in the **CKS222 Assignment Group** chat using WhatsApp polls mapped to our agreement scale (Lucid Meetings, n.d.):
- **Scope & cut-scope alignment (10:46 PM):** Confirming focus strictly on (1) automated incomplete-document reminders three days before the intake deadline and (2) the applicant missing-document status view, while excluding SMS/in-app channels (email only for this increment), admin analytics dashboard, bulk CSV import, payment/PTPTN integration, and mobile app / multi-language / MQA report export.
- **Process & role-ownership alignment (8:47 AM):** Confirming role ownership across Lim, Gabriel, Chiew, Irwan, and Yusri, alongside fixed increment scope, test-before-merge checks, pair programming on the first review cycle, test-first practice, and CI checks blocking red builds.

### 6.4.2 Vote Evidence and Resolution of Votes Below Three

> **Evidence Note (Appendix D):** Both unedited WhatsApp group chat screenshots are included in **Appendix D**. Because WhatsApp polls display aggregate option tallies rather than per-voter names or a 0–5 numeric count, the table below records the exact poll results without fabricating individual row assignments.

| Consensus Poll / Option | Tally Recorded | Notes / Interpretation on Scale |
| :--- | :---: | :--- |
| **Poll 1 — Two-Feature Scope Comfort:** `5 - Fully support` | **3 votes** | Strong alignment with building only the two core features |
| **Poll 1 — Two-Feature Scope Comfort:** `4 - Support, minor reservations` | **2 votes** | Supportive with minor reservations; no `< 3` blocking votes |
| **Poll 2 — Five-Person Process Workability:** `5 - Fully support` | **5 votes** | Unanimous top-tier support for role split, testing/CI gates, and scope freeze |
| **Poll 2 — Five-Person Process Workability:** `4 - Support, minor reservations` | **0 votes** | No reservations recorded on process workability |

**Resolution of Any Vote Below 3:** No vote below `3` (or below `4` on the WhatsApp poll options) was recorded across either poll. Minor reservations on scope were addressed by explicitly freezing the feature set to the two core workflows and documenting excluded features up front rather than expanding scope mid-way.

---

## References

- Armbrust, O., Katahira, M., Miyamoto, Y., Münch, J., Nakao, H., & Ocampo, A. (2008). Scoping software process models: Initial concepts and experience from defining space standards. *Lecture Notes in Computer Science*, 5007, 160–172.
- Group 36. (2026a). *UniNotify: Assignment & Deadline Reminder System — System analysis (CCA103 Report 1)*. School of Computer Sciences, Universiti Sains Malaysia.
- Group 36. (2026b). *UniNotify: Assignment & Deadline Reminder System — System design and implementation (CCA103 Report 2)*. School of Computer Sciences, Universiti Sains Malaysia.
- Lucid Meetings. (n.d.). *What is Fist to Five?* https://www.lucidmeetings.com/glossary/fist-five
- Münch, J., Armbrust, O., Kowalczyk, M., & Soto, M. (2012). *Software process definition and management*. Springer.
- Tuckman, B. W. (1965). Developmental sequence in small groups. *Psychological Bulletin*, 63(6), 384–399.
- Vialing. (n.d.-a). *Vialing SaaS campus management system*. https://www.vialing.com/
