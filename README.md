FactorRecon Enterprise: Project Blueprint & Outline

Executive Summary

FactorRecon is a specialized cloud-based financial software (ERP) designed for businesses that utilize Accounts Receivable (A/R) Factoring. It tracks the lifecycle of factored invoices, manages the dual-accounting nature of cash advances (Asset vs. Liability), and utilizes Artificial Intelligence to automate the notoriously tedious process of reconciling complex settlement reports from factoring companies.

1. What It Is For (The Purpose)

Many B2B businesses (like freight brokers, staffing agencies, and manufacturers) use factoring to improve cash flow. They sell their unpaid invoices to a factoring company in exchange for an immediate advance (e.g., 80% of the invoice value).

The Problem: Traditional accounting software struggles with factoring. When a business gets that 80% advance, it isn't pure revenue—it's essentially a short-term liability until the end-customer pays the factor. Furthermore, the factor holds back 20% (the Reserve) and deducts various fees (wire fees, aging fees, interest) before releasing the final amount.

Tracking what invoices are open, how much reserve cash is locked up, and matching bulk deposits to specific invoices takes hours of manual spreadsheet work. FactorRecon is built to eliminate this manual accounting nightmare.

2. What It Does (Core Capabilities)

Asset & Liability Separation: Automatically splits a factored invoice into two buckets: the Face Value (what you are owed) and the Factor Liability (the cash advanced to you that the factor must recoup).

Reserve Equity Tracking: Calculates exactly how much cash is held in "Reserve" by the factor, representing your future expected cash flow.

AI-Powered Settlement (The "Magic" Feature): Allows users to copy and paste unstructured emails or PDF text from their factoring company into the app. The AI reads the text, identifies which invoices were paid, extracts the dates, finds hidden fees, and automatically settles the accounts in the database.

Standalone Fee Ledger: Isolates the cost of capital. Instead of just "losing" money from the reserve, every wire fee, aging fee, or interest charge is extracted by the AI and placed in a dedicated ledger for tax and profitability analysis.

Velocity & Cost Insights: Tracks your "Days to Pay" (DTP) to show how fast your customers actually pay, and calculates your effective fee ratio to show you the true cost of your capital.

Bulk Operations: Supports CSV import for mass-onboarding of invoices and CSV export for syncing with tools like QuickBooks or Xero.

3. How It Works (Technical Mechanics)

The Frontend (React & Tailwind): A responsive, single-page application that works seamlessly on desktop, tablet, and mobile. It uses a modern, dashboard-driven UI for financial clarity.

The Backend (Firebase Cloud Services): * Authentication: Secure login system isolating each company's data.

Firestore Database: Uses real-time listeners. If a team member adds an invoice on their phone, the CFO's desktop dashboard updates instantly without refreshing.

Private Collections: Data is stored securely under /users/{userId}/... to ensure strict tenant isolation.

The AI Engine (Gemini 2.5 Flash): When a user pastes a settlement report, the app packages the text alongside the user's current open liabilities and sends it to the Gemini API. The prompt forces Gemini to return a strictly formatted JSON array containing the exact invoice numbers, dates, and fee amounts to update the database via a transactional write batch.

4. What You Need To Do (The User Workflow)

To use FactorRecon effectively, a business follows a simple 4-step loop:

Step 1: Onboard Assets (Daily/Weekly)

When you generate new invoices and send them to your factor, you add them to FactorRecon. You can click "+ Add Asset" for single invoices or use "Bulk Import" to upload a CSV.

Action: Input Invoice #, Client Name, Face Amount, and Advance Rate (e.g., 80%).

Result: Your dashboard updates, increasing your A/R Asset, your Factor Liability, and your Reserve Equity.

Step 2: Monitor the Dashboard

Throughout the month, you monitor the Executive Dashboard.

Action: Watch for the red "Aging A/R" alerts. These tell you which invoices have passed their expected terms, meaning the factor might start charging you late fees.

Step 3: Automate Reconciliations (When the Factor Pays)

When the factoring company collects from your customer, they send you a "Settlement Report" and wire you the remaining 20% reserve (minus their fees).

Action: Go to the AI Recon tab. Copy the text from the factor's email or PDF and paste it into the engine. Click "Process Settlement".

Result: The AI matches the text to your open invoices. It marks the invoices as "Settled," removes the liability from your dashboard, and logs any fees the factor took.

Step 4: Review Insights & Fees

At the end of the month, review your financial health.

Action: Go to the Factoring Insights tab to see your average Days to Pay and total cost of capital. Go to the Operating Fees ledger to see exactly how much you paid in wire/interest fees to export to your accountant.

5. Why It Helps (The Business Value)

Massive Time Reduction: What used to take a bookkeeper 4 hours of VLOOKUPs in Excel every Friday now takes 15 seconds using the AI Recon Engine.

Prevents "Fee Leakage": Factoring companies often bury small fees ($25 here, $50 there) in bulk settlement reports. FactorRecon's AI catches these and isolates them so you know exactly what your financing is costing you.

True Cash Visibility: It prevents founders from looking at their bank account and thinking they have more money than they do. The dashboard clearly delineates the "Liability" (cash that belongs to the factor) from the "Equity" (cash that is truly yours).

Operational Agility: Because it is cloud-based and mobile-responsive, sales teams and executives can check the status of funded invoices from anywhere, rather than waiting on a weekly report from the accounting department.
