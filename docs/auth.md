# Authentication (JWT)

The Chatbot API uses **JSON Web Tokens (JWT)** to secure endpoints and verify user identity.

All protected endpoints require a valid JWT token in the request header.

---


## Overview

JWT authentication works in three steps:

1. The user logs in with credentials.
2. The API returns a signed JWT token.
3. The client sends the token with each request.

The server validates the token before processing the request.

---


## Login to Get Token

Use the login endpoint to obtain a JWT token.

**Endpoint**
POST /auth/login

---


**Request Body**

```
json
{
  "username": "admin",
  "password": "password"
}
```
**Response**

```
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR...",
  "token_type": "bearer"
}
```

---


## Using the Token

- Include the token in the Authorization header:

- Authorization: Bearer YOUR_JWT_TOKEN

- All protected API requests must include this header.

**Token Expiration**

- Tokens expire after a fixed time (e.g. 30 minutes).

- Expired tokens return a 401 Unauthorized error.

- Clients must login again to obtain a new token.

---


## Security Best Practices

- Always use HTTPS.

- Never expose tokens in logs.

- Store tokens securely on the client.

- Rotate secrets regularly.

---

## Common Errors

|**Code**| **Meaning**                |
|--------|----------------------------|
| 401    |Invalid or expired token    |
| 403    |Missing Authorization header|

---