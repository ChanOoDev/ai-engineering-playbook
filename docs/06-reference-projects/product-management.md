# Product Management

The Product Management reference project demonstrates how AI-assisted engineering can support a business application with clear domain concepts, workflow rules, API boundaries, and user-facing documentation.

## Scenario

A product management system maintains product records, categories, pricing, lifecycle status, and approval workflows. It may integrate with inventory, order management, catalog publishing, and reporting systems.

## Architecture Pattern

A typical implementation includes:

- A web frontend for product managers and operations users.
- Backend APIs for product, category, price, and status management.
- A relational database for authoritative product data.
- Integration events or APIs for downstream systems.
- Audit logging for product changes and approval decisions.
- Role-based access control for create, update, approve, and publish actions.

## AI-Assisted Workflow

The [System Analyst](../03-agents/system-analyst.md) agent can clarify product lifecycle rules and acceptance criteria. The [Solution Architect](../03-agents/solution-architect.md) can define service boundaries and integration contracts. [Backend](../03-agents/backend-developer.md) and [Frontend](../03-agents/frontend-developer.md) agents can implement the API and interface. The [Security Auditor](../03-agents/security-auditor.md) can review access control, auditability, and data exposure.

## Documentation Outputs

Useful documentation includes domain glossary, user workflow, API reference, data model summary, permission matrix, operational runbook, and release notes.

## Quality Considerations

Review data validation, duplicate product handling, price precision, audit trails, approval state transitions, and integration failure behavior. Product data often feeds customer-facing or revenue-impacting systems, so traceability matters.

## First Implementation Slice

Start with a narrow vertical slice: create a product record with category, price, lifecycle status, validation, and audit logging.

### Sample Backlog

| Item | Outcome |
| --- | --- |
| Define product fields and lifecycle states | Shared domain model and glossary |
| Create product API | Validated endpoint for product creation |
| Add product list view | Product managers can inspect created records |
| Capture audit event | Product creation is traceable |
| Add tests | Happy path, validation errors, duplicate SKU, invalid category |

### Acceptance Criteria

- A user with create permission can create a product with required fields.
- Invalid price, missing SKU, or inactive category is rejected with clear errors.
- A duplicate SKU cannot be created.
- Product status starts in the agreed initial state.
- The change writes an audit record with actor, timestamp, and product ID.

### Review Checklist

- Validate price precision and currency assumptions.
- Confirm role-based access control for create and update actions.
- Confirm audit logging is durable and searchable.
- Confirm downstream integrations are not triggered until publishing is approved.
## Extension Ideas

Teams can extend this project with bulk import, product versioning, approval notifications, catalog publishing, analytics dashboards, or integration with master data management systems.

---
*Last updated: 2026-06-21 | Version: 1.1*