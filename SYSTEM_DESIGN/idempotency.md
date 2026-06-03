# Idempotency

## Problem

The same event may be delivered multiple times.

Example:

ORDER_CREATED_123

↓

Delivered Twice

↓

Customer Receives Two Emails

## Solution

Assign a unique Event ID.

Process the event only once.

## Flow

Receive Event

↓

Check Event ID

↓

Already Processed?

├─ Yes → Skip

└─ No → Process Event

## Benefits

- prevents duplicate processing
- improves consistency
- supports retries safely

## Real-world systems

Kafka

RabbitMQ

AWS SQS

Payment Gateways

## Example Use Cases

- notification systems
- payment processing
- order creation
- webhook handling