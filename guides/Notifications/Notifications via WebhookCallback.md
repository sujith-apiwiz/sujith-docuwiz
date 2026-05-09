---
title: "Notifications via Webhook/Callback"
pageId: "69b3ede4ea357772de95c7e3"
---

## Overview

Notifications via Webhook/Callback delivers real\-time alerts to customers, employees, and systems about transaction events, account activities, and banking milestones. A robust notification layer is critical for customer trust, fraud detection, and operational awareness.

## How It Works

When a transaction event occurs, the banking platform publishes the event to the notification engine. The engine evaluates subscription rules, formats the message according to the channel template, and dispatches it to the configured recipient. Delivery status is tracked and retried on failure.

## Key Features

- **Event\-driven dispatch** — notifications triggered in real time on banking events
- **Template management** — customizable message templates per event type
- **Delivery tracking** — monitor sent, delivered, opened, and failed statuses
- **Retry logic** — automatic retry with backoff on delivery failure
- **Opt\-in/opt\-out management** — respect customer communication preferences

## API Endpoint

```text
POST /notifications/webhook
```

### Sample Request

```json
{
  "eventType": "TRANSACTION_CREDIT",
  "recipient": "customer@example.com",
  "channel": "WEBHOOK",
  "templateId": "CREDIT_ALERT_001",
  "variables": {
    "accountNumber": "****7890",
    "amount": "PHP 5,000.00",
    "timestamp": "2024-01-01 10:00 AM"
  }
}
```

### Sample Response

```json
{
  "notificationId": "NOTIF-001",
  "status": "SENT",
  "deliveredAt": "2024-01-01T10:00:05Z",
  "message": "Notification dispatched successfully"
}
```

## Common Notification Events

## Error Codes

## Use Cases

1. **Transaction alerts** — notify customers of every debit and credit in real time
1. **OTP delivery** — send one\-time passwords for 2FA authentication flows
1. **Fraud alerts** — instantly notify customers of suspicious activity
1. **Loan and account updates** — keep customers informed of application status
1. **Regulatory notices** — deliver mandated disclosures and consent updates

## Best Practices

- Always honor customer opt\-out preferences immediately
- Use short, clear message templates with essential information only
- Include fallback channels for critical alerts
- Monitor delivery rates by channel to detect provider issues early
- Avoid sending non\-critical notifications between 10 PM and 7 AM