---
title: "Manage Funds via Operating Bank Accounts"
pageId: "69b3ec53ea357772de95c6dd"
---

## Overview

Manage Funds via Operating Bank Accounts provides businesses with the ability to programmatically open, configure, and manage bank accounts directly through the banking API. This capability is foundational for fintechs, neobanks, and enterprises that need to automate account lifecycle management at scale.

## How It Works

Account management APIs expose operations for account creation, inquiry, configuration, and closure. Each account is assigned a unique identifier and can be configured with specific permissions, transaction limits, and linked products. Balances and transaction histories are available in real time.

## Key Features

- **Programmatic account creation** — open accounts via API without manual branch processes
- **Real\-time balance inquiry** — fetch current and available balance at any time
- **Account configuration** — set limits, permissions, and linked services per account
- **Multi\-currency accounts** — manage accounts in different currencies under one entity
- **Statement generation** — pull account statements for any date range on demand

## Core Operations

### Account Inquiry

```text
GET /accounts/{accountNumber}
```

```json
{
  "accountNumber": "1234567890",
  "accountName": "Acme Corp Account",
  "accountType": "CURRENT",
  "currency": "PHP",
  "availableBalance": 500000.00,
  "currentBalance": 510000.00,
  "status": "ACTIVE"
}
```

## Account Types

## Error Codes

## Use Cases

1. **Corporate treasury** — manage multiple operating accounts across subsidiaries
1. **Wallet issuance** — provision virtual accounts for end users
1. **Marketplace escrow** — hold buyer funds pending delivery confirmation
1. **Payroll accounts** — maintain separate accounts per department or entity
1. **Project funding accounts** — isolate project\-specific cash flows

## Best Practices

- Use dedicated accounts per business function for cleaner reconciliation
- Automate balance monitoring to trigger alerts on low\-balance conditions
- Generate and archive monthly statements for financial reporting
- Regularly review and update account permissions as team roles change
- Implement account\-level transaction limits as a risk control layer