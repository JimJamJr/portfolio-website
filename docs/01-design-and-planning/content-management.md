# Content Management

## 1. Overview

The Content Management System (CMS) will provide a central interface for managing the dynamic content displayed by the portfolio website.

The primary purpose of the CMS is to make routine content updates faster and more reliable than modifying the website's source code.

The CMS should allow new projects, education achievements, experience and other content to be created through structured forms while maintaining consistent presentation across the public website.

The CMS should prioritise functionality and reliability over visual polish in Version 1.

---

## 2. CMS Objectives

The CMS should:

- Reduce the need for hardcoded content changes.

- Allow new content to be added without modifying the frontend.

- Provide structured forms for common content types.

- Validate content before publication.

- Provide a preview before publishing.

- Support drafts and unpublished content.

- Allow existing content to be edited.

- Provide controlled customisation where the standard structure is insufficient.

- Provide centralised management of global website information.

- Provide a foundation for future CMS functionality.

The CMS should itself demonstrate competent system design and database-driven development.

---

## 3. Dashboard

The dashboard will be the main interface for managing the website.

The initial dashboard should provide access to:

- Projects.

- Education.

- Experience.

- Featured projects.

- Temporary banners.

- Contact information.

- Profile information.

Additional management sections can be introduced as the CMS develops.

The dashboard should prioritise quick access to frequently performed actions.

---

## 4. Project Management

Project management is the most important CMS feature for Version 1.

The CMS should allow a user to:

1. Create a project.

2. Upload or select a cover image.

3. Set the project status.

4. Enter the required project information.

5. Select a category.

6. Add tags.

7. Add contributors.

8. Add a GitHub link where appropriate.

9. Add optional content sections.

10. Add project media.

11. Configure relevant metadata.

12. Preview the project.

13. Save it as a draft.

14. Publish the project.

The process should require as few unnecessary interactions as possible.

---

## 5. Project Editor

The project editor should use a structured form based on the project content model.

Required fields should be clearly distinguished from optional fields.

Optional sections should be addable when required rather than being displayed as a large form containing empty fields for every possible section.

For example:

```text
Project Information
[Required fields]

Add Section
┌─────────────────────────┐
│ Problem                 │
│ Research                │
│ Testing                 │
│ Results                 │
│ Gallery                 │
│ Documentation           │
│ Custom Section          │
└─────────────────────────┘
```

This should make project creation substantially faster, particularly for smaller projects.

---

## 6. Media Management

The CMS should allow project media to be managed alongside the project.

Supported media should include:

- Images.

- Videos.

- Audio.

Media should be associated with the relevant project and assigned an identifier or number where appropriate.

The system should provide enough information to distinguish media items and allow them to be referenced within project content.

Media management should not require the user to manually manage database identifiers.

---

## 7. Preview System

Projects should be previewable before publication.

The preview should show the project using the same or substantially similar rendering system as the public website.

The preview should allow the user to identify:

- Formatting problems.

- Missing information.

- Incorrect images.

- Broken sections.

- Poor presentation.

- Other content problems.

The goal is to ensure that a project can be reviewed before becoming publicly visible.

---

## 8. Draft and Publishing System

Projects should support a draft workflow.

A project should not become publicly visible simply because it has been created.

The basic workflow should be:

```text
Create
  ↓
Draft
  ↓
Edit
  ↓
Preview
  ↓
Validation
  ↓
Publish
  ↓
Public Website
```

Projects should also be capable of being unpublished or hidden when necessary.

---

## 9. Validation

The CMS should validate content before publication.

Validation should check requirements such as:

- Required fields being completed.

- Valid content formats.

- Valid links.

- Appropriate media.

- Required project structure.

- Other constraints necessary for the frontend to display the content correctly.

Validation should help prevent malformed content from reaching the public website.

Validation should not unnecessarily restrict legitimate content.

---

## 10. Validation Overrides

The CMS must provide a controlled override mechanism for situations where the standard validation or content structure is unsuitable.

When an override is selected, the CMS should:

1. Display a clear warning.

2. Explain what standard validation will be bypassed.

3. Ask the user to explicitly confirm the action.

4. Record that the override has been enabled.

5. Clearly identify the content as using an override.

An override may allow the project to bypass the normal page structure and point to a specifically implemented hardcoded page instead.

Because this bypasses the standard content system, it should be treated as an advanced feature rather than the normal method of creating projects.

---

## 11. Education Management

The CMS should provide a simple form for adding and editing education records.

The form should support information such as:

- Institution.

- Qualification.

- Subjects.

