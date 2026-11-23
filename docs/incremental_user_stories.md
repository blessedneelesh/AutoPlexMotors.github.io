# AutoPlex Motors: Incremental User Stories

Each story below is small enough to build, test, and merge to main on its own. A story depends only on earlier stories. Every **Not yet** line says what is deliberately left out and which later story adds it, so no story refers to a table that does not exist yet.

Banking is built before receivables and payables. Every customer payment is saved directly as a Bank Receipt, and every vendor payment directly as a Bank Payment. No temporary payment tables are needed and nothing has to be migrated later.

## Delivery sequence

- Phase 1, Master data: 1 Manage customers, 2 Manage employees, 3 Manage vendors
- Phase 2, Inventory: 4 Add a vehicle to inventory, 5 Browse vehicle inventory, 6 Manage parts inventory
- Phase 3, Banking foundation: 7 Banks and bank accounts, 8 Internal transaction ledger, 9 Simulated statement lines, 10 Transfer between accounts
- Phase 4, Sales invoice: 11 Create a draft sales invoice, 12 Post a sales invoice, 13 Cancel and browse sales invoices
- Phase 5, Accounts Receivable: 14 Payment condition, receipt, and AR, 15 Record a later customer payment, 16 Record a receipt not linked to AR, 17 AR list and aging, 18 Customer balances
- Phase 6, Accounts Payable: 19 Vehicle purchase payment condition and AP, 20 Record a later vendor payment, 21 Record a payment not linked to AP, 22 AP list and aging
- Phase 7, Corrections: 23 Reverse a banking transaction
- Phase 8, Statement adjustments: 24 Statement-only adjustment, 25 Add and post an adjustment
- Phase 9, Reporting: 26 Revenue, 27 COGS, 28 Operating expenses, 29 Profit & Loss report, 30 Compare periods, 31 Drill-down and export

## Rules that apply to every story

- Posting is atomic: all related records save, or none do.
- Posted records are reversed or cancelled, never deleted.
- Money uses decimal arithmetic.
- Records keep their creation date, user, reference, and status.
- Validation errors are shown before posting.
- Every receipt and payment has a bank account. Cash uses a Cash on hand account.
- Every posted receipt, payment, transfer, and adjustment creates exactly one Transaction and one statement line.

## Data model notes

- Bank Receipt links to the Sales Invoice (`salesInvoiceId`) and, when one exists, the AR Invoice (`arInvoiceId`). A fully paid sale has no AR Invoice, so the Sales Invoice link is what ties its receipt to the sale.
- Bank Payment links to the Vehicle (`vehicleId`) and, when one exists, the AP Bill (`apBillId`), for the same reason.
- No Customer Payment or Vendor Payment table is used.

## Phase 1: Master data

### Story 1: Manage customers

**Depends on:** nothing

As a salesperson,

**I want to:**

- Create, edit, and view customers (name, phone, email, address, city, state, ZIP)
- Search customers and set them Active or Inactive

**so that:**

- Sales invoices can select an existing customer

**Not yet:** balance and totalPurchases exist but stay 0 until Story 18.

**Acceptance criteria**

1. First name and last name are required.
2. Email must be a valid format when provided.
3. New customers are Active.
4. Inactive customers cannot be selected on new invoices.
5. Balance and totalPurchases are read-only and default to 0.

### Story 2: Manage employees

**Depends on:** nothing

As an administrator,

**I want to:**

- Create, edit, and view employees (name, department, job, salary, bonus, commission rate, hire date, status)
- Identify which employees are salespeople

**so that:**

- Invoices can record the responsible salesperson

**Not yet:** payroll and commission expense in reports (Story 28).

**Acceptance criteria**

1. First name and last name are required.
2. Salary and bonus cannot be negative.
3. Commission rate must be between 0 and 100 percent.
4. Inactive employees cannot be assigned to new invoices.

### Story 3: Manage vendors

**Depends on:** nothing

As a purchasing officer,

