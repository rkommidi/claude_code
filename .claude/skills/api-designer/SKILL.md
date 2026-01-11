---
name: api-designer
description: Designs REST APIs with best practices. Use when creating endpoints, API routes, or when user asks to design an API.
---

When designing APIs, follow these principles:

## URL Structure
- Use nouns, not verbs: `/users` not `/getUsers`
- Plural resources: `/users`, `/orders`
- Nested for relationships: `/users/{id}/orders`

## HTTP Methods
- GET: Read (idempotent)
- POST: Create
- PUT: Full update
- PATCH: Partial update
- DELETE: Remove

## Response Format
Always return consistent JSON:
```json
{
  "success": true,
  "data": { ... },
  "meta": { "page": 1, "total": 100 }
}
```

## Error Format
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Email is required",
    "field": "email"
  }
}
```

## Status Codes
- 200: Success
- 201: Created
- 400: Bad request
- 401: Unauthorized
- 404: Not found
- 500: Server error
