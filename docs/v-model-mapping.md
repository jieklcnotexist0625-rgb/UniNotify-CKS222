# Task 3: Symmetrical Verification and Validation (V-Model Design)
**Author:** Chiew Yee Fan (Member C, Verification and Validation Engineer)  
**Audited Company:** Vialing - SkyCMS (Cyberjaya, Selangor)  
**Comparison Project:** CCA103 Systems Analysis and Design (Semester II, 2025/2026, Group 36) - UniNotify: Assignment and Deadline Reminder System

## 3.1 V-Model Symmetrical Mapping (Vialing: Student Records and Payment Data)
SkyCMS handles sensitive campus data such as student admissions, academic records, and FPX fee payments. Leaving testing until the end of development is risky because any defect can corrupt student accounts or cause billing errors.

A symmetrical V-Model connects each constructive phase on the left to a matching analytical testing phase on the right through parallel test engineering. Test plans and checks are written at the same time as requirements and design documents rather than after coding. Catching bugs early is critical because fixing a defect costs 1 time in requirements, 10 to 15 times in coding, and 100 to 1000 times in live production.

| Constructive Phase (Left) | SkyCMS Focus                                                   | Analytical Phase (Right) | Test Document Prepared         |
| :------------------------ | :------------------------------------------------------------- | :----------------------- | :----------------------------- |
| Requirements Analysis     | Student privacy rules, role permissions, and FPX payment needs | Acceptance Testing (UAT) | Acceptance Test Plan           |
| System Design             | End-to-end payment states, security controls, and audit logs   | System Testing           | System Test Plan               |
| Architectural Design      | Module boundaries, database setup, and FPX gateway APIs        | Integration Testing      | Integration Test Specification |
| Module / Detailed Design  | Input validators, encryption helpers, and database queries     | Unit Testing             | Unit Test Cases                |

## 3.2 Quality Attribute, Technical Constraint, and Verification vs. Validation
- **Quality Attribute (99.99% uptime):** Chosen internally so SkyCMS stays available for admissions, student records, and FPX fee payments during critical semester periods. It is verified through failover, redundancy, and stress tests before release, and validated through UAT and live uptime monitoring.
- **Technical Constraint (PDPA-compliant local data storage):** Mandated externally so Malaysian student and payment records stay secure and stored locally under PDPA rules. It is verified by checking database schemas, access controls, encryption, and local hosting settings, and validated through compliance reviews and stakeholder sign-off.
- **Verification vs. Validation:** Verification consists of activities checking whether the system is built right against written specs, including reviews, inspections, static analysis, and unit tests. Validation consists of outcomes proving the right system was built for real users, including UAT and stakeholder sign-off.

## 3.3 Comparison with UniNotify (CCA103)
Only Lim Chin Jiek and Gabriel Gan built the original CCA103 UniNotify project, while Chiew Yee Fan contributes through the CKS222 audit and expansion.
- **Module A (User Management):** UniNotify tested registration, login, password hashing, and RBAC mainly at module level after coding. SkyCMS handles high-stakes student and fee data, so it enforces stricter pre-release security reviews and access gates.
- **Module B (Reminder and Notification):** UniNotify verified deadline alerts, email or in-app delivery, and retry handling within a coursework scope. Vialing requires stricter production reliability, audit trails, and end-to-end gate checks across campus alerts and payment workflows.
