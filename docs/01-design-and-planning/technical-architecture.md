# Technical Architecture

## 1. Overview

The portfolio will use a separated frontend, backend and database architecture.

The system will be designed around the principle that the public website primarily renders content retrieved from the database, while the CMS and backend are responsible for creating, validating and managing that content.

The architecture should remain relatively simple for Version 1 while providing a strong foundation for future expansion.

The primary applications will be:

1. Public Website.

2. CMS Dashboard.

3. Backend API.

4. Database.

Media storage will operate alongside the database infrastructure.

---

## 2. High-Level Architecture

```text
                         ┌─────────────────────┐
                         │      Visitors       │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │   Next.js Website   │
                         │   Static Frontend   │
                         └──────────┬──────────┘
                                    │
                              API requests
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    Fastify API      │
                         │      Backend        │
                         └───────┬─────┬───────┘
                                 │     │
                    ┌────────────┘     └────────────┐
                    ▼                               ▼
          ┌─────────────────┐             ┌─────────────────┐
          │   PostgreSQL    │             │   Cloudflare    │
          │    Database     │             │       R2        │
          └─────────────────┘             │  Media Storage  │
                                          └─────────────────┘

                         ┌─────────────────────┐
                         │    CMS Dashboard    │
                         │      Frontend       │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    Fastify API      │
                         └─────────────────────┘
```

The public website and CMS should not communicate directly with the database.

All database operations should pass through the backend API.

---

## 3. Public Website

The public website will use:

- Next.js.

- TypeScript.

- Tailwind CSS.

- Radix UI.

- CSS animations where appropriate.

The website should primarily operate as a rendering system for database-driven content.

The frontend should not contain hardcoded copies of projects, education records or other dynamic content.

Instead:

```text
Database
    ↓
Backend API
    ↓
Next.js
    ↓
Rendered Page
```

This allows content to be changed through the CMS without modifying the website application.

---

## 4. Static Site Generation

Version 1 should use static site generation where practical.

This is appropriate because most website content does not need to change for individual visitors.

Static generation provides:

- Low hosting requirements.

- Fast page delivery.

- Good SEO performance.

- Reduced server-side processing.

- A simpler architecture.

When content is changed through the CMS, the appropriate pages should be regenerated or revalidated so the public website reflects the new content.

---

## 5. Future Rendering Architecture

The architecture should not prevent a future transition to server-side rendering.

SSR may become useful if the website eventually introduces:

- Visitor accounts.

- Personalised content.

- Recruiter accounts.

- Dynamic dashboards.

- Personalised recommendations.

- AI-powered features.

This is not required for Version 1.

---

## 6. Backend API

The backend will use:

- Node.js.

- TypeScript.

- Fastify.

The backend will provide a REST API for communication between the frontend, CMS and database.

The backend will be responsible for:

- Database access.

- Authentication.

- Authorisation.

- Validation.

- Content management.

- Media management.

- API responses.

- Business logic.

- Security-sensitive operations.

The backend should prevent the frontend from directly accessing sensitive database operations.

---

## 7. REST API

REST is preferred because it provides a straightforward and widely understood API architecture.

The API should use logical resource-based endpoints.

For example:

```text
GET    /projects
GET    /projects/:id
POST   /projects
PATCH  /projects/:id
DELETE /projects/:id

GET    /education
POST   /education
PATCH  /education/:id

GET    /experience
POST   /experience
PATCH  /experience/:id

GET    /banners
POST   /banners
PATCH  /banners/:id
DELETE /banners/:id
```

The exact endpoint structure will be defined in the API design documentation.

---

## 8. API Responsibilities

The API should act as the controlled boundary between applications and the database.

For example:

```text
CMS
 ↓
API request
 ↓
Authentication
 ↓
Authorisation
 ↓
Validation
 ↓
Business logic
 ↓
Database
 ↓
API response
 ↓
CMS
```

