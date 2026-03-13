# Cache Aside Pattern

Cache Aside is the most commonly used caching strategy in backend systems.

In this pattern the application is responsible for interacting with the cache.

The database remains the source of truth while Redis acts as a performance layer.

## Read Flow

1. Application checks cache first
2. If data exists → return immediately (cache hit)
3. If data missing → query database
4. Store result in cache
5. Return response

Example flow:

Client → API → Redis → PostgreSQL

If Redis hit:
Redis → Response

If Redis miss:
PostgreSQL → Redis → Response

## Example Use Case

URL shortener redirect.

When a user visits a short URL:

1. API checks Redis for the shortCode
2. If found → redirect immediately
3. If not found → query PostgreSQL
4. Cache the result in Redis
5. Redirect user

## Advantages

- Reduces database load
- Faster response time
- Cache stores frequently accessed data

## Disadvantages

- Cache invalidation required when data changes
- Slightly more complex application logic

## When To Use

- Systems with high read traffic
- Frequently accessed data
- Performance-critical endpoints

Examples:

- URL shorteners
- product catalog APIs
- social media feeds