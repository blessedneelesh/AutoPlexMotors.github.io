# AutoPlex Motors: Incremental User Stories

Each story below is small enough to build, test, and merge to main on its own. A story depends only on earlier stories. Every 'Not yet' line says what is deliberately left out and which later story adds it, so no story refers to a table that does not exist yet.

## Delivery sequence

- Phase 1, Master data: 1 Manage customers, 2 Manage employees, 3 Manage vendors
- Phase 2, Inventory: 4 Add a vehicle to inventory, 5 Browse vehicle inventory, 6 Manage parts inventory
- Phase 3, Sales invoice: 7 Create a draft sales invoice, 8 Post a sales invoice, 9 Cancel and browse sales invoices
- Phase 4, Accounts Receivable: 10 Payment condition and AR, 11 Record a later customer payment, 12 AR list and aging, 13 Customer balances
- Phase 5, Accounts Payable: 14 Vehicle purchase payment condition and AP, 15 Record a later vendor payment, 16 AP list and aging
- Phase 6, Banking: 17 Banks and bank accounts, 18 Bank receipts, 19 Bank payments, 20 Internal transaction ledger, 21 Reverse a banking transaction, 22 Transfer between accounts
- Phase 7, Simulated bank statement: 23 Generate statement lines, 24 Statement-only adjustment, 25 Add and post an adjustment
- Phase 8, Reconciliation: 26 Reconciliation data and balances, 27 Suggest matches, 28 Confirm a match, 29 Post an unmatched adjustment, 30 Reset or reopen reconciliation
- Phase 9, Reporting: 31 Revenue, 32 COGS, 33 Operating expenses, 34 Profit & Loss report, 35 Compare periods, 36 Drill-down and export

## Rules that apply to every story

- Posting is atomic: all related records save, or none do.
- Posted records are reversed or cancelled, never deleted.
- Money uses decimal arithmetic.
- Records keep their creation date, user, reference, and status.
- Validation errors are shown before posting.

## Phase 1: Master data

### Story 1: Manage customers

**Depends on:** nothing

As a salesperson,

**I want to:**

- Create, edit, and view customers (name, phone, email, address, city, state, ZIP)
- Search customers and set them Active or Inactive

**so that:**

- Sales invoices can select an existing customer

**Not yet:** balance and totalPurchases exist but stay 0 until Story 13.

**Acceptance criteria**

- First name and last name are required.
- Email must be a valid format when provided.
- New customers are Active.
- Inactive customers cannot be selected on new invoices.
- Balance and totalPurchases are read-only and default to 0.

### Story 2: Manage employees

**Depends on:** nothing

As an administrator,

**I want to:**

- Create, edit, and view employees (name, department, job, salary, bonus, commission rate, hire date, status)
- Identify which employees are salespeople

**so that:**

- Invoices can record the responsible salesperson

**Not yet:** payroll and commission expense in reports (Story 33).

**Acceptance criteria**

- First name and last name are required.
- Salary and bonus cannot be negative.
- Commission rate must be between 0 and 100 percent.
- Inactive employees cannot be assigned to new invoices.

### Story 3: Manage vendors

**Depends on:** nothing

As a purchasing officer,

**I want to:**

- Create, edit, and view vendors (name, contact, phone, email, address, type, status)
- Search vendors and set them Active or Inactive

**so that:**

- Vehicle and parts purchases can reference the supplier

**Not yet:** vendor balance and totalPurchases stay 0 until Stories 14 to 16.

**Acceptance criteria**

- Vendor name is required.
- Type is one of Vehicle, Parts, or Service.
- Inactive vendors cannot be selected on new purchases.
- Balance and totalPurchases are read-only and default to 0.

## Phase 2: Inventory

### Story 4: Add a vehicle to inventory

**Depends on:** Story 3

As a purchasing officer,

**I want to:**

- Select a vendor
- Enter VIN, make, model, year, color, purchase date, warehouse, and intended selling price
- Enter the purchase price and additional costs
- Have the system calculate the total vehicle cost

**so that:**

- The vehicle is in inventory with its full acquisition cost

