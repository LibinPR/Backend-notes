# Fire-and-Forget Pattern

Fire-and-forget is a backend design pattern where a task is triggered but the system does not wait for the task to finish before responding to the client.

This improves response latency for user-facing operations.

## Example

In a URL shortener service, when a user clicks a short URL we want to:

1. Redirect the user quickly
2. Increment the click count

If the server waits for the database update before redirecting, it adds latency to the request.

Instead, we can update analytics asynchronously.

## Flow

Request → redirect → async analytics update

Example pseudo code:

redirect(originalUrl)

trackClick(shortCode) // executed asynchronously

The redirect happens immediately while the analytics update runs in the background.

## Benefits

- lower response latency
- better user experience
- non-critical work handled asynchronously

## Real-world systems

Large systems often push these background tasks to message queues like:

Kafka  
RabbitMQ

Workers process analytics events asynchronously.

## Example Use Cases

- click tracking
- sending emails
- logging events
- analytics processing
