# Retry Pattern

## Problem

External systems can fail temporarily.

Examples:

SMTP unavailable

Network timeout

Third-party API failure

## Solution

Retry the operation after a delay.

Stop retrying after a maximum number of attempts.

## Flow

Send Notification

↓

Failure

↓

Increment Retry Count

↓

Schedule Next Retry

↓

Success OR Max Retry Reached

## Benefits

- handles transient failures
- improves reliability
- reduces manual intervention

## Real-world systems

Common strategies:

Fixed Delay

Exponential Backoff

Jitter

Dead Letter Queues

## Example Use Cases

- email sending
- payment processing
- message delivery
- external API integrations