```text
Total Vehicle Cost =
Purchase Price + Additional Costs
```

**Not yet:** payment condition, AP Bill, and any payment (Stories 14 and 19).

**Acceptance criteria**

- Vendor is required.
- VIN is required and unique.
- Purchase price must be greater than zero.
- Additional costs and intended selling price cannot be negative.
- Total cost equals purchase price plus additional costs.
- The vehicle is saved with Available status.

### Story 5: Browse vehicle inventory

**Depends on:** Story 4

As an inventory manager,

**I want to:**

- View all vehicles with vendor, cost, selling price, and status
- Search by VIN, make, or model, and filter by status
- See potential profit and margin per vehicle

**so that:**

- Sales staff can find available vehicles and management sees profitability

```text
Gross Profit = Selling Price − Total Vehicle Cost
Gross Margin % = Gross Profit ÷ Selling Price × 100
```

**Not yet:** Sold status, which Story 8 sets.

**Acceptance criteria**

- The list shows one current status per vehicle.
- Profit and margin use total cost, not only purchase price.
- Search and status filters work together.
- Margin shows as unavailable when the selling price is zero.

### Story 6: Manage parts inventory

**Depends on:** Story 3

As a parts inventory manager,

**I want to:**

- Create and edit parts (part number, name, category, vendor, cost price, selling price, quantity, reorder level, warehouse)
- See current inventory value and low-stock parts

**so that:**

- Parts are reordered before stock runs out

**Not yet:** quantity changes from sales or usage, and parts COGS (Story 32). Quantity is edited manually for now.

**Acceptance criteria**

- Part number is required and unique.
- Vendor is required.
- Prices and quantity cannot be negative.
- A part is low stock when quantity is at or below its reorder level.
- Inventory value equals quantity × cost price.

## Phase 3: Sales invoice

### Story 7: Create a draft sales invoice

**Depends on:** Stories 1, 2, 4

As a salesperson,

**I want to:**

- Select an existing customer and an available vehicle
- See the vehicle's VIN, make and model, selling price, and inventory cost
- Assign the responsible salesperson
- Enter sale price, discount, tax, fees, invoice date, and due date
- Have the system calculate the invoice total and save a Draft

**so that:**

- The sale is prepared and checked before it is posted

```text
Invoice Total =
Sale Price + Tax + Fees − Discount
```

**Not yet:** posting, vehicle status change, payments, AR, receipts, bank, and statement (Stories 8, 10, 18).

**Acceptance criteria**

- Only vehicles with Available status can be selected.
- Customer, salesperson, vehicle, invoice date, and sale price are required.
- The discount cannot exceed the sale price.
- The invoice total must be greater than zero.
- A Draft invoice has paid = 0, balance = total, and does not change the vehicle.
- Each invoice gets a unique number.

### Story 8: Post a sales invoice

**Depends on:** Story 7

As a salesperson,

**I want to:**

- Validate and confirm posting of a Draft invoice
- Have the vehicle marked as Sold and linked to the invoice

**so that:**

- The vehicle cannot be sold twice
- Revenue and COGS can be reported later

**Not yet:** payment condition and AR (Story 10). Posted invoices start as Unpaid.

**Acceptance criteria**

- Only Draft invoices can be posted.
- Validation runs again at posting and errors are shown before saving.
- Posting changes the vehicle status to Sold and stores the invoice ID on the vehicle.
- A Sold vehicle no longer appears in the available-vehicle selector.
- If two invoices try to post the same vehicle, only one succeeds.
- Posted invoices cannot be edited or deleted.

### Story 9: Cancel and browse sales invoices

**Depends on:** Story 8

As a salesperson,

**I want to:**

- Cancel a posted invoice with a reason
- List, search, and open invoices

**so that:**

- Mistakes are corrected without losing history
- The vehicle can return to inventory

**Not yet:** cancelling invoices that already have payments (Story 21).

**Acceptance criteria**

- Cancelling sets the status to Cancelled and the vehicle back to Available.
- Only invoices with paid = 0 can be cancelled.
- A reason is required.
- The list searches by number, customer, VIN, and status, and filters by date.
- Cancelled invoices stay visible.

