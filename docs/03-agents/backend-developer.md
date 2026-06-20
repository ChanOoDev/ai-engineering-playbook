# Backend Developer

!!! info "Agent Type: **Role**"
    This agent represents an engineering persona with responsibilities, review focus, and collaboration patterns. Use it when you need a server-side perspective on implementation work. For technical capabilities, this agent draws on skills like [.NET Enterprise API](../04-skills/dotnet-enterprise-api.md) (for .NET projects), or applies equivalent patterns for other stacks (Spring Boot, FastAPI, Django, Express).

The Backend Developer agent supports server-side implementation, API design, data access, integration logic, and automated testing. It helps turn clear requirements into maintainable service behavior while following the repository's architecture and coding standards.

## Responsibilities

- Analyze existing backend structure before proposing changes.
- Implement endpoints, services, domain logic, data access, and validation.
- Generate or improve unit, integration, and contract tests.
- Identify edge cases, error handling gaps, and performance concerns.
- Document API behavior and operational assumptions.

## Inputs

Useful inputs include user stories, API contracts, database schemas, error logs, failing tests, architecture notes, and examples of existing service patterns.

## Outputs

Expected outputs include implementation diffs, test updates, migration notes, API documentation, and a concise explanation of validation performed.

## Collaboration Guidance

Use this agent when requirements are reasonably clear and the repository contains enough context to infer local conventions. For cross-service changes, pair it with the Solution Architect or System Analyst agent before implementation.

## Example Prompts

**Implementing an endpoint from a user story:**

```
Implement the POST /api/orders endpoint based on this user story:

"As a customer, I can place an order so that items are reserved and I receive a confirmation."

Requirements:
- Validate that all line items exist and are in stock
- Create the order with status "Pending"
- Reserve inventory atomically
- Return the order ID and confirmation number
- Follow the existing patterns in src/Services/OrderService.cs
```

**Adding integration tests:**

```
Write integration tests for the OrderService.CreateOrder method.
Cover these scenarios:
- Happy path with valid items
- Empty cart rejection
- Insufficient inventory
- Duplicate submission idempotency

Use the existing test patterns in tests/Integration/OrderTests.cs.
Run with: dotnet test --filter "OrderTests"
```

**Investigating a failing test:**

```
The test CreateOrder_WithValidItems_ShouldReturnConfirmation is failing
on main. Investigate the failure, identify the root cause, and propose
a fix. Do not change the test unless the test itself is wrong.

Run: dotnet test --filter "CreateOrder_WithValidItems" --logger "console;verbosity=detailed"
```

**Reviewing a PR for backend concerns:**

```
Review this PR diff for backend concerns. Focus on:
- Authentication and authorization correctness
- Input validation and error handling
- Transaction boundaries and data consistency
- SQL injection or ORM misuse
- Missing tests or edge cases

Flag issues with severity (critical/warning/suggestion) and explain why.
```

**Implementing an endpoint (Python/FastAPI):**

```
Implement a POST /api/products endpoint in this FastAPI project.

Requirements:
- Accept JSON body with name, sku, price, category_id
- Validate: name required, sku unique, price positive
- Return 201 with the created product
- Return 422 with structured errors for validation failures
- Follow existing patterns in app/routers/products.py
- Add tests in tests/test_products.py

Run with: pytest tests/test_products.py -v
```

**Implementing an endpoint (Node/Express):**

```
Add a GET /api/orders/:id endpoint to this Express API.

Requirements:
- Look up order by ID, return 404 if not found
- Include order items and totals in response
- Require authentication (use existing auth middleware)
- Follow patterns in src/routes/orders.js
- Add tests using the existing supertest setup

Run with: npm test -- --grep "orders"
```

## Good vs. Bad Usage

!!! tip "Good usage"
    - Clear requirements with acceptance criteria
    - References to existing code patterns and files
    - Specific test scenarios to cover
    - Named constraints (e.g., "use the existing UnitOfWork pattern")

!!! warning "Avoid"
    - Vague requests like "fix the API" without context
    - Asking for production access changes without review
    - Delegating architecture decisions without human input
    - Accepting output without running tests

## Review Focus

Review authentication, authorization, validation, transaction boundaries, data consistency, observability, and backwards compatibility. Generated backend code should never be accepted without tests or a clear explanation of why tests were not practical.

## External References

- [ASP.NET Core documentation](https://learn.microsoft.com/aspnet/core/)
- [Spring Guides](https://spring.io/guides)
- [FastAPI documentation](https://fastapi.tiangolo.com/)
- [PostgreSQL documentation](https://www.postgresql.org/docs/)
- [Microservices by Martin Fowler](https://martinfowler.com/articles/microservices.html)

## Third-Party Repositories

- [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore)
- [spring-projects/spring-boot](https://github.com/spring-projects/spring-boot)
- [fastapi/fastapi](https://github.com/fastapi/fastapi)
- [django/django](https://github.com/django/django)
- [expressjs/express](https://github.com/expressjs/express)

---
*Last updated: 2026-06-21 | Version: 1.1*
