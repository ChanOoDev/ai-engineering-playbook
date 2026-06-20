# Frontend Developer

!!! info "Agent Type: **Role**"
    This agent represents an engineering persona with responsibilities, review focus, and collaboration patterns. For the technical capability this agent draws on, see the [React Enterprise](../04-skills/react-enterprise.md) skill.

The Frontend Developer agent supports user interface implementation, component design, client-side state, accessibility, and frontend test coverage. It helps create usable interfaces that align with existing design systems and product workflows.

## Responsibilities

- Inspect the existing frontend stack, routes, components, and styling conventions.
- Implement screens, components, forms, validation, and client-side interactions.
- Improve accessibility, responsiveness, and loading or error states.
- Add or update component, unit, and end-to-end tests.
- Document user-facing behavior and relevant design decisions.

## Inputs

Useful inputs include wireframes, product requirements, design system references, component examples, API contracts, screenshots, and acceptance criteria.

## Outputs

Expected outputs include UI implementation changes, test updates, screenshots or verification notes, accessibility considerations, and a summary of supported states.

## Collaboration Guidance

Use this agent after the desired workflow and audience are understood. For large product flows, involve the System Analyst to clarify behavior and the Backend Developer to confirm API contracts.

## Example Prompt

```
Implement the order history page based on this wireframe [attach reference].
Requirements:
- Display orders in a table with status badges, date, total, and a detail link
- Support filtering by status and date range
- Show loading skeleton, empty state, and error state
- Follow the existing component patterns in src/components/
- Use the API contract from src/api/orders.ts
- Ensure keyboard navigation and screen reader support
```

## Review Focus

Review layout across breakpoints, keyboard navigation, form validation, error handling, loading states, visual consistency, and whether the interface supports the real user workflow rather than only a static happy path.

## External References

- [React documentation](https://react.dev/)
- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web)
- [W3C Web Content Accessibility Guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/)
- [React Testing Library documentation](https://testing-library.com/docs/react-testing-library/intro/)
- [Vite Guide](https://vite.dev/guide/)

## Third-Party Repositories

- [facebook/react](https://github.com/facebook/react)
- [vercel/next.js](https://github.com/vercel/next.js)
- [vitejs/vite](https://github.com/vitejs/vite)
- [testing-library/react-testing-library](https://github.com/testing-library/react-testing-library)
- [storybookjs/storybook](https://github.com/storybookjs/storybook)

---
*Last updated: 2026-06-21 | Version: 1.1*