**I want to:**

- Create, edit, and view vendors (name, contact, phone, email, address, type, status)
- Search vendors and set them Active or Inactive

**so that:**

- Vehicle and parts purchases can reference the supplier

**Not yet:** vendor balance and totalPurchases stay 0 until Stories 19 to 22.

**Acceptance criteria**

1. Vendor name is required.
2. Type is one of Vehicle, Parts, or Service.
3. Inactive vendors cannot be selected on new purchases.
4. Balance and totalPurchases are read-only and default to 0.

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

**Not yet:** payment condition, AP Bill, and any payment (Story 19).

**Acceptance criteria**

1. Vendor is required.
2. VIN is required and unique.
3. Purchase price must be greater than zero.
4. Additional costs and intended selling price cannot be negative.
5. Total cost equals purchase price plus additional costs.
6. The vehicle is saved with Available status.

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

**Not yet:** Sold status, which Story 12 sets.

**Acceptance criteria**

1. The list shows one current status per vehicle.
2. Profit and margin use total cost, not only purchase price.
3. Search and status filters work together.
4. Margin shows as unavailable when the selling price is zero.

### Story 6: Manage parts inventory

**Depends on:** Story 3

As a parts inventory manager,

**I want to:**

- Create and edit parts (part number, name, category, vendor, cost price, selling price, quantity, reorder level, warehouse)
- See current inventory value and low-stock parts

**so that:**

- Parts are reordered before stock runs out

**Not yet:** quantity changes from sales or usage, and parts COGS (Story 27). Quantity is edited manually for now.

**Acceptance criteria**

1. Part number is required and unique.
2. Vendor is required.
3. Prices and quantity cannot be negative.
4. A part is low stock when quantity is at or below its reorder level.
5. Inventory value equals quantity × cost price.

## Phase 3: Banking foundation

### Story 7: Banks and bank accounts

**Depends on:** nothing (can be built in parallel with Phases 1 and 2)

As an accountant,

**I want to:**

- Create and maintain banks
- Add accounts under each bank (name, account number, routing number, type, opening balance, status)
- See each account's current book balance

**so that:**

- AutoPlex can track cash held at different institutions

**Not yet:** transactions and statement lines (Stories 8 and 9), receipts (Story 14), and payments (Story 19).

**Acceptance criteria**

1. A Bank Account must belong to a Bank.
2. Account name and account type are required.
3. Opening balance cannot be negative.
4. Book balance starts equal to the opening balance.
5. Account numbers are masked in lists.
6. Inactive accounts are saved but cannot be used in later stories.
7. Type includes Cash on hand, so cash receipts and payments also have an account.

### Story 8: Internal transaction ledger

**Depends on:** Story 7

As an accountant,

**I want to:**

- Record every bank movement as an internal Transaction through one posting service
- Have each posted Transaction update its account's book balance
- List and filter Transactions

**so that:**

- Every bank movement can be audited
- Book balances can be calculated from transactions
- Transfers, receipts, payments, adjustments, and reversals all post the same way

**Not yet:** the screens that create Transactions: transfers (Story 10), receipts (Stories 14 to 16), payments (Stories 19 to 21), adjustments (Story 25), and reversals (Story 23). This story is tested through the posting service until Story 10 adds the first screen.

**Acceptance criteria**

1. Direction is in or out, and amount is greater than zero.
2. Each Transaction references one active bank account and records its source type and source number.
3. A posted incoming Transaction increases the book balance. A posted outgoing Transaction decreases it.
4. An outgoing Transaction cannot exceed the account's book balance.
5. Draft Transactions do not affect balances.
6. Posted Transactions cannot be edited or deleted.
7. The list filters by account, direction, and date.

### Story 9: Simulated statement lines

**Depends on:** Story 8

As an accountant,

**I want to:** have a simulated bank statement line created automatically for each posted Transaction

**so that:**

- The statement can later be compared with the internal ledger

