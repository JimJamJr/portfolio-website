

# API Design

## 1. Overview

The portfolio will use a REST API to provide controlled communication between the public website, CMS and database.

The API will be implemented using Node.js, TypeScript and Fastify.

The API will act as the central application layer for:

- Retrieving website content.

- Creating and modifying CMS content.

- Validating data.

- Managing authentication and authorisation.

- Managing media references.

- Applying business rules.

- Protecting the database from direct external access.

The API should remain simple enough to understand and maintain while following established REST principles.

---

## 2. API Objectives

The API should:

- Provide a clear interface between applications and data.

- Prevent direct database access from the frontend.

- Centralise validation and business logic.

- Provide predictable endpoints.

- Return consistent responses.

- Support both public and authenticated operations.

- Be straightforward to test.

- Be documented sufficiently for future development.

- Provide a foundation for future applications or integrations.

---

## 3. API Consumers

The initial API will have two primary consumers.

### Public Website

The public website will use the API to retrieve published content.

Typical operations include:

- Retrieving projects.

- Retrieving individual projects.

- Retrieving education.

- Retrieving experience.

- Retrieving featured projects.

- Retrieving active banners.

- Retrieving global website information.

### CMS

The CMS will use the API for authenticated management operations.

Typical operations include:

- Creating projects.

- Editing projects.

- Publishing projects.

- Managing drafts.

- Uploading media.

- Managing education.

- Managing experience.

- Managing banners.

- Managing featured projects.

- Updating global information.

---

## 4. API Boundary

The API should be the only application-level route to the database.

```text
Website ───────┐
               │
               ▼
            Fastify
               │
               ▼
          PostgreSQL
               ▲
               │
CMS ───────────┘
```

The frontend and CMS should not contain independent database access logic.

This prevents database rules from becoming duplicated between applications.

---

## 5. REST Principles

The API should use standard REST conventions wherever practical.

Resources should be represented as nouns rather than actions.

For example:

```text
GET /projects
```

rather than:

```text
GET /getProjects
```

Similarly:

```text
POST /projects
```

rather than:

```text
POST /createProject
```

HTTP methods should communicate the intended operation.

---

## 6. HTTP Methods

The API should primarily use:

| Method | Purpose                              |
| ------ | ------------------------------------ |
| GET    | Retrieve data                        |
| POST   | Create data                          |
| PATCH  | Partially update data                |
| PUT    | Replace a resource where appropriate |
| DELETE | Remove or disable a resource         |

`PATCH` should generally be preferred for CMS editing because most edits will only modify part of a record.

---

## 7. Initial Resource Structure

The initial API should be organised around resources such as:

```text
/projects
/education
/experience
/banners
/featured
/profile
/skills
/media
```

Authentication-related routes will be provided through Better Auth rather than being manually recreated where possible.

The exact endpoint structure will be defined once the database schema has been finalised.

---

## 8. Project Endpoints

The project resource will be the most substantial API resource.

The initial structure should support operations such as:

```text
GET    /projects
GET    /projects/:id

POST   /projects
PATCH  /projects/:id
DELETE /projects/:id
```

Additional operations may be required for:

- Publishing.

- Unpublishing.

- Previewing.

- Managing media.

- Managing contributors.

- Managing sections.

These should only become separate endpoints where doing so produces a clearer API.

---

## 9. Public Project Requests

The public website should only be able to retrieve appropriate public content.

For example:

```text
GET /projects
```

should not expose:

- Draft projects.

- Private projects.

- Internal metadata.

- Administrative information.

- Authentication data.

- Internal database identifiers where they are unnecessary.

The API should determine what content is publicly visible rather than relying on the frontend to hide private information.

---

## 10. CMS Project Requests

Authenticated CMS requests will have access to additional project information.

For example:

```text
GET /projects
```

from the CMS may return:

- Published projects.

- Drafts.

- Hidden projects.

- Status information.

- Metadata.

- Internal management information.

The API should determine which fields and operations are available based on the authenticated user's permissions.

---

## 11. Project Filtering

The projects endpoint should support filtering where useful.

Potential filters include:

```text
/projects?category=software
/projects?tag=typescript
/projects?status=published
/projects?category=automotive&tag=engine
```

Filtering should be implemented where it provides genuine value rather than creating an unnecessarily complex query system.

---

## 12. Pagination

Pagination should be considered for collection endpoints.

It is unlikely to be important for Version 1 because the portfolio will contain relatively few projects.

However, the API should avoid an architecture that assumes the number of records will always remain extremely small.

Pagination can therefore be introduced where required without fundamentally changing the API.

---

## 13. Validation

All data entering the API should be validated.

Validation should occur at the API boundary rather than relying exclusively on frontend validation.

For example:

```text
CMS Form
    ↓
Frontend Validation
    ↓
API
    ↓
Server Validation
    ↓
Database
```

Frontend validation improves user experience.

Backend validation provides actual protection against invalid data.

---

## 14. Error Handling

The API should provide consistent error responses.

Errors should contain enough information for the frontend or CMS to display an appropriate message without exposing sensitive internal information.

A general structure could be:

```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "The project title is required."
  }
}
```

Internal stack traces, database details and sensitive information should not be returned to users.

---

## 15. HTTP Status Codes

