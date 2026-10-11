# Overview

This document is the Software Requirements Specification (SRS) for AutoPlex Motors, a dealership management system covering master data (customers, employees, vendors), vehicle and parts inventory, sales invoicing, accounts receivable and payable, banking, simulated bank statements and reconciliation, and Profit & Loss reporting. It converts the 36 incremental user stories into testable "shall" requirements and groups them by feature (for example, everything about the customer form sits under one "Customer Management" feature). 

**How to read it:** features are numbered in delivery order; each requirement has an ID (`FR-` functional, `NFR-` non-functional) and ends with the user story it came from in brackets, e.g. *[S8]* = Story 8. Requirements under a feature may rely on earlier features only, matching the story dependency order. Markdown does not render nested numbering (1.1, 1.2) well, so the ID is the reliable way to refer to a requirement.

# Functional Requirements

1. **Customer Management** (Customer form and list)
    1. FR-CUS-01: The system shall let a salesperson create, edit, and view customers with name, phone, email, address, city, state, and ZIP. *[S1]*
    2. FR-CUS-02: The system shall require first name and last name. *[S1]*
    3. FR-CUS-03: The system shall validate that email is in a valid format when provided. *[S1]*
    4. FR-CUS-04: The system shall create new customers with status Active and allow them to be set Active or Inactive. *[S1]*
    5. FR-CUS-05: The system shall support searching customers. *[S1]*
    6. FR-CUS-06: The system shall not allow Inactive customers to be selected on new invoices. *[S1]*
    7. FR-CUS-07: The system shall show balance and totalPurchases as read-only fields defaulting to 0. *[S1]*
    8. FR-CUS-08: The system shall set customer balance to the sum of that customer's open AR balances, and totalPurchases to the sum of posted, non-cancelled invoice totals. *[S13]*
    9. FR-CUS-09: The system shall update both values on invoice posting, payment, and cancellation, and shall never show a negative balance. *[S13]*
2. **Employee Management** (Employee form)
    1. FR-EMP-01: The system shall let an administrator create, edit, and view employees with name, department, job, salary, bonus, commission rate, hire date, and status. *[S2]*
    2. FR-EMP-02: The system shall allow an employee to be flagged as a salesperson. *[S2]*
    3. FR-EMP-03: The system shall require first name and last name. *[S2]*
    4. FR-EMP-04: The system shall reject negative salary or bonus. *[S2]*
    5. FR-EMP-05: The system shall require commission rate to be between 0 and 100 percent. *[S2]*
    6. FR-EMP-06: The system shall not allow Inactive employees to be assigned to new invoices. *[S2]*
3. **Vendor Management** (Vendor form and list)
    1. FR-VEN-01: The system shall let a purchasing officer create, edit, view, and search vendors with name, contact, phone, email, address, type, and status. *[S3]*
    2. FR-VEN-02: The system shall require vendor name. *[S3]*
    3. FR-VEN-03: The system shall restrict vendor type to Vehicle, Parts, or Service. *[S3]*
    4. FR-VEN-04: The system shall allow vendors to be set Active or Inactive and shall not allow Inactive vendors on new purchases. *[S3]*
    5. FR-VEN-05: The system shall show vendor balance and totalPurchases as read-only fields defaulting to 0. *[S3]*
    6. FR-VEN-06: The system shall keep vendor outstanding balance equal to the sum of that vendor's open AP balances, updated on each vendor payment. *[S15, S16]*
4. **Vehicle Purchase Form** (adding a vehicle to inventory)
    1. FR-VEH-01: The system shall let a purchasing officer select a vendor and enter VIN, make, model, year, color, purchase date, warehouse, intended selling price, purchase price, and additional costs. *[S4]*
    2. FR-VEH-02: The system shall require a vendor and a unique VIN. *[S4]*
    3. FR-VEH-03: The system shall require purchase price greater than zero and reject negative additional costs or intended selling price. *[S4]*
    4. FR-VEH-04: The system shall calculate Total Vehicle Cost = Purchase Price + Additional Costs. *[S4]*
    5. FR-VEH-05: The system shall save new vehicles with status Available. *[S4]*
    6. FR-VEH-06: The system shall record whether the vehicle was paid in full, paid partially, or bought on credit, with amount paid now, method, and reference. *[S14]*
    7. FR-VEH-07: The system shall save the initial amount as a Vendor Payment record. *[S14]*
    8. FR-VEH-08: The system shall reject an amount paid now that is negative or exceeds total cost. *[S14]*
    9. FR-VEH-09: The system shall create an AP Bill, equal to the vehicle total cost, only for partial and credit purchases, and none when paid in full. *[S14]*
    10. FR-VEH-10: The system shall keep vehicle total cost unchanged when the AP Bill is paid. *[S14]*