```text
New Running Balance =
Previous Running Balance + Deposit − Withdrawal
```

**Not yet:** statement-only adjustments (Story 24).

**Acceptance criteria**

1. Each posted Transaction creates exactly one line in the same save, with source Simulated and status Cleared.
2. Incoming Transactions set a deposit and outgoing set a withdrawal. Never both.
3. Lines created from Transactions start as Matched and store the Transaction ID.
4. Running balance is calculated in statement-date order.
5. No backfill is needed, because no receipts or payments exist before this story.
6. The list filters by account, month, and type.

### Story 10: Transfer between bank accounts

**Depends on:** Story 9

As an accountant,

**I want to:** move money between two AutoPlex bank accounts

**so that:**

- Cash can move between operating, payroll, and savings accounts
- Total cash does not change

**Acceptance criteria**

1. Source and destination must be different, active accounts.
2. Amount must be greater than zero and not exceed the source balance.
3. One outgoing and one incoming Transaction share a transfer reference.
4. Both balances update together.
5. A transfer does not affect revenue or operating expenses.
6. Each side gets its own statement line.

## Phase 4: Sales invoice

### Story 11: Create a draft sales invoice

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

**Not yet:** posting, vehicle status change, payments, AR, receipts, bank, and statement (Stories 12 and 14).

**Acceptance criteria**

1. Only vehicles with Available status can be selected.
2. Customer, salesperson, vehicle, invoice date, and sale price are required.
3. The discount cannot exceed the sale price.
4. The invoice total must be greater than zero.
5. A Draft invoice has paid = 0, balance = total, and does not change the vehicle.
6. Each invoice gets a unique number.

### Story 12: Post a sales invoice

**Depends on:** Story 11

As a salesperson,

**I want to:**

- Validate and confirm posting of a Draft invoice
- Have the vehicle marked as Sold and linked to the invoice

**so that:**

- The vehicle cannot be sold twice
- Revenue and COGS can be reported later

**Not yet:** payment condition, receipt, and AR (Story 14). Posted invoices start as Unpaid.

**Acceptance criteria**

1. Only Draft invoices can be posted.
2. Validation runs again at posting and errors are shown before saving.
3. Posting changes the vehicle status to Sold and stores the invoice ID on the vehicle.
4. A Sold vehicle no longer appears in the available-vehicle selector.
5. If two invoices try to post the same vehicle, only one succeeds.
6. Posted invoices cannot be edited or deleted.

### Story 13: Cancel and browse sales invoices

**Depends on:** Story 12

As a salesperson,

**I want to:**

- Cancel a posted invoice with a reason
- List, search, and open invoices

**so that:**

- Mistakes are corrected without losing history
- The vehicle can return to inventory

**Not yet:** cancelling invoices that already have payments (Story 23).

**Acceptance criteria**

1. Cancelling sets the status to Cancelled and the vehicle back to Available.
2. Only invoices with paid = 0 can be cancelled.
3. A reason is required.
4. The list searches by number, customer, VIN, and status, and filters by date.
5. Cancelled invoices stay visible.

### Story 13.1: View a customer's sales invoices

As a salesperson or accountant, I want to list all sales invoices for one customer, so that I can review what they bought, what they owe, and follow up on unpaid invoices.

**Acceptance criteria**

- `GET /SalesInvoice/GetSalesInvoiceByCustomer?customerId=` returns that customer's invoices as 200.
- A customer with no invoices returns 200 with empty items, not 404.
- The response is NOT paged (PageNumber, PageSize, capped by the existing RequestParameters limit) and ordered by invoice date, newest first, then by number.
- Each item has the same fields as GetSalesInvoiceByCustomer with attributes:

  | Invoice_Number | Invoice_Date | Vehicle | Salesperson | Amount | Paid | Payment_Status |
  | -------------- | ------------ | ------- | ----------- | ------ | ---- | -------------- |

- An unknown customerId returns an empty list, not an error.
- It is read-only: nothing is written or changed.