This ensures that database rules and security logic are not duplicated across multiple applications.

---

## 9. Database

The production database will use PostgreSQL.

PostgreSQL has been selected because it:

- Uses SQL directly.

- Is widely used professionally.

- Provides strong relational data modelling.

- Supports complex relationships.

- Has extensive documentation and community support.

- Provides a strong learning opportunity.

- Can support future expansion.

The database should be designed around the actual information requirements of the portfolio rather than attempting to support every possible future feature.

---

## 10. Database Development Environment

A separate local development database should be maintained.

The development environment should allow:

- Database schema experimentation.

- Test data.

- CMS development.

- API development.

- Migration testing.

- Feature testing.

The production database should remain isolated from development work.

The intended architecture is:

```text
Development

Local Website
     ↓
Local API
     ↓
Local PostgreSQL
     ↓
Test Data


Production

Vercel Website
     ↓
Production API
     ↓
Production PostgreSQL
     ↓
Live Data
```

This separation should significantly reduce the risk of development changes affecting the live website.

---

## 11. Database Access

Drizzle ORM will be used alongside raw SQL.

Drizzle should provide:

- Type-safe database access.

- Schema management.

- Convenient queries.

- TypeScript integration.

Raw SQL should still be used where it provides meaningful value or improves understanding of the database.

The project should avoid abstracting database operations so heavily that the underlying SQL becomes impossible to understand.

---

## 12. Media Storage

Media should not initially be stored directly inside PostgreSQL as large binary objects.

Instead, media files should be stored in Cloudflare R2.

PostgreSQL should store the metadata and reference required to locate the media.

For example:

```text
PostgreSQL

Media ID
Project ID
Filename
File Type
File Size
Storage Key
Alt Text
Upload Date
Display Order
```

while R2 stores:

```text
Actual image
Actual video
Actual audio file
```

This provides the benefits of centralised content management without unnecessarily increasing database size.

---

## 13. Media Architecture

The relationship should therefore be:

```text
CMS
 │
 │ Upload
 ▼
Backend API
 │
 ├──────────────► R2
 │                 │
 │                 └── Media file
 │
 └──────────────► PostgreSQL
                   │
                   └── Media metadata
```

The database remains the source of truth for which media belongs to which project, while R2 provides the actual file storage.

---

## 14. Authentication

CMS authentication will use Better Auth.

The CMS should require authentication before allowing content-management operations.

The intended security model will combine application-level authentication with network-level access restrictions.

The CMS should ideally only be accessible through the personal Tailscale network.

This provides an additional security layer:

```text
Internet
   │
   X
   │
CMS inaccessible

Tailscale Network
   │
   ▼
Authentication
   │
   ▼
CMS
```

Tailscale should not be treated as a replacement for authentication.

Both layers should remain in place.

---

## 15. Authorisation

Authentication determines who the user is.

Authorisation determines what that user is allowed to do.

Version 1 will only require a small number of privileged CMS users, potentially only one.

The architecture should nevertheless keep authorisation separate from authentication so that additional account types can be introduced later.

---

## 16. Frontend Component Architecture

The frontend should use reusable components rather than implementing each page independently.

The component system will use:

- Tailwind CSS.

- Radix UI.

Radix UI will provide accessible behavioural primitives while Tailwind will control the visual implementation.

This provides more control than using a complete pre-styled component library while avoiding the need to build common interactive components from scratch.

shadcn/ui may be introduced later if a specific component would benefit from it.

---

## 17. Abstraction Level

The frontend should use a moderate-to-high level of abstraction.

Common components should be reusable across pages.

Examples include:

- Navigation.

- Project cards.

- Buttons.

- Tags.

- Media galleries.

- Section layouts.

- Content blocks.

- Forms.

- Modals.

- Alerts.

- Project metadata.

However, abstraction should not be taken so far that simple components become unnecessarily difficult to understand.

The goal is reusable code without unnecessary framework complexity.

