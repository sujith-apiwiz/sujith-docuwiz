---
title: "Send Funds via Checkwriter"
pageId: "69b3e9dfea357772de95c4e3"
---

## Overview

Send Funds via Checkwriter is a core disbursement capability that allows enterprises to initiate outbound payments through the banking platform. This channel is designed for businesses that need programmatic, scalable fund movement with full transaction visibility and compliance controls.

## How It Works

The client submits an API request with sender and beneficiary details, amount, and channel\-specific parameters. The platform validates the request, performs balance and compliance checks, then processes the transaction through the appropriate channel infrastructure. Status updates are delivered via webhook or polling.

## Key Features

- **Secure disbursement** — multi\-layer authentication and authorization
- **Transaction tracking** — unique reference IDs for end\-to\-end reconciliation
- **Real\-time status** — instant confirmation or failure notification
- **Compliance screening** — automated AML and sanctions checks
- **Audit logging** — full audit trail for regulatory compliance

## API Endpoint

```text
POST /disbursements/checkwriter
```

### Authentication

```text
Authorization: Bearer <access_token>
```

OAuth2 Bearer token with `sendfunds` scope required.

### Sample Request

```json
{
  "senderAccountNumber": "1234567890",
  "beneficiaryName": "Sample Beneficiary",
  "amount": 10000.00,
  "currency": "PHP",
  "remarks": "Payment reference",
  "referenceNumber": "REF-001"
}
```

### Sample Response

```json
{
  "transactionId": "TXN-001",
  "status": "SUCCESS",
  "referenceNumber": "REF-001",
  "timestamp": "2024-01-01T10:00:00Z",
  "message": "Funds disbursed successfully"
}
```

## Error Codes

## Use Cases

1. **Vendor payments** — disburse funds to business partners and suppliers
1. **Employee disbursements** — send allowances, reimbursements, and incentives
1. **Customer payouts** — process refunds and reward cashouts
1. **Operational transfers** — fund operational accounts across branches
1. **Agent payouts** — disburse earnings to field agents or representatives

## Best Practices

- Always validate beneficiary details before initiating large disbursements
- Use correlation IDs to trace requests across distributed systems
- Implement retry logic with idempotency keys for network resilience
- Set up webhook endpoints to receive real\-time transaction status updates
- Regularly reconcile disbursement reports against internal records

## Security Considerations

- Restrict API access via IP whitelisting
- Enforce per\-transaction and daily disbursement limits
- Require dual authorization for high\-value transactions
- Monitor for anomalous disbursement patterns
- Encrypt all sensitive data fields in transit and at rest