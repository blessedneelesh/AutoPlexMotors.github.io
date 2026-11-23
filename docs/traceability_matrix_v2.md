# Traceability Matrix

This matrix traces each of the 32 incremental user stories (Stories 1 to 31, plus Story 13.1) in [incremental_user_stories.md](incremental_user_stories.md) forward to the requirements in [software_requirements_specification.md](software_requirements_specification.md), the design diagrams that model them, and the test cases that verify them. It also traces each requirement back to its story.

**How to read it**

- **Requirements:** three or more consecutive IDs are shown as a range, for example `FR-CUS-01 to FR-CUS-07`. A requirement may trace to more than one story, so it may appear in more than one row.
- **Design:** short codes for diagrams in the `artifacts` folder. The [Design Artifacts](#design-artifacts) table links each code to its image.
- **Test cases:** `TC-<story>-<n>` is test case *n* for that story. The first test cases are the story's acceptance criteria, in order. Any after those are **derived** test cases, added for requirements that no acceptance criterion covers. `TC-R-<n>` tests a rule that applies to every story. The [Test Case Catalog](#test-case-catalog) describes each one.

## Story-to-Requirement Traceability

| Story | Title | Functional Requirements | Non-functional Requirements | Design | Test Cases |
|---|---|---|---|---|---|
| S1 | Manage customers | FR-CUS-01 to FR-CUS-07 | NFR-MNT-02 | DCD-1, DTD-1, ERD | TC-01-01 to TC-01-07 |
| S2 | Manage employees | FR-EMP-01 to FR-EMP-06 | - | DCD-2, DTD-2, ERD | TC-02-01 to TC-02-06 |
| S3 | Manage vendors | FR-VEN-01 to FR-VEN-05 | NFR-MNT-02 | DCD-3, DTD-3, ERD | TC-03-01 to TC-03-05 |
| S4 | Add a vehicle to inventory | FR-VEH-01 to FR-VEH-05 | NFR-INT-05 | UC-PV, AD-PV, DCD-4, DTD-4, SM-VEH, ERD | TC-04-01 to TC-04-07 |
| S5 | Browse vehicle inventory | FR-INV-01 to FR-INV-04 | NFR-USE-01, NFR-USE-02 | DCD-5, DTD-5, ERD | TC-05-01 to TC-05-04 |
| S6 | Manage parts inventory | FR-PRT-01 to FR-PRT-06 | NFR-INT-05 | DCD-6, DTD-6, ERD | TC-06-01 to TC-06-07 |
| S7 | Banks and bank accounts | FR-BNK-01 to FR-BNK-06 | NFR-SEC-01 | DCD-7, ERD | TC-07-01 to TC-07-07 |
| S8 | Internal transaction ledger | FR-LED-01 to FR-LED-07 | NFR-INT-06, NFR-AUD-02, NFR-ACC-02, NFR-MNT-03 | DCD-8, DTD-8, SD-8, ERD | TC-08-01 to TC-08-08 |
| S9 | Simulated statement lines | FR-STM-01 to FR-STM-05 | NFR-INT-03 | DCD-9, DTD-9, SD-9, ERD | TC-09-01 to TC-09-06 |
| S10 | Transfer between bank accounts | FR-TRF-01 to FR-TRF-05 | NFR-INT-06 | DCD-10, DTD-10, SD-10, ERD | TC-10-01 to TC-10-06 |
| S11 | Create a draft sales invoice | FR-SIN-01 to FR-SIN-08 | NFR-INT-05 | UC-SI, AD-SI, DCD-11, DTD-11, SM-INV, ERD | TC-11-01 to TC-11-09 |
| S12 | Post a sales invoice | FR-POS-01 to FR-POS-06 | NFR-INT-01 | UC-SI, AD-SI, DCD-12, DTD-12, SM-INV, SM-VEH, ERD | TC-12-01 to TC-12-06 |
| S13 | Cancel and browse sales invoices | FR-SIL-01 to FR-SIL-04 | NFR-AUD-01, NFR-USE-01 | DCD-13, DTD-13, SM-INV, SM-VEH, ERD | TC-13-01 to TC-13-05 |
| S13.1 | View a customer's sales invoices | FR-CSI-01 to FR-CSI-05 | NFR-USE-03 | DCD-13.1, DTD-13.1, ERD | TC-13.1-01 to TC-13.1-06 |
| S14 | Payment condition, receipt, and AR | FR-PAY-01 to FR-PAY-09 | NFR-INT-02 | AD-SI, DTD-14, SD-14, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-01 to TC-14-08 |
| S15 | Record a later customer payment | FR-RCP-01 to FR-RCP-06 | NFR-INT-02 | DCD-15, DTD-15, SD-15, OD-14-15, SM-INV, ERD | TC-15-01 to TC-15-10 |
| S16 | Record a receipt not linked to AR | FR-RCT-01 to FR-RCT-05 | - | DCD-16, DTD-16, SD-16, ERD | TC-16-01 to TC-16-06 |
| S17 | AR list and aging | FR-ARL-01 to FR-ARL-04 | NFR-USE-01 | DCD-17, DTD-17, SD-17, ERD | TC-17-01 to TC-17-04 |
| S18 | Customer balances | FR-CUS-08, FR-CUS-09 | - | DCD-18, DTD-18, SD-18, ERD | TC-18-01 to TC-18-04 |
| S19 | Vehicle purchase payment condition and AP | FR-VPC-01 to FR-VPC-07 | NFR-INT-02, NFR-INT-06 | UC-PV, AD-PV, ERD | TC-19-01 to TC-19-08 |
| S20 | Record a later vendor payment | FR-VEN-06, FR-APB-01 to FR-APB-04 | NFR-INT-02, NFR-INT-06 | ERD | TC-20-01 to TC-20-09 |
| S21 | Record a payment not linked to AP | FR-BPY-01 to FR-BPY-06 | NFR-INT-06 | ERD | TC-21-01 to TC-21-05 |
| S22 | AP list and aging | FR-VEN-06, FR-APB-05, FR-APB-06 | - | ERD | TC-22-01 to TC-22-04 |
| S23 | Reverse a banking transaction | FR-SIL-03, FR-REV-01 to FR-REV-05 | NFR-INT-04, NFR-AUD-01 | ERD | TC-23-01 to TC-23-07 |
| S24 | Statement-only adjustment | FR-ADJ-01 to FR-ADJ-04 | NFR-INT-05 | ERD | TC-24-01 to TC-24-06 |
| S25 | Add and post an adjustment to books | FR-ADJ-05, FR-ADJ-06 | NFR-INT-04 | ERD | TC-25-01 to TC-25-05 |
| S26 | Revenue | FR-REVN-01 to FR-REVN-04 | - | **None yet** | TC-26-01 to TC-26-05 |
| S27 | Cost of goods sold | FR-COGS-01 to FR-COGS-03 | - | **None yet** | TC-27-01 to TC-27-04 |
| S28 | Operating expenses | FR-OPEX-01 to FR-OPEX-04 | - | **None yet** | TC-28-01 to TC-28-05 |
| S29 | Profit & Loss report | FR-PNL-01 to FR-PNL-03 | NFR-ACC-01 | **None yet** | TC-29-01 to TC-29-04 |
| S30 | Compare periods | FR-PNL-04, FR-PNL-05 | NFR-USE-02 | **None yet** | TC-30-01 to TC-30-04 |
| S31 | Drill-down and export | FR-PNL-06 to FR-PNL-08 | NFR-AUD-03, NFR-SEC-02, NFR-ACC-03 | **None yet** | TC-31-01 to TC-31-05 |

## Requirements Not Tied to One Story

| Source | Requirements | Test Cases |
|---|---|---|
| Rules that apply to every story | NFR-ALL-01 to NFR-ALL-05, NFR-ALL-07, NFR-ALL-08 | TC-07-07, TC-08-06, TC-09-01, TC-10-06, TC-12-02, TC-12-06, TC-13-05, TC-14-07, TC-14-08, TC-15-03, TC-15-06, TC-16-01, TC-16-04, TC-19-06, TC-19-07, TC-20-03, TC-21-01, TC-21-03, TC-23-05, TC-25-01, TC-25-05, TC-R-01, TC-R-02, TC-R-03, TC-R-04 |
| Introduction to the user stories | NFR-ALL-06 | TC-R-05 |
| Data model notes | NFR-MNT-01 | TC-R-06 |

## Requirement-to-Story Traceability

| Requirement | Feature | Story | Design | Test Cases |
|---|---|---|---|---|
| FR-CUS-01 | Customer Management | S1 | DCD-1, DTD-1, ERD | TC-01-06 |
| FR-CUS-02 | Customer Management | S1 | DCD-1, DTD-1, ERD | TC-01-01 |
| FR-CUS-03 | Customer Management | S1 | DCD-1, DTD-1, ERD | TC-01-02 |
| FR-CUS-04 | Customer Management | S1 | DCD-1, DTD-1, ERD | TC-01-03, TC-01-04 |
| FR-CUS-05 | Customer Management | S1 | DCD-1, DTD-1, ERD | TC-01-07 |
| FR-CUS-06 | Customer Management | S1 | DCD-1, DTD-1, ERD | TC-01-04 |
| FR-CUS-07 | Customer Management | S1 | DCD-1, DTD-1, ERD | TC-01-05 |
| FR-CUS-08 | Customer Management | S18 | DCD-18, DTD-18, SD-18, ERD | TC-18-01, TC-18-02 |
| FR-CUS-09 | Customer Management | S18 | DCD-18, DTD-18, SD-18, ERD | TC-18-03, TC-18-04 |
| FR-EMP-01 | Employee Management | S2 | DCD-2, DTD-2, ERD | TC-02-05 |
| FR-EMP-02 | Employee Management | S2 | DCD-2, DTD-2, ERD | TC-02-06 |
| FR-EMP-03 | Employee Management | S2 | DCD-2, DTD-2, ERD | TC-02-01 |
| FR-EMP-04 | Employee Management | S2 | DCD-2, DTD-2, ERD | TC-02-02 |
| FR-EMP-05 | Employee Management | S2 | DCD-2, DTD-2, ERD | TC-02-03 |
| FR-EMP-06 | Employee Management | S2 | DCD-2, DTD-2, ERD | TC-02-04 |
| FR-VEN-01 | Vendor Management | S3 | DCD-3, DTD-3, ERD | TC-03-05 |
| FR-VEN-02 | Vendor Management | S3 | DCD-3, DTD-3, ERD | TC-03-01 |
| FR-VEN-03 | Vendor Management | S3 | DCD-3, DTD-3, ERD | TC-03-02 |
| FR-VEN-04 | Vendor Management | S3 | DCD-3, DTD-3, ERD | TC-03-03 |
| FR-VEN-05 | Vendor Management | S3 | DCD-3, DTD-3, ERD | TC-03-04 |
| FR-VEN-06 | Vendor Management | S20, S22 | ERD | TC-20-05, TC-22-04 |
| FR-VEH-01 | Vehicle Purchase Form | S4 | UC-PV, AD-PV, DCD-4, DTD-4, SM-VEH, ERD | TC-04-07 |
| FR-VEH-02 | Vehicle Purchase Form | S4 | UC-PV, AD-PV, DCD-4, DTD-4, SM-VEH, ERD | TC-04-01, TC-04-02 |
| FR-VEH-03 | Vehicle Purchase Form | S4 | UC-PV, AD-PV, DCD-4, DTD-4, SM-VEH, ERD | TC-04-03, TC-04-04 |
| FR-VEH-04 | Vehicle Purchase Form | S4 | UC-PV, AD-PV, DCD-4, DTD-4, SM-VEH, ERD | TC-04-05 |
| FR-VEH-05 | Vehicle Purchase Form | S4 | UC-PV, AD-PV, DCD-4, DTD-4, SM-VEH, ERD | TC-04-06 |
| FR-INV-01 | Vehicle Inventory List | S5 | DCD-5, DTD-5, ERD | TC-05-01 |
| FR-INV-02 | Vehicle Inventory List | S5 | DCD-5, DTD-5, ERD | TC-05-03 |
| FR-INV-03 | Vehicle Inventory List | S5 | DCD-5, DTD-5, ERD | TC-05-02 |
| FR-INV-04 | Vehicle Inventory List | S5 | DCD-5, DTD-5, ERD | TC-05-04 |
| FR-PRT-01 | Parts Inventory Form and List | S6 | DCD-6, DTD-6, ERD | TC-06-06 |
| FR-PRT-02 | Parts Inventory Form and List | S6 | DCD-6, DTD-6, ERD | TC-06-01, TC-06-02 |
| FR-PRT-03 | Parts Inventory Form and List | S6 | DCD-6, DTD-6, ERD | TC-06-03 |
| FR-PRT-04 | Parts Inventory Form and List | S6 | DCD-6, DTD-6, ERD | TC-06-04 |
| FR-PRT-05 | Parts Inventory Form and List | S6 | DCD-6, DTD-6, ERD | TC-06-05 |
| FR-PRT-06 | Parts Inventory Form and List | S6 | DCD-6, DTD-6, ERD | TC-06-07 |
| FR-BNK-01 | Bank and Bank Account Form | S7 | DCD-7, ERD | TC-07-01 |
| FR-BNK-02 | Bank and Bank Account Form | S7 | DCD-7, ERD | TC-07-01, TC-07-02 |
| FR-BNK-03 | Bank and Bank Account Form | S7 | DCD-7, ERD | TC-07-03, TC-07-04 |
| FR-BNK-04 | Bank and Bank Account Form | S7 | DCD-7, ERD | TC-07-04, TC-07-05 |
| FR-BNK-05 | Bank and Bank Account Form | S7 | DCD-7, ERD | TC-07-06 |
| FR-BNK-06 | Bank and Bank Account Form | S7 | DCD-7, ERD | TC-07-07 |
| FR-LED-01 | Internal Transaction Ledger | S8 | DCD-8, DTD-8, SD-8, ERD | TC-08-08 |
| FR-LED-02 | Internal Transaction Ledger | S8 | DCD-8, DTD-8, SD-8, ERD | TC-08-01 |
| FR-LED-03 | Internal Transaction Ledger | S8 | DCD-8, DTD-8, SD-8, ERD | TC-08-02 |
| FR-LED-04 | Internal Transaction Ledger | S8 | DCD-8, DTD-8, SD-8, ERD | TC-08-03 |
| FR-LED-05 | Internal Transaction Ledger | S8 | DCD-8, DTD-8, SD-8, ERD | TC-08-04 |
| FR-LED-06 | Internal Transaction Ledger | S8 | DCD-8, DTD-8, SD-8, ERD | TC-08-05, TC-08-06 |
| FR-LED-07 | Internal Transaction Ledger | S8 | DCD-8, DTD-8, SD-8, ERD | TC-08-07 |
| FR-STM-01 | Bank Statement | S9 | DCD-9, DTD-9, SD-9, ERD | TC-09-01 |
| FR-STM-02 | Bank Statement | S9 | DCD-9, DTD-9, SD-9, ERD | TC-09-02 |
| FR-STM-03 | Bank Statement | S9 | DCD-9, DTD-9, SD-9, ERD | TC-09-03 |
| FR-STM-04 | Bank Statement | S9 | DCD-9, DTD-9, SD-9, ERD | TC-09-04 |
| FR-STM-05 | Bank Statement | S9 | DCD-9, DTD-9, SD-9, ERD | TC-09-06 |
| FR-TRF-01 | Bank Transfer Form | S10 | DCD-10, DTD-10, SD-10, ERD | TC-10-01 |
| FR-TRF-02 | Bank Transfer Form | S10 | DCD-10, DTD-10, SD-10, ERD | TC-10-02 |
| FR-TRF-03 | Bank Transfer Form | S10 | DCD-10, DTD-10, SD-10, ERD | TC-10-03, TC-10-04 |
| FR-TRF-04 | Bank Transfer Form | S10 | DCD-10, DTD-10, SD-10, ERD | TC-10-06 |
| FR-TRF-05 | Bank Transfer Form | S10 | DCD-10, DTD-10, SD-10, ERD | TC-10-05 |
| FR-SIN-01 | Sales Invoice Form | S11 | UC-SI, AD-SI, DCD-11, DTD-11, SM-INV, ERD | TC-11-01 |
| FR-SIN-02 | Sales Invoice Form | S11 | UC-SI, AD-SI, DCD-11, DTD-11, SM-INV, ERD | TC-11-07 |
| FR-SIN-03 | Sales Invoice Form | S11 | UC-SI, AD-SI, DCD-11, DTD-11, SM-INV, ERD | TC-11-08 |
| FR-SIN-04 | Sales Invoice Form | S11 | UC-SI, AD-SI, DCD-11, DTD-11, SM-INV, ERD | TC-11-02 |
| FR-SIN-05 | Sales Invoice Form | S11 | UC-SI, AD-SI, DCD-11, DTD-11, SM-INV, ERD | TC-11-03, TC-11-04 |
| FR-SIN-06 | Sales Invoice Form | S11 | UC-SI, AD-SI, DCD-11, DTD-11, SM-INV, ERD | TC-11-09 |
| FR-SIN-07 | Sales Invoice Form | S11 | UC-SI, AD-SI, DCD-11, DTD-11, SM-INV, ERD | TC-11-05 |
| FR-SIN-08 | Sales Invoice Form | S11 | UC-SI, AD-SI, DCD-11, DTD-11, SM-INV, ERD | TC-11-06 |
| FR-POS-01 | Sales Invoice Posting | S12 | UC-SI, AD-SI, DCD-12, DTD-12, SM-INV, SM-VEH, ERD | TC-12-01 |
| FR-POS-02 | Sales Invoice Posting | S12 | UC-SI, AD-SI, DCD-12, DTD-12, SM-INV, SM-VEH, ERD | TC-12-02 |
| FR-POS-03 | Sales Invoice Posting | S12 | UC-SI, AD-SI, DCD-12, DTD-12, SM-INV, SM-VEH, ERD | TC-12-03 |
| FR-POS-04 | Sales Invoice Posting | S12 | UC-SI, AD-SI, DCD-12, DTD-12, SM-INV, SM-VEH, ERD | TC-12-04 |
| FR-POS-05 | Sales Invoice Posting | S12 | UC-SI, AD-SI, DCD-12, DTD-12, SM-INV, SM-VEH, ERD | TC-12-05 |
| FR-POS-06 | Sales Invoice Posting | S12 | UC-SI, AD-SI, DCD-12, DTD-12, SM-INV, SM-VEH, ERD | TC-12-06 |
| FR-SIL-01 | Sales Invoice List and Cancellation | S13 | DCD-13, DTD-13, SM-INV, SM-VEH, ERD | TC-13-04 |
| FR-SIL-02 | Sales Invoice List and Cancellation | S13 | DCD-13, DTD-13, SM-INV, SM-VEH, ERD | TC-13-03 |
| FR-SIL-03 | Sales Invoice List and Cancellation | S13, S23 | DCD-13, DTD-13, SM-INV, SM-VEH, ERD | TC-13-02, TC-23-04 |
| FR-SIL-04 | Sales Invoice List and Cancellation | S13 | DCD-13, DTD-13, SM-INV, SM-VEH, ERD | TC-13-01, TC-13-05 |
| FR-CSI-01 | Customer Sales Invoices | S13.1 | DCD-13.1, DTD-13.1, ERD | TC-13.1-01 |
| FR-CSI-02 | Customer Sales Invoices | S13.1 | DCD-13.1, DTD-13.1, ERD | TC-13.1-02, TC-13.1-05 |
| FR-CSI-03 | Customer Sales Invoices | S13.1 | DCD-13.1, DTD-13.1, ERD | TC-13.1-03 |
| FR-CSI-04 | Customer Sales Invoices | S13.1 | DCD-13.1, DTD-13.1, ERD | TC-13.1-04 |
| FR-CSI-05 | Customer Sales Invoices | S13.1 | DCD-13.1, DTD-13.1, ERD | TC-13.1-06 |
| FR-PAY-01 | Customer Payment Condition | S14 | AD-SI, DTD-14, SD-14, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-01, TC-14-02, TC-14-03 |
| FR-PAY-02 | Customer Payment Condition | S14 | AD-SI, DTD-14, SD-14, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-06 |
| FR-PAY-03 | Customer Payment Condition | S14 | AD-SI, DTD-14, SD-14, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-05 |
| FR-PAY-04 | Customer Payment Condition | S14 | AD-SI, DTD-14, SD-14, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-01 |
| FR-PAY-05 | Customer Payment Condition | S14 | AD-SI, DTD-14, SD-14, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-02 |
| FR-PAY-06 | Customer Payment Condition | S14 | AD-SI, DTD-14, SD-14, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-03 |
| FR-PAY-07 | Customer Payment Condition | S14 | AD-SI, DTD-14, SD-14, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-04 |
| FR-PAY-08 | Customer Payment Condition | S14 | AD-SI, DTD-14, SD-14, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-07 |
| FR-PAY-09 | Customer Payment Condition | S14 | AD-SI, DTD-14, SD-14, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-08 |
| FR-RCP-01 | Record Customer Payment Form | S15 | DCD-15, DTD-15, SD-15, OD-14-15, SM-INV, ERD | TC-15-09 |
| FR-RCP-02 | Record Customer Payment Form | S15 | DCD-15, DTD-15, SD-15, OD-14-15, SM-INV, ERD | TC-15-01, TC-15-02 |
| FR-RCP-03 | Record Customer Payment Form | S15 | DCD-15, DTD-15, SD-15, OD-14-15, SM-INV, ERD | TC-15-03, TC-15-08 |
| FR-RCP-04 | Record Customer Payment Form | S15 | DCD-15, DTD-15, SD-15, OD-14-15, SM-INV, ERD | TC-15-04, TC-15-05 |
| FR-RCP-05 | Record Customer Payment Form | S15 | DCD-15, DTD-15, SD-15, OD-14-15, SM-INV, ERD | TC-15-06, TC-15-07 |
| FR-RCP-06 | Record Customer Payment Form | S15 | DCD-15, DTD-15, SD-15, OD-14-15, SM-INV, ERD | TC-15-10 |
| FR-RCT-01 | Other Receipt Form | S16 | DCD-16, DTD-16, SD-16, ERD | TC-16-03 |
| FR-RCT-02 | Other Receipt Form | S16 | DCD-16, DTD-16, SD-16, ERD | TC-16-01, TC-16-02, TC-16-05 |
| FR-RCT-03 | Other Receipt Form | S16 | DCD-16, DTD-16, SD-16, ERD | TC-16-03 |
| FR-RCT-04 | Other Receipt Form | S16 | DCD-16, DTD-16, SD-16, ERD | TC-16-04 |
| FR-RCT-05 | Other Receipt Form | S16 | DCD-16, DTD-16, SD-16, ERD | TC-16-06 |
| FR-ARL-01 | Accounts Receivable List and Aging | S17 | DCD-17, DTD-17, SD-17, ERD | TC-17-01 |
| FR-ARL-02 | Accounts Receivable List and Aging | S17 | DCD-17, DTD-17, SD-17, ERD | TC-17-02 |
| FR-ARL-03 | Accounts Receivable List and Aging | S17 | DCD-17, DTD-17, SD-17, ERD | TC-17-03 |
| FR-ARL-04 | Accounts Receivable List and Aging | S17 | DCD-17, DTD-17, SD-17, ERD | TC-17-04 |
| FR-VPC-01 | Vehicle Purchase Payment Condition | S19 | UC-PV, AD-PV, ERD | TC-19-01, TC-19-02 |
| FR-VPC-02 | Vehicle Purchase Payment Condition | S19 | UC-PV, AD-PV, ERD | TC-19-04 |
| FR-VPC-03 | Vehicle Purchase Payment Condition | S19 | UC-PV, AD-PV, ERD | TC-19-08 |
| FR-VPC-04 | Vehicle Purchase Payment Condition | S19 | UC-PV, AD-PV, ERD | TC-19-01, TC-19-02, TC-19-03 |
| FR-VPC-05 | Vehicle Purchase Payment Condition | S19 | UC-PV, AD-PV, ERD | TC-19-06 |
| FR-VPC-06 | Vehicle Purchase Payment Condition | S19 | UC-PV, AD-PV, ERD | TC-19-05 |
| FR-VPC-07 | Vehicle Purchase Payment Condition | S19 | UC-PV, AD-PV, ERD | TC-19-07 |
| FR-APB-01 | Vendor Payment Form and AP List | S20 | ERD | TC-20-08 |
| FR-APB-02 | Vendor Payment Form and AP List | S20 | ERD | TC-20-01, TC-20-02, TC-20-06 |
| FR-APB-03 | Vendor Payment Form and AP List | S20 | ERD | TC-20-03, TC-20-04 |
| FR-APB-04 | Vendor Payment Form and AP List | S20 | ERD | TC-20-07, TC-20-09 |
| FR-APB-05 | Vendor Payment Form and AP List | S22 | ERD | TC-22-01 |
| FR-APB-06 | Vendor Payment Form and AP List | S22 | ERD | TC-22-02, TC-22-03 |
| FR-BPY-01 | Other Payment Form | S21 | ERD | TC-21-01 |
| FR-BPY-02 | Other Payment Form | S21 | ERD | TC-21-01 |
| FR-BPY-03 | Other Payment Form | S21 | ERD | TC-21-02 |
| FR-BPY-04 | Other Payment Form | S21 | ERD | TC-21-03 |
| FR-BPY-05 | Other Payment Form | S21 | ERD | TC-21-04 |
| FR-BPY-06 | Other Payment Form | S21 | ERD | TC-21-05 |
| FR-REV-01 | Reverse Transaction Form | S23 | ERD | TC-23-01 |
| FR-REV-02 | Reverse Transaction Form | S23 | ERD | TC-23-02, TC-23-03 |
| FR-REV-03 | Reverse Transaction Form | S23 | ERD | TC-23-04 |
| FR-REV-04 | Reverse Transaction Form | S23 | ERD | TC-23-05, TC-23-06 |
| FR-REV-05 | Reverse Transaction Form | S23 | ERD | TC-23-07 |
| FR-ADJ-01 | Statement Adjustment Form | S24 | ERD | TC-24-06 |
| FR-ADJ-02 | Statement Adjustment Form | S24 | ERD | TC-24-01, TC-24-02 |
| FR-ADJ-03 | Statement Adjustment Form | S24 | ERD | TC-24-03 |
| FR-ADJ-04 | Statement Adjustment Form | S24 | ERD | TC-24-04, TC-24-05 |
| FR-ADJ-05 | Statement Adjustment Form | S25 | ERD | TC-25-01, TC-25-02, TC-25-04, TC-25-05 |
| FR-ADJ-06 | Statement Adjustment Form | S25 | ERD | TC-25-03 |
| FR-REVN-01 | Revenue Report Section | S26 | **None yet** | TC-26-05 |
| FR-REVN-02 | Revenue Report Section | S26 | **None yet** | TC-26-01 |
| FR-REVN-03 | Revenue Report Section | S26 | **None yet** | TC-26-02 |
| FR-REVN-04 | Revenue Report Section | S26 | **None yet** | TC-26-03, TC-26-04 |
| FR-COGS-01 | Cost of Goods Sold Report Section | S27 | **None yet** | TC-27-01 |
| FR-COGS-02 | Cost of Goods Sold Report Section | S27 | **None yet** | TC-27-04 |
| FR-COGS-03 | Cost of Goods Sold Report Section | S27 | **None yet** | TC-27-02, TC-27-03 |
| FR-OPEX-01 | Operating Expenses Report Section | S28 | **None yet** | TC-28-01 |
| FR-OPEX-02 | Operating Expenses Report Section | S28 | **None yet** | TC-28-02 |
| FR-OPEX-03 | Operating Expenses Report Section | S28 | **None yet** | TC-28-03 |
| FR-OPEX-04 | Operating Expenses Report Section | S28 | **None yet** | TC-28-04, TC-28-05 |
| FR-PNL-01 | Profit & Loss Report | S29 | **None yet** | TC-29-04 |
| FR-PNL-02 | Profit & Loss Report | S29 | **None yet** | TC-29-01 |
| FR-PNL-03 | Profit & Loss Report | S29 | **None yet** | TC-29-02 |
| FR-PNL-04 | Profit & Loss Report | S30 | **None yet** | TC-30-01 |
| FR-PNL-05 | Profit & Loss Report | S30 | **None yet** | TC-30-02, TC-30-03, TC-30-04 |
| FR-PNL-06 | Profit & Loss Report | S31 | **None yet** | TC-31-01 |
| FR-PNL-07 | Profit & Loss Report | S31 | **None yet** | TC-31-03, TC-31-04 |
| FR-PNL-08 | Profit & Loss Report | S31 | **None yet** | TC-31-02, TC-31-05 |
| NFR-ALL-01 | System-wide | Rules that apply to every story | - | TC-14-08, TC-19-07, TC-25-05, TC-R-01 |
| NFR-ALL-02 | System-wide | Rules that apply to every story | - | TC-08-06, TC-12-06, TC-13-05, TC-23-05 |
| NFR-ALL-03 | System-wide | Rules that apply to every story | - | TC-R-02 |
| NFR-ALL-04 | System-wide | Rules that apply to every story | - | TC-R-03 |
| NFR-ALL-05 | System-wide | Rules that apply to every story | - | TC-12-02, TC-R-04 |
| NFR-ALL-06 | System-wide | Introduction to the user stories | - | TC-R-05 |
| NFR-ALL-07 | System-wide | Rules that apply to every story | - | TC-07-07, TC-14-07, TC-15-06, TC-16-01, TC-19-06, TC-21-01 |
| NFR-ALL-08 | System-wide | Rules that apply to every story | - | TC-09-01, TC-10-06, TC-15-03, TC-16-04, TC-20-03, TC-21-03, TC-25-01 |
| NFR-INT-01 | Data integrity | S12 | UC-SI, AD-SI, DCD-12, DTD-12, SM-INV, SM-VEH, ERD | TC-12-05 |
| NFR-INT-02 | Data integrity | S14, S15, S19, S20 | UC-PV, AD-PV, AD-SI, DCD-15, DTD-14, DTD-15, SD-14, SD-15, OD-14, OD-14-15, SM-INV, SM-14, ERD | TC-14-08, TC-15-04, TC-19-07, TC-20-04 |
| NFR-INT-03 | Data integrity | S9 | DCD-9, DTD-9, SD-9, ERD | TC-09-01, TC-09-05 |
| NFR-INT-04 | Data integrity | S23, S25 | ERD | TC-23-06, TC-25-04 |
| NFR-INT-05 | Data integrity | S4, S6, S11, S24 | UC-PV, UC-SI, AD-PV, AD-SI, DCD-4, DCD-6, DCD-11, DTD-4, DTD-6, DTD-11, SM-INV, SM-VEH, ERD | TC-04-02, TC-06-01, TC-11-06, TC-24-05 |
| NFR-INT-06 | Data integrity | S8, S10, S19, S20, S21 | UC-PV, AD-PV, DCD-8, DCD-10, DTD-8, DTD-10, SD-8, SD-10, ERD | TC-08-04, TC-10-02, TC-19-06, TC-20-06, TC-21-02 |
| NFR-AUD-01 | Auditability | S13, S23 | DCD-13, DTD-13, SM-INV, SM-VEH, ERD | TC-13-03, TC-13-05, TC-23-01, TC-23-05 |
| NFR-AUD-02 | Auditability | S8 | DCD-8, DTD-8, SD-8, ERD | TC-08-02 |
| NFR-AUD-03 | Auditability | S31 | **None yet** | TC-31-01 |
| NFR-SEC-01 | Security and privacy | S7 | DCD-7, ERD | TC-07-05 |
| NFR-SEC-02 | Security and privacy | S31 | **None yet** | TC-31-05 |
| NFR-ACC-01 | Accuracy and consistency | S29 | **None yet** | TC-29-03 |
| NFR-ACC-02 | Accuracy and consistency | S8 | DCD-8, DTD-8, SD-8, ERD | TC-07-04, TC-08-03 |
| NFR-ACC-03 | Accuracy and consistency | S31 | **None yet** | TC-31-04 |
| NFR-USE-01 | Usability | S5, S13, S17 | DCD-5, DCD-13, DCD-17, DTD-5, DTD-13, DTD-17, SD-17, SM-INV, SM-VEH, ERD | TC-05-03, TC-13-04, TC-17-04 |
| NFR-USE-02 | Usability | S5, S30 | DCD-5, DTD-5, ERD | TC-05-01, TC-05-04, TC-30-02 |
| NFR-USE-03 | Usability | S13.1 | DCD-13.1, DTD-13.1, ERD | TC-13.1-02, TC-13.1-05 |
| NFR-MNT-01 | Maintainability | Data model notes | - | TC-R-06 |
| NFR-MNT-02 | Maintainability | S1, S3 | DCD-1, DCD-3, DTD-1, DTD-3, ERD | TC-01-05, TC-03-04 |
| NFR-MNT-03 | Maintainability | S8 | DCD-8, DTD-8, SD-8, ERD | TC-08-08 |

## Design Artifacts

| Code | Diagram | Stories |
|---|---|---|
| UC-PV | [Use case: Purchase Vehicle](../artifacts/useCaseDiagram/purchase%20Vehicle.png) | S4, S19 |
| UC-SI | [Use case: Create Sales Invoice](../artifacts/useCaseDiagram/Create%20Invoice.png) | S11, S12 |
| AD-PV | [Activity: Purchase Vehicle](../artifacts/activityDiagram/activityPurchaseVehicle.png) | S4, S19 |
| AD-SI | [Activity: Create Invoice](../artifacts/activityDiagram/activityCreateInvoice.png) | S11, S12, S14 |
| DCD-1 | [Domain class: Story 1](../artifacts/classDiagram/DomainClassDiagram/story1.png) | S1 |
| DCD-2 | [Domain class: Story 2](../artifacts/classDiagram/DomainClassDiagram/story2.png) | S2 |
| DCD-3 | [Domain class: Story 3](../artifacts/classDiagram/DomainClassDiagram/story3.png) | S3 |
| DCD-4 | [Domain class: Story 4](../artifacts/classDiagram/DomainClassDiagram/story4.png) | S4 |
| DCD-5 | [Domain class: Story 5](../artifacts/classDiagram/DomainClassDiagram/story5.png) | S5 |
| DCD-6 | [Domain class: Story 6](../artifacts/classDiagram/DomainClassDiagram/story6.png) | S6 |
| DCD-7 | [Domain class: Story 7](../artifacts/classDiagram/DomainClassDiagram/story7.png) | S7 |
| DCD-8 | [Domain class: Story 8](../artifacts/classDiagram/DomainClassDiagram/story8.png) | S8 |
| DCD-9 | [Domain class: Story 9](../artifacts/classDiagram/DomainClassDiagram/story9.png) | S9 |
| DCD-10 | [Domain class: Story 10](../artifacts/classDiagram/DomainClassDiagram/story10.png) | S10 |
| DCD-11 | [Domain class: Story 11](../artifacts/classDiagram/DomainClassDiagram/story11.png) | S11 |
| DCD-12 | [Domain class: Story 12](../artifacts/classDiagram/DomainClassDiagram/story12.png) | S12 |
| DCD-13 | [Domain class: Story 13](../artifacts/classDiagram/DomainClassDiagram/story13.png) | S13 |
| DCD-13.1 | [Domain class: Story 13.1](../artifacts/classDiagram/DomainClassDiagram/story13.1.png) | S13.1 |
| DCD-15 | [Domain class: Story 15](../artifacts/classDiagram/DomainClassDiagram/story15.png) | S15 |
| DCD-16 | [Domain class: Story 16](../artifacts/classDiagram/DomainClassDiagram/story16.png) | S16 |
| DCD-17 | [Domain class: Story 17](../artifacts/classDiagram/DomainClassDiagram/story17.png) | S17 |
| DCD-18 | [Domain class: Story 18](../artifacts/classDiagram/DomainClassDiagram/story18.png) | S18 |
| DTD-1 | [Detail class: Story 1](../artifacts/classDiagram/DetailClassDiagram/story1.png) | S1 |
| DTD-2 | [Detail class: Story 2](../artifacts/classDiagram/DetailClassDiagram/story2.png) | S2 |
| DTD-3 | [Detail class: Story 3](../artifacts/classDiagram/DetailClassDiagram/story3.png) | S3 |
| DTD-4 | [Detail class: Story 4](../artifacts/classDiagram/DetailClassDiagram/story4.png) | S4 |
| DTD-5 | [Detail class: Story 5](../artifacts/classDiagram/DetailClassDiagram/story5%20with%20calculateProfit%20method.png) | S5 |
| DTD-6 | [Detail class: Story 6](../artifacts/classDiagram/DetailClassDiagram/Story6%20with%20private%20service%20methods.png) | S6 |
| DTD-8 | [Detail class: Story 8](../artifacts/classDiagram/DetailClassDiagram/story8.png) | S8 |
| DTD-9 | [Detail class: Story 9](../artifacts/classDiagram/DetailClassDiagram/story9.png) | S9 |
| DTD-10 | [Detail class: Story 10](../artifacts/classDiagram/DetailClassDiagram/story10.png) | S10 |
| DTD-11 | [Detail class: Story 11](../artifacts/classDiagram/DetailClassDiagram/story11.png) | S11 |
| DTD-12 | [Detail class: Story 12](../artifacts/classDiagram/DetailClassDiagram/story12.png) | S12 |
| DTD-13 | [Detail class: Story 13](../artifacts/classDiagram/DetailClassDiagram/story13.png) | S13 |
| DTD-13.1 | [Detail class: Story 13.1](../artifacts/classDiagram/DetailClassDiagram/story13.1.png) | S13.1 |
| DTD-14 | [Detail class: Story 14](../artifacts/classDiagram/DetailClassDiagram/story14.png) | S14 |
| DTD-15 | [Detail class: Story 15](../artifacts/classDiagram/DetailClassDiagram/story15.png) | S15 |
| DTD-16 | [Detail class: Story 16](../artifacts/classDiagram/DetailClassDiagram/story16.png) | S16 |
| DTD-17 | [Detail class: Story 17](../artifacts/classDiagram/DetailClassDiagram/story17.png) | S17 |
| DTD-18 | [Detail class: Story 18](../artifacts/classDiagram/DetailClassDiagram/story18.png) | S18 |
| SD-8 | [Sequence: Story 8](../artifacts/sequenceDiagram/story8.png) | S8 |
| SD-9 | [Sequence: Story 9](../artifacts/sequenceDiagram/story9.png) | S9 |
| SD-10 | [Sequence: Story 10](../artifacts/sequenceDiagram/story10.png) | S10 |
| SD-14 | [Sequence: Story 14](../artifacts/sequenceDiagram/story14.png) | S14 |
| SD-15 | [Sequence: Story 15](../artifacts/sequenceDiagram/story15.png) | S15 |
| SD-16 | [Sequence: Story 16](../artifacts/sequenceDiagram/story16.png) | S16 |
| SD-17 | [Sequence: Story 17](../artifacts/sequenceDiagram/story17.png) | S17 |
| SD-18 | [Sequence: Story 18](../artifacts/sequenceDiagram/story18.png) | S18 |
| OD-14 | [Object: Story 14](../artifacts/objectDiagram/AutoPlex_Story14_Object_Diagram.png) | S14 |
| OD-14-15 | [Object: Stories 14–15 multiple payments](../artifacts/objectDiagram/AutoPlex_Story14_15_Multiple_Payments_Object_Diagram.png) | S14, S15 |
| SM-INV | [State machine: Sales Invoice and AR Invoice (Stories 11–15)](../artifacts/stateMachineDiagram/AutoPlex_Story14_15_State_Machine_Diagram.png) | S11, S12, S13, S14, S15 |
| SM-VEH | [State machine: Vehicle](../artifacts/stateMachineDiagram/Vehicle.png) | S4, S12, S13 |
| SM-14 | [State machine: Story 14](../artifacts/stateMachineDiagram/AutoPlex_Story14_State_Machine_Diagram.png) | S14 |
| ERD | [Entity relationship diagram v3](../artifacts/ERDiagram/autoplex_motors_erd_v3.png) | S1 to S25 |

## Test Case Catalog

| Test Case | Source | Basis | What it checks |
|---|---|---|---|
| TC-01-01 | S1 | AC 1 | First name and last name are required. |
| TC-01-02 | S1 | AC 2 | Email must be a valid format when provided. |
| TC-01-03 | S1 | AC 3 | New customers are Active. |
| TC-01-04 | S1 | AC 4 | Inactive customers cannot be selected on new invoices. |
| TC-01-05 | S1 | AC 5 | Balance and totalPurchases are read-only and default to 0. |
| TC-01-06 | S1 | Derived | Create, edit, and view a customer with all contact fields. |
| TC-01-07 | S1 | Derived | Search customers by name. |
| TC-02-01 | S2 | AC 1 | First name and last name are required. |
| TC-02-02 | S2 | AC 2 | Salary and bonus cannot be negative. |
| TC-02-03 | S2 | AC 3 | Commission rate must be between 0 and 100 percent. |
| TC-02-04 | S2 | AC 4 | Inactive employees cannot be assigned to new invoices. |
| TC-02-05 | S2 | Derived | Create, edit, and view an employee with all fields. |
| TC-02-06 | S2 | Derived | Flag an employee as a salesperson and see them in the salesperson selector. |
| TC-03-01 | S3 | AC 1 | Vendor name is required. |
| TC-03-02 | S3 | AC 2 | Type is one of Vehicle, Parts, or Service. |
| TC-03-03 | S3 | AC 3 | Inactive vendors cannot be selected on new purchases. |
| TC-03-04 | S3 | AC 4 | Balance and totalPurchases are read-only and default to 0. |
| TC-03-05 | S3 | Derived | Create, edit, view, and search a vendor with all fields. |
| TC-04-01 | S4 | AC 1 | Vendor is required. |
| TC-04-02 | S4 | AC 2 | VIN is required and unique. |
| TC-04-03 | S4 | AC 3 | Purchase price must be greater than zero. |
| TC-04-04 | S4 | AC 4 | Additional costs and intended selling price cannot be negative. |
| TC-04-05 | S4 | AC 5 | Total cost equals purchase price plus additional costs. |
| TC-04-06 | S4 | AC 6 | The vehicle is saved with Available status. |
| TC-04-07 | S4 | Derived | Enter all vehicle fields for a selected vendor and save. |
| TC-05-01 | S5 | AC 1 | The list shows one current status per vehicle. |
| TC-05-02 | S5 | AC 2 | Profit and margin use total cost, not only purchase price. |
| TC-05-03 | S5 | AC 3 | Search and status filters work together. |
| TC-05-04 | S5 | AC 4 | Margin shows as unavailable when the selling price is zero. |
| TC-06-01 | S6 | AC 1 | Part number is required and unique. |
| TC-06-02 | S6 | AC 2 | Vendor is required. |
| TC-06-03 | S6 | AC 3 | Prices and quantity cannot be negative. |
| TC-06-04 | S6 | AC 4 | A part is low stock when quantity is at or below its reorder level. |
| TC-06-05 | S6 | AC 5 | Inventory value equals quantity × cost price. |
| TC-06-06 | S6 | Derived | Create and edit a part with all fields. |
| TC-06-07 | S6 | Derived | Edit part quantity manually. |
| TC-07-01 | S7 | AC 1 | A Bank Account must belong to a Bank. |
| TC-07-02 | S7 | AC 2 | Account name and account type are required. |
| TC-07-03 | S7 | AC 3 | Opening balance cannot be negative. |
| TC-07-04 | S7 | AC 4 | Book balance starts equal to the opening balance. |
| TC-07-05 | S7 | AC 5 | Account numbers are masked in lists. |
| TC-07-06 | S7 | AC 6 | Inactive accounts are saved but cannot be used in later stories. |
| TC-07-07 | S7 | AC 7 | Type includes Cash on hand, so cash receipts and payments also have an account. |
| TC-08-01 | S8 | AC 1 | Direction is in or out, and amount is greater than zero. |
| TC-08-02 | S8 | AC 2 | Each Transaction references one active bank account and records its source type and source number. |
| TC-08-03 | S8 | AC 3 | A posted incoming Transaction increases the book balance. A posted outgoing Transaction decreases it. |
| TC-08-04 | S8 | AC 4 | An outgoing Transaction cannot exceed the account's book balance. |
| TC-08-05 | S8 | AC 5 | Draft Transactions do not affect balances. |
| TC-08-06 | S8 | AC 6 | Posted Transactions cannot be edited or deleted. |
| TC-08-07 | S8 | AC 7 | The list filters by account, direction, and date. |
| TC-08-08 | S8 | Derived | Receipts, payments, transfers, adjustments, and reversals all post through the same posting service. |
| TC-09-01 | S9 | AC 1 | Each posted Transaction creates exactly one line in the same save, with source Simulated and status Cleared. |
| TC-09-02 | S9 | AC 2 | Incoming Transactions set a deposit and outgoing set a withdrawal. Never both. |
| TC-09-03 | S9 | AC 3 | Lines created from Transactions start as Matched and store the Transaction ID. |
| TC-09-04 | S9 | AC 4 | Running balance is calculated in statement-date order. |
| TC-09-05 | S9 | AC 5 | No backfill is needed, because no receipts or payments exist before this story. |
| TC-09-06 | S9 | AC 6 | The list filters by account, month, and type. |
| TC-10-01 | S10 | AC 1 | Source and destination must be different, active accounts. |
| TC-10-02 | S10 | AC 2 | Amount must be greater than zero and not exceed the source balance. |
| TC-10-03 | S10 | AC 3 | One outgoing and one incoming Transaction share a transfer reference. |
| TC-10-04 | S10 | AC 4 | Both balances update together. |
| TC-10-05 | S10 | AC 5 | A transfer does not affect revenue or operating expenses. |
| TC-10-06 | S10 | AC 6 | Each side gets its own statement line. |
| TC-11-01 | S11 | AC 1 | Only vehicles with Available status can be selected. |
| TC-11-02 | S11 | AC 2 | Customer, salesperson, vehicle, invoice date, and sale price are required. |
| TC-11-03 | S11 | AC 3 | The discount cannot exceed the sale price. |
| TC-11-04 | S11 | AC 4 | The invoice total must be greater than zero. |
| TC-11-05 | S11 | AC 5 | A Draft invoice has paid = 0, balance = total, and does not change the vehicle. |
| TC-11-06 | S11 | AC 6 | Each invoice gets a unique number. |
| TC-11-07 | S11 | Derived | The selected vehicle shows VIN, make and model, selling price, and inventory cost. |
| TC-11-08 | S11 | Derived | Sale price, discount, tax, fees, invoice date, and due date are accepted. |
| TC-11-09 | S11 | Derived | Invoice Total = Sale Price + Tax + Fees − Discount is calculated correctly. |
| TC-12-01 | S12 | AC 1 | Only Draft invoices can be posted. |
| TC-12-02 | S12 | AC 2 | Validation runs again at posting and errors are shown before saving. |
| TC-12-03 | S12 | AC 3 | Posting changes the vehicle status to Sold and stores the invoice ID on the vehicle. |
| TC-12-04 | S12 | AC 4 | A Sold vehicle no longer appears in the available-vehicle selector. |
| TC-12-05 | S12 | AC 5 | If two invoices try to post the same vehicle, only one succeeds. |
| TC-12-06 | S12 | AC 6 | Posted invoices cannot be edited or deleted. |
| TC-13-01 | S13 | AC 1 | Cancelling sets the status to Cancelled and the vehicle back to Available. |
| TC-13-02 | S13 | AC 2 | Only invoices with paid = 0 can be cancelled. |
| TC-13-03 | S13 | AC 3 | A reason is required. |
| TC-13-04 | S13 | AC 4 | The list searches by number, customer, VIN, and status, and filters by date. |
| TC-13-05 | S13 | AC 5 | Cancelled invoices stay visible. |
| TC-13.1-01 | S13.1 | AC 1 | `GET /SalesInvoice/GetSalesInvoiceByCustomer?customerId=` returns that customer's invoices as 200. |
| TC-13.1-02 | S13.1 | AC 2 | A customer with no invoices returns 200 with empty items, not 404. |
| TC-13.1-03 | S13.1 | AC 3 | The response is NOT paged (PageNumber, PageSize, capped by the existing RequestParameters limit) and ordered by invoice date, newest first, then by number. |
| TC-13.1-04 | S13.1 | AC 4 | Each item has the same fields as GetSalesInvoiceByCustomer with attributes: |
| TC-13.1-05 | S13.1 | AC 5 | An unknown customerId returns an empty list, not an error. |
| TC-13.1-06 | S13.1 | AC 6 | It is read-only: nothing is written or changed. |
| TC-14-01 | S14 | AC 1 | Paid in full: paid = total, balance = 0, status Paid, one Bank Receipt, no AR record. |
| TC-14-02 | S14 | AC 2 | Partial payment: balance = total − paid, status Partial, one Bank Receipt, AR created. |
| TC-14-03 | S14 | AC 3 | Credit sale: paid = 0, status Unpaid, AR created, no Bank Receipt. |
| TC-14-04 | S14 | AC 4 | The AR amount, paid, and balance match the Sales Invoice. |
| TC-14-05 | S14 | AC 5 | Amount received cannot be negative or exceed the total. |
| TC-14-06 | S14 | AC 6 | Method is one of Cash, Card, Transfer, or Check. |
| TC-14-07 | S14 | AC 7 | A bank account is required whenever an amount is received. Inactive accounts are rejected. |
| TC-14-08 | S14 | AC 8 | The invoice, AR, Bank Receipt, Transaction, statement line, and book balance save together. |
| TC-15-01 | S15 | AC 1 | Amount must be greater than zero. |
| TC-15-02 | S15 | AC 2 | Amount cannot exceed the AR balance. |
| TC-15-03 | S15 | AC 3 | Each payment creates a separate Bank Receipt with its own Transaction and statement line. |
| TC-15-04 | S15 | AC 4 | AR and Sales Invoice paid, balance, and status update together. |
| TC-15-05 | S15 | AC 5 | Full payment sets Paid. Partial payment sets Partial. |
| TC-15-06 | S15 | AC 6 | A bank account is required. Inactive accounts are rejected. |
| TC-15-07 | S15 | AC 7 | The selected account's book balance increases. |
| TC-15-08 | S15 | AC 8 | Previous receipts are never overwritten. |
| TC-15-09 | S15 | Derived | Only open AR invoices can be selected for a later payment. |
| TC-15-10 | S15 | Derived | Payment history shows every receipt on the invoice. |
| TC-16-01 | S16 | AC 1 | Payer, date, amount, method, bank account, and description are required. |
| TC-16-02 | S16 | AC 2 | Amount must be greater than zero. |
| TC-16-03 | S16 | AC 3 | The receipt does not change any customer, invoice, or AR balance. |
| TC-16-04 | S16 | AC 4 | The receipt creates one Transaction and one statement line and increases the book balance. |
| TC-16-05 | S16 | AC 5 | Inactive accounts are rejected. |
| TC-16-06 | S16 | AC 6 | Each receipt is separate and previous receipts are never overwritten. |
| TC-17-01 | S17 | AC 1 | The list shows customer, invoice, due date, amount, paid, balance, days, and status. |
| TC-17-02 | S17 | AC 2 | Days overdue is the as-of date minus the due date, never below zero. |
| TC-17-03 | S17 | AC 3 | An open AR with a past due date shows Overdue. |
| TC-17-04 | S17 | AC 4 | The list filters by status and customer. |
| TC-18-01 | S18 | AC 1 | Customer balance equals the sum of that customer's open AR balances. |
| TC-18-02 | S18 | AC 2 | Total purchases equals the sum of posted, non-cancelled invoice totals. |
| TC-18-03 | S18 | AC 3 | Both update on posting, payment, and cancellation. |
| TC-18-04 | S18 | AC 4 | Balance is never negative. |
| TC-19-01 | S19 | AC 1 | Paid in full creates no AP Bill. |
| TC-19-02 | S19 | AC 2 | Partial and credit purchases create an AP Bill. |
| TC-19-03 | S19 | AC 3 | The AP amount equals the vehicle total cost. |
| TC-19-04 | S19 | AC 4 | Amount paid now cannot be negative or exceed the total cost. |
| TC-19-05 | S19 | AC 5 | Vehicle total cost does not change when the AP Bill is paid. |
| TC-19-06 | S19 | AC 6 | A bank account is required whenever an amount is paid, and the payment cannot exceed its book balance. |
| TC-19-07 | S19 | AC 7 | The AP Bill, Bank Payment, Transaction, statement line, and book balance save together. |
| TC-19-08 | S19 | Derived | The Bank Payment stores vehicleId and, when one exists, apBillId. |
| TC-20-01 | S20 | AC 1 | Amount must be greater than zero. |
| TC-20-02 | S20 | AC 2 | Amount cannot exceed the AP balance. |
| TC-20-03 | S20 | AC 3 | Each installment creates a separate Bank Payment with its own Transaction and statement line. |
| TC-20-04 | S20 | AC 4 | AP paid, balance, and status update together. |
| TC-20-05 | S20 | AC 5 | Vendor outstanding balance updates. |
| TC-20-06 | S20 | AC 6 | The payment cannot exceed the bank account's book balance. |
| TC-20-07 | S20 | AC 7 | Previous payments are never overwritten. |
| TC-20-08 | S20 | Derived | Only open AP Bills can be selected for a later payment. |
| TC-20-09 | S20 | Derived | Payment history shows every payment on the bill. |
| TC-21-01 | S21 | AC 1 | Payee, payment category, date, amount, method, and bank account are required. |
| TC-21-02 | S21 | AC 2 | Payment cannot exceed the available bank balance. |
| TC-21-03 | S21 | AC 3 | The payment creates one Transaction and one statement line and decreases the book balance. |
| TC-21-04 | S21 | AC 4 | Inventory purchases and AP settlements are not treated as operating expenses. |
| TC-21-05 | S21 | AC 5 | Each payment is separate and previous payments are never overwritten. |
| TC-22-01 | S22 | AC 1 | The list shows vendor, bill, due date, amount, paid, balance, days, and status. |
| TC-22-02 | S22 | AC 2 | Days overdue is never below zero. |
| TC-22-03 | S22 | AC 3 | An open bill with a past due date shows Overdue. |
| TC-22-04 | S22 | AC 4 | Vendor outstanding balance equals the sum of that vendor's open AP balances. |
| TC-23-01 | S23 | AC 1 | A reversal requires a reason and references the original Transaction. |
| TC-23-02 | S23 | AC 2 | A reversed receipt creates an outgoing Transaction. A reversed payment creates an incoming Transaction. |
| TC-23-03 | S23 | AC 3 | The reversal amount equals the amount being reversed. |
| TC-23-04 | S23 | AC 4 | Bank balance, AR or AP balance, and invoice or bill status are restored. |
| TC-23-05 | S23 | AC 5 | The original and the reversal both stay visible. |
| TC-23-06 | S23 | AC 6 | The same Transaction cannot be reversed twice. |
| TC-23-07 | S23 | AC 7 | The reversal Transaction gets its own statement line. |
| TC-24-01 | S24 | AC 1 | Account, date, type, direction, amount, and description are required. |
| TC-24-02 | S24 | AC 2 | Interest defaults to incoming and bank charges to outgoing. |
| TC-24-03 | S24 | AC 3 | No Transaction is created and the book balance does not change. |
| TC-24-04 | S24 | AC 4 | The statement running balance updates. |
| TC-24-05 | S24 | AC 5 | A bank reference is unique within the account when provided. |
| TC-24-06 | S24 | Derived | Only the seven listed adjustment types can be selected. |
| TC-25-01 | S25 | AC 1 | Exactly one Transaction and one statement line are created and linked. |
| TC-25-02 | S25 | AC 2 | The line is marked Matched. |
| TC-25-03 | S25 | AC 3 | Book balance increases for incoming and decreases for outgoing adjustments. |
| TC-25-04 | S25 | AC 4 | No duplicate statement line is created. |
| TC-25-05 | S25 | AC 5 | Posting is atomic. |
| TC-26-01 | S26 | AC 1 | Revenue comes from posted, non-cancelled Sales Invoices, regardless of payment status. |
| TC-26-02 | S26 | AC 2 | Sales tax, AR receipts, and bank transfers are excluded. |
| TC-26-03 | S26 | AC 3 | Interest and other income come from posted incoming adjustments only. |
| TC-26-04 | S26 | AC 4 | Statement-only unmatched adjustments are excluded. |
| TC-26-05 | S26 | Derived | Total Revenue = Vehicle + Service + Fee + Interest + Other Income − Discounts is calculated correctly. |
| TC-27-01 | S27 | AC 1 | Only vehicles on posted invoices are included, once each. |
| TC-27-02 | S27 | AC 2 | Unsold inventory and AP payments create no COGS. |
| TC-27-03 | S27 | AC 3 | Cancelled sales reverse their COGS. |
| TC-27-04 | S27 | AC 4 | Parts COGS stays zero until part sale or usage records exist. |
| TC-28-01 | S28 | AC 1 | Salary, bonus, and commission come from employee and invoice records. |
| TC-28-02 | S28 | AC 2 | Categorized bank payments and posted bank charges are included. |
| TC-28-03 | S28 | AC 3 | Vehicle and parts purchases, AP settlements for inventory, loan principal, tax, transfers, and revenue-reversing refunds are excluded. |
| TC-28-04 | S28 | AC 4 | The same expense is never counted from both an accrual and a cash payment. |
| TC-28-05 | S28 | AC 5 | Interest received is income, not a negative expense. |
| TC-29-01 | S29 | AC 1 | Shows total revenue, COGS, gross profit, operating expenses, net profit, gross margin, and net margin. |
| TC-29-02 | S29 | AC 2 | Draft and cancelled invoices are excluded. |
| TC-29-03 | S29 | AC 3 | Results are the same for the same period and data. |
| TC-29-04 | S29 | Derived | The report runs for a selected month, quarter, and year to date. |
| TC-30-01 | S30 | AC 1 | Periods do not overlap and use the same rules. |
| TC-30-02 | S30 | AC 2 | Change shows as unavailable when the previous amount is zero. |
| TC-30-03 | S30 | AC 3 | Negative profit displays clearly. |
| TC-30-04 | S30 | Derived | Percentage Change = (Current − Previous) ÷ \|Previous\| × 100 is calculated correctly. |
| TC-31-01 | S31 | AC 1 | Drill-down totals equal the report amount, and records keep their references. |
| TC-31-02 | S31 | AC 2 | Posted records cannot be edited from the report without permission. |
| TC-31-03 | S31 | AC 3 | Exports show the period, current and previous values, company name, and generation date. |
| TC-31-04 | S31 | AC 4 | Exported totals match the screen, and exporting changes no data. |
| TC-31-05 | S31 | AC 5 | Only authorized users can drill down into or export sensitive reports. |
| TC-R-01 | Rules | Derived | A failure part-way through posting rolls back every related record. |
| TC-R-02 | Rules | Derived | Money amounts are stored and calculated as decimal, with no rounding drift. |
| TC-R-03 | Rules | Derived | Every saved record has creation date, user, reference, and status. |
| TC-R-04 | Rules | Derived | Invalid input returns all validation errors and saves nothing. |
| TC-R-05 | Rules | Derived | Each story's tests pass on main before any later story is merged. |
| TC-R-06 | Rules | Derived | The schema has no Customer Payment or Vendor Payment table. |

## Coverage Gaps

Every requirement traces to at least one story or rule and to at least one test case. Design coverage is not complete yet:

- **No design diagram yet:** S26, S27, S28, S29, S30, S31 (reporting).
- **Only the ERD so far:** S20, S21, S22, S23, S24, S25.
- **No sequence diagram yet:** S1, S2, S3, S4, S5, S6, S7, S11, S12, S13, S13.1, S19, S20, S21, S22, S23, S24, S25, S26, S27, S28, S29, S30, S31.
- **No detail class diagram:** S7. **No domain class diagram:** S14.