## Phase 5: Accounts Receivable

### Story 14: Payment condition, receipt, and AR

**Depends on:** Stories 9, 12

As a salesperson,

**I want to:**

- Record whether the customer paid in full, paid partially, or bought on credit
- Enter the amount received, payment method, reference, and the bank account it goes into
- Have AR created only when a balance remains

**so that:**

- Fully paid invoices create no unnecessary AR records
- Outstanding balances appear in Accounts Receivable
- Money received shows in the correct account straight away

The amount received is saved as a Bank Receipt linked to the Sales Invoice, and to the AR Invoice when one is created. The receipt posts its Transaction and statement line through Stories 8 and 9.

**Not yet:** later payments (Story 15) and customer balances (Story 18).

**Acceptance criteria**

1. Paid in full: paid = total, balance = 0, status Paid, one Bank Receipt, no AR record.
2. Partial payment: balance = total − paid, status Partial, one Bank Receipt, AR created.
3. Credit sale: paid = 0, status Unpaid, AR created, no Bank Receipt.
4. The AR amount, paid, and balance match the Sales Invoice.
5. Amount received cannot be negative or exceed the total.
6. Method is one of Cash, Card, Transfer, or Check.
7. A bank account is required whenever an amount is received. Inactive accounts are rejected.
8. The invoice, AR, Bank Receipt, Transaction, statement line, and book balance save together.

### Story 15: Record a later customer payment

**Depends on:** Story 14

As an accounts receivable clerk,

**I want to:**

- Select an open AR invoice and enter the date, amount, method, reference, and bank account
- See the payment history on the invoice

**so that:**

- AR and invoice balances stay current
- Customer money is deposited into the correct account

**Acceptance criteria**

1. Amount must be greater than zero.
2. Amount cannot exceed the AR balance.
3. Each payment creates a separate Bank Receipt with its own Transaction and statement line.
4. AR and Sales Invoice paid, balance, and status update together.
5. Full payment sets Paid. Partial payment sets Partial.
6. A bank account is required. Inactive accounts are rejected.
7. The selected account's book balance increases.
8. Previous receipts are never overwritten.

### Story 16: Record a receipt not linked to AR

**Depends on:** Story 9

As an accounts receivable clerk,

**I want to:** record money received from another payer that is not linked to an invoice

**so that:**

- All money received is recorded in the correct account

**Acceptance criteria**

1. Payer, date, amount, method, bank account, and description are required.
2. Amount must be greater than zero.
3. The receipt does not change any customer, invoice, or AR balance.
4. The receipt creates one Transaction and one statement line and increases the book balance.
5. Inactive accounts are rejected.
6. Each receipt is separate and previous receipts are never overwritten.

### Story 17: AR list and aging

**Depends on:** Story 14

As an accountant,

**I want to:** view outstanding AR with days overdue and status

**so that:**

- I know which customers owe money and how late they are

**Acceptance criteria**

1. The list shows customer, invoice, due date, amount, paid, balance, days, and status.
2. Days overdue is the as-of date minus the due date, never below zero.
3. An open AR with a past due date shows Overdue.
4. The list filters by status and customer.

### Story 18: Customer balances

**Depends on:** Stories 14, 15

As an accountant,

**I want to:** keep customer balance and total purchases up to date

**so that:**

- Each customer's outstanding amount is visible

**Acceptance criteria**

1. Customer balance equals the sum of that customer's open AR balances.
2. Total purchases equals the sum of posted, non-cancelled invoice totals.
3. Both update on posting, payment, and cancellation.
4. Balance is never negative.

## Phase 6: Accounts Payable

### Story 19: Vehicle purchase payment condition and AP

**Depends on:** Stories 4, 9

As a purchasing officer,

**I want to:**

- Record whether the vehicle was paid in full, paid partially, or bought on credit
- Enter the amount paid now, method, reference, and the bank account it comes from
- Have an AP Bill created only when a vendor balance remains

**so that:**

