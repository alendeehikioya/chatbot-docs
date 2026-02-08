# Quick Start

Get started with the Chatbot API in under 5 minutes using JWT authentication.

---

## Prerequisites

- Running Chatbot API server
- HTTP client (curl, Postman, or code)
- Valid login credentials

---

## Step 1 — Login and Get Token

Authenticate and receive a JWT token.

```
curl -X POST http://localhost:8000/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username":"admin","password":"password"}'
```

Copy the access_token.

---


## Step 2 — Send Message

Send a message using your JWT token.
```
curl -X POST http://localhost:8000/chat/send \
  -H "Authorization: Bearer JWT_TOKEN_HERE" \
  -H "Content-Type: application/json" \
  -d '{"user_id":"1","message":"hello"}'
```

**Response**
```
{
  "reply": "Hi! How can I help you?",
  "session_id": "abc-123"
}
```

---


### Step 3 — Fetch Conversation History

Use the returned session_id.

```
curl http://localhost:8000/chat/history/abc-123 \
-H "Authorization: Bearer JWT_TOKEN_HERE"

```

---


## Step 4 — Handle Errors

- 401 Unauthorized → Token missing or expired

-  422 Validation Error → Invalid request body

Login again if the token expires.