# Optimistic Locking

## Problem

Multiple users update the same record concurrently.

Example:

User A reads stock = 5

User B reads stock = 5

User A reserves 1 item

User B reserves 1 item

Expected stock = 3

Actual stock = 4

This is known as the Lost Update Problem.

## Solution

Use a version field.

Each update verifies that the version has not changed.

If another transaction modified the record first, the update fails.

## Flow

Read Product (version = 1)

↓

Reserve Stock

↓

Update Product

WHERE id = ? AND version = 1

↓

Success → version becomes 2

OR

Optimistic Lock Exception

## Benefits

- prevents lost updates
- no database locks held
- scales well for read-heavy systems

## Real-world systems

- E-commerce inventory
- Ticket booking systems
- Banking systems

## Example Use Cases

- product stock reservation
- seat booking
- account balance updates