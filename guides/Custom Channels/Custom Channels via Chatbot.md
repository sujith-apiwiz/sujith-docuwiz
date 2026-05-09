---
title: "Custom Channels via Chatbot"
pageId: "69b3f026ea357772de95c9b5"
---

## Overview

Custom Channels via Chatbot enables businesses to deliver banking services and customer experiences through fully customized digital touchpoints. Rather than relying on standard bank interfaces, businesses can embed, extend, or entirely build their own channels powered by the banking platform's core APIs.

## How It Works

Custom channels consume the banking platform's APIs and integrate them within a tailored user interface or automated interaction layer. The platform handles authentication, transaction processing, compliance, and data management — while the custom channel controls the user experience and branding.

## Key Features

- **Full API access** — all core and value\-adding banking functions available via API
- **White\-label capability** — custom branding without exposing the underlying bank
- **Authentication integration** — OAuth2 and OpenID Connect for secure user sessions
- **Event\-driven updates** — webhooks and websockets for real\-time UI updates
- **Sandbox environment** — develop and test without impacting production data

## Integration Architecture

```text
Custom Channel (Custom Channels via Chatbot)
        ↓ OAuth2 Token
Banking API Gateway
        ↓
Core Banking Services (Payments, Accounts, Lending, etc.)
```

## API Endpoint

```text
POST /channels/chatbot/register
GET  /channels/chatbot/{channelId}/status
```

### Sample Registration

```json
{
  "channelType": "CHATBOT",
  "channelName": "My Business Banking Channel",
  "callbackUrl": "https://myapp.example.com/banking/callback",
  "webhookUrl": "https://myapp.example.com/banking/events",
  "scopes": ["sendfunds", "receivefunds", "accounts"]
}
```

### Sample Response

```json
{
  "channelId": "CH-REG-001",
  "clientId": "client_abc123",
  "status": "ACTIVE",
  "message": "Custom channel registered successfully"
}
```

## Channel Comparison

## Error Codes

## Use Cases

1. **Neobank products** — launch a fully branded digital bank on top of the platform
1. **Embedded finance** — integrate payments and accounts into non\-banking apps
1. **Corporate banking portals** — build custom treasury and payments dashboards
1. **Conversational banking** — offer account and payment management via chat
1. **Agent banking** — equip field agents with a lightweight mobile banking tool

## Best Practices

- Never expose client secrets in client\-side code
- Implement certificate pinning in mobile apps to prevent MITM attacks
- Use the sandbox environment extensively before go\-live
- Design for offline resilience — cache critical data and queue actions when disconnected
- Maintain accessibility standards \(WCAG 2.1\) for inclusive design