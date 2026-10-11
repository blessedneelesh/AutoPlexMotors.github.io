# Traceability Matrix

This matrix links each of the 36 user stories to the requirements in [software_requirements_specification.md](software_requirements_specification.md) derived from them. Consecutive requirement IDs are shown as ranges, for example, `FR-CUS-01 to FR-CUS-07`. A requirement may trace to more than one story, so it may appear in multiple rows.

## Story-to-Requirement Traceability

| Story | Title | Feature(s) | Functional Requirements | Non-functional Requirements |
|---|---|---|---|---|
| S1 | Manage customers | Customer Management | FR-CUS-01 to FR-CUS-07 | NFR-MNT-02 |
| S2 | Manage employees | Employee Management | FR-EMP-01 to FR-EMP-06 | - |
| S3 | Manage vendors | Vendor Management | FR-VEN-01 to FR-VEN-05 | NFR-MNT-02 |
| S4 | Add a vehicle to inventory | Vehicle Purchase Form | FR-VEH-01 to FR-VEH-05 | NFR-INT-05 |
| S5 | Browse vehicle inventory | Vehicle Inventory List | FR-INV-01 to FR-INV-04 | NFR-USE-01, NFR-USE-02 |
| S6 | Manage parts inventory | Parts Inventory Form and List | FR-PRT-01 to FR-PRT-06 | NFR-INT-05 |
| S7 | Create a draft sales invoice | Sales Invoice Form | FR-SIN-01 to FR-SIN-08 | NFR-INT-05 |
| S8 | Post a sales invoice | Sales Invoice Posting | FR-POS-01 to FR-POS-06 | NFR-INT-01 |
| S9 | Cancel and browse sales invoices | Sales Invoice List and Cancellation | FR-SIL-01 to FR-SIL-04 | NFR-AUD-01, NFR-USE-01 |
| S10 | Payment conditions and AR | Customer Payment Conditions | FR-PAY-01 to FR-PAY-07 | NFR-MNT-02 |
| S11 | Record a later customer payment | Record Customer Payment Form | FR-RCP-01 to FR-RCP-05 | NFR-INT-02 |
| S12 | AR list and aging | Accounts Receivable List and Aging | FR-ARL-01 to FR-ARL-04 | NFR-USE-01 |
| S13 | Customer balances | Customer Management | FR-CUS-08, FR-CUS-09 | - |
| S14 | Vehicle purchase payment conditions and AP | Vehicle Purchase Form | FR-VEH-06 to FR-VEH-10 | - |
| S15 | Record a later vendor payment | Vendor Management; Vendor Payment Form and AP List | FR-VEN-06, FR-APB-01 to FR-APB-04 | NFR-INT-02 |
| S16 | AP list and aging | Vendor Management; Vendor Payment Form and AP List | FR-VEN-06, FR-APB-05, FR-APB-06 | - |
| S17 | Banks and bank accounts | Bank and Bank Account Form | FR-BNK-01 to FR-BNK-05 | NFR-SEC-01 |
| S18 | Bank receipts | Bank Receipt Form | FR-RCT-01 to FR-RCT-06 | - |
| S19 | Bank payments | Bank Payment Form | FR-BPY-01 to FR-BPY-07 | - |
| S20 | Internal transaction ledger | Internal Transaction Ledger | FR-LED-01 to FR-LED-08 | NFR-INT-03, NFR-MNT-01 |
| S21 | Reverse a banking transaction | Sales Invoice List and Cancellation; Reverse Transaction Form | FR-SIL-03, FR-REV-01 to FR-REV-04 | NFR-AUD-01 |
| S22 | Transfer between accounts | Bank Transfer Form | FR-TRF-01 to FR-TRF-04 | - |
| S23 | Generate statement lines | Bank Statement Lines | FR-STM-01 to FR-STM-05 | NFR-INT-03 |
| S24 | Statement-only adjustment | Statement Adjustment Form | FR-ADJ-01 to FR-ADJ-04 | NFR-INT-05 |
| S25 | Add and post an adjustment | Statement Adjustment Form | FR-ADJ-05, FR-ADJ-06 | - |
| S26 | Reconciliation data and balances | Reconciliation Screen | FR-REC-01 to FR-REC-05 | NFR-ACC-02 |
| S27 | Suggest matches | Reconciliation Matching | FR-MAT-01 to FR-MAT-04 | - |
| S28 | Confirm a match | Reconciliation Matching | FR-MAT-05, FR-MAT-06 | NFR-INT-04 |
| S29 | Post an unmatched adjustment | Reconciliation Matching | FR-MAT-07, FR-MAT-08 | NFR-INT-04 |
| S30 | Reset or reopen reconciliation | Reconciliation Matching | FR-MAT-09 to FR-MAT-11 | NFR-AUD-01, NFR-SEC-02 |
| S31 | Revenue | Revenue Report Section | FR-REVN-01 to FR-REVN-04 | - |
| S32 | COGS | Cost of Goods Sold Report Section | FR-COGS-01 to FR-COGS-03 | - |
| S33 | Operating expenses | Operating Expenses Report Section | FR-OPEX-01 to FR-OPEX-04 | - |
| S34 | Profit and Loss report | Profit and Loss Report | FR-PNL-01 to FR-PNL-03 | NFR-ACC-01 |
| S35 | Compare periods | Profit and Loss Report | FR-PNL-04, FR-PNL-05 | NFR-USE-02 |
| S36 | Drill down and export | Profit and Loss Report | FR-PNL-06 to FR-PNL-08 | NFR-AUD-02, NFR-SEC-02, NFR-ACC-03 |

