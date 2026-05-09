---
title: "Utilize Funds via Co-Branded Cards"
pageId: "69b3eca9ea357772de95c727"
---

## Overview

Utilize Funds via Co\-Branded Cards allows businesses and their customers to use deposited funds for specific financial purposes. This capability bridges banking balances with real\-world spending and financial utility, enabling seamless integration between fund storage and fund usage in a single platform.

## How It Works

The client initiates a utilization request specifying the type of payment, the target biller or merchant, the amount, and the source account. The platform validates the request, confirms fund availability, and processes the transaction through the appropriate payment or card network.

## Key Features

- **Instant processing** — real\-time or near\-real\-time fund utilization
- **Biller directory integration** — pre\-built connections to major billers and merchants
- **Payment confirmation** — immediate acknowledgment with reference numbers
- **Spending controls** — configurable limits and category restrictions
- **Itemized receipts** — detailed transaction records for reconciliation

## API Endpoint

```text
POST /payments/CoBrandedCards
```

### Sample Request

```json
{
  "sourceAccountNumber": "1234567890",
  "billerCode": "MERALCO",
  "billerReferenceNumber": "9876543210",
  "amount": 3500.00,
  "currency": "PHP",
  "referenceNumber": "PAY-20240101-001"
}
```

### Sample Response

```json
{
  "paymentId": "PAY-20240101-001",
  "status": "SUCCESS",
  "confirmationNumber": "CONF-ABC123",
  "timestamp": "2024-01-01T10:00:00Z",
  "message": "Payment processed successfully"
}
```

## Error Codes

## Use Cases

1. **Corporate utility payments** — pay electricity, water, and telecom bills
1. **Employee benefits** — enable staff to pay for company\-approved expenses
1. **Co\-branded spending** — issue branded cards linked to business accounts
1. **Supplier invoice settlement** — pay approved invoices directly
1. **Subscription management** — manage recurring business software payments

## Best Practices

- Validate biller codes against the current directory before submission
- Use idempotency keys to prevent duplicate payment submissions
- Implement spending category controls for co\-branded card programs
- Monitor payment success rates by biller for operational insights
- Automate reconciliation by matching payment IDs to invoice records