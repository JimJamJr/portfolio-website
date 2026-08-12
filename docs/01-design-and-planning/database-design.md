# Database Design

## 1. Overview

The portfolio website will use PostgreSQL as its primary relational database.

The database will provide the central source of truth for dynamic website content managed through the CMS.

It will store structured information such as:

- Projects.

- Project sections.

- Project categories.

- Project tags.

- Contributors.

- Education.

- Experience.

- Banners.

- Featured content.

- Profile information.

- Skills.

- Media metadata.

- CMS-related information.

Large media files themselves will be stored separately in Cloudflare R2, with the database storing references and metadata for those files.

---

## 2. Database Objectives

The database should:

- Store all dynamic website content reliably.

- Support the CMS without requiring hardcoded content.

- Represent relationships between different content types.

- Allow projects to contain variable numbers of sections.

- Support project filtering through categories and tags.

- Support media galleries.

- Maintain consistent relationships between projects and contributors.

- Separate development data from production data.

- Provide a useful opportunity to develop practical SQL skills.

- Remain understandable and maintainable.

- Support future expansion without unnecessary complexity.

The database should be designed around the requirements of the current portfolio rather than attempting to support every possible future feature.

---

## 3. Database Architecture

There will be two primary database environments.

### Development

A local PostgreSQL database will be used during development.

It will contain:

- Test projects.

- Test media references.

- Test education records.

- Test experience.

- Test users.

- Other development data.

The development database can be modified freely without affecting the public website.

### Production

A separate production PostgreSQL database will contain the live website's data.

It should only contain production content and accounts.

The two environments must remain separate.

```text
Development

Local Applications
       ↓
Local PostgreSQL
       ↓
Development Data


Production

Live Applications
       ↓
Production PostgreSQL
       ↓
Live Data
```

---

## 4. Database Source of Truth

The database should be the authoritative source for dynamic website content.

For example, project information should not be duplicated as hardcoded content inside the Next.js application.

Instead:

```text
CMS
 ↓
API
 ↓
PostgreSQL
 ↓
Project Data
 ↓
Website
```

This allows content to be changed without modifying application code.

---

## 5. Project Data

Projects are the central content type of the portfolio.

A project should contain information such as:

- Unique identifier.

- Title.

- Description.

- Cover image reference.

- Date.

- Last updated date.

- Category.

- Tags.

- Status.

- Visibility.

- Contributors.

- GitHub link.

- Other external links.

- SEO metadata.

- Content sections.

The database should avoid storing large amounts of duplicated information.

---

## 6. Project Sections

Projects should support optional sections.

Potential sections include:

- Problem.

- Research.

- Planning.

- Design.

- Implementation.

- Testing.

- Results.

- Challenges.

- Future improvements.

- Gallery.

- Documentation.

- External links.

- GitHub.

- Custom sections.

A project should not be required to contain every possible section.

This means the database needs to support variable project structures.

The frontend will render only the sections that exist for a particular project.

---

## 7. Content Block Approach

Project sections should be represented in a way that allows the frontend to render them through reusable components.

Conceptually:

```text
Project
 ├── Problem
 ├── Research
 ├── Implementation
 ├── Testing
 ├── Gallery
 └── Custom Section
```

The database should therefore store enough information to identify:

- Section type.

- Section order.

- Section content.

- Section-specific data where necessary.

This allows different projects to use different combinations of content.

---

## 8. Custom Sections

Projects should support custom text-based sections.

A custom section should contain at minimum:

- Title.

- Text/content.

- Position within the project.

The system should allow multiple custom sections within a project.

This provides additional flexibility without requiring a new database schema every time a project requires a slightly different explanation.

---

## 9. Categories

Projects should belong to a primary category.

Initial categories may include:

- Software.

- Automotive.

- Research.

Additional categories should be possible in the future.

Categories should provide the high-level organisation used on the projects page.

---

## 10. Tags

Projects should support multiple tags.

Tags provide more specific classification than categories.

Examples could include:

- Python.

- TypeScript.

- JavaScript.

- SQL.

- AI.

- Web Development.

- Embedded Systems.

- Electronics.

- Robotics.

- Engines.

- Automotive.

Projects and tags should use a many-to-many relationship.

```text
Project A ───┬── TypeScript
             ├── Web Development
             └── React

Project B ───┬── Python
             ├── AI
             └── SQL
```

This allows visitors to filter projects by multiple characteristics.

