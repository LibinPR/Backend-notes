# JWT Authentication Flow

JWT (JSON Web Token) is a stateless authentication mechanism widely used in modern backend APIs.

Instead of storing session state on the server, the client sends a signed token with each request.

## Login Flow

1. User sends credentials to login endpoint
2. Server verifies credentials
3. Server generates a JWT token
4. Client stores the token
5. Client sends token in Authorization header

## Example Request

Authorization: Bearer <token>

## Token Structure

A JWT contains three parts:

Header  
Payload  
Signature

Example format:

header.payload.signature

## Verification

For each protected request:

1. Extract token from Authorization header
2. Verify signature using secret key
3. Decode payload
4. Allow request if token is valid

## Advantages

- stateless authentication
- scalable across multiple servers
- no session storage required

## Common Use Cases

- REST APIs
- microservices authentication
- mobile app authentication
