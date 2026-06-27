# FinanceOS V1 - Minimum Viable Product (MVP)

## Version

v1.0

---

# Objective

FinanceOS V1 aims to provide users with a simple yet powerful financial simulation platform.

Instead of answering isolated financial questions, the application enables users to simulate their financial future based on their current income, expenses, loans, and savings.

The primary objective is to provide visibility into future cash flow, loan repayment, investment growth, and projected net worth.

**No optimization or AI-based recommendations are included in this version.**

---

# Product Goals

FinanceOS V1 should enable users to:

* Add their financial profile
* Configure a home loan
* Configure monthly investments
* Simulate their finances month-by-month
* View projected net worth
* Compare simple scenarios
* Visualize financial growth

---

# Out of Scope

The following features are intentionally excluded from V1:

* AI Advisor
* Recommendation Engine
* Tax Optimization
* Portfolio Rebalancing
* Monte Carlo Simulation
* Stock Portfolio Tracking
* Multi-user Support
* Authentication
* Bank Integrations
* Real-time Market Data
* Insurance Planning
* Retirement Optimization

---

# Core Features

## 1. User Financial Profile

The user can configure:

* Monthly salary
* Monthly expenses
* Annual salary growth (%)
* Simulation duration (years)

Purpose:

This serves as the primary input for the simulation engine.

---

## 2. Loan Management

Initially supports only one home loan.

User inputs:

* Loan amount
* Interest rate
* Loan tenure
* EMI start date
* Prepayment preference (Reduce Tenure / Reduce EMI)

Outputs:

* EMI
* Amortization schedule
* Outstanding balance
* Total interest
* Loan closure date

---

## 3. Investment Management

Supported investments:

* Fixed Deposit (FD)
* Recurring Deposit (RD)

For each investment:

User configures:

* Monthly contribution
* Interest rate
* Investment duration

Outputs:

* Investment corpus
* Interest earned
* Maturity value

---

## 4. Loan Prepayment

Users can configure recurring prepayments.

Examples:

* ₹20,000 every month
* ₹2,00,000 every year
* RD maturity used for prepayment

Simulation recalculates:

* Remaining principal
* Interest saved
* Revised loan closure date

---

## 5. Simulation Engine

The simulation runs month by month.

For every month:

1. Salary credited
2. Expenses deducted
3. EMI deducted
4. Loan interest applied
5. Loan principal updated
6. Investment contributions made
7. Investment interest compounded
8. Net worth updated

Repeat until simulation duration ends.

---

## 6. Net Worth Calculation

Every month:

Assets

* Cash
* FD
* RD
* House Equity

Minus

Liabilities

* Outstanding Home Loan

Result:

Projected Net Worth

---

## 7. Dashboard

The dashboard displays:

### Summary Cards

* Current Net Worth
* Outstanding Loan
* Total Interest Paid
* Total Investment Corpus
* Loan Closure Date

---

### Charts

* Loan Balance vs Time
* Investment Growth
* Net Worth Growth
* Monthly Cash Flow

---

## 8. Scenario Comparison

Users can create multiple scenarios.

Example:

Scenario A

No prepayment

Scenario B

₹20k monthly prepayment

Scenario C

₹50k monthly FD

Scenario D

₹20k RD + Annual Prepayment

Compare:

* Net Worth
* Interest Paid
* Loan Closure Date
* Investment Corpus

---

# Pages

## Home

Introduction to FinanceOS.

---

## Dashboard

Displays current financial summary.

---

## Financial Profile

Configure salary and expenses.

---

## Loan

Manage home loan.

---

## Investments

Manage FD and RD.

---

## Scenario Builder

Create multiple strategies.

---

## Results

Simulation outputs.

---

# Backend Modules

* Profile Service
* Loan Engine
* Investment Engine
* Simulation Engine
* Net Worth Engine

---

# APIs

Examples:

POST /profile

POST /loan

POST /investment

POST /scenario

POST /simulate

GET /results

---

# Success Criteria

FinanceOS V1 is considered complete when a user can:

* Configure a financial profile
* Add a home loan
* Add FD/RD investments
* Configure loan prepayments
* Simulate finances for any duration
* Compare multiple strategies
* View charts and reports
* Understand the financial impact of each strategy

Without requiring spreadsheets or manual calculations.
