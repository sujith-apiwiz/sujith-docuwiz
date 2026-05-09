---
title: "Reports via Automated Emails"
pageId: "69b3ee33ea357772de95c822"
---

## Overview

Reports via Automated Emails provides structured access to banking transaction data, account activity, and financial summaries. Comprehensive reporting is essential for reconciliation, regulatory compliance, financial planning, and audit readiness.

## How It Works

Reports are generated on\-demand or on a scheduled basis. The reporting engine queries the transaction ledger, applies filters and aggregations, and formats output according to the requested format \(JSON, CSV, PDF, XLSX\). Reports are delivered through the configured channel.

## Key Features

- **On\-demand generation** — generate reports for any date range instantly
- **Scheduled reports** — configure automated daily, weekly, or monthly delivery
- **Multiple formats** — JSON, CSV, XLSX, PDF output formats
- **Advanced filtering** — filter by account, transaction type, date, amount, status
- **Audit\-ready exports** — tamper\-evident exports with digital signatures

## API Endpoint

```text
POST /reports/automated-email/generate
GET  /reports/automated-email/{reportId}/status
GET  /reports/automated-email/{reportId}/download
```

### Sample Request

```json
{
  "reportType": "TRANSACTION_SUMMARY",
  "accountNumber": "1234567890",
  "dateFrom": "2024-01-01",
  "dateTo": "2024-01-31",
  "format": "CSV"
}
```

### Sample Response

```json
{
  "reportId": "RPT-20240101-001",
  "status": "QUEUED",
  "estimatedReady": "2024-01-01T10:05:00Z",
  "message": "Report generation initiated"
}
```

## Report Types

## Error Codes

## Use Cases

1. **Month\-end reconciliation** — match platform transactions to internal ERP records
1. **Audit preparation** — export complete transaction history for auditors
1. **Regulatory submission** — generate central bank mandated reports
1. **Customer billing** — send monthly statements to account holders
1. **Cash flow analysis** — analyze inflow and outflow patterns over time

## Best Practices

- Schedule recurring reports during off\-peak hours to reduce latency
- Use CSV or JSON for automated reconciliation workflows
- Implement report checksum validation to detect data corruption
- Retain archives for the regulatory required retention period \(typically 5–7 years\)