# Worker Recovery Pattern

## Problem

A worker crashes while processing a task.

Example:

PENDING

↓

PROCESSING

↓

Application Crash

↓

Task Stuck Forever

## Solution

Track processing start time.

Recover tasks that exceed a timeout threshold.

## Flow

PENDING

↓

PROCESSING

↓

processing_started_at

↓

Worker Crash

↓

Recovery Scheduler

↓

PENDING

↓

Reprocessed

## Benefits

- prevents stuck jobs
- improves reliability
- supports automatic recovery

## Real-world systems

RabbitMQ Unacked Messages

Kafka Consumer Recovery

AWS SQS Visibility Timeout

## Example Use Cases

- email processing
- background jobs
- report generation
- notification systems