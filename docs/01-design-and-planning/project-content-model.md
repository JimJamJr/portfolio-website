# Project Content Model

## 1. Overview

Projects are one of the primary content types on the website and will provide much of the evidence used to demonstrate Joe's engineering ability.

The project content model must therefore be flexible enough to represent software, automotive, mechanical and research projects without forcing every project into the same structure.

The model should provide a consistent core structure while allowing optional sections to be added when they are relevant to the project.

The content model should also support the future addition of interactive project demonstrations and other content types without requiring the fundamental project system to be redesigned.

---

## 2. Project Core Information

Every project should contain a core set of information required for it to be displayed correctly across the website.

The required information should include:

- Title.

- Main image.

- Date.

- Description.

- Category.

- Tags.

- Status.

- Contributors.

The date should be automatically populated with the current date when a project is created, but it must remain editable.

The project should also have a last updated date so that visitors can identify recently changed projects.

---

## 3. Project Main Image

Every project should have a main image used when the project is displayed across the website.

A project should still be visually complete if an appropriate project image is unavailable.

The system should therefore provide generic built-in images that can be used where a project does not have an appropriate image.

The main image should be distinct from the project's gallery and should be usable in:

- Project cards.

- The featured project.

- Project page headers.

- Other project previews.

---

## 4. Project Description

Every project should have a concise description suitable for use as the initial explanation of the project.

This description should be useful to visitors who are quickly scanning the portfolio and should explain what the project is and why it is relevant.

More detailed technical information should be provided through optional content blocks rather than forcing the main description to contain the complete project history.

---

## 5. Project Metadata

Projects should support metadata that improves organisation, discovery and search engine visibility.

Metadata should be configurable during project creation through an advanced section of the CMS.

Potential metadata includes:

- Page title.

- Search description.

- Keywords or tags.

- Social sharing information.

- Other relevant search engine metadata.

The CMS should make this information easy to provide without requiring the user to understand the underlying implementation of search engine optimisation.

The metadata system should be expanded only where it provides a clear benefit rather than introducing unnecessary complexity.

---

## 6. Categories

Every project should belong to a category.

Initial categories are expected to include:

- Software.

- Automotive.

- Research.

The category system should remain extensible because future projects may not fit neatly into these initial groups.

Categories provide the primary organisational structure of the Projects page.

---

## 7. Tags

Projects should support multiple tags.

Tags provide more specific information than categories and allow visitors to filter projects based on particular technologies, subjects or areas of work.

Examples include:

- JavaScript.

- Python.

- AI.

- Web Development.

- Simulation.

- Motorcycle.

- Engine.

- Restoration.

- Electronics.

A project may have multiple tags and should not be restricted to a single tag.

---

## 8. Project Status

Every project should have a status.

The status should communicate the current state of the project to visitors and should also help manage projects internally through the CMS.

Potential statuses include:

- Planned.

- In Development.

- Completed.

- Archived.

The exact status values may be adjusted during technical implementation.

Status should not be used as a replacement for visibility controls. A project can have a status indicating that it is complete while still being hidden from the public website.

---

## 9. Visibility

Projects should support visibility controls so that content can be prepared before it is publicly available.

This should allow projects to exist in states such as:

- Draft.

- Preview.

- Published.

- Hidden or archived.

Visibility controls are particularly important because projects may need to be developed and reviewed before publication.

The public website should never display content that has not been intentionally published.

---

## 10. Optional Content Blocks

Projects should support optional content blocks.

The initial set of supported blocks should include:

- Problem.

- Research.

- Planning.

- Design.

- Implementation.

- Testing.

- Results.

- Challenges.

- Future Improvements.

- Gallery.

- Documentation.

- External Links.

- GitHub.

- Custom Section.

Each block should only be displayed when relevant content has been provided.

This allows the project structure to adapt to the complexity and nature of the work.

---

## 11. Custom Sections

A project should support custom text-based sections.

Each custom section should contain:

- Section title.

- Section text.

This provides a simple way to add information that does not fit naturally into one of the predefined blocks.

Custom sections should not be used to replace the standard content structure unnecessarily, but they provide flexibility when a project requires something outside the predefined format.

---

## 12. Project Media

Projects should support multiple types of media.

The gallery should be capable of containing:

- Images.

- Videos.

- Audio files.

Media should support different appropriate file types rather than being restricted to a single format.

The main project image should remain separate from the gallery.

Gallery items should be numbered so that individual pieces of media can be referenced from project documentation or descriptions.

For example:

