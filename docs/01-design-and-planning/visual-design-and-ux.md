# Visual Design and UX

## 1. Overview

The website should present a professional but highly personal engineering identity.

It should avoid the appearance of a conventional corporate portfolio or online CV. Instead, the design should feel like an interactive window into Joe Waldron's engineering work, interests and development.

The visual identity should combine:

- Motorsport influence.

- Futuristic technology.

- Software engineering.

- Engineering credibility.

- Approachability.

- Personal identity.

The website should encourage visitors to explore rather than simply scan a list of achievements.

---

## 2. Design Goals

The design should:

- Create a strong first impression.

- Make important information immediately visible.

- Encourage visitors to explore projects.

- Make technical work visually interesting.

- Remain professional enough for recruiters and hiring managers.

- Feel approachable rather than corporate.

- Support both quick scanning and deeper reading.

- Provide a consistent visual identity across all pages.

- Remain practical to implement within the Version 1 timeframe.

Visual polish should be concentrated on the areas that visitors interact with most.

---

## 3. Visual Inspiration

The design direction is influenced by several existing interfaces:

### Spotify

The dark interface and strong use of contrast provide inspiration for the overall dark visual environment.

### Octopus Energy

The use of distinctive colour and visual identity provides inspiration for making the website feel recognisable rather than generic.

### Aston Martin

The cohesiveness and premium engineering identity provide inspiration for the overall brand presentation.

### BBC

The navigation provides inspiration for creating a clear and accessible primary navigation system.

These references should influence the design without resulting in direct imitation.

---

## 4. Dark Theme

The website should use a dark theme as its primary and initially only theme.

A dark interface is preferred because it:

- Fits the intended technical aesthetic.

- Works well with motorsport-inspired visual design.

- Provides strong contrast for project imagery.

- Creates a more immersive environment.

- Matches Joe's personal preference.

A light mode is not required for Version 1.

---

## 5. Colour System

The colour system should use a dark base with carefully selected accent colours.

The accents should provide:

- Visual hierarchy.

- Interactive feedback.

- Branding.

- Project highlighting.

- Links and calls to action.

The colour palette should be distinctive enough to create a recognisable identity while remaining professional.

Colour should not be used excessively. Important actions and information should receive the strongest visual emphasis.

---

## 6. Motorsport and Technology Influence

The visual language should take inspiration from modern motorsport and technology without becoming a themed racing website.

Appropriate influences may include:

- Technical typography.

- Strong visual hierarchy.

- Structured layouts.

- Subtle geometric elements.

- High-contrast imagery.

- Technical data presentation.

- Motion-inspired visual details.

- Precise spacing and alignment.

The design should communicate engineering rather than simply displaying racing imagery.

---

## 7. Personal Rather Than Corporate

The website should feel like a personal engineer's portfolio rather than a corporate recruitment site.

It should communicate:

- Curiosity.

- Passion.

- Creativity.

- Adaptability.

- Technical confidence.

- Approachability.

The design should allow Joe's personality to be visible without sacrificing professionalism.

---

## 8. Homepage Design

The homepage should receive the highest level of visual polish.

The initial viewport should communicate the core identity immediately.

It should prominently present:

- Joe Waldron's name.

- A concise description of his engineering direction.

- The strongest current project or achievement.

- A clear visual element.

- Direct contact and professional links.

The featured project should be visually dominant enough to encourage interaction.

The homepage should not attempt to display every achievement immediately.

---

## 9. Project Cards

Project cards should provide a visually engaging way to browse the portfolio.

A typical project card should contain:

```text
┌─────────────────────────┐
│                         │
│         Image           │
│                         │
└─────────────────────────┘
Project Title
[Tag] [Tag] [Tag]

Short description of the
project and its purpose.
```

The card should provide enough information to establish whether the project is interesting without attempting to explain the complete project.

Project cards should provide clear visual feedback when interacted with.

---

## 10. Project Pages

Project pages should prioritise the quality of the project itself.

The page should provide a strong visual introduction before moving into detailed technical information.

The layout should avoid the common article design where all content is placed into a narrow central column with large amounts of unused space or unrelated content surrounding it.

Instead, the page should make effective use of the available screen space while maintaining comfortable reading widths.

Project pages should combine:

- Large visual elements.

- Structured technical sections.

- Supporting media.

- Clear headings.

- Evidence.

- Links.

- Appropriate whitespace.

---

## 11. Technical Information

Technical explanations should be presented at a level suitable for technically knowledgeable visitors while remaining understandable to recruiters.

The top layer of information should provide a concise explanation of the technical work.

Deeper sections can then provide:

- Technical terminology.

- Implementation details.

- Design decisions.

- Testing methodology.

- Results.

- Supporting evidence.

Future versions may introduce expandable technical explanations or information inserts where they provide value.

