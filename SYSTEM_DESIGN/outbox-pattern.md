# Outbox Pattern

## Problem

Business operation succeeds but notification fails.

Example:

Order saved successfully

↓

Email service unavailable

↓

Notification lost

## Solution

Store an event in an Outbox table within the same transaction.

A separate worker processes the event later.

## Flow

Save Order

↓

Save Outbox Event

↓

Commit Transaction

↓

Worker Reads Event

↓

Send Notification

↓

Mark Event As SENT

## Benefits

- prevents lost events
- improves reliability
- supports retries

## Real-world systems

Large systems often implement Outbox with:

Kafka

RabbitMQ

Workers consume events asynchronously.

## Example Use Cases

- order confirmations
- payment notifications
- analytics events
- audit logs