The API should use appropriate HTTP status codes.

Examples:

| Status | Use                                      |
| ------ | ---------------------------------------- |
| 200    | Successful request                       |
| 201    | Resource created                         |
| 204    | Successful request with no response body |
| 400    | Invalid request                          |
| 401    | Unauthenticated                          |
| 403    | Not authorised                           |
| 404    | Resource not found                       |
| 409    | Conflict                                 |
| 422    | Validation failure                       |
| 500    | Unexpected server error                  |

The exact usage should be documented in the API specification.

---

## 16. Authentication

Authentication for CMS operations will use Better Auth.

Authenticated requests should provide the API with the necessary user identity information.

The API should never assume that a request is trusted simply because it originated from the CMS application.

The server must verify authentication before performing protected operations.

---

## 17. Authorisation

Protected API endpoints should verify that the authenticated user has permission to perform the requested operation.

For Version 1 this may be relatively simple because the CMS is intended for personal use.

However, authorisation should remain separate from authentication to allow future expansion.

---

## 18. Public vs Protected Endpoints

The API should distinguish clearly between public and protected operations.

### Public

Examples:

```text
GET /projects
GET /projects/:id
GET /education
GET /experience
GET /featured
GET /banners
```

### Protected

Examples:

```text
POST   /projects
PATCH  /projects/:id
DELETE /projects/:id

POST   /education
PATCH  /education/:id

POST   /media
PATCH  /banners/:id
```

The exact list will be finalised alongside the API implementation.

---

## 19. Media API

Media management should be handled through the API rather than directly from the frontend.

The general flow should be:

```text
CMS
 ↓
API
 ↓
Authentication
 ↓
Validation
 ↓
R2 Upload
 ↓
Database Metadata
 ↓
Response
```

The API should manage the relationship between stored files and database records.

The actual media file should remain in R2 rather than PostgreSQL.

---

## 20. Featured Content

The API should provide a controlled way to determine which project is featured.

The CMS should be able to update the featured project without modifying the website source code.

The public website should retrieve the current featured project through the API.

---

## 21. Banners

The API should provide operations for managing temporary banners.

The public website should only retrieve active banners.

The CMS should be able to:

- Create banners.

- Edit banners.

- Enable banners.

- Disable banners.

- Delete banners.

Expired or disabled banners should not be displayed publicly.

---

## 22. Caching and Static Generation

Because the public website will primarily use static generation, API responses used for public pages should be compatible with caching and revalidation.

The system should avoid unnecessarily requesting the same content repeatedly.

When CMS content changes, the appropriate website content should be regenerated or revalidated.

The exact implementation will be determined during the Next.js deployment design.

---

## 23. API Versioning

The API should be designed so that future breaking changes can be introduced safely.

A version prefix such as:

```text
/api/v1/projects
```

may be used if it provides useful separation between versions.

Versioning should not be introduced purely for appearance.

The initial implementation should prioritise simplicity while ensuring that future API changes can be managed without breaking the website and CMS simultaneously.

---

## 24. API Security Principles

The API should:

- Validate all incoming data.

- Authenticate protected requests.

- Authorise protected operations.

- Never expose secrets.

- Avoid exposing unnecessary database information.

- Use secure transport.

- Apply appropriate request limits where necessary.

- Return safe error messages.

- Keep security-sensitive logic server-side.

Complex custom cybersecurity systems are not required.

Established libraries and platform security features should be preferred wherever practical.

---

## 25. API Testing

The API should be tested independently from the frontend.

Tests should cover important behaviours such as:

- Valid project creation.

- Invalid project creation.

- Project editing.

- Project publishing.

- Project visibility.

- Authentication.

- Authorisation.

- Invalid requests.

- Missing resources.

- Media operations.

- Banner management.

The testing strategy should be scaled according to the importance and complexity of each endpoint.

---

## 26. API Documentation

The API should have dedicated documentation within the repository.

Documentation should eventually include:

- Endpoint list.

- HTTP methods.

- Request formats.

- Response formats.

- Authentication requirements.

- Error responses.

- Validation rules.

- Example requests.

- Example responses.

Automatic API documentation may be introduced where it provides meaningful value without creating unnecessary development overhead.

---

## 27. API Design Principles

The API should follow these principles:

### Simple

Avoid unnecessary abstraction and complexity.

### Predictable

Similar resources should behave in similar ways.

### Secure

All protected operations must be authenticated and authorised.

### Validated

The backend must never blindly trust client input.

### Database-independent

The frontend should not need to understand the database implementation.

### Reusable

The API should be usable by both the website and CMS.

### Understandable

The implementation should remain understandable to the developer maintaining it.

### Extensible

Future applications and features should be able to use the API without requiring a complete redesign.

---

## 28. Version 1 API Scope

The Version 1 API should provide enough functionality to support:

- Public project retrieval.

- Project creation.

- Project editing.

- Project publishing.

- Project visibility.

- Project filtering.

- Project media.

- Featured project management.

- Education management.

- Experience management.

- Banner management.

- Profile/global information management.

- CMS authentication.

- Validation.

- Error handling.

The API should not attempt to implement future features until they are actually required.

The primary objective is to provide a reliable connection between the CMS, database and public website that can be expanded as the portfolio develops.
