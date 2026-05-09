---
title: "Send Funds via International Funds Transfer"
pageId: "69b3e924ea357772de95c412"
---

## Overview

International Funds Transfer \(IFT\) allows businesses and financial institutions to send money across borders to foreign bank accounts. Powered by SWIFT messaging standards and correspondent banking networks, international transfers are essential for import payments, overseas payroll, remittances, and global treasury operations.

## How It Works

The sender initiates an outward remittance request by providing the beneficiary's foreign bank details \(SWIFT/BIC code, IBAN or account number\), the destination currency, and the transfer amount. The platform performs AML/sanctions screening, converts currency if needed via real\-time FX rates, and routes the message through the SWIFT network to the beneficiary's correspondent bank.

```text
Client → API Request → AML/Sanctions Screen → FX Conversion → SWIFT Message → Correspondent Bank → Beneficiary Bank → Credit
```

## Key Features

- **SWIFT/GPI compliance** — full end\-to\-end tracking via SWIFT Global Payment Innovation
- **Multi\-currency support** — send in USD, EUR, GBP, JPY, SGD, and 50\+ currencies
- **Real\-time FX rates** — live exchange rate lock\-in at time of submission
- **Correspondent bank routing** — automatic optimal routing via partner correspondent banks
- **UETR tracking** — Unique End\-to\-End Transaction Reference for full traceability
- **Cut\-off time management** — respects SWIFT value date and cut\-off rules per currency

## API Endpoint

```text
POST /disbursements/international-transfer
```

### Authentication

OAuth2 Bearer token with `sendfunds` scope required.

```text
Authorization: Bearer <access_token>
```

### Request Body

```json
{
  "senderAccountNumber": "1234567890",
  "beneficiaryName": "Acme Corp Ltd",
  "beneficiaryAccountNumber": "DE89370400440532013000",
  "beneficiaryBankSwiftCode": "DEUTDEDB",
  "beneficiaryBankName": "Deutsche Bank",
  "beneficiaryBankAddress": "Frankfurt, Germany",
  "beneficiaryCountry": "DE",
  "amount": 10000.00,
  "currency": "EUR",
  "sourceCurrency": "PHP",
  "purpose": "Payment for imported goods - Invoice #IMP-2024-005",
  "referenceNumber": "INTL-20240101-0001"
}
```

### Response

```json
{
  "transactionId": "INTL-20240101-0001",
  "uetr": "f47ac10b-58cc-4372-a567-0e02b2c3d479",
  "status": "PROCESSING",
  "swiftMessageId": "202401010001USD",
  "estimatedDelivery": "2024-01-03",
  "fxRate": 57.25,
  "phpEquivalent": 572500.00,
  "message": "International transfer initiated successfully"
}
```

## Supported Transfer Types

## Required Beneficiary Information

## Compliance & Regulatory Requirements

- **AML Screening** — all transfers screened against OFAC, UN, EU, and local sanction lists
- **KYC Verification** — sender must be fully KYC\-verified before IFT access is granted
- **BSP Reporting** — transfers above threshold amounts are reported to central bank \(BSP\)
- **Purpose Codes** — mandatory classification of transfer purpose for FX monitoring
- **Supporting Documents** — commercial invoices or contracts may be required for large transfers

## Error Codes

## Use Cases

1. **Import payments** — pay foreign suppliers for goods and services
1. **Overseas payroll** — credit salaries to employees abroad
1. **Investment transfers** — fund foreign investment accounts
1. **Royalties and licensing** — pay IP fees to foreign rights holders
1. **Education remittances** — transfer tuition fees for students abroad

## Best Practices

- Lock FX rate at submission time for predictable cost management
- Always include a detailed `purpose` description for compliance
- Use UETR to track SWIFT GPI payment status end\-to\-end
- Initiate transfers before currency cut\-off times to avoid value date delays
- Maintain a sanctions screening log for audit purposes