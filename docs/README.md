# Project Documentation

This directory contains the planning, requirements, architecture, technical design, testing, and development documentation for the Joe Waldron Portfolio Website.

The documentation is intended to record the project as a complete engineering process, from the initial requirements and architectural decisions through to implementation, testing, deployment, and future development.

## Documentation Structure

### 01 — Design and Planning

Contains the initial vision, goals, audience, content strategy, UX direction, CMS requirements, and other high-level planning documents.

This section describes **what the website is intended to achieve and why**.

### 02 — Requirements

Contains the formal functional and non-functional requirements for the website.

This section defines **what the system must do** and provides the basis for determining whether features are complete.

### 03 — Architecture

Contains the high-level and detailed architecture of the system, including the frontend, backend, CMS, data flows, deployment architecture, and security architecture.

This section describes **how the major parts of the system fit together**.

### 04 — Technology

Contains the technology selection and justification for the technologies used throughout the project.

This includes the frontend, backend, database, authentication, media storage, testing, and development environment.

### 05 — Database

Contains the database design, schema, relationships, migrations, indexing strategy, and development seed data.

This section describes **how the website's structured data is stored and related**.

### 06 — API

Contains the REST API design and documentation.

This includes endpoint definitions, authentication, request and response structures, validation, error handling, and the relationship between the API and the frontend/CMS.

### 07 — Frontend

Contains the frontend architecture and design implementation documentation.

This includes page structure, component architecture, the design system, content rendering, responsive behaviour, and frontend-specific technical decisions.

### 08 — CMS

Contains documentation for the content management system.

This includes project management, content creation, validation, previewing, publishing, media management, and the custom override system.

### 09 — Testing

Contains the testing strategy, test plans, test cases, automated testing documentation, test data, and test results.

Testing will be scaled according to the importance and complexity of each feature rather than applying unnecessary testing overhead to simple functionality.

### 10 — Deployment and Maintenance

Contains documentation covering development and production environments, deployment, environment variables, backups, rollback procedures, maintenance, and disaster recovery.

### 11 — Roadmaps

Contains development roadmaps covering Version 1, post-Version 1 development, future features, and technical debt.

This section will be used to track the planned evolution of the website.

### 12 — Architecture Decision Records

Contains Architecture Decision Records (ADRs) documenting significant technical and architectural decisions.

ADRs preserve **why a decision was made**, not simply what the final implementation is.

Superseded decisions will remain in the repository so that the evolution of the architecture can be followed.

### 13 — Development Logs

Contains chronological development logs documenting the progress of the project.

These logs will record significant implementation work, problems encountered, solutions, decisions, milestones, and lessons learned.

### 14 — Images

Contains images used within the documentation, including screenshots, interface designs, project images, and other supporting visual material.

### 15 — Diagrams

Contains diagrams used to explain the architecture and design of the system.

Diagrams may be stored as source files where appropriate, alongside rendered versions for use in documentation.

### 16 — Reference

Contains supporting information that does not belong directly within the technical design.

This may include terminology, a glossary, useful external resources, and other reference material.

---

## Documentation Principles

The documentation follows several principles:

### Document decisions, not just results

Important decisions should include their reasoning, alternatives considered, and consequences.

### Keep requirements separate from implementation

Requirements describe **what the system must achieve**.

Technical design describes **how the system will achieve it**.

### Keep documentation proportional

Documentation should demonstrate engineering discipline without becoming a burden that slows development unnecessarily.

### Record the development process

The repository should allow another developer to understand how the project evolved from its initial requirements to the implemented system.

### Keep documentation current

Documents should be updated when significant changes are made rather than allowing the documentation to become disconnected from the implementation.

---

## Engineering Process

The project broadly follows this cycle:

```text
Requirements
     ↓
Planning
     ↓
Architecture
     ↓
Technical Design
     ↓
Implementation
     ↓
Testing
     ↓
Deployment
     ↓
Review
     ↓
Iteration
```

Major decisions made during this process are recorded as ADRs, while development progress is recorded through the development logs.

---

## Documentation Status

Documentation is developed alongside the project.

Some sections will initially contain only the decisions and requirements necessary to begin implementation. Additional documentation will be added as the corresponding systems are designed and implemented.

The documentation therefore represents the **current state and development history of the project**, rather than attempting to define every future feature in advance.
