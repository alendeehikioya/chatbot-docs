# Developer API Guide


**Base URL**
http://localhost:8000

---


## Authentication (JWT)

First, obtain a token:

**Request**

```
json
{
  "username": "admin",
  "password": "password"
}
```

**Response** 
```
json
{
  "access_token": "JWT_TOKEN",
  "token_type": "bearer"
}
```

**Use the token:**
Authorization: Bearer JWT_TOKEN

---


## Send Message

**Endpoint**

POST /chat/send

**Header**
Authorization: Bearer JWT_TOKEN


**Body**
``` 
json
{
  "user_id": "1",
  "message": "hello"
}
```

**Response**
``` 
json
{
  "reply": "Hi! How can I help you?",
  "session_id": "uuid"
}
```
---


## Get History

**End point**
GET /chat/history/{session_id}

**Response**
``` json
{
  "messages": [
    {"from": "user", "text": "hello"},
    {"from": "bot", "text": "Hi! How can I help you?"}
  ]
}
```

### Errors
| **Code** | **Meaning**      |
| -------- | ---------------- |
| 401      | Unauthorized     |
| 422      | Validation error |
| 500      | Server error     |


---

---