5. **Vehicle Inventory List**
    1. FR-INV-01: The system shall list all vehicles with vendor, cost, selling price, and one current status each. *[S5]*
    2. FR-INV-02: The system shall support searching by VIN, make, or model and filtering by status, with both working together. *[S5]*
    3. FR-INV-03: The system shall show Gross Profit = Selling Price − Total Vehicle Cost and Gross Margin % = Gross Profit ÷ Selling Price × 100, using total cost rather than purchase price. *[S5]*
    4. FR-INV-04: The system shall show margin as unavailable when selling price is zero. *[S5]*
6. **Parts Inventory Form and List**
    1. FR-PRT-01: The system shall let a parts inventory manager create and edit parts with part number, name, category, vendor, cost price, selling price, quantity, reorder level, and warehouse. *[S6]*
    2. FR-PRT-02: The system shall require a unique part number and a vendor. *[S6]*
    3. FR-PRT-03: The system shall reject negative prices or quantity. *[S6]*
    4. FR-PRT-04: The system shall flag a part as low stock when quantity is at or below its reorder level. *[S6]*
    5. FR-PRT-05: The system shall show inventory value as quantity × cost price. *[S6]*
    6. FR-PRT-06: The system shall allow quantity to be edited manually until part sale or usage records exist. *[S6]*
7. **Sales Invoice Form** (draft creation)
    1. FR-SIN-01: The system shall let a salesperson select an existing customer, an Available vehicle, and a responsible salesperson. *[S7]*
    2. FR-SIN-02: The system shall display the selected vehicle's VIN, make and model, selling price, and inventory cost. *[S7]*
    3. FR-SIN-03: The system shall accept sale price, discount, tax, fees, invoice date, and due date. *[S7]*
    4. FR-SIN-04: The system shall require customer, salesperson, vehicle, invoice date, and sale price. *[S7]*
    5. FR-SIN-05: The system shall reject a discount greater than the sale price and an invoice total of zero or less. *[S7]*
    6. FR-SIN-06: The system shall calculate Invoice Total = Sale Price + Tax + Fees − Discount. *[S7]*
    7. FR-SIN-07: The system shall save the invoice as Draft with paid = 0 and balance = total, without changing the vehicle. *[S7]*
    8. FR-SIN-08: The system shall assign each invoice a unique number. *[S7]*
8. **Sales Invoice Posting**
    1. FR-POS-01: The system shall allow only Draft invoices to be posted, after the user confirms. *[S8]*
    2. FR-POS-02: The system shall re-run validation at posting and show errors before saving. *[S8]*
    3. FR-POS-03: The system shall, on posting, set the vehicle to Sold and store the invoice ID on the vehicle. *[S8]*
    4. FR-POS-04: The system shall remove Sold vehicles from the available-vehicle selector. *[S8]*
    5. FR-POS-05: The system shall ensure that when two invoices post the same vehicle, only one succeeds. *[S8]*
    6. FR-POS-06: The system shall prevent posted invoices from being edited or deleted, and shall start them as Unpaid. *[S8]*
9. **Sales Invoice List and Cancellation**
    1. FR-SIL-01: The system shall list, search (number, customer, VIN, status), filter by date, and open invoices. *[S9]*
    2. FR-SIL-02: The system shall let a user cancel a posted invoice only with a required reason. *[S9]*
    3. FR-SIL-03: The system shall allow cancellation only when paid = 0, unless the invoice's receipts have first been reversed. *[S9, S21]*
    4. FR-SIL-04: The system shall set a cancelled invoice to Cancelled and its vehicle back to Available, and keep it visible in the list. *[S9]*
