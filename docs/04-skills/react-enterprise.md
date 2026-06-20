# React Enterprise

!!! info "Skill Type: **Technical Capability**"
    This skill represents a reusable technical domain competency. The [Frontend Developer](../03-agents/frontend-developer.md) agent draws on this skill for React component design, state management, and accessibility patterns.

The React Enterprise skill supports scalable frontend development with React and related ecosystems. It focuses on maintainable component design, predictable state management, accessibility, performance, testing, and integration with enterprise APIs.

## When To Use

Use this skill for React applications, component libraries, design system adoption, forms, routing, data fetching, frontend architecture, and UI test strategy.

## Capabilities

- Design component structures that fit existing application patterns.
- Implement accessible forms, navigation, data grids, dashboards, and workflows.
- Review state management, API integration, caching, and error handling.
- Improve performance through sensible rendering and loading strategies.
- Add unit, component, and end-to-end tests.

## Inputs

Provide product requirements, screenshots, design references, API contracts, existing components, routing structure, and target browser or accessibility requirements.

## Expected Output

A useful response should include implementation details, component responsibilities, state and data flow notes, test coverage, and verification across relevant screen sizes.

## Example Prompt

```
Implement a reusable DataTable component for the admin dashboard that:
- Supports sorting, filtering, and pagination
- Renders status badges, action buttons, and formatted dates
- Handles loading, empty, and error states
- Supports keyboard navigation and screen readers
- Follows the existing design system in src/components/ui/

Include: component API, TypeScript interfaces, and Storybook stories.
```

## Review Notes

Review accessibility, keyboard support, responsive layout, loading and empty states, error recovery, form validation, and whether the interface supports the user's real workflow.

## External References

- [React Documentation](https://react.dev/)
- [Next.js Documentation](https://nextjs.org/docs)
- [Vite Guide](https://vite.dev/guide/)
- [TanStack Query Documentation](https://tanstack.com/query/latest/docs/framework/react/overview)
- [W3C Web Content Accessibility Guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/)

## Third-Party Repositories

- [facebook/react](https://github.com/facebook/react)
- [vercel/next.js](https://github.com/vercel/next.js)
- [vitejs/vite](https://github.com/vitejs/vite)
- [TanStack/query](https://github.com/TanStack/query)
- [storybookjs/storybook](https://github.com/storybookjs/storybook)

---
*Last updated: 2026-06-21 | Version: 1.1*
