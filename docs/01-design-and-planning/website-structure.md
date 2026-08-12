# Website Structure

## 1. Overview

The website should use a simple primary navigation while providing enough structure beneath it for visitors to explore projects and other information in depth.

The structure should prioritise the needs of recruiters while still allowing technically experienced visitors to investigate projects and supporting documentation.

The website should not feel like a traditional CV website. The structure should instead encourage visitors to explore the work and understand how Joe approaches engineering problems.

---

## 2. Primary Navigation

The main navigation will contain:

- Home

- Projects

- About Me

- Education

- Experience

- Contact

Project pages should not appear as individual items in the main navigation.

The Contact section should also be a single page rather than being divided into separate contact form or contact information pages.

The navigation should remain consistent throughout the public website so that visitors can move between major sections without needing to return to the homepage.

---

## 3. Website Hierarchy

The public website should follow a structure broadly similar to:

```text
Home
│
├── Featured Project
│   └── Project Page
│
├── Projects
│   ├── Software
│   │   ├── Project
│   │   ├── Project
│   │   └── Project
│   │
│   ├── Automotive
│   │   ├── Project
│   │   ├── Project
│   │   └── Project
│   │
│   └── Research
│       └── Project
│
├── About Me
│
├── Education
│
├── Experience
│
└── Contact
```

The project structure should be generated from the project data rather than requiring individual project pages to be manually created.

---

## 4. Homepage

The homepage should provide the strongest initial impression of the website.

The visitor should immediately be able to identify:

- Joe Waldron's name.

- His connection to software engineering and the automotive industry.

- His strongest current project.

- His most important achievement or selling point.

- How to make contact or access professional profiles.

The homepage should contain a featured project selected through the CMS.

The featured project should be capable of changing over time as new projects become more technically significant or relevant to current applications.

The homepage should prioritise visual impact and clarity over displaying large amounts of information.

---

## 5. Projects Page

The Projects page should provide an overview of the complete portfolio.

Projects should initially be grouped into broad categories, for example:

```text
Software
Project A    Project B    Project C    Project D

Automotive
Project 1    Project 2    Project 3    Project 4

Research
Research A   Research B   Research C
```

The exact categories should remain configurable enough to accommodate future projects.

Projects should be presented as visual cards containing enough information to determine whether the project is worth exploring further.

A project card should contain, at minimum:

- Main project image.

- Project title.

- Relevant tags.

- Short description.

- Appropriate project status or update information.

The card should link directly to the relevant project page.

---

## 6. Project Filtering

Projects should support filtering using tags.

The primary category structure should remain visible rather than being replaced entirely by a filter system.

A filter control may open a selection interface allowing visitors to select one or more relevant tags.

For example:

```text
Category: Software

Tags:
[JavaScript]
[Python]
[AI]
[Web Development]
[Simulation]
```

The filtering system should make it easier to locate relevant projects without making the basic Projects page difficult to understand.

Filtering should be introduced in a way that remains useful if the number of projects increases substantially in the future.

---

## 7. Project Pages

Each project should have its own page generated from a reusable project blueprint.

The page should be populated from the structured project content stored by the CMS.

This means that adding a new project should not normally require creating a new frontend page manually.

The project page should be capable of presenting:

- Title.

- Main image.

- Date or last updated date.

- Status.

- Category.

- Tags.

- Description.

- Contributor information.

- Optional technical sections.

- Gallery.

- Videos and audio.

- Documentation.

- External links.

- GitHub repository.

- Future project demonstrations.

The page should only display optional sections when relevant content has been provided.

---

## 8. Project Information Hierarchy

Project pages should use progressive disclosure so that visitors can understand the project without immediately being presented with its entire technical history.

A typical project page should progress from:

```text
Project identity
      ↓
Quick overview
      ↓
Visual evidence
      ↓
Engineering explanation
      ↓
Technical details
      ↓
Supporting evidence
      ↓
External resources
```

This structure supports both the recruiter and technical-engineer journeys.

The initial content should answer:

> What is this project and why should I care?

Deeper content should answer:

> How was it built, what problems were encountered, and how effective was the solution?

---

## 9. Different Project Structures

Projects should not be required to follow a single rigid structure.

The CMS should provide a collection of optional content blocks that can be included when relevant.

Potential blocks include:

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

- Custom sections.

This allows a major software project to contain substantial technical documentation while allowing a smaller project to remain concise.

