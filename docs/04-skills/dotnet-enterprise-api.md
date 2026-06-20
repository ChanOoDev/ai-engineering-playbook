# .NET Enterprise API

!!! info "Skill Type: **Technical Capability**"
    This skill represents a reusable technical domain competency. The [Backend Developer](../03-agents/backend-developer.md) agent draws on this skill for ASP.NET Core implementation, API design, and data access patterns.

The .NET Enterprise API skill supports design, implementation, and review of production-grade APIs built with modern .NET. It focuses on maintainability, security, performance, observability, and clean service boundaries.

## When To Use

Use this skill for ASP.NET Core APIs, Minimal APIs, controller-based services, authentication and authorization flows, validation, data access, integration testing, and API documentation.

## Capabilities

- Design RESTful API endpoints and application service boundaries.
- Implement validation, error handling, dependency injection, and configuration patterns.
- Review Entity Framework, Dapper, or repository usage for correctness and performance.
- Improve OpenAPI documentation and client-facing contracts.
- Add unit, integration, and contract tests.

## Inputs

Provide requirements, existing API code, data models, OpenAPI contracts, authentication requirements, error logs, and examples of local conventions.

## Expected Output

A useful response should include implementation guidance, code changes when requested, tests, validation commands, and notes on compatibility or migration impact.

## Example Prompts

**Designing a new API endpoint:**

```
Design a GET /api/customers/{id}/orders endpoint that:
- Returns paginated orders with cursor-based pagination
- Supports filtering by status (Pending, Shipped, Delivered)
- Includes order items and totals in the response
- Follows the existing controller patterns in src/Controllers/
- Returns proper ProblemDetails for 404 and 400 errors
```

**Adding validation and error handling:**

```
Add FluentValidation to the CreateProductCommand in src/Features/Products/.
Validation rules:
- Name: required, 3-200 characters
- Price: positive, max 2 decimal places
- SKU: required, unique, alphanumeric only
- CategoryId: must reference an existing active category

Return validation errors as a structured ProblemDetails response.
Follow the existing validation patterns in src/Features/Orders/.
```

**Reviewing EF Core query performance:**

```
Review the query in src/Features/Reports/SalesReportQuery.cs for
performance issues. Check for:
- N+1 queries from missing Includes
- Client-side evaluation
- Missing indexes for the WHERE/ORDER BY columns
- Over-fetching data that isn't used in the response

Suggest specific changes and explain the expected impact.
```

**Generating OpenAPI documentation:**

```
Generate or update the OpenAPI documentation for the Products controller
in src/Controllers/ProductsController.cs. Include:
- Accurate request/response schemas with examples
- All possible status codes with descriptions
- Authentication requirements (Bearer token)
- Pagination parameter documentation

Use the existing Swashbuckle configuration in Program.cs.
```

## Review Notes

Review authorization, model validation, exception handling, query performance, logging, dependency lifetimes, and backwards compatibility. Public APIs require special care around versioning and error contracts.

## External References

- [ASP.NET Core Documentation](https://learn.microsoft.com/aspnet/core/)
- [Entity Framework Core Documentation](https://learn.microsoft.com/ef/core/)
- [.NET Architecture Guides](https://dotnet.microsoft.com/learn/dotnet/architecture-guides)
- [Microsoft REST API Guidelines](https://github.com/microsoft/api-guidelines)
- [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Third-Party Repositories

- [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore)
- [dotnet/efcore](https://github.com/dotnet/efcore)
- [dotnet-architecture/eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb)
- [dotnet-architecture/eShop](https://github.com/dotnet/eShop)
- [domaindrivendev/Swashbuckle.AspNetCore](https://github.com/domaindrivendev/Swashbuckle.AspNetCore)

---
*Last updated: 2026-06-21 | Version: 1.1*
