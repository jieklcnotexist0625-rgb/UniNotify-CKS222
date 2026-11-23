# Task 4: Lean Waste Auditing and XP Practice Alignment

## Lean Waste Audit

| # | Lean Waste | Case-Specific Example (Vialing / UniNotify) | Evidence Basis |
|---|---|---|---|
| W1 | Waiting | Finance waits for the academic office to confirm enrolment eligibility before reconciling fee balances; Vialing reports reconciliation delays between academic and finance offices. | Vialing (n.d.-a) |
| W2 | Defects | The same student record is re-entered in admissions, registry and faculty systems, creating mismatched data and rework. | Vialing (n.d.-a) |
| W3 | Extra processes | High-stakes operations rely on offline spreadsheets and manual guideline recall rather than automated validation; MQA audit trails are assembled by hand. | Vialing (n.d.-a) |
| W4 | Handoffs (motion) / task switching | In UniNotify, four modules were built independently and integrated only in Iteration 4; coordination errors and late integration rework arose at the handoff. | Group 36 (2026a, 2026b) |

## Remedies and Expected Process Improvement

| Waste | Specific Remedy | Expected Improvement |
|---|---|---|
| W1 Waiting | Trigger reconciliation automatically when enrolment status changes; use a shared status event instead of waiting for a monthly spreadsheet. | Shorter reconciliation cycle; supports the reported 25–40% collection-turnaround improvement (Vialing, n.d.-a). |
| W2 Defects | Single source of truth for student records with referential integrity, uniqueness constraints and duplicate checks. | Fewer duplicate records and fewer manual corrections. |
| W3 Extra processes | Encode institutional rules as automated validation and generate MQA logs from the transaction record; retire spreadsheet copies. | Automated compliance evidence and fewer version conflicts. |
| W4 Handoffs / task switching | Continuous integration with automated build triggers so each module is integrated on every commit instead of once at Weeks 10–13. | Earlier detection of interface errors and less integration rework. |

## Extreme Programming (XP) Practices

### Pair Programming
Two developers share one workstation: the driver writes code while the navigator reviews each line as it is written. For this group, pair programming transfers CCA103 domain knowledge from the two experienced members to the three new members and catches duplicate record handling defects (W2) early.

### Test-First Programming and TDD
Test-first programming inverts the usual order: write a failing test first, implement the minimum code to pass, then refactor. For US-1, Scenario 1B ("no reminder for complete applications") is written before implementation, replacing CCA103's end-loaded testing in Weeks 14–15 with immediate feedback and supplying unit-test evidence for the V-Model.

### Continuous Integration (Planned Adoption)
Continuous integration requires every member to merge into a shared mainline frequently with automated build, lint, static analysis, and unit test checks blocking red builds. This directly removes end-of-semester integration handoffs (W4). (Status: Planned adoption for automated CI pipeline; branch and Pull Request review gates are currently active in this repository).