## Phase 4: Accounts Receivable

### Story 10: Payment condition and AR

**Depends on:** Story 8

As a salesperson,

**I want to:**

- Record whether the customer paid in full, paid partially, or bought on credit
- Enter the amount received, payment method, and reference
- Have AR created only when a balance remains

**so that:**

- Fully paid invoices create no unnecessary AR records
- Outstanding balances appear in Accounts Receivable

The initial amount is saved as a Customer Payment record (invoice, date, amount, method, reference). It has no bank account yet.

**Not yet:** bank account, bank receipt, transaction, and statement line (Stories 18, 20, 23).

**Acceptance criteria**

- Paid in full: paid = total, balance = 0, status Paid, no AR record.
- Partial payment: balance = total − paid, status Partial, AR created.
- Credit sale: paid = 0, status Unpaid, AR created, no Customer Payment.
- The AR amount, paid, and balance match the Sales Invoice.
- Amount received cannot be negative or exceed the total.
- Method is one of Cash, Card, Transfer, or Check.

### Story 11: Record a later customer payment

**Depends on:** Story 10

As an accounts receivable clerk,

**I want to:**

- Select an open AR invoice and enter the date, amount, method, and reference
- See the payment history on the invoice

**so that:**

- AR and invoice balances stay current

**Not yet:** bank account (Story 18).

**Acceptance criteria**

- Amount must be greater than zero.
- Amount cannot exceed the AR balance.
- Each payment creates a separate Customer Payment record.
- AR and Sales Invoice paid, balance, and status update together.
- Full payment sets Paid. Partial payment sets Partial.
- Previous payments are never overwritten.

### Story 12: AR list and aging

**Depends on:** Story 10

As an accountant,

I want to view outstanding AR with days overdue and status

**so that:**

- I know which customers owe money and how late they are

**Acceptance criteria**

- The list shows customer, invoice, due date, amount, paid, balance, days, and status.
- Days overdue is the as-of date minus the due date, never below zero.
- An open AR with a past due date shows Overdue.
- The list filters by status and customer.

### Story 13: Customer balances

**Depends on:** Stories 10, 11

As an accountant,

I want customer balance and total purchases kept up to date

**so that:**

- Each customer's outstanding amount is visible

**Acceptance criteria**

- Customer balance equals the sum of that customer's open AR balances.
- Total purchases equals the sum of posted, non-cancelled invoice totals.
- Both update on posting, payment, and cancellation.
- Balance is never negative.

## Phase 5: Accounts Payable

### Story 14: Vehicle purchase payment condition and AP

**Depends on:** Story 4

As a purchasing officer,

**I want to:**

- Record whether the vehicle was paid in full, paid partially, or bought on credit
- Enter the amount paid now, method, and reference
- Have an AP Bill created only when a vendor balance remains

**so that:**

- Unpaid vendor balances appear in Accounts Payable
- Inventory cost is unaffected by payment

The initial amount is saved as a Vendor Payment record with no bank account yet.

```text
Vehicle cost:      $40,000
Immediate payment: $15,000
AP Bill: amount $40,000, paid $15,000, balance $25,000, status Partial
```

**Not yet:** bank account, bank payment, transaction, and statement line (Stories 19, 20, 23).

**Acceptance criteria**

- Paid in full creates no AP Bill.
- Partial and credit purchases create an AP Bill.
- The AP amount equals the vehicle total cost.
- Amount paid now cannot be negative or exceed the total cost.
- Vehicle total cost does not change when the AP Bill is paid.

### Story 15: Record a later vendor payment

**Depends on:** Story 14

As an accounts payable clerk,

**I want to:**

- Select an open AP Bill and enter the date, amount, method, and reference
- See the payment history on the bill

**so that:**

- AP and vendor balances stay current

**Not yet:** bank account and balance check (Story 19).

**Acceptance criteria**

- Amount must be greater than zero.
- Amount cannot exceed the AP balance.
- Each installment creates a separate Vendor Payment record.
- AP paid, balance, and status update together.
- Vendor outstanding balance updates.

### Story 16: AP list and aging

**Depends on:** Story 14

