# DataAnalytics-Assessment
1. Base Table: users_customuser:
I extracted the customer identity and personal information from the Base Table: users_customuser
This query identifies customers who have both a savings and an investment plan and sorts them by total deposit amount in descending order.

-- Assessment_Q2.sql
-- Transaction Frequency Analysis
-- 1. Calculate number of transactions per user per month
-- 2. Compute average monthly transactions per user
-- 3. Categorize users based on transaction frequency
-- 4. Aggregate results by frequency category

-- Assessment_Q3.sql
-- Account Inactivity Alert: Identify accounts with no transactions in the last 365 days

-- Assessment_Q4.sql
-- Customer Lifetime Value (CLV) Estimation

Challenges and Resolutions
1. Dual Criteria Matching (Savings + Investment)
Challenge: Ensuring customers own both plan types.

Resolution: Used two INNER JOINs, which naturally enforce the requirement that both conditions must be satisfied (i.e., presence in both subqueries).

2. Deposits Source Table
Challenge: Determining which table contains actual confirmed deposit values.

Resolution: Assumed savings_savingsaccount.confirmed_amount is the correct and available field for calculating deposit totals.

3. Dealing with NULL Deposits
Challenge: Some users may not have any deposits, which could cause NULL values in the final result.

Resolution: Wrapped deposit value in IFNULL(..., 0) to ensure graceful handling of missing data.

4. Unit Conversion
Challenge: The deposit amounts are stored in kobo (or minor units).

Resolution: Divided by 100 and wrapped in ROUND(..., 2) for proper currency formatting.