---

## 11. Contributors

Projects should support multiple contributors.

A contributor should be associated with a project through a relationship rather than storing contributor information directly inside every project.

Each contributor should be able to have a role.

Examples include:

- Developer.

- Designer.

- Mechanical Engineer.

- Researcher.

- Collaborator.

- Project Lead.

The database should allow the same contributor to appear across multiple projects.

---

## 12. Project Status

Projects should have a status that communicates their current development state.

Potential statuses include:

- Planning.

- In Progress.

- Completed.

- Archived.

The exact status list should be kept deliberately small.

Status should be stored separately from visibility because a project can be completed while still being hidden from the public website.

---

## 13. Visibility

Visibility determines whether a project is publicly accessible.

Possible states may include:

- Draft.

- Published.

- Hidden.

- Archived.

Visibility should be separate from project status.

For example:

```text
Project:
Status = Completed
Visibility = Draft
```

This allows a completed project to remain unpublished until it is ready.

---

## 14. Dates

Projects should contain:

- Creation/post date.

- Last updated date.

The creation date should default to the current date when a project is created.

The CMS should allow the date to be manually changed where necessary.

The last updated date should change when meaningful project content is modified.

This information can be used to display a "Recently Updated" indicator on project cards.

---

## 15. Media

The database should store metadata for media associated with projects.

Media records should contain information such as:

- Unique identifier.

- Project relationship.

- Filename.

- File type.

- File size.

- Storage key.

- Upload date.

- Display order.

- Alt text where applicable.

- Media type.

The actual file should be stored in Cloudflare R2.

---

## 16. Media Storage Relationship

The relationship should be:

```text
PostgreSQL
│
├── Media ID
├── Project ID
├── Filename
├── File type
├── File size
└── R2 storage key
          │
          ▼
      Cloudflare R2
          │
          └── Actual media file
```

This keeps the database efficient while allowing all project content to be managed through the same CMS.

---

## 17. Media Ordering

Media should have an explicit display order.

This allows the CMS to control the order in which images, videos and audio appear in galleries.

The ordering should not depend on filenames or upload order.

This also allows media to be referenced by a predictable number within project documentation.

---

## 18. Education

Education records should contain information such as:

- Institution.

- Qualification.

- Subject/course.

- Start date.

- End date.

- Grade.

- Description.

- Relevant achievements.

- Relevant projects.

The structure should allow multiple education records.

---

## 19. Experience

Experience records should support different forms of activity.

A record may contain:

- Title.

- Organisation.

- Experience type.

- Start date.

- End date.

- Description.

- Responsibilities.

- Skills gained.

- External links.

Experience types may include:

- Employment.

- Work experience.

- Talk.

- Workshop.

- Other.

---

## 20. Banners

Temporary banners should be stored as database records.

A banner should contain information such as:

- Title.

- Message.

- Link where appropriate.

- Active state.

- Start date where required.

- End date where required.

- Creation date.

The public website should only display banners that are currently active.

The CMS should control the banner lifecycle.

---

## 21. Featured Projects

Featured project selection should be stored in the database rather than hardcoded into the homepage.

The database should allow the CMS to determine which project is currently featured.

The system should be capable of supporting multiple featured projects in the future, even if Version 1 primarily uses one.

---

## 22. Profile Information

Global profile information should be stored centrally where it is intended to be CMS-editable.

This may include:

- Name.

- Biography.

- Profile image.

- Contact details.

- LinkedIn.

- GitHub.

- Other social links.

- Featured homepage text.

The website should retrieve this information from a central source rather than duplicating it across individual pages.

---

## 23. Skills

The database should eventually support a skills section.

Skills may contain:

- Skill name.

- Category.

- Description.

- Level or experience indicator where appropriate.

- Associated projects.

The exact implementation can remain simple in Version 1.

---

## 24. Metadata and SEO

Projects should support metadata fields that can be configured through the CMS.

Potential information includes:

- Page title.

- Meta description.

- Search keywords where appropriate.

- Social preview image.

- Other relevant metadata.

Metadata should be stored separately from the primary project content where doing so makes the schema clearer.

The CMS should expose these fields through an advanced section.

---

## 25. Database Relationships

The database will contain several relationships.

A simplified representation is:

```text
Project
 ├── Category
 ├── Tags
 ├── Contributors
 ├── Media
 ├── Content Sections
 └── Metadata

Education
Experience
Banners
Profile
Skills
Featured Projects
```