---

## 18. Content Rendering Architecture

Project pages should be generated from structured database content.

The general process should be:

```text
Project Record
      ↓
Project API
      ↓
Project Data
      ↓
Project Renderer
      ↓
Content Blocks
      ↓
Project Page
```

Each optional project section should correspond to a reusable rendering component.

For example:

```text
Problem
   ↓
ProblemSection

Testing
   ↓
TestingSection

Gallery
   ↓
GallerySection

Custom Section
   ↓
CustomSection
```

This allows projects to contain different combinations of sections without requiring a unique frontend implementation for every project.

---

## 19. Custom Page Overrides

The standard rendering system should be the default.

However, the architecture should allow specific projects to use a hardcoded page implementation where necessary.

The relationship should be:

```text
Project
   │
   ├── Standard renderer
   │
   └── Override renderer
```

The CMS should control which mode is used.

Override activation must use the warning and confirmation process defined in the CMS requirements.

---

## 20. Data Flow

The normal public project request should follow:

```text
Visitor
   ↓
Next.js
   ↓
API
   ↓
PostgreSQL
   ↓
Project data
   ↓
Next.js renderer
   ↓
Static page
   ↓
Visitor
```

CMS content creation should follow:

```text
User
   ↓
CMS
   ↓
Fastify API
   ↓
Authentication
   ↓
Validation
   ↓
Database / R2
   ↓
Success response
   ↓
CMS
```

The public website should therefore remain separated from the internal content-management operations.

---

## 21. Repository Architecture

The repository should support the separation of applications and documentation.

A likely structure is:

```text
portfolio/
├── apps/
│   ├── website/
│   ├── cms/
│   └── api/
│
├── packages/
│   ├── ui/
│   ├── types/
│   └── config/
│
├── docs/
│   ├── design-and-planning/
│   ├── architecture/
│   ├── api/
│   ├── database/
│   ├── diagrams/
│   ├── images/
│   ├── adr/
│   ├── testing/
│   ├── dev-logs/
│   └── requirements/
│
├── README.md
├── package.json
├── pnpm-workspace.yaml
└── ...
```

The exact monorepo structure will be finalised during repository setup.

---

## 22. Package Management

The project will use pnpm.

pnpm is preferred because it:

- Is efficient with disk space.

- Provides fast dependency installation.

- Supports monorepos well.

- Has strong modern TypeScript/JavaScript ecosystem support.

- Allows shared packages between the website, CMS and API.

---

## 23. TypeScript

TypeScript will be used across the frontend and backend.

This should allow:

- Shared types.

- Better API contracts.

- Earlier error detection.

- Improved IDE support.

- Safer database interactions.

- Easier maintenance.

Where practical, types shared between applications should be centralised rather than duplicated.

---

## 24. Deployment Architecture

The public website will be deployed to Vercel.

The API and database deployment strategy will be selected based on the final infrastructure requirements and cost constraints.

The architecture should prioritise services with sustainable free tiers or self-hosting where practical.

The system should avoid unnecessary paid managed services.

---

## 25. Version 1 Architecture Priorities

The architecture should prioritise:

1. Working public website.

2. Working database.

3. Working API.

4. Working CMS.

5. Reliable project creation and publishing.

6. Static project rendering.

7. Secure CMS authentication.

8. Media management.

9. Maintainable component architecture.

10. Clear documentation.

Advanced scalability should not be prioritised above completing the core system.

---

## 26. Future Architecture

The architecture should leave room for:

- Visitor accounts.

- Recruiter accounts.

- SSR.

- Personalised content.

- Blog functionality.

- Development logs.

- Project demonstrations.

- Analytics.

- Social media integration.

- AI-assisted portfolio search.

- Recruiter-facing AI summaries.

- Notifications.

- Meeting booking.

These features should not be implemented prematurely.

The Version 1 architecture should provide a solid foundation without attempting to solve problems that do not currently exist.
