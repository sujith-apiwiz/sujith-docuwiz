---
title: "Borrow Funds via Corporate Loans"
pageId: "69b3ed04ea357772de95c766"
---

## Overview

Borrow Funds via Corporate Loans enables businesses and individuals to access credit facilities through the banking platform API. This programmatic lending capability supports automated credit assessment, digital documentation, and end\-to\-end disbursement workflows.

## How It Works

A loan application is submitted via API with borrower information, requested amount, purpose, and supporting financial data. The platform triggers automated credit scoring, bureau checks, and risk assessment. Upon approval, funds are disbursed to the designated account.

## Key Features

- **Digital loan origination** — fully paperless application and approval process
- **Automated credit assessment** — real\-time scoring using internal and bureau data
- **Flexible repayment structures** — fixed, declining, or bullet repayment options
- **Integrated disbursement** — approved loans credited directly to linked accounts
- **Amortization schedules** — auto\-generated repayment schedules on approval
- **Prepayment support** — partial and full early settlement with penalty calculation

## API Endpoint

```text
POST /lending/CorporateLoans
```

### Sample Application Request

```json
{
  "borrowerAccountNumber": "1234567890",
  "requestedAmount": 500000.00,
  "currency": "PHP",
  "loanPurpose": "Working Capital",
  "loanTenure": 12,
  "repaymentFrequency": "MONTHLY",
  "referenceNumber": "LOAN-20240101-001"
}
```

### Sample Response

```json
{
  "loanApplicationId": "LOAN-20240101-001",
  "status": "UNDER_REVIEW",
  "estimatedDecisionTime": "2024-01-01T12:00:00Z",
  "message": "Loan application submitted successfully"
}
```

## Loan Lifecycle

```text
APPLICATION → UNDER_REVIEW → APPROVED/REJECTED → ACCEPTED → DISBURSED → ACTIVE → CLOSED
```

## Credit Assessment Factors

## Error Codes

## Use Cases

1. **Working capital financing** — fund day\-to\-day operational expenses
1. **Equipment financing** — purchase machinery or technology assets
1. **Inventory loans** — stock up before peak selling seasons
1. **Bridge financing** — cover short\-term cash flow gaps
1. **Project financing** — fund specific business expansion initiatives

## Best Practices

- Submit complete and accurate financial data to speed up credit decisions
- Integrate loan status webhooks to automate internal approval workflows
- Monitor repayment due dates and automate debit for on\-time payments
- Archive all loan documents digitally for regulatory compliance