Mechanical projects should also be able to use a structure appropriate to the way the work was actually completed rather than being forced into a software-development workflow.

---

## 10. About Me

The About Me page should provide the personal context behind the rest of the portfolio.

It should explain Joe's interests, motivations and direction while avoiding unnecessary repetition of information already contained in the project, education and experience sections.

The page should contribute to the friendly and approachable character of the website.

---

## 11. Education

The Education page should provide a structured overview of Joe's academic background.

Education milestones should be displayed in a way that allows visitors to quickly understand:

- Institution.

- Qualification.

- Subjects.

- Dates.

- Grades.

- Relevant achievements.

More detailed information can be accessed where appropriate.

The structure should support additional academic achievements being added through the CMS.

---

## 12. Experience

The Experience page should provide an overview of relevant professional and practical experience.

It should support different experience types rather than assuming every entry represents a conventional job.

Potential entries include:

- Employment.

- Work experience.

- Talks.

- Workshops.

- Other relevant professional activities.

The presentation should emphasise what was learned and what was contributed rather than simply listing dates and positions.

---

## 13. Contact

The Contact page should provide a single destination for contacting Joe.

It should contain the contact form alongside appropriate professional contact information and links.

The page should not have separate contact subpages.

Contact options should also be accessible from other areas of the website, particularly the homepage.

The overall goal is that a visitor should be able to reach some form of contact with very few interactions.

---

## 14. Global Content

Some content will appear across multiple pages and should therefore be managed centrally.

This includes:

- Profile image.

- Contact details.

- Social media links.

- GitHub link.

- LinkedIn link.

- Temporary announcements.

- Featured project.

- Potentially skills and other global information.

Changing this information through the CMS should update all relevant areas of the public website.

This avoids duplicated information becoming inconsistent across different pages.

---

## 15. Temporary Banners

The website should support temporary announcement banners that can be displayed across appropriate pages.

These banners are intended to communicate current information rather than permanent content.

Examples include:

- A new project being released.

- A significant project milestone.

- Current application activity.

- A temporary announcement about the website.

- Other information that is relevant for a limited period.

Banners should be controlled through the CMS and should be capable of being disabled or replaced without changing the frontend source code.

---

## 16. Content-Driven Pages

The public website should be primarily driven by structured content.

The frontend should provide reusable layouts and components while the CMS and backend provide the content that populates them.

This separation means that:

```text
Content changes
        ↓
CMS
        ↓
Backend / API
        ↓
Database
        ↓
Website rendering
```

Routine content changes should therefore not require modifications to the frontend application.

Changes to the design or behaviour of the reusable layouts will still require code changes.

---

## 17. Customisation and Overrides

The normal website structure should use reusable templates and structured content.

However, some projects may require presentation that cannot reasonably be represented by the standard project structure.

The CMS should therefore eventually support controlled overrides.

An override should allow a project to bypass normal validation or page structuring and instead point to a specifically implemented page.

Because this bypasses the normal safety and consistency provided by the CMS, the system should:

1. Clearly warn the user that the standard validation or structure is being bypassed.

2. Require explicit confirmation before applying the override.

3. Clearly identify that the project is using a custom implementation.

4. Prevent accidental use of the override during normal project creation.

This provides flexibility without making the standard content system unnecessarily complicated.

---

## 18. Information Architecture Principles

The website structure should follow several principles:

### Simple navigation

The primary navigation should contain only the major sections visitors need.

### Progressive disclosure

Visitors should see the most important information first, with deeper technical information available when required.

### Content-driven structure

Projects and other repeatable content should be generated from structured data rather than manually implemented pages.

### Flexible project presentation

Different projects should be able to communicate their work in different ways.

### Evidence-focused exploration

The structure should encourage visitors to move from claims and summaries towards evidence, documentation and source code.

### Minimal friction

Important destinations such as contact, LinkedIn and GitHub should remain easy to reach.

### Designed for growth

The structure should remain practical as the portfolio expands without requiring a fundamental redesign.

---

## 19. Structural Goal

The final structure should make the website feel less like a traditional online CV and more like a window into Joe's engineering work.

The visitor should be able to enter through a visually engaging project, become curious about how it works, investigate the evidence, explore other projects and eventually understand the wider development journey behind the portfolio.

The structure should therefore support both **quick evaluation** and **deep technical exploration** without compromising either experience.
