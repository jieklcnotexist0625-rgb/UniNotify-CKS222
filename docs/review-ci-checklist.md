# Code Review and Continuous Integration (CI) Checklist

## 1. Pre-Review & Pull Request Checklist (SPEM Task T1)
- [ ] Branch follows naming convention (docs/... /, evidence/... /, or chore/... /).
- [ ] Commit messages follow conventional format and use the author's verified USM email.
- [ ] Review Package (WP1) includes committed diff, linked User Story ID and Given-When-Then (GWT) acceptance criteria.
- [ ] At least one non-author reviewer is assigned before merging into main.

## 2. Static Analysis & Quality Gate Checklist (SPEM Task T2)
- [ ] Build is reproducible from committed source.
- [ ] Static analysis ruleset executed, all findings classified as true positive, false positive or accepted risk.
- [ ] Zero blocking security, data integrity or payment-flow defects remain in WP2.
- [ ] Review Decision Record (WP3) logged with status (Accept, Rework, or Reject), owner and due date.

## 3. Continuous Integration (CI) & XP Alignment Checklist
- [ ] Changes are integrated frequently into mainline rather than held until end-of-semester.
- [ ] Automated build, lint, static analysis and unit tests pass before merge.
- [ ] Pair programming / peer review feedback addressed via comments rather than direct overwriting of another member's work.
