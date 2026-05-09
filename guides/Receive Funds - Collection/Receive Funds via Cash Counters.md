---
title: "Receive Funds via Cash Counters"
pageId: "69b3eb13ea357772de95c5d8"
---

## Overview

Receive Funds via Cash Counters enables businesses to collect payments from customers, partners, or counterparties through a structured API\-driven collection workflow. This channel supports automated reconciliation, real\-time acknowledgment, and end\-to\-end transaction visibility for incoming funds.

## How It Works

The collection is initiated either by the business \(push\-based\) or triggered by the payer \(pull\-based depending on the channel\). The platform validates the incoming funds, matches them to an open collection request, and posts the receipt to the designated account. Confirmation is sent via webhook or polling response.

## Key Features

- **Automated reconciliation** — incoming payments matched against open invoices or reference numbers
- **Real\-time credit notification** — instant webhook alerts on fund receipt
- **Multi\-payer support** — collect from multiple payers simultaneously
- **Overpayment and partial payment handling** — configurable rules for exceptions
- **Transaction audit trail** — full history of all collections with timestamps

## API Endpoint

```text
POST /collections/cashcountersreceive
```

### Authentication

```text
Authorization: Bearer <access_token>
```

OAuth2 Bearer token with `receivefunds` scope required.

### Sample Request

```json
{
  "collectionAccountNumber": "9876543210",
  "expectedAmount": 25000.00,
  "currency": "PHP",
  "referenceNumber": "COL-20240101-001",
  "description": "Payment for Invoice INV-2024-100",
  "expiryDateTime": "2024-01-02T23:59:59Z"
}
```

### Sample Response

```json
{
  "collectionId": "COL-20240101-001",
  "status": "PENDING",
  "collectionReference": "COLREF-XYZ123",
  "expiryDateTime": "2024-01-02T23:59:59Z",
  "message": "Collection request created successfully"
}
```

## Collection Status Lifecycle

```text
PENDING → RECEIVED → MATCHED → POSTED → SETTLED
                   ↘ UNMATCHED → Manual Review
```

## Error Codes

## Use Cases

1. **Invoice collection** — receive payments against issued invoices
1. **Subscription billing** — collect recurring fees from subscribers
1. **E\-commerce payments** — accept payments from online buyers
1. **Marketplace settlements** — receive merchant proceeds in one pool account
1. **Utility fee collection** — gather payments for services rendered

## Best Practices

- Set appropriate expiry times on collection requests to avoid stale references
- Implement webhook handlers with idempotent processing
- Use descriptive reference numbers that link back to your internal records
- Reconcile collections against your accounts receivable ledger daily
- Handle partial payments by configuring tolerance thresholds

## Security Considerations

- Validate the authenticity of incoming webhook notifications using HMAC signatures
- Restrict collection account access to authorized API consumers
- Monitor for unusual collection patterns that may indicate fraud
- Maintain a complete audit log of all collection events