The initial version should avoid unnecessary interface complexity.

---

## 12. Typography

Typography should prioritise:

- Readability.

- Strong hierarchy.

- Technical character.

- Consistency.

Different text levels should be visually distinguishable so that visitors can scan content quickly.

Long technical explanations should remain comfortable to read without being forced into an excessively narrow column.

Typography should contribute to the technical aesthetic without sacrificing accessibility.

---

## 13. Navigation

The navigation should be:

- Consistent.

- Easy to identify.

- Available throughout the website.

- Simple enough to understand immediately.

- Visually integrated with the overall design.

The navigation should be inspired by the clarity of the BBC navigation system while adapting it to the website's own visual identity.

The navigation should not dominate the page.

---

## 14. Interaction Design

Interactive elements should provide clear feedback.

This may include:

- Hover states.

- Focus states.

- Active states.

- Subtle movement.

- Highlight effects.

- Transitions.

Animations are not a major requirement for Version 1.

If implementation time becomes limited, clear visual feedback should take priority over complex animation.

---

## 15. Animation

Animation should be subtle and purposeful.

Potential uses include:

- Project card interaction.

- Button transitions.

- Page transitions.

- Navigation interaction.

- Media interaction.

Animations should never make the website feel slower or interfere with navigation.

Complex animation should be considered a later enhancement rather than a Version 1 requirement.

---

## 16. Pop-ups

The website should avoid unnecessary pop-ups.

There should be no intrusive:

- Newsletter prompts.

- Account registration prompts.

- Advertising.

- Promotional overlays.

- Repeated sign-in requests.

The primary exception is the cookie/privacy consent interface where legally required.

The website should allow visitors to explore content without interruption.

---

## 17. Responsive Design

The initial website should be designed primarily for desktop and laptop visitors because recruiters and engineers are likely to access the portfolio from larger screens.

However, the layout should remain functional on smaller screens.

A dedicated mobile-specific design is a future enhancement rather than a Version 1 requirement.

The underlying component system should avoid decisions that make future mobile optimisation unnecessarily difficult.

---

## 18. Accessibility

Accessibility should be considered during the initial implementation rather than being treated entirely as a future feature.

The website should provide:

- Appropriate colour contrast.

- Keyboard-accessible controls.

- Clear focus states.

- Semantic structure.

- Readable typography.

- Meaningful alternative text for images where appropriate.

More advanced accessibility features, including options specifically designed around dyslexia, can be introduced later.

Accessibility improvements should not require a fundamental redesign of the site.

---

## 19. Media Presentation

Images, videos and audio should be treated as important project evidence.

Media components should:

- Present content clearly.

- Support appropriate aspect ratios.

- Avoid unnecessarily large downloads where possible.

- Provide suitable controls.

- Fit naturally into project pages.

The component system should provide reusable media presentation rather than requiring each project to implement its own gallery.

---

## 20. Visual Hierarchy

The website should consistently prioritise information in the following general order:

1. Identity.

2. Current achievement or featured project.

3. Evidence.

4. Project explanation.

5. Supporting technical information.

6. Additional portfolio information.

7. Contact and external resources.

This hierarchy should help visitors understand the website quickly while encouraging deeper exploration.

---

## 21. Design Priorities for Version 1

Because development time is limited, visual effort should be concentrated in the following order:

### Highest priority

- Homepage.

- Featured project presentation.

- Default project page.

- Project cards.

- Primary navigation.

- Typography and colour system.

### Medium priority

- About Me.

- Education.

- Experience.

- Contact.

- Filtering interactions.

### Lower priority

- Complex animations.

- Advanced transitions.

- Highly customised CMS styling.

- Advanced mobile layouts.

- Experimental visual effects.

The website should be functional and visually credible before additional polish is attempted.

---

## 22. UX Principles

The website should follow these principles:

### Curiosity over information overload

The design should encourage visitors to investigate rather than present every detail immediately.

### Evidence over decoration

Visual elements should primarily support the projects and engineering work.

### Professional but personal

The site should feel credible to employers while still representing Joe as an individual.

### Clear over complex

Visual effects and interactions should never make the website difficult to understand.

### Consistent

Reusable components should provide a consistent experience across the website.

### Fast

Visual design should not compromise loading performance.

### Accessible

Visitors should be able to navigate and understand the website regardless of their method of interaction.

---

## 23. Overall Design Direction

The final visual direction can be summarised as:

> **A dark, motorsport-inspired engineering portfolio with a futuristic technical aesthetic, presented through a friendly and approachable personal identity.**

The website should feel like an engineer's workspace translated into an accessible digital experience rather than a traditional online CV.

The design should make visitors curious enough to investigate the projects, while the underlying content and evidence should provide the technical credibility to support that curiosity.