```text
Figure 1 — Engine before rebuild
Figure 2 — Cylinder removed
Figure 3 — Reassembled engine
```

This should make it easier to connect written explanations with visual evidence.

---

## 13. Documentation

Projects should support documentation that provides deeper technical evidence.

Documentation may include:

- Written technical documentation.

- Diagrams.

- Testing information.

- Supporting files.

- Other relevant project material.

The project content system should not assume that every project requires documentation.

Where documentation exists, it should be accessible directly from the project page.

---

## 14. External Links

Projects should support multiple external links.

These may include:

- Project websites.

- Documentation.

- References.

- Demonstrations.

- Related resources.

- Other relevant external pages.

External links should be stored separately from the main project description so that they can be presented consistently.

---

## 15. GitHub Integration

Projects should provide a dedicated GitHub link where source code is available.

The GitHub link should be easy for visitors to identify and access.

This is particularly important for software projects because it allows technically experienced visitors to inspect the implementation directly.

A GitHub link should not be required for projects where source code does not exist or cannot reasonably be published.

---

## 16. Contributors

Projects should contain information about who contributed to the work.

Each contributor should be able to have a role associated with them.

Potential roles include:

- Primary contributor.

- Co-developer.

- Collaborator.

- Supervisor.

- Contributor.

The system should allow multiple contributors to be associated with a project.

This is particularly important for projects completed collaboratively, such as mechanical projects completed with Joe's brother.

The contributor structure should make Joe's own involvement clear without incorrectly presenting collaborative work as entirely individual.

---

## 17. Dates and Updates

Projects should contain a publication or project date and a last updated date.

The creation date should be automatically populated when a project is initially created but remain editable.

The last updated date should change when significant project content is modified.

Projects that have been recently updated may display a visual indicator on the Projects page.

Projects do not require a development timeline within the project itself.

A more detailed chronological development history can instead be represented through the future development log system.

---

## 18. Future Interactive Content

The project model should be capable of supporting interactive demonstrations in future.

This is particularly relevant for projects such as the audio tachometer, where allowing visitors to interact with a working demonstration could provide significant value.

Interactive demos are not required for Version 1.

The project content model should nevertheless avoid decisions that would prevent an embedded or integrated demonstration from being added later.

---

## 19. Standard Structure and Overrides

The standard project structure should be the default method for creating project pages.

This provides:

- Consistent presentation.

- Predictable validation.

- Reusable frontend components.

- Faster project creation.

- Easier maintenance.

However, some projects may require a presentation that cannot reasonably be represented using the standard structure.

The CMS should therefore provide an override mechanism.

An override should allow the project to bypass the normal page validation or structure and instead point to a specifically implemented hardcoded page.

Because this bypasses the standard content system, the CMS must:

1. Display a clear warning.

2. Explain what validation or structure will be bypassed.

3. Require explicit confirmation.

4. Clearly identify that the project uses a custom implementation.

5. Prevent accidental activation during normal project editing.

The standard structure should remain the preferred approach.

---

## 20. Content Model Principles

The project content model should follow these principles:

### Required core, optional depth

Every project should have enough information to be displayed correctly, while deeper sections should only be included when they add value.

### Evidence-focused

Projects should support media, documentation, testing results and source code where applicable.

### Flexible across disciplines

The same system should support software, automotive, mechanical and research projects.

### Consistent presentation

Projects should normally use the same reusable page structure.

### Controlled customisation

Projects that genuinely require a unique presentation should be able to override the standard structure through an explicit and controlled mechanism.

### CMS-first management

The content model should be designed around efficient project creation and management through the CMS.

### Future compatibility

The model should leave room for future demonstrations, development logs and other project-related features without requiring the core project system to be replaced.

---

## 21. Example Project Structure

A typical substantial software project could therefore contain:

```text
Project
├── Core Information
│   ├── Title
│   ├── Main Image
│   ├── Date
│   ├── Description
│   ├── Category
│   ├── Tags
│   ├── Status
│   └── Contributors
│
├── Problem
├── Research
├── Planning
├── Design
├── Implementation
├── Testing
├── Results
├── Challenges
├── Future Improvements
│
├── Gallery
│   ├── Image 1
│   ├── Image 2
│   ├── Video 1
│   └── Audio 1
│
├── Documentation
├── External Links
├── GitHub
│
└── Custom Sections
    ├── Section
    └── Section
```

A smaller project may contain only a subset of these sections.

This flexibility is a core requirement of the content model rather than an exception to it. 