10. **Customer Payment Condition** (on the posted invoice)
    1. FR-PAY-01: The system shall let the user record paid in full, paid partially, or credit sale, with amount received, method, and reference. *[S10]*
    2. FR-PAY-02: The system shall restrict method to Cash, Card, Transfer, or Check. *[S10]*
    3. FR-PAY-03: The system shall reject an amount received that is negative or exceeds the invoice total. *[S10]*
    4. FR-PAY-04: For paid in full, the system shall set paid = total, balance = 0, status Paid, and create no AR record. *[S10]*
    5. FR-PAY-05: For partial payment, the system shall set balance = total − paid, status Partial, and create an AR record. *[S10]*
    6. FR-PAY-06: For credit sale, the system shall set paid = 0, status Unpaid, create an AR record, and create no Customer Payment. *[S10]*
    7. FR-PAY-07: The system shall store each initial amount as a Customer Payment (invoice, date, amount, method, reference) and keep AR amount, paid, and balance matching the invoice. *[S10]*
11. **Record Customer Payment Form** (later payments)
    1. FR-RCP-01: The system shall let an AR clerk select an open AR invoice and enter date, amount, method, and reference. *[S11]*
    2. FR-RCP-02: The system shall require amount greater than zero and not above the AR balance. *[S11]*
    3. FR-RCP-03: The system shall create a separate Customer Payment per entry and never overwrite earlier payments. *[S11]*
    4. FR-RCP-04: The system shall update AR and invoice paid, balance, and status together (Paid on full, Partial otherwise). *[S11]*
    5. FR-RCP-05: The system shall show payment history on the invoice. *[S11]*
12. **Accounts Receivable List and Aging**
    1. FR-ARL-01: The system shall show customer, invoice, due date, amount, paid, balance, days overdue, and status. *[S12]*
    2. FR-ARL-02: The system shall calculate days overdue as as-of date minus due date, never below zero. *[S12]*
    3. FR-ARL-03: The system shall show Overdue for an open AR past its due date. *[S12]*
    4. FR-ARL-04: The system shall filter by status and customer. *[S12]*
13. **Vendor Payment Form and AP List** (later payments, aging)
    1. FR-APB-01: The system shall let an AP clerk select an open AP Bill and enter date, amount, method, and reference. *[S15]*
    2. FR-APB-02: The system shall require amount greater than zero and not above the AP balance. *[S15]*
    3. FR-APB-03: The system shall create a separate Vendor Payment per installment and update AP paid, balance, and status together. *[S15]*
    4. FR-APB-04: The system shall show payment history on the bill. *[S15]*
    5. FR-APB-05: The system shall list open AP Bills with vendor, bill, due date, amount, paid, balance, days overdue, and status. *[S16]*
    6. FR-APB-06: The system shall never show days overdue below zero and shall show Overdue for open bills past due. *[S16]*
14. **Bank and Bank Account Form**
    1. FR-BNK-01: The system shall let an accountant create and maintain banks and add accounts under each (name, account number, routing number, type, opening balance, status). *[S17]*
    2. FR-BNK-02: The system shall require each account to belong to a bank and require account name and type. *[S17]*
    3. FR-BNK-03: The system shall reject a negative opening balance and start book balance equal to it. *[S17]*
    4. FR-BNK-04: The system shall mask account numbers in lists. *[S17]*
    5. FR-BNK-05: The system shall save Inactive accounts but prevent their use in later transactions. *[S17]*
15. **Bank Receipt Form**
    1. FR-RCT-01: The system shall let an AR clerk assign a bank account to a customer payment, including the initial payment, converting it to a Bank Receipt. *[S18]*
    2. FR-RCT-02: The system shall let an AR clerk record a receipt from another payer not linked to AR, without changing any customer balance. *[S18]*
    3. FR-RCT-03: The system shall require a bank account for Card, Transfer, and Check receipts and reject Inactive accounts. *[S18]*
    4. FR-RCT-04: The system shall reject a receipt exceeding the selected AR balance. *[S18]*
    5. FR-RCT-05: The system shall increase the selected account's book balance when a receipt is posted. *[S18]*
    6. FR-RCT-06: The system shall keep each receipt separate and leave earlier payments without a bank account unchanged. *[S18]*
