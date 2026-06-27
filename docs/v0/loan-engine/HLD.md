# Loan Engine

# High Level Design (HLD)

Version: 1.0

Status: Draft

Author: Geetika Gupta

---

# Table of Contents

1. Introduction
2. Purpose
3. Responsibilities
4. Scope
5. High Level Architecture
6. Components
7. Processing Flow
8. Inputs
9. Outputs
10. Interaction with Other Engines
11. Error Handling
12. Future Evolution
13. Summary

---

# 1. Introduction

The Loan Engine is responsible for simulating the lifecycle of a loan within FinanceOS.

It manages loan-related computations throughout the simulation period and provides loan state updates to the Simulation Engine.

The Loan Engine focuses exclusively on loan behavior and is independent of other financial domains such as investments, cash flow, or net worth.

Version 1 supports Home Loans with fixed interest rates.

---

# 2. Purpose

The purpose of the Loan Engine is to model how a loan evolves over time.

It receives loan details from the Simulation Engine and produces loan-related information for every simulated period.

The Loan Engine serves as the single source of truth for all loan-related calculations within FinanceOS.

---

# 3. Responsibilities

The Loan Engine is responsible for:

- Loan initialization
- EMI calculation
- Monthly loan progression
- Interest tracking
- Principal repayment tracking
- Outstanding balance tracking
- Loan prepayment handling
- Loan closure detection
- Loan summary generation

The Loan Engine is not responsible for:

- Investment calculations
- Cash flow calculations
- Net worth calculations
- User interface rendering
- Data persistence

---

# 4. Scope

Version 1 supports:

- Single Home Loan
- Fixed Interest Rate
- Monthly EMI
- Partial Prepayments
- Early Loan Closure

Out of Scope:

- Floating Interest Rates
- Multiple Loans
- Loan Refinancing
- Balance Transfer
- Moratorium Periods
- Loan Insurance

These features may be added in future versions.

---

# 5. High Level Architecture

```
                Simulation Engine
                        │
                        ▼
                  Loan Engine
                        │
        ┌───────────────┼───────────────┐
        ▼               ▼               ▼
 Loan Processor   Prepayment Handler   Summary Generator
                        │
                        ▼
                 Loan Simulation Result
                        │
                        ▼
                Simulation Engine
```

The Loan Engine is invoked by the Simulation Engine during each simulation run and returns loan-related outputs.

---

# 6. Components

## Loan Processor

Responsible for managing the monthly progression of the loan.

Responsibilities:

- Process scheduled EMI
- Update outstanding balance
- Track principal repayment
- Track interest repayment

---

## Prepayment Handler

Responsible for processing user-defined loan prepayments.

Responsibilities:

- Apply prepayments
- Update outstanding principal
- Recalculate loan state
- Detect early loan closure

---

## Summary Generator

Responsible for preparing loan-level summary information.

Responsibilities:

- Total Interest Paid
- Total Principal Repaid
- Loan Closure Date
- Total Prepayments
- Remaining Balance

---

# 7. Processing Flow

Every simulation follows the same high-level process.

```
Receive Loan Details

↓

Initialize Loan

↓

Process Monthly EMI

↓

Apply Prepayments (if any)

↓

Update Loan State

↓

Repeat Until

• Simulation Ends OR

• Loan Closes

↓

Generate Loan Summary

↓

Return Results
```

The Loan Engine executes this process independently and returns the resulting loan information to the Simulation Engine.

---

# 8. Inputs

The Loan Engine receives loan configuration from the Simulation Engine.

Version 1 inputs include:

- Loan Amount
- Interest Rate
- Loan Tenure
- Loan Start Date
- Prepayment Schedule

Future versions may include:

- Floating Interest Rules
- Refinancing Details
- Loan Insurance
- Processing Fees

---

# 9. Outputs

The Loan Engine returns loan-related information to the Simulation Engine.

Version 1 outputs include:

- Monthly EMI
- Outstanding Balance
- Principal Repaid
- Interest Paid
- Loan Status
- Loan Closure Date
- Total Interest Paid
- Total Principal Paid
- Total Prepayments

These outputs are later consumed by other engines such as Cash Flow and Net Worth.

---

# 10. Interaction with Other Engines

The Loan Engine does not communicate directly with any engine other than the Simulation Engine.

```
Simulation Engine
        │
        ▼
Loan Engine
        │
        ▼
Simulation Engine
```

This architecture keeps the Loan Engine independent and prevents coupling with other financial domains.

Future engines such as Cash Flow and Net Worth will consume loan outputs through the Simulation Engine rather than interacting with the Loan Engine directly.

---

# 11. Error Handling

The Loan Engine validates loan-related inputs before processing.

Examples of invalid inputs include:

- Loan Amount less than or equal to zero
- Invalid Interest Rate
- Invalid Loan Tenure
- Invalid Prepayment Amount
- Prepayment exceeding outstanding balance

Errors are returned to the Simulation Engine with sufficient context for reporting to the caller.

---

# 12. Future Evolution

Future versions of the Loan Engine may support:

- Floating Interest Rates
- Multiple Concurrent Loans
- Loan Refinancing
- Loan Balance Transfer
- Moratorium Periods
- Interest Rate Revisions
- Commercial Loans
- Vehicle Loans
- Personal Loans
- Education Loans

The architecture is designed to support these enhancements while maintaining backward compatibility with existing functionality.

---

# 13. Summary

The Loan Engine is the dedicated component responsible for simulating the lifecycle of a loan within FinanceOS.

It owns all loan-related business logic and provides loan progression and summary information to the Simulation Engine.

By isolating loan processing into a dedicated engine, FinanceOS maintains a modular architecture where each financial domain has clear ownership and can evolve independently.