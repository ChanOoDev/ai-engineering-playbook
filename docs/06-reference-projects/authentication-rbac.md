# Authentication & RBAC

The Authentication and Role-Based Access Control reference project demonstrates how AI-assisted engineering can support identity-aware applications while preserving strong security review practices.

## Scenario

An application authenticates users through an identity provider and authorizes actions based on roles, permissions, groups, or claims. The system must protect administrative actions, sensitive data, and tenant or organization boundaries.

## Architecture Pattern

A typical implementation includes:

- Identity provider integration using standards such as OAuth 2.0 or OpenID Connect.
- Backend authorization policies for protected endpoints.
- Frontend route guards and user experience states.
- Role and permission management workflows.
- Audit logging for privileged actions.
- Automated tests for allowed and denied access paths.

## AI-Assisted Workflow

The System Analyst can define actors, permissions, and protected workflows. The Solution Architect can choose the authorization model. Backend and Frontend agents can implement policy checks and user experience behavior. The Security Auditor should review the design before release.

## Documentation Outputs

Useful documentation includes authentication flow diagrams, permission matrix, token and claim handling notes, administrative workflows, security assumptions, and troubleshooting guidance.

## Quality Considerations

Review default-deny behavior, privilege escalation paths, tenant isolation, token validation, session handling, error messages, audit coverage, and test cases for negative access scenarios.

## First Implementation Slice

Start with a protected administrative workflow: authenticated users can access their profile, while only administrators can manage roles or permissions.

### Sample Backlog

| Item | Outcome |
| --- | --- |
| Define actors, roles, and protected actions | Permission matrix and access rules |
| Configure identity provider integration | Application can validate authenticated users |
| Protect backend endpoints | Default-deny access model for sensitive actions |
| Add frontend route guards | Users see only allowed workflows |
| Add negative tests | Unauthorized and forbidden paths are covered |

### Acceptance Criteria

- Unauthenticated users cannot access protected endpoints or screens.
- Authenticated non-admin users cannot perform administrative actions.
- Administrators can manage the agreed role or permission workflow.
- Token validation, expiration, and claim mapping are documented.
- Access-denied responses do not leak sensitive details.

### Review Checklist

- Confirm default-deny behavior across backend and frontend routes.
- Confirm tenant or organization boundaries if the application is multi-tenant.
- Confirm audit events for privileged actions.
- Confirm negative authorization tests are included in CI.
## Extension Ideas

Teams can extend this project with delegated administration, just-in-time access, approval workflows, external identity federation, service-to-service authorization, or policy-as-code enforcement.

---
*Last updated: 2026-06-21 | Version: 1.1*