16. **Bank Payment Form**
    1. FR-BPY-01: The system shall let an AP clerk assign a bank account to a vendor payment, including the initial payment. *[S19]*
    2. FR-BPY-02: The system shall let the clerk record a payment to a vendor, employee, or other payee, with a payment category, not linked to AP. *[S19]*
    3. FR-BPY-03: The system shall require a bank account for Card, Transfer, and Check payments. *[S19]*
    4. FR-BPY-04: The system shall require payee and payment category for payments not linked to AP. *[S19]*
    5. FR-BPY-05: The system shall reject a payment exceeding the available bank balance or the selected AP balance. *[S19]*
    6. FR-BPY-06: The system shall decrease the account's book balance when a payment is posted. *[S19]*
    7. FR-BPY-07: The system shall not treat inventory purchases or AP settlements as operating expenses. *[S19]*
17. **Internal Transaction Ledger**
    1. FR-LED-01: The system shall create exactly one Transaction for each posted receipt or payment. *[S20]*
    2. FR-LED-02: The system shall set direction in for receipts and out for payments, with amount greater than zero. *[S20]*
    3. FR-LED-03: The system shall link each Transaction to one bank account and its source. *[S20]*
    4. FR-LED-04: The system shall start reconciliation status as Unreconciled, kept separate from posting status. *[S20]*
    5. FR-LED-05: The system shall exclude Draft Transactions from balances and prevent deletion of posted Transactions. *[S20]*
    6. FR-LED-06: The system shall backfill existing receipts and payments exactly once each. *[S20]*
    7. FR-LED-07: The system shall filter the ledger by account, direction, and date. *[S20]*
    8. FR-LED-08: The system shall calculate book balances from posted Transactions. *[S20]*
18. **Reverse Transaction Form**
    1. FR-REV-01: The system shall let an accountant reverse a receipt or payment, requiring a reason and a reference to the original Transaction. *[S21]*
    2. FR-REV-02: The system shall create an outgoing Transaction for a reversed receipt and an incoming Transaction for a reversed payment, for the same amount. *[S21]*
    3. FR-REV-03: The system shall restore bank balance, AR or AP balance, and invoice or bill status. *[S21]*
    4. FR-REV-04: The system shall keep both original and reversal visible and prevent reversing the same Transaction twice. *[S21]*
19. **Bank Transfer Form**
    1. FR-TRF-01: The system shall let an accountant move money between two different, active AutoPlex bank accounts. *[S22]*
    2. FR-TRF-02: The system shall require amount greater than zero and not above the source balance. *[S22]*
    3. FR-TRF-03: The system shall create one outgoing and one incoming Transaction sharing a transfer reference, updating both balances together. *[S22]*
    4. FR-TRF-04: The system shall exclude transfers from revenue and operating expenses. *[S22]*
20. **Bank Statement (Simulated)**
    1. FR-STM-01: The system shall create exactly one statement line per posted Transaction, with source Simulated and status Cleared. *[S23]*
    2. FR-STM-02: The system shall set a deposit for incoming and a withdrawal for outgoing Transactions, never both. *[S23]*
    3. FR-STM-03: The system shall create these lines as Matched and store the Transaction ID. *[S23]*
    4. FR-STM-04: The system shall calculate New Running Balance = Previous Running Balance + Deposit − Withdrawal, in statement-date order. *[S23]*
    5. FR-STM-05: The system shall backfill existing Transactions exactly once each and filter the list by account, month, and type. *[S23]*
21. **Statement Adjustment Form**
    1. FR-ADJ-01: The system shall let an accountant add statement-only activity of type Interest Received, Bank Service Charge, Returned Customer Payment, Vendor Refund, Automatic Loan Payment, Card Processing Fee, or Other Adjustment. *[S24]*
    2. FR-ADJ-02: The system shall require account, date, type, direction, amount, and description; default interest to incoming and bank charges to outgoing. *[S24]*
    3. FR-ADJ-03: The system shall save statement-only lines with transactionId = null, source Manual, status Cleared, and match status Unmatched, creating no Transaction and leaving book balance unchanged. *[S24]*
    4. FR-ADJ-04: The system shall update the statement running balance and require any bank reference to be unique within the account. *[S24]*
    5. FR-ADJ-05: The system shall offer an "add and post" option that creates exactly one linked Transaction and one statement line atomically, marked Matched, with no duplicate line. *[S25]*
    6. FR-ADJ-06: The system shall increase book balance for incoming and decrease it for outgoing posted adjustments. *[S25]*
