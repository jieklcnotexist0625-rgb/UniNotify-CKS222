# Task 2 — Requirements Quality and Agile User Stories

**Owner:** Gabriel Gan Heng Qing (`24304331`, `gabzerhq@student.usm.my`)  
**Audited Organisation:** Vialing (SkyCMS)  
**University Project Comparison:** CCA103 UniNotify — Module B (Reminder & Notification)



## 1. Selected Backlog Item: Automated Reminder for Incomplete Documents

**Backlog Item:**  
"Admissions officers need the system to chase applicants whose document uploads are incomplete before an intake closes, instead of maintaining a manual spreadsheet of follow-ups."

- Derived from Vialing's published admissions dashboard showing an intake with 2,847 applications, 1,203 offers, 891 enrolled, "12 incomplete files" and a queued reminder SMS (Vialing, n.d.-a).
- **CCA103 UniNotify Analogue:** Module B (*Reminder & Notification*) — *"Receive Deadline Alerts"* use case, which triggers reminders from deadline proximity and configured lead time. Vialing expands this into a multi-party workflow (admissions officer, applicant, registry) requiring an audit trail.



## 2. Agile User Stories

- **US-1 (Admissions side):**  
  As an admissions officer, I want the system to automatically send a reminder to every applicant whose required documents are incomplete three days before the intake deadline, so that I can close the intake without manually chasing applicants by phone or spreadsheet.

- **US-2 (Applicant side):**  
  As an applicant, I want to see exactly which documents are missing and receive a reminder with a link to the upload page so that I can complete my application before the deadline without contacting the admissions office.



## 3. INVEST Evaluation

| INVEST Criterion | US-1 (Admissions Reminder) | US-2 (Applicant Document Status) | Verdict |
| :--- | :--- | :--- | :--- |
| **Independent** | Can be delivered without changing billing or exam modules; depends only on the admissions document list. | Shares the document list but can be released as a read-only view before automated reminders exist. | Pass (sequencing noted) |
| **Negotiable** | Lead time ("three days") and channel are open to negotiation with the registrar; states intent, not implementation. | Presentation of "exactly which documents" is open to discussion with applicants. | Pass |
| **Valuable** | Removes manual follow-up and supports the 40–60% administrative turnaround improvement claimed by Vialing. | Reduces applicant anxiety and repeated calls to admissions; clear end-user value. | Pass |
| **Estimable** | Bounded scope: one query, one scheduler, one message template; estimable using CCA103 notification code. | Bounded to a status view; no new data model required. | Pass |
| **Small** | One feature, one intake, one channel in the first increment. | One screen and one status API. | Pass |
| **Testable** | GWT scenarios define exact trigger, boundary, and failure behaviour. | GWT scenarios define visible status and missing-document list. | Pass |

### Managing Weaker Criteria
- **Independent (US-2):** Reads the same document state as US-1, so US-2 is released first as a read-only view before automation is added.
- **Small (US-1):** Could expand across SMS, email, and in-app channels at once; restricted to one channel in the first increment.
- **Estimable:** Initial estimate comes from the two members with CCA103 notification experience and is reviewed by the team.


## 4. Given-When-Then (GWT) Acceptance Criteria

### Positive Scenarios
- **US-1 — Scenario 1A: Reminder sent within lead time:**  
  **Given** an applicant has two required documents marked "incomplete" and the intake deadline is three days away,  
  **When** the daily reminder job runs,  
  **Then** the system sends one reminder to that applicant listing the two missing documents and the deadline,  
  **And** writes a reminder log entry with applicant ID, timestamp and channel.

- **US-2 — Scenario 2A: Applicant sees missing documents:**  
  **Given** an applicant is authenticated and has one missing document,  
  **When** the applicant opens the application status page,  
  **Then** the page displays the missing document name and an active upload link,  
  **And** the page states the date and time by which the upload must be completed.

### Negative & Boundary Scenarios
- **US-1 — Scenario 1B: No reminder for complete applications:**  
  **Given** an applicant has all required documents verified,  
  **When** the daily reminder job runs,  
  **Then** no reminder is sent to that applicant.

- **US-1 — Scenario 1C: Boundary at the deadline:**  
  **Given** an applicant's documents are incomplete and the intake deadline has already passed,  
  **When** the daily reminder job runs,  
  **Then** no "before deadline" reminder is sent, the application is flagged as "late" for officer review,  
  **And** the system records the reason for auditability.

- **US-2 — Scenario 2B: Reminder channel unavailable:**  
  **Given** the SMS gateway is unavailable when the reminder job runs,  
  **When** the job attempts delivery,  
  **Then** the system retains the reminder with status "RETRY", logs the failure and does not mark the applicant as notified,  
  **And** a retry occurs on the next scheduled run (mirroring CCA103 Module B test case TC-B-U09).

- **US-2 — Scenario 2C: Unauthenticated access:**  
  **Given** a user is not authenticated,  
  **When** the user requests the application status page,  
  **Then** access is denied and the user is redirected to login, with no document information disclosed.



## 5. Definition of Done (DoD)

1. All GWT scenarios pass, including the negative and boundary cases.
2. Code change has a completed Review Package (WP1) and Review Decision Record (WP3) with an Accept decision.
3. Static analysis reports no blocking defect, or accepted risks are signed off by the V&V Engineer in WP2.
4. Unit and integration tests cover the new behavior. Integration includes the boundary between admissions and notification modules, matching CCA103's four-level testing strategy.
5. Personal data (applicant identifiers and document metadata) is protected by JWT authentication, RBAC, and HTTPS, with no data leaked in logs.
6. Notion EPG review log records the commit ID, decision, and reviewer, and the GitHub commit references the story ID.