- Dates.

- Grades.

- Relevant achievements.

- Description.

The structure should allow additional academic achievements to be added over time without requiring source-code changes.

---

## 12. Experience Management

The CMS should allow new experience records to be created and edited.

Experience should support multiple formats, including:

- Employment.

- Work experience.

- Talks.

- Workshops.

- Other relevant activities.

The CMS should provide an appropriate structure for each type while keeping the management experience straightforward.

---

## 13. Featured Projects

The CMS should control which project or projects are featured on the homepage.

The featured project should not need to be changed through source code.

The system should allow a new project to replace the current featured project as the portfolio develops.

The selected featured project should automatically use the standard project rendering system unless a deliberate custom implementation has been configured.

---

## 14. Temporary Banners

The CMS should provide management of temporary website banners.

The user should be able to:

- Create a banner.

- Edit a banner.

- Enable or disable a banner.

- Replace an existing banner.

- Remove an expired banner.

Banners should be intended for temporary announcements rather than permanent website content.

Potential uses include:

- New project announcements.

- Current development work.

- Application activity.

- Major achievements.

- Other time-sensitive information.

---

## 15. Global Information

The CMS should eventually centralise information that appears across multiple areas of the website.

This includes:

- Contact details.

- LinkedIn.

- GitHub.

- Other social media links.

- Profile image.

- Featured text.

- Skills.

- Other appropriate global information.

Changing this information should update all relevant parts of the website automatically.

---

## 16. Profile Image Management

The CMS should allow the current profile image to be updated without modifying the website source code.

The system should ensure that the image is displayed consistently wherever the profile image is used.

Older images may eventually be retained for historical purposes, although this is not required for Version 1.

---

## 17. Metadata Management

Project metadata should be available through an advanced section of the CMS.

This should make it possible to configure information that improves search engine discovery without requiring manual modification of page source code.

The metadata interface should remain understandable to a user without specialist SEO knowledge.

More advanced SEO functionality can be added later if it provides meaningful value.

---

## 18. CMS Authentication

The CMS should not be publicly accessible as an unrestricted content management interface.

Access should require authentication.

The intended Version 1 security model should combine:

- Secure authentication.

- Strong password handling.

- Additional authentication protection where practical.

- Network-level restriction through the personal Tailscale network.

The CMS should be designed so that future improvements to authentication can be introduced without replacing the content-management system.

Visitor accounts are not required for Version 1.

---

## 19. Content That Must Not Be Editable

Certain parts of the website should remain code-controlled.

The CMS must not provide controls for:

- Passwords.

- API keys.

- Secrets.

- Sensitive configuration.

- Navigation structure.

- Core branding.

- Footer implementation.

- Global theme implementation.

- Other security-sensitive configuration.

These should only be modified through controlled code changes.

---

## 20. CMS Design Principles

The CMS should follow several principles.

### Function before appearance

The CMS does not need to be highly polished visually. A clear and reliable interface is more important.

### Minimal clicks

Frequently performed actions should require as few interactions as reasonably possible.

### Structured by default

The CMS should encourage consistent content without making legitimate customisation difficult.

### Safe overrides

Customisation should be possible, but potentially destructive or structurally significant actions must require explicit confirmation.

### Preview before publication

Content should be reviewable before becoming publicly visible.

### Centralised management

Information that appears across multiple parts of the website should have a single source of truth.

### Code for infrastructure, CMS for content

The CMS should manage content while fundamental website behaviour and security remain controlled by the codebase.

---

## 21. Version 1 CMS Scope

The minimum viable CMS should provide:

- Authentication.

- Dashboard.

- Project creation.

- Project editing.

- Project deletion or unpublishing.

- Project visibility controls.

- Project validation.

- Project preview.

- Project publishing.

- Optional project sections.

- Project media management.

- Featured project management.

- Temporary banner management.

- Basic education management.

- Basic experience management.

- Centralised contact details.

The CMS should establish the underlying connection between the dashboard, backend, database and public website even if some management features are initially basic.

This connection is important because the CMS is intended to become the foundation for future dynamic functionality rather than being a standalone administrative page.

---

## 22. Future CMS Features

The following features are intentionally outside the Version 1 scope but should remain possible within the architecture:

- Centralised contact message management.

- Analytics.

- Social media publishing and importing.

- Blog management.

- Development log management.

- Visitor accounts.

- Recruiter subscriptions.

- Project demonstration management.

- More advanced media management.

- More sophisticated SEO controls.

- AI-assisted content management.

These features should not influence Version 1 to the point where they delay the September release.