22. **Reconciliation Screen** (balances)
    1. FR-REC-01: The system shall let an accountant pick a bank account and statement date. *[S26]*
    2. FR-REC-02: The system shall show Statement Closing Balance = Opening + Cleared Deposits − Cleared Withdrawals. *[S26]*
    3. FR-REC-03: The system shall show Book Closing Balance = Opening + Posted Incoming − Posted Outgoing, and Difference = Statement − Book. *[S26]*
    4. FR-REC-04: The system shall include only posted Transactions and cleared lines of the selected account through the same cutoff date, ordered by date and reference. *[S26]*
    5. FR-REC-05: The system shall clear unrelated selections when the account is switched. *[S26]*
23. **Reconciliation Matching**
    1. FR-MAT-01: The system shall suggest matches requiring same account, amount, and direction, a compatible date, and a compatible reference or description. *[S27]*
    2. FR-MAT-02: The system shall match incoming Transactions only to deposits and outgoing only to withdrawals. *[S27]*
    3. FR-MAT-03: The system shall classify results as Exact, Suggested, Missing internal Transaction, or Ambiguous, requiring manual confirmation for Ambiguous. *[S27]*
    4. FR-MAT-04: The system shall allow one Transaction to match at most one line and vice versa, and not re-suggest Reconciled Transactions. *[S27]*
    5. FR-MAT-05: The system shall, on confirming a match, mark the Transaction Reconciled and the line linked and Matched, without changing amounts. *[S28]*
    6. FR-MAT-06: The system shall record user and reconciliation date, lock reconciled records, prevent confirming the same match twice, and recalculate the difference immediately. *[S28]*
    7. FR-MAT-07: The system shall show a Post Adjustment action only on unmatched manual statement lines. *[S29]*
    8. FR-MAT-08: The system shall create the missing Transaction using the line's account, date, amount, and direction, without a second statement line, updating book balance once and marking the line Matched; the same line cannot be posted twice. *[S29]*
    9. FR-MAT-09: The system shall let only authorized users reset or reopen a reconciliation, with a required reason. *[S30]*
    10. FR-MAT-10: The system shall unlock eligible matches, restore previous statuses, delete no Transactions or lines, and record user and date. *[S30]*
    11. FR-MAT-11: The system shall require elevated permission to reopen finalized periods. *[S30]*
24. **Revenue Report Section**
    1. FR-REVN-01: The system shall calculate Total Revenue = Vehicle + Service + Fee + Interest + Other Income − Discounts. *[S31]*
    2. FR-REVN-02: The system shall take revenue from posted, non-cancelled Sales Invoices regardless of payment status. *[S31]*
    3. FR-REVN-03: The system shall exclude sales tax, AR receipts, and bank transfers. *[S31]*
    4. FR-REVN-04: The system shall take interest and other income only from posted incoming adjustments, excluding statement-only unmatched ones. *[S31]*
25. **Cost of Goods Sold Report Section**
    1. FR-COGS-01: The system shall calculate Vehicle COGS = Vehicle.totalCost, only for vehicles on posted invoices, once each. *[S32]*
    2. FR-COGS-02: The system shall calculate Parts COGS = quantity sold × cost price, remaining zero until part sale or usage records exist. *[S32]*
    3. FR-COGS-03: The system shall create no COGS for unsold inventory or AP payments and reverse COGS on cancelled sales. *[S32]*
26. **Operating Expenses Report Section**
    1. FR-OPEX-01: The system shall derive salary, bonus, and commission from employee and invoice records. *[S33]*
    2. FR-OPEX-02: The system shall include categorized bank payments and posted bank charges. *[S33]*
    3. FR-OPEX-03: The system shall exclude vehicle and parts purchases, inventory AP settlements, loan principal, tax, transfers, and revenue-reversing refunds. *[S33]*
    4. FR-OPEX-04: The system shall never count the same expense from both an accrual and a cash payment, and treat interest received as income, not negative expense. *[S33]*