## Requirements Not Tied to One Story

| Source | Requirements |
|---|---|
| Rules that apply to every story | NFR-ALL-01 to NFR-ALL-05 |
| Introduction to the User Stories | NFR-ALL-06 |

## Requirement-to-Story Traceability

| Requirement | Story |
|---|---|
| FR-CUS-01 | S1 |
| FR-CUS-02 | S1 |
| FR-CUS-03 | S1 |
| FR-CUS-04 | S1 |
| FR-CUS-05 | S1 |
| FR-CUS-06 | S1 |
| FR-CUS-07 | S1 |
| FR-CUS-08 | S13 |
| FR-CUS-09 | S13 |
| FR-EMP-01 | S2 |
| FR-EMP-02 | S2 |
| FR-EMP-03 | S2 |
| FR-EMP-04 | S2 |
| FR-EMP-05 | S2 |
| FR-EMP-06 | S2 |
| FR-VEN-01 | S3 |
| FR-VEN-02 | S3 |
| FR-VEN-03 | S3 |
| FR-VEN-04 | S3 |
| FR-VEN-05 | S3 |
| FR-VEN-06 | S15, S16 |
| FR-VEH-01 | S4 |
| FR-VEH-02 | S4 |
| FR-VEH-03 | S4 |
| FR-VEH-04 | S4 |
| FR-VEH-05 | S4 |
| FR-VEH-06 | S14 |
| FR-VEH-07 | S14 |
| FR-VEH-08 | S14 |
| FR-VEH-09 | S14 |
| FR-VEH-10 | S14 |
| FR-INV-01 | S5 |
| FR-INV-02 | S5 |
| FR-INV-03 | S5 |
| FR-INV-04 | S5 |
| FR-PRT-01 | S6 |
| FR-PRT-02 | S6 |
| FR-PRT-03 | S6 |
| FR-PRT-04 | S6 |
| FR-PRT-05 | S6 |
| FR-PRT-06 | S6 |
| FR-SIN-01 | S7 |
| FR-SIN-02 | S7 |
| FR-SIN-03 | S7 |
| FR-SIN-04 | S7 |
| FR-SIN-05 | S7 |
| FR-SIN-06 | S7 |
| FR-SIN-07 | S7 |
| FR-SIN-08 | S7 |
| FR-POS-01 | S8 |
| FR-POS-02 | S8 |
| FR-POS-03 | S8 |
| FR-POS-04 | S8 |
| FR-POS-05 | S8 |
| FR-POS-06 | S8 |
| FR-SIL-01 | S9 |
| FR-SIL-02 | S9 |
| FR-SIL-03 | S9, S21 |
| FR-SIL-04 | S9 |
| FR-PAY-01 | S10 |
| FR-PAY-02 | S10 |
| FR-PAY-03 | S10 |
| FR-PAY-04 | S10 |
| FR-PAY-05 | S10 |
| FR-PAY-06 | S10 |
| FR-PAY-07 | S10 |
| FR-RCP-01 | S11 |
| FR-RCP-02 | S11 |
| FR-RCP-03 | S11 |
| FR-RCP-04 | S11 |
| FR-RCP-05 | S11 |
| FR-ARL-01 | S12 |
| FR-ARL-02 | S12 |
| FR-ARL-03 | S12 |
| FR-ARL-04 | S12 |
| FR-APB-01 | S15 |
| FR-APB-02 | S15 |
| FR-APB-03 | S15 |
| FR-APB-04 | S15 |
| FR-APB-05 | S16 |
| FR-APB-06 | S16 |
| FR-BNK-01 | S17 |
| FR-BNK-02 | S17 |
| FR-BNK-03 | S17 |
| FR-BNK-04 | S17 |
| FR-BNK-05 | S17 |
| FR-RCT-01 | S18 |
| FR-RCT-02 | S18 |
| FR-RCT-03 | S18 |
| FR-RCT-04 | S18 |
| FR-RCT-05 | S18 |
| FR-RCT-06 | S18 |
| FR-BPY-01 | S19 |
| FR-BPY-02 | S19 |
| FR-BPY-03 | S19 |
| FR-BPY-04 | S19 |
| FR-BPY-05 | S19 |
| FR-BPY-06 | S19 |
| FR-BPY-07 | S19 |
| FR-LED-01 | S20 |
| FR-LED-02 | S20 |
| FR-LED-03 | S20 |
| FR-LED-04 | S20 |
| FR-LED-05 | S20 |
| FR-LED-06 | S20 |
| FR-LED-07 | S20 |
| FR-LED-08 | S20 |
| FR-REV-01 | S21 |
| FR-REV-02 | S21 |
| FR-REV-03 | S21 |
| FR-REV-04 | S21 |
| FR-TRF-01 | S22 |
| FR-TRF-02 | S22 |
| FR-TRF-03 | S22 |
| FR-TRF-04 | S22 |
| FR-STM-01 | S23 |
| FR-STM-02 | S23 |
| FR-STM-03 | S23 |
| FR-STM-04 | S23 |
| FR-STM-05 | S23 |
| FR-ADJ-01 | S24 |
| FR-ADJ-02 | S24 |
| FR-ADJ-03 | S24 |
| FR-ADJ-04 | S24 |
| FR-ADJ-05 | S25 |
| FR-ADJ-06 | S25 |
| FR-REC-01 | S26 |
| FR-REC-02 | S26 |
| FR-REC-03 | S26 |
| FR-REC-04 | S26 |
| FR-REC-05 | S26 |
| FR-MAT-01 | S27 |
| FR-MAT-02 | S27 |
| FR-MAT-03 | S27 |
| FR-MAT-04 | S27 |
| FR-MAT-05 | S28 |
| FR-MAT-06 | S28 |
| FR-MAT-07 | S29 |
| FR-MAT-08 | S29 |
| FR-MAT-09 | S30 |
| FR-MAT-10 | S30 |
| FR-MAT-11 | S30 |
| FR-REVN-01 | S31 |
| FR-REVN-02 | S31 |
| FR-REVN-03 | S31 |
| FR-REVN-04 | S31 |
| FR-COGS-01 | S32 |
| FR-COGS-02 | S32 |
| FR-COGS-03 | S32 |
| FR-OPEX-01 | S33 |
| FR-OPEX-02 | S33 |
| FR-OPEX-03 | S33 |
| FR-OPEX-04 | S33 |
| FR-PNL-01 | S34 |
| FR-PNL-02 | S34 |
| FR-PNL-03 | S34 |
| FR-PNL-04 | S35 |
| FR-PNL-05 | S35 |
| FR-PNL-06 | S36 |
| FR-PNL-07 | S36 |
| FR-PNL-08 | S36 |
| NFR-ALL-01 | Rules |
| NFR-ALL-02 | Rules |
| NFR-ALL-03 | Rules |
| NFR-ALL-04 | Rules |
| NFR-ALL-05 | Rules |
| NFR-ALL-06 | Introduction to the User Stories |
| NFR-INT-01 | S8 |
| NFR-INT-02 | S11, S15 |
| NFR-INT-03 | S20, S23 |
| NFR-INT-04 | S28, S29 |
| NFR-INT-05 | S4, S6, S7, S24 |
| NFR-AUD-01 | S9, S21, S30 |
| NFR-AUD-02 | S36 |
| NFR-SEC-01 | S17 |
| NFR-SEC-02 | S30, S36 |
| NFR-ACC-01 | S34 |
| NFR-ACC-02 | S26 |
| NFR-ACC-03 | S36 |
| NFR-USE-01 | S5, S9, S12 |
| NFR-USE-02 | S5, S35 |
| NFR-MNT-01 | S20 |
| NFR-MNT-02 | S1, S3, S10 |