As an accountant,

I want to view open AP Bills with days overdue and status

**so that:**

- I know what we owe and when it is due

**Acceptance criteria**

- The list shows vendor, bill, due date, amount, paid, balance, days, and status.
- Days overdue is never below zero.
- An open bill with a past due date shows Overdue.
- Vendor outstanding balance equals the sum of that vendor's open AP balances.

## Phase 6: Banking

### Story 17: Banks and bank accounts

**Depends on:** nothing (can be built in parallel with earlier phases)

As an accountant,

**I want to:**

- Create and maintain banks
- Add accounts under each bank (name, account number, routing number, type, opening balance, status)
- See each account's current book balance

**so that:**

- AutoPlex can track cash held at different institutions

**Not yet:** receipts, payments, transactions, and statements.

**Acceptance criteria**

- A Bank Account must belong to a Bank.
- Account name and account type are required.
- Opening balance cannot be negative.
- Book balance starts equal to the opening balance.
- Account numbers are masked in lists.
- Inactive accounts are saved but cannot be used in later stories.

### Story 18: Bank receipts

**Depends on:** Stories 11, 17

As an accounts receivable clerk,

**I want to:**

- Assign a bank account to a customer payment, including the initial payment in Story 10
- Record a receipt from another payer that is not linked to AR

**so that:**

- Customer money is deposited into the correct account
- The bank-account balance increases

Customer Payment records become Bank Receipts. Earlier payments without a bank account stay as they are.

**Not yet:** internal transaction and statement line (Stories 20, 23).

**Acceptance criteria**

- A bank account is required for Card, Transfer, and Check receipts.
- Inactive accounts are rejected.
- A posted receipt increases the selected account's book balance.
- Receipt amount cannot exceed the selected AR balance.
- A receipt not linked to AR does not change any customer balance.
- Each receipt is separate and previous receipts are never overwritten.

### Story 19: Bank payments

**Depends on:** Stories 15, 17

As an accounts payable clerk,

**I want to:**

- Assign a bank account to a vendor payment, including the initial payment in Story 14
- Record a payment to a vendor, employee, or other payee, with a payment category, not linked to AP

**so that:**

- Money paid out reduces the correct account
- Expenses carry a category for reporting

**Not yet:** internal transaction and statement line (Stories 20, 23).

**Acceptance criteria**

- A bank account is required for Card, Transfer, and Check payments.
- Payee and payment category are required for payments not linked to AP.
- Payment cannot exceed the available bank balance.
- Payment cannot exceed the selected AP balance.
- A posted payment decreases the account's book balance.
- Inventory purchases and AP settlements are not treated as operating expenses.

### Story 20: Internal transaction ledger

**Depends on:** Stories 18, 19

As an accountant,

I want every bank receipt and payment recorded as an internal Transaction

**so that:**

- Every bank movement can be audited
- Book balances can be calculated from transactions

**Not yet:** statement lines and reconciliation status changes (Stories 23, 28).

**Acceptance criteria**

- Each posted receipt or payment creates exactly one Transaction.
- Direction is in for receipts and out for payments, and amount is greater than zero.
- Each Transaction references one bank account and its source.
- Reconciliation status starts as Unreconciled and is kept separate from posting status.
- Draft Transactions do not affect balances.
- Posted Transactions cannot be deleted.
- Existing receipts and payments are backfilled, once each.
- The list filters by account, direction, and date.

### Story 21: Reverse a banking transaction

**Depends on:** Story 20

As an accountant,

I want to reverse an incorrect receipt or payment

**so that:**

- History is preserved and balances are corrected
- AR or AP balances are restored

This also lets Story 9 cancel invoices that were paid, after their receipts are reversed.

**Acceptance criteria**

- A reversal requires a reason and references the original Transaction.
- A reversed receipt creates an outgoing Transaction. A reversed payment creates an incoming Transaction.
- The reversal amount equals the amount being reversed.
- Bank balance, AR or AP balance, and invoice or bill status are restored.
- The original and the reversal both stay visible.
- The same Transaction cannot be reversed twice.

### Story 22: Transfer between bank accounts