- Unpaid vendor balances appear in Accounts Payable
- Inventory cost is unaffected by payment

The amount paid now is saved as a Bank Payment linked to the vehicle, and to the AP Bill when one is created. The payment posts its Transaction and statement line through Stories 8 and 9.

```text
Vehicle cost:      $40,000
Immediate payment: $15,000
AP Bill: amount $40,000, paid $15,000, balance $25,000, status Partial
```

**Not yet:** later vendor payments (Story 20).

**Acceptance criteria**

1. Paid in full creates no AP Bill.
2. Partial and credit purchases create an AP Bill.
3. The AP amount equals the vehicle total cost.
4. Amount paid now cannot be negative or exceed the total cost.
5. Vehicle total cost does not change when the AP Bill is paid.
6. A bank account is required whenever an amount is paid, and the payment cannot exceed its book balance.
7. The AP Bill, Bank Payment, Transaction, statement line, and book balance save together.

### Story 20: Record a later vendor payment

**Depends on:** Story 19

As an accounts payable clerk,

**I want to:**

- Select an open AP Bill and enter the date, amount, method, reference, and bank account
- See the payment history on the bill

**so that:**

- AP and vendor balances stay current

**Acceptance criteria**

1. Amount must be greater than zero.
2. Amount cannot exceed the AP balance.
3. Each installment creates a separate Bank Payment with its own Transaction and statement line.
4. AP paid, balance, and status update together.
5. Vendor outstanding balance updates.
6. The payment cannot exceed the bank account's book balance.
7. Previous payments are never overwritten.

### Story 21: Record a payment not linked to AP

**Depends on:** Story 9

As an accounts payable clerk,

**I want to:** record a payment to a vendor, employee, or other payee, with a payment category, that is not linked to AP

**so that:**

- Money paid out reduces the correct account
- Expenses carry a category for reporting

**Acceptance criteria**

1. Payee, payment category, date, amount, method, and bank account are required.
2. Payment cannot exceed the available bank balance.
3. The payment creates one Transaction and one statement line and decreases the book balance.
4. Inventory purchases and AP settlements are not treated as operating expenses.
5. Each payment is separate and previous payments are never overwritten.

### Story 22: AP list and aging

**Depends on:** Story 19

As an accountant,

**I want to:** view open AP Bills with days overdue and status

**so that:**

- I know what we owe and when it is due

**Acceptance criteria**

1. The list shows vendor, bill, due date, amount, paid, balance, days, and status.
2. Days overdue is never below zero.
3. An open bill with a past due date shows Overdue.
4. Vendor outstanding balance equals the sum of that vendor's open AP balances.

## Phase 7: Corrections

### Story 23: Reverse a banking transaction

**Depends on:** Stories 15, 16, 20, 21

As an accountant,

**I want to:** reverse an incorrect receipt or payment

**so that:**

- History is preserved and balances are corrected
- AR or AP balances are restored

This also lets Story 13 cancel invoices that were paid, after their receipts are reversed.

**Acceptance criteria**

1. A reversal requires a reason and references the original Transaction.
2. A reversed receipt creates an outgoing Transaction. A reversed payment creates an incoming Transaction.
3. The reversal amount equals the amount being reversed.
4. Bank balance, AR or AP balance, and invoice or bill status are restored.
5. The original and the reversal both stay visible.
6. The same Transaction cannot be reversed twice.
7. The reversal Transaction gets its own statement line.

## Phase 8: Statement adjustments

### Story 24: Statement-only adjustment

**Depends on:** Story 9

As an accountant,

**I want to:** add bank-originated activity such as interest, charges, and refunds to the statement only

**so that:**

- The statement can show bank-originated activity before it is recorded in the books

Types: Interest Received, Bank Service Charge, Returned Customer Payment, Vendor Refund, Automatic Loan Payment, Card Processing Fee, Other Adjustment.

```text
transactionId = null
source = Manual
statementStatus = Cleared
matchStatus = Unmatched
```

