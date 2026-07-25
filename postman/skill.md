---
inclusion: auto
---

# Postman Collection Standards

Quality standards for Postman API collections. Defines what a well-maintained collection looks like — independent of tooling, automation, or specific projects.

## 1. Collection Principles

Collections should be:

- **Accurate** — reflects the actual API surface at all times
- **Minimal** — no redundant requests, no stale examples
- **Idempotent** — running the collection produces consistent results
- **Human-readable** — anyone can understand the purpose of any request without reading source code
- **Environment-independent** — works across local, staging, and production via variables alone
- **Consistent** — follows the same patterns throughout

## 2. URLs

Never hardcode hostnames, ports, or protocols.

```
✅  {{baseUrl}}/users/{{userId}}
❌  http://localhost:3000/users/123
❌  https://api.prod.example.com/users/123
```

Use a single base URL variable for all requests. The variable name is a project convention — common choices: `baseUrl`, `apiUrl`, `host`.

## 3. Variables

### Scopes (broadest to narrowest)

| Scope | Use for | Example |
|-------|---------|---------|
| Environment | Values that change per deployment | base URL, API keys, region |
| Collection | Shared constants and dynamic values | auth tokens, test data IDs |
| Local (scripts) | Temporary values within a single request | parsed response fields |

### Rules

- Use camelCase for all variable names
- Never store secrets in collection variables — use environment variables with type `secret`
- Provide meaningful initial values or empty strings — never leave undefined
- Document each variable's purpose
- Prefer descriptive names over abbreviations: `accessToken` not `at`, `userId` not `uid`

### Current vs Initial values

- **Initial values** are shared with the team (committed, visible)
- **Current values** are local only (never shared)
- Store secrets only in current values

## 4. Authentication

### Inheritance

- Set authentication at the collection or folder level
- Individual requests should inherit auth from their parent
- Only override auth on a request when that endpoint has different auth requirements
- Never duplicate inherited auth on child requests

### Patterns

- Use Postman's built-in auth types (Bearer, Basic, API Key) rather than manual headers when possible
- Store tokens in collection variables, populated by a login request's test script
- Document which request populates the auth token

## 5. Request Documentation

Every request must have a description that answers:

- **What** does this endpoint do? (one sentence)
- **Auth** — what authentication is required?
- **Input** — what does the request body/params look like?
- **Output** — what does a successful response look like?
- **Errors** — what are the common failure cases and status codes?
- **Constraints** — rate limits, file size limits, pagination, timeouts?

Keep descriptions concise. Use markdown formatting.

## 6. Request Naming

- Use natural language describing the action: `Create User`, `Get Order Details`, `Delete Session`
- Do NOT prefix with HTTP method: `Create User` not `POST Create User`
- Do NOT prefix with tags or markers: `Create User` not `[API] Create User`
- Do NOT use raw paths as names: `Create User` not `POST /api/users`
- Keep names concise but unambiguous within their folder context

## 7. Folder Organization

### Principles

- Group by resource or domain, not by HTTP method or technical concern
- Use clear, human-readable folder names
- Never include file extensions: `Authentication` not `Authentication (auth.js)`
- Never include implementation details: `Onboarding` not `Onboarding (useOnboardingState.js)`
- Nest folders only when it adds clarity — avoid deep nesting (max 2-3 levels)

### Common patterns

```
By resource:     Users, Orders, Products, Payments
By domain:       Authentication, Account, Billing, Notifications
By workflow:     Onboarding, Checkout, Verification
```

### Ordering

- Place setup/auth requests first (login, token refresh)
- Follow the natural workflow order where possible
- Group related CRUD operations together

## 8. Request Bodies

- Use realistic but obviously fake data — never real credentials or PII
- Include all required fields with representative values
- Show optional fields commented or with placeholder values
- Use the correct content type (raw/JSON, form-data, x-www-form-urlencoded)
- Reference variables for values that change: `{{userId}}`, `{{testEmail}}`

## 9. Response Examples

- Include at least one success example for each request
- Include error examples for common failure cases (401, 404, 422)
- Examples should be minimal but representative
- Never include real secrets, tokens, or PII in examples
- Mark generated examples clearly — distinguish from manually authored ones
- Keep examples up to date when the response schema changes

## 10. Test Scripts

### What to validate

- **Status code** — always validate expected status codes (including error cases)
- **Response shape** — key fields exist and have correct types
- **Business logic** — critical values match expectations
- **Performance** — response time within acceptable bounds (use sparingly)

### What to avoid

- Brittle assertions on exact string values that change frequently
- Testing implementation details (database IDs, timestamps)
- Assertions that break across environments
- Over-testing — validate the contract, not every field

### Patterns

```javascript
// Status code validation
pm.test('Successful response', () => {
    pm.expect(pm.response.code).to.be.oneOf([200, 201]);
});

// Response shape validation
pm.test('Has required fields', () => {
    const json = pm.response.json();
    pm.expect(json).to.have.property('id');
    pm.expect(json).to.have.property('email');
});

// Chaining — store values for subsequent requests
pm.collectionVariables.set('resourceId', pm.response.json().id);
```

## 11. Versioning

- Represent API versions clearly in folder names or request paths
- When a new version is introduced, keep the previous version visible
- Mark deprecated versions in their folder or request description
- Never silently remove old versions — deprecate first, then remove in a later pass

## 12. Deprecation

- Mark deprecated requests with `[DEPRECATED]` at the start of the description
- Include the deprecation date and replacement endpoint if available
- Do not delete deprecated requests immediately — allow a transition period
- Group deprecated requests in a dedicated folder if there are many

## 13. Common Mistakes

| Mistake | Fix |
|---------|-----|
| Hardcoded URLs | Use `{{baseUrl}}` variable |
| Duplicated auth on every request | Set auth at folder/collection level, inherit |
| HTTP method in request name | Use action descriptions only |
| File extensions in folder names | Use domain/feature names |
| Stale response examples | Update or remove when schema changes |
| Secrets in collection variables | Use environment variables with type `secret` |
| No test scripts | Every request validates at minimum the status code |
| Duplicated variables across scopes | Use the narrowest appropriate scope |
| Unnamed or auto-generated request names | Give every request a clear, human-readable name |
| Deep folder nesting (4+ levels) | Flatten — max 2-3 levels |

## 14. Collection Metadata

- Collection description should explain: what API this covers, how to authenticate, and how to get started
- Include a brief "Getting Started" section for new team members
- Document any required setup steps (environment import, auth token acquisition)
- Keep the description current — stale docs are worse than no docs