**Depends on:** Story 20

As an accountant,

I want to move money between two AutoPlex bank accounts

**so that:**

- Cash can move between operating, payroll, and savings accounts
- Total cash does not change

**Not yet:** statement lines for each side (Story 23).

**Acceptance criteria**

- Source and destination must be different, active accounts.
- Amount must be greater than zero and not exceed the source balance.
- One outgoing and one incoming Transaction share a transfer reference.
- Both balances update together.
- A transfer does not affect revenue or operating expenses.

## Phase 7: Simulated bank statement

### Story 23: Generate statement lines

**Depends on:** Stories 20, 22

As an accountant,

I want a simulated bank statement line for each posted Transaction

**so that:**

- The statement can later be compared with the internal ledger

```text
New Running Balance =
Previous Running Balance + Deposit − Withdrawal
```

**Acceptance criteria**

- Each Transaction creates exactly one line with source Simulated and status Cleared.
- Incoming Transactions set a deposit and outgoing set a withdrawal. Never both.
- Lines created from Transactions start as Matched and store the Transaction ID.
- Running balance is calculated in statement-date order.
- Existing Transactions are backfilled, once each.
- The list filters by account, month, and type.

### Story 24: Statement-only adjustment

**Depends on:** Story 23

As an accountant,

I want to add bank-originated activity such as interest, charges, and refunds to the statement only

**so that:**

- The statement can differ from the books until reconciliation

Types: Interest Received, Bank Service Charge, Returned Customer Payment, Vendor Refund, Automatic Loan Payment, Card Processing Fee, Other Adjustment.

```text
transactionId = null
source = Manual
statementStatus = Cleared
matchStatus = Unmatched
```

**Acceptance criteria**

- Account, date, type, direction, amount, and description are required.
- Interest defaults to incoming and bank charges to outgoing.
- No Transaction is created and the book balance does not change.
- The statement running balance updates.
- A bank reference is unique within the account when provided.

### Story 25: Add and post an adjustment to books

**Depends on:** Story 24

As an accountant,

I want to add an adjustment and post its internal Transaction at the same time

**so that:**

- Known interest and charges are recorded in both places immediately

**Acceptance criteria**

- Exactly one Transaction and one statement line are created and linked.
- The line is marked Matched.
- Book balance increases for incoming and decreases for outgoing adjustments.
- No duplicate statement line is created.
- Posting is atomic.

## Phase 8: Reconciliation

### Story 26: Reconciliation data and balances

**Depends on:** Stories 23, 24

As an accountant,

I want to pick a bank account and statement date and see book and statement balances

**so that:**

- I can see the difference between the ledger and the statement

```text
Statement Closing Balance =
Statement Opening Balance + Cleared Deposits − Cleared Withdrawals

Book Closing Balance =
Book Opening Balance + Posted Incoming − Posted Outgoing

Difference =
Statement Closing Balance − Book Closing Balance
```

**Acceptance criteria**

- Only posted Transactions and cleared lines through the selected date are included.
- Transactions and lines from other accounts are excluded.
- Both balances use the same cutoff date.
- Unmatched statement lines change only the statement balance.
- Data is ordered by date and reference.
- Switching accounts clears unrelated selections.

### Story 27: Suggest matches

**Depends on:** Story 26

As an accountant,

I want suggested matches between Transactions and statement lines

**so that:**

- I do not compare every record by hand

**Acceptance criteria**

- A match requires the same account, amount, and direction, a compatible date, and a compatible reference or description.
- Incoming Transactions match only deposits. Outgoing match only withdrawals.
- Results are Exact, Suggested, Missing internal Transaction, or Ambiguous.
- One Transaction matches at most one line, and one line at most one Transaction.
- Reconciled Transactions are not suggested again.
- Ambiguous matches need manual confirmation.

### Story 28: Confirm a match

**Depends on:** Story 27

As an accountant,

I want to confirm a suggested match

**so that:**

- Both records are marked reconciled and cannot be reconciled twice

**Acceptance criteria**