**Acceptance criteria**

1. Account, date, type, direction, amount, and description are required.
2. Interest defaults to incoming and bank charges to outgoing.
3. No Transaction is created and the book balance does not change.
4. The statement running balance updates.
5. A bank reference is unique within the account when provided.

### Story 25: Add and post an adjustment to books

**Depends on:** Story 24

As an accountant,

**I want to:** add an adjustment and post its internal Transaction at the same time

**so that:**

- Known interest and charges are recorded in both places immediately

**Acceptance criteria**

1. Exactly one Transaction and one statement line are created and linked.
2. The line is marked Matched.
3. Book balance increases for incoming and decreases for outgoing adjustments.
4. No duplicate statement line is created.
5. Posting is atomic.

## Phase 9: Reporting

### Story 26: Revenue

**Depends on:** Stories 12, 25

As a financial controller,

**I want to:** have revenue calculated from posted business records

**so that:**

- Collections are not counted twice and tax is not reported as income

```text
Total Revenue =
Vehicle Revenue + Service Revenue + Fee Income
+ Interest Income + Other Income − Discounts
```

**Acceptance criteria**

1. Revenue comes from posted, non-cancelled Sales Invoices, regardless of payment status.
2. Sales tax, AR receipts, and bank transfers are excluded.
3. Interest and other income come from posted incoming adjustments only.
4. Statement-only unmatched adjustments are excluded.

### Story 27: Cost of goods sold

**Depends on:** Stories 6, 12

As a financial controller,

**I want to:** have COGS calculated from the cost of inventory sold

**so that:**

- Gross profit reflects true cost

```text
Vehicle COGS = Vehicle.totalCost
Parts COGS = Actual quantity sold × Cost Price
```

**Acceptance criteria**

1. Only vehicles on posted invoices are included, once each.
2. Unsold inventory and AP payments create no COGS.
3. Cancelled sales reverse their COGS.
4. Parts COGS stays zero until part sale or usage records exist.

### Story 28: Operating expenses

**Depends on:** Stories 2, 21, 25

As a financial controller,

**I want to:** see operating expenses from payroll and categorized payments

**so that:**

- Inventory and loan payments are not expensed

**Acceptance criteria**

1. Salary, bonus, and commission come from employee and invoice records.
2. Categorized bank payments and posted bank charges are included.
3. Vehicle and parts purchases, AP settlements for inventory, loan principal, tax, transfers, and revenue-reversing refunds are excluded.
4. The same expense is never counted from both an accrual and a cash payment.
5. Interest received is income, not a negative expense.

### Story 29: Profit & Loss report

**Depends on:** Stories 26, 27, 28

As a financial controller,

**I want to:** see a Profit & Loss report for a selected month, quarter, or year to date

**so that:**

- I can evaluate profitability

**Acceptance criteria**

1. Shows total revenue, COGS, gross profit, operating expenses, net profit, gross margin, and net margin.
2. Draft and cancelled invoices are excluded.
3. Results are the same for the same period and data.

### Story 30: Compare periods

**Depends on:** Story 29

As a financial controller,

**I want to:** compare the current period with a previous one

**so that:**

- I can see growth, decline, and margin changes

```text
Percentage Change =
(Current − Previous) ÷ Absolute Previous × 100
```

**Acceptance criteria**

1. Periods do not overlap and use the same rules.
2. Change shows as unavailable when the previous amount is zero.
3. Negative profit displays clearly.

### Story 31: Drill-down and export

**Depends on:** Story 29

As an accountant,

**I want to:** open the records behind each amount and export the report

**so that:**

- Every figure is auditable and shareable

**Acceptance criteria**

1. Drill-down totals equal the report amount, and records keep their references.
2. Posted records cannot be edited from the report without permission.
3. Exports show the period, current and previous values, company name, and generation date.
4. Exported totals match the screen, and exporting changes no data.
5. Only authorized users can drill down into or export sensitive reports.