Many-to-many relationships will be used where appropriate rather than duplicating information.

---

## 26. Referential Integrity

The database should use appropriate relationships and constraints to prevent invalid references.

For example:

- A project section should belong to a valid project.

- Project media should reference a valid project.

- Project tags should reference valid tags.

- Contributors should reference valid contributor records.

Foreign keys should be used where appropriate.

The database should be responsible for maintaining fundamental data integrity rather than relying entirely on application code.

---

## 27. Deletion Strategy

Deletion should be considered carefully for portfolio content.

Where historical information may be useful, soft deletion or archival may be preferable to permanently deleting records.

For example, an old project could be marked:

```text
Visibility = Archived
```

rather than being permanently removed.

Permanent deletion should be reserved for data that genuinely needs to be removed.

Media deletion should also consider whether the file is still referenced elsewhere before removing it from R2.

---

## 28. Database Migrations

Database structure should be managed through migrations.

Changes to the schema should be recorded so that:

- Development databases can be updated consistently.

- Production changes can be applied safely.

- Previous database states can be understood.

- Schema changes can be tracked through Git.

Drizzle's migration tooling should be used where appropriate.

---

## 29. Raw SQL

Raw SQL should be used where it provides educational or practical value.

Examples may include:

- Complex filtering.

- Joins.

- Aggregations.

- Analytics queries.

- Performance-sensitive queries.

Drizzle should be used for common operations where it improves development speed and type safety.

The project should maintain a balance between learning SQL and completing the website.

---

## 30. Database Security

The database should not be directly exposed to the public website.

Database access should occur through the backend.

Credentials should be stored as environment variables or secure deployment secrets and must never be committed to Git.

The database should use encrypted connections where supported by the hosting environment.

Backups and recovery options should be considered for the production database before the website becomes an important long-term portfolio asset.

---

## 31. Development Data

Development data should be clearly separated from production data.

Test projects and generated content may be used to test:

- Different project structures.

- Missing optional sections.

- Large galleries.

- Different media types.

- Invalid inputs.

- Draft projects.

- Custom sections.

- Validation overrides.

This will allow the CMS and website to be tested without affecting live content.

---

## 32. Database Performance

The expected traffic and dataset size are relatively small.

The database therefore does not require complex performance optimisation for Version 1.

However, the schema should use sensible:

- Primary keys.

- Foreign keys.

- Indexes.

- Query patterns.

Indexes should be added where they provide clear value, particularly for commonly queried fields such as:

- Project status.

- Visibility.

- Category.

- Tags.

- Dates.

- Slugs.

---

## 33. Slugs and URLs

Projects should have a stable URL-friendly identifier or slug.

For example:

```text
/projects/audio-tachometer
/projects/engine-simulator
```

The slug should be separate from the project's display title so that a title can be changed without unnecessarily changing the URL.

The system should consider how slug changes are handled to avoid broken links.

---

## 34. Database Design Principles

The database should follow these principles:

### Relational

Use PostgreSQL's relational capabilities to represent meaningful relationships.

### Normalised where practical

Avoid unnecessary duplication while not over-normalising simple data.

### Understandable

The schema should remain understandable to its developer.

### CMS-driven

Dynamic website content should be manageable through the CMS.

### Integrity-focused

The database should enforce important relationships and constraints.

### Extensible

Future functionality should be possible without requiring a complete database replacement.

### Simple

Do not create tables or relationships purely to prepare for hypothetical future features.

---

## 35. Version 1 Database Scope

The initial database should support:

- Projects.

- Project sections.

- Categories.

- Tags.

- Contributors.

- Project media.

- Project metadata.

- Education.

- Experience.

- Banners.

- Featured projects.

- Profile information.

- Skills.

- CMS authentication data where managed by the selected authentication system.

The exact table structure, columns, indexes and relationships will be defined in the dedicated database schema documentation before implementation.

---

## 36. Future Database Expansion

The database should leave room for future features such as:

- Blog posts.

- Development logs.

- Contact messages.

- Visitor accounts.

- Recruiter accounts.

- Subscriptions.

- Analytics.

- Meeting bookings.

- Project demo data.

- Social media integrations.

- AI conversation records.

These should not be included in the Version 1 schema unless there is a concrete requirement for them.

The database should provide a solid foundation for the portfolio without becoming a database designed around features that may never be implemented.
