# SQL Queries for Debt and Transaction Analysis

This repository contains SQL queries used for analyzing debt and transaction data, as well as determining the payment capabilities of enrolled contacts. The queries include Common Table Expressions (CTEs) to aggregate, filter, and calculate transaction data for financial assessments.

## Overview

The SQL code in this repository focuses on the following:

1. **Current Balance Analysis**:
   - Retrieves the latest balance data for each enrolled contact and labels it as "Current Balance."

2. **Transaction Data**:
   - Joins multiple tables to retrieve transaction data such as settlement payments, fees, and other financial transactions.
   - Filters records based on their statuses and eligibility.

3. **Corrected Transactions**:
   - Truncates dates to months and computes a cumulative sum of transactions for each contact over time, taking into account transaction priorities.

4. **Aggregated Transaction Data**:
   - Aggregates data to retrieve the minimum balance for each contact per month and tracks the most recent month for each contact.

5. **Payment Capabilities**:
   - Determines the capability of each contact to settle debts through various installment plans, such as one-time, three-payment, six-payment, nine-payment, and twelve-payment plans.
   - Considers the contact's current debt, fee percentages, and transaction history.

## Key Components

- **VW_TRANSACTIONS**: A CTE that retrieves the latest transaction or balance record for each contact.
- **VW_CORRECTED_TRANSACTIONS**: A CTE that calculates the cumulative sum of amounts for each contact.
- **VW_AGG_TRANSACTIONS**: A CTE that aggregates transaction data by month and calculates the minimum balance per contact.
- **PAYMENT_CAPABILITIES**: A CTE that calculates the different payment options for contacts based on their cumulative balances.

## How to Use

1. **Set up the database**:
   - Ensure you have access to the relevant database tables such as `CONTACT_BALANCES`, `TRANSACTIONS`, `DEBTS`, `SETTLEMENTS`, etc.
   - These queries expect the following schema and data structure:
     - `CONTACT_BALANCES`: Contains the balance details for each contact.
     - `TRANSACTIONS`: Holds transaction records.
     - `SETTLEMENTS`: Contains settlement data for certain transactions.
     - `DEBTS`: Tracks debt information for enrolled contacts.

2. **Run the Queries**:
   - The code can be executed in a compatible SQL environment.
   - Review the results and ensure that the necessary tables and fields are accessible to compute the desired outputs.

3. **Modify the Queries** (if needed):
   - Adjust the filters, date ranges, and other parameters according to your analysis requirements.

## Output

The output of these queries will provide insights into the following:

- The current balance and transaction history of each contact.
- The payment capabilities of contacts, indicating whether they can settle their debts through one-time or multiple payments.
- Financial details including settlement amounts, performance fees, and the status of debts.

## Example Output Fields:

- `CONTACT_NAME`: Name of the contact.
- `DEBT_ID`: Identifier for the debt associated with the contact.
- `AMT_NEEDED`: Total amount needed for settlement.
- `ONE_PAYMENT`, `THREE_PAYMENTS`, etc.: Boolean values indicating if the contact can settle the debt in one, three, six, nine, or twelve payments.

## Prerequisites

- SQL environment compatible with `WITH`, `JOIN`, and `CASE` statements (e.g., PostgreSQL, Redshift, BigQuery).
- Access to the necessary financial and contact-related tables in your database.
  
## License

This repository is licensed under the [MIT License](LICENSE).
