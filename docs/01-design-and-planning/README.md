# Design and Planning

This section contains the high-level planning and design decisions that define the purpose, structure, content, user experience, and future direction of the Joe Waldron Portfolio Website.

These documents describe **what the website is intended to achieve and why** before implementation details are considered.

## Documents

| Document                       | Purpose                                                                        |
| ------------------------------ | ------------------------------------------------------------------------------ |
| Vision and Purpose             | Defines the purpose of the website and the impression it should create         |
| Audience                       | Defines the primary and secondary audiences and their information needs        |
| Content Strategy               | Defines the content the website will present                                   |
| Content Management             | Defines how website content should be managed through the CMS                  |
| Website Structure              | Defines the information architecture and navigation                            |
| Project Content Model          | Defines the structure and flexibility of project content                       |
| Visual Design and UX           | Defines the visual identity and user experience                                |
| User Journeys                  | Defines how key users are expected to interact with the website                |
| Long-Term Growth               | Defines potential future development beyond Version 1                          |
| Constraints                    | Defines the project's practical, technical and time constraints                |
| Feature Prioritisation and MVP | Defines Version 1 priorities and separates essential features from future work |

## Planning Principles

The project follows several principles established during planning:

### Build a working system first

The September deadline takes priority over unnecessary polish or complexity. Version 1 should provide a functional, usable website before additional features are developed.

### Design for extension

The system should be modular so that new sections, content types and functionality can be added without requiring significant changes to unrelated parts of the website.

### Separate content from presentation

Where practical, website content should be stored independently from the presentation of that content. This allows the CMS to manage content without requiring changes to the frontend for routine updates.

### Use established technologies where appropriate

Existing libraries and services should be used where they provide reliable functionality that would otherwise require significant development time.

Custom implementation should be focused on the parts of the system that provide meaningful engineering value or are important to understanding the system.

### Prioritise the visitor experience

The homepage and project presentation should receive the highest level of visual polish because they are the primary opportunity to demonstrate both technical ability and engineering thinking.

### Preserve flexibility

The system should support optional content, configurable project structures and controlled overrides so that unusual projects can be presented appropriately without forcing every project into an identical format.

### Avoid premature complexity

Features that are not required for Version 1 should not unnecessarily influence the initial architecture unless supporting them later requires a decision to be made now.

## Planning → Design → Implementation

The planning documents establish the high-level requirements and intended behaviour.

Detailed technical decisions will be documented separately in:

- `02-requirements/`

- `03-architecture/`

- `04-technology/`

- `05-database/`

- `06-api/`

- `07-frontend/`

- `08-cms/`

This separation allows the project to distinguish between **what the website needs to achieve** and **how the system will implement it**.
