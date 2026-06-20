# Payments Service

The **Payments Service** handles all payment processing for the platform.

## Overview

This service integrates with Stripe and PayPal to process transactions securely.

## Architecture

The service runs as a stateless Node.js API behind a load balancer.

### Key Components

- **Payment Gateway**: Routes payments to the correct provider
- **Webhook Handler**: Processes async payment events
- **Reconciliation Job**: Daily job to reconcile transactions

## API Reference

### POST /payments

Creates a new payment intent.

```json
{
  "amount": 1000,
  "currency": "usd",
  "customer_id": "cust_123"
}
```

### GET /payments/:id

Retrieves payment status.

## Runbook

### Common Issues

**Payments failing with 402**: Check Stripe API key configuration.

**Webhook not received**: Verify webhook URL is publicly accessible.

## On-Call Guide

- PagerDuty: `payments-team`
- Slack: `#payments-oncall`
- Escalation: Contact the platform team after 30 minutes