- The Transaction becomes Reconciled and the line is linked and Matched.
- Amounts are never changed by matching.
- User and reconciliation date are kept.
- Reconciled records are locked.
- The same match cannot be confirmed twice.
- The difference recalculates immediately.

### Story 29: Post an unmatched adjustment

**Depends on:** Stories 25, 28

As an accountant,

I want to create the missing Transaction for an unmatched statement line

**so that:**

- The book balance is corrected and the difference is resolved

**Acceptance criteria**

- Post Adjustment appears only on unmatched manual statement lines.
- The new Transaction uses the line's account, date, amount, and direction.
- No second statement line is created.
- Book balance updates once and the line becomes Matched.
- The same line cannot be posted twice.

### Story 30: Reset or reopen reconciliation

**Depends on:** Story 28

As an authorized accountant,

I want to reset or reopen a reconciliation

**so that:**

- Wrong matches can be fixed with an audit trail

**Acceptance criteria**

- Only authorized users can reset, and a reason is required.
- Eligible matches unlock and statuses return to their previous state.
- No Transactions or statement lines are deleted.
- User and date are recorded.
- Finalized periods need elevated permission to reopen.

## Phase 9: Reporting

### Story 31: Revenue

**Depends on:** Stories 8, 25

As a financial controller,

I want revenue calculated from posted business records

**so that:**

- Collections are not counted twice and tax is not reported as income

```text
Total Revenue =
Vehicle Revenue + Service Revenue + Fee Income
+ Interest Income + Other Income − Discounts
```

**Acceptance criteria**

- Revenue comes from posted, non-cancelled Sales Invoices, regardless of payment status.
- Sales tax, AR receipts, and bank transfers are excluded.
- Interest and other income come from posted incoming adjustments only.
- Statement-only unmatched adjustments are excluded.

### Story 32: Cost of goods sold

**Depends on:** Stories 6, 8

As a financial controller,

I want COGS calculated from the cost of inventory sold

**so that:**

- Gross profit reflects true cost

```text
Vehicle COGS = Vehicle.totalCost
Parts COGS = Actual quantity sold × Cost Price
```

**Acceptance criteria**

- Only vehicles on posted invoices are included, once each.
- Unsold inventory and AP payments create no COGS.
- Cancelled sales reverse their COGS.
- Parts COGS stays zero until part sale or usage records exist.

### Story 33: Operating expenses

**Depends on:** Stories 2, 19, 25

As a financial controller,

I want operating expenses from payroll and categorized payments

**so that:**

- Inventory and loan payments are not expensed

**Acceptance criteria**

- Salary, bonus, and commission come from employee and invoice records.
- Categorized bank payments and posted bank charges are included.
- Vehicle and parts purchases, AP settlements for inventory, loan principal, tax, transfers, and revenue-reversing refunds are excluded.
- The same expense is never counted from both an accrual and a cash payment.
- Interest received is income, not a negative expense.

### Story 34: Profit & Loss report

**Depends on:** Stories 31, 32, 33

As a financial controller,

I want a Profit & Loss report for a selected month, quarter, or year to date

**so that:**

- I can evaluate profitability

**Acceptance criteria**

- Shows total revenue, COGS, gross profit, operating expenses, net profit, gross margin, and net margin.
- Draft and cancelled invoices are excluded.
- Results are the same for the same period and data.

### Story 35: Compare periods

**Depends on:** Story 34

As a financial controller,

I want to compare the current period with a previous one

**so that:**

- I can see growth, decline, and margin changes

```text
Percentage Change =
(Current − Previous) ÷ Absolute Previous × 100
```

**Acceptance criteria**

- Periods do not overlap and use the same rules.
- Change shows as unavailable when the previous amount is zero.
- Negative profit displays clearly.

### Story 36: Drill-down and export

**Depends on:** Story 34

As an accountant,

I want to open the records behind each amount and export the report

**so that:**

- Every figure is auditable and shareable

**Acceptance criteria**

- Drill-down totals equal the report amount, and records keep their references.
- Posted records cannot be edited from the report without permission.
- Exports show the period, current and previous values, company name, and generation date.
- Exported totals match the screen, and exporting changes no data.
- Only authorized users can drill down into or export sensitive reports.