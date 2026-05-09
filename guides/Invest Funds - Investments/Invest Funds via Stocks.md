---
title: "Invest Funds via Stocks"
pageId: "69b3ed64ea357772de95c792"
---

## Overview

Invest Funds via Stocks enables businesses and individuals to deploy surplus funds into investment products directly through the banking platform API. This integrates investment account management, order placement, portfolio tracking, and settlement into a unified programmatic interface.

## How It Works

An investment order is submitted via API, specifying the instrument, quantity or amount, order type, and source account. The platform routes the order to the appropriate market or product desk, validates eligibility and funding, executes the trade, and updates the portfolio.

## Key Features

- **Multi\-instrument support** — access to fixed income, equities, and digital assets
- **Real\-time pricing** — live or last\-traded price for order sizing
- **Portfolio management** — unified view of all holdings across instrument types
- **Dividend and income handling** — automatic credit of coupon payments and dividends
- **Tax document generation** — automated tax reporting per regulatory requirements

## API Endpoint

```text
POST /investments/Stocks
```

### Sample Order Request

```json
{
  "investorAccountNumber": "INV-1234567890",
  "orderType": "BUY",
  "amount": 100000.00,
  "currency": "PHP",
  "sourceAccount": "1234567890",
  "referenceNumber": "INV-20240101-001"
}
```

### Sample Response

```json
{
  "orderId": "INV-20240101-001",
  "status": "ORDER_PLACED",
  "estimatedSettlement": "2024-01-03",
  "message": "Investment order placed successfully"
}
```

## Order Lifecycle

```text
ORDER_PLACED → PENDING_SETTLEMENT → SETTLED → ACTIVE_HOLDING
            ↘ REJECTED (suitability or funding failure)
```

## Error Codes

## Use Cases

1. **Corporate treasury management** — invest idle cash in short\-term instruments
1. **Endowment fund management** — manage institutional investment portfolios
1. **Retirement fund services** — build long\-term investment portfolios for employees
1. **Investment product distribution** — offer investment products within your platform
1. **Digital asset management** — manage crypto exposure programmatically

## Best Practices

- Always perform suitability assessment before enabling investment access
- Use portfolio inquiry endpoints to monitor mark\-to\-market positions daily
- Generate and archive transaction records for tax reporting compliance
- Automate reinvestment of dividends and coupon income where supported