27. **Profit & Loss Report**
    1. FR-PNL-01: The system shall produce a report for a selected month, quarter, or year to date. *[S34]*
    2. FR-PNL-02: The system shall show total revenue, COGS, gross profit, operating expenses, net profit, gross margin, and net margin. *[S34]*
    3. FR-PNL-03: The system shall exclude Draft and cancelled invoices. *[S34]*
    4. FR-PNL-04: The system shall let the user compare the current period with a previous, non-overlapping period using the same rules. *[S35]*
    5. FR-PNL-05: The system shall calculate Percentage Change = (Current − Previous) ÷ |Previous| × 100, shown as unavailable when previous is zero, with negative profit displayed clearly. *[S35]*
    6. FR-PNL-06: The system shall let the user drill down to the records behind each amount, with totals equal to the report amount and references retained. *[S36]*
    7. FR-PNL-07: The system shall export the report showing period, current and previous values, company name, and generation date, with totals matching the screen. *[S36]*
    8. FR-PNL-08: The system shall restrict drill-down and export of sensitive reports to authorized users and prevent editing posted records from the report without permission. *[S36]*

# Non-Functional Requirements

1. **System-wide (all features)**
    1. NFR-ALL-01: Posting shall be atomic: all related records save, or none do. *[Rules]*
    2. NFR-ALL-02: Posted records shall be reversed or cancelled, never deleted. *[Rules]*
    3. NFR-ALL-03: Money shall use decimal arithmetic, not floating point. *[Rules]*
    4. NFR-ALL-04: Every record shall keep its creation date, user, reference, and status. *[Rules]*
    5. NFR-ALL-05: Validation errors shall be shown before posting. *[Rules]*
    6. NFR-ALL-06: Each story shall be buildable, testable, and mergeable independently, depending only on earlier stories. *[Intro]*
2. **Data integrity (Invoices, Payments, AR/AP, Banking)**
    1. NFR-INT-01: Concurrent posting of the same vehicle shall result in exactly one success. *[S8]*
    2. NFR-INT-02: AR/AP and invoice/bill paid, balance, and status shall always update in one transaction. *[S11, S15]*
    3. NFR-INT-03: Backfills of Transactions and statement lines shall be idempotent (each record created once). *[S20, S23]*
    4. NFR-INT-04: Matching and posting shall be idempotent: the same match or adjustment cannot be applied twice. *[S28, S29]*
    5. NFR-INT-05: VIN, part number, invoice number, and in-account bank reference shall be enforced unique at the database level. *[S4, S6, S7, S24]*
3. **Auditability (Banking, Reconciliation, Reporting)**
    1. NFR-AUD-01: Reversals, cancellations, and reconciliation resets shall store reason, user, and date, and keep original records visible. *[S9, S21, S30]*
    2. NFR-AUD-02: Report figures shall be traceable to source records through drill-down. *[S36]*
4. **Security and privacy (Banking, Reconciliation, Reports)**
    1. NFR-SEC-01: Bank account numbers shall be masked in list views. *[S17]*
    2. NFR-SEC-02: Reset/reopen of reconciliation and drill-down/export of sensitive reports shall require authorization; reopening finalized periods shall require elevated permission. *[S30, S36]*
5. **Accuracy and consistency (Reporting, Balances)**
    1. NFR-ACC-01: Reports shall return identical results for the same period and data. *[S34]*
    2. NFR-ACC-02: Statement and book balances shall use the same cutoff date. *[S26]*
    3. NFR-ACC-03: Exports shall match on-screen totals and shall not change any data. *[S36]*
6. **Usability (Lists and forms)**
    1. NFR-USE-01: Search and filters on lists shall work in combination. *[S5, S9, S12]*
    2. NFR-USE-02: Lists and forms shall show each record's current single status clearly, including unavailable values (for example margin) rather than errors. *[S5, S35]*
7. **Maintainability (Data model)**
    1. NFR-MNT-01: Reconciliation status shall be stored separately from posting status. *[S20]*
    2. NFR-MNT-02: Later-story fields (balances, totalPurchases, bank account links) shall exist from the start with safe defaults so earlier stories need no rework. *[S1, S3, S10]*