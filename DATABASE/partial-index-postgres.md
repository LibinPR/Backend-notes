# Partial Index in PostgreSQL

A partial index is an index built on a subset of rows in a table.

Instead of indexing the entire table, PostgreSQL indexes only rows that satisfy a condition.

## Example

Suppose we have a table storing shortened URLs:

urls

- short_code
- original_url
- is_active

Only active URLs are used for redirects.

Inactive URLs should not appear in search results.

Instead of indexing the entire table:

CREATE INDEX idx_urls_short_code
ON urls(short_code);

We create a partial index:

CREATE INDEX idx_urls_short_code
ON urls(short_code)
WHERE is_active = TRUE;

## Why This Helps

The index now contains only active rows.

Benefits:

- smaller index size
- faster lookups
- less memory usage

## Use Case in URL Shortener

Redirect requests only need active URLs.

The query:

SELECT \* FROM urls
WHERE short_code = $1
AND is_active = TRUE;

Using a partial index improves performance.

## When to Use Partial Index

- tables with many inactive rows
- queries that filter on a condition
- improving performance of selective queries

Example scenarios:

- active users only
- non-deleted records
- recent transactions
