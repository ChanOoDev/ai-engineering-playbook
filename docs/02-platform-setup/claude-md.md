# CLAUDE.md

CLAUDE.md is a special file that Claude Code reads automatically when it starts a session in a repository. It provides project-specific context, conventions, and constraints that shape how the AI assistant behaves. Think of it as the bridge between this playbook's governance principles and the actual AI workflow.

## Why CLAUDE.md Matters

This playbook defines principles, agent roles, skills, and review expectations. CLAUDE.md is where you encode those into Claude Code's working context. Without it, every session starts from scratch. With it, Claude Code understands your project's conventions before you type your first prompt.

A well-written CLAUDE.md reduces repetitive instruction, enforces consistency, and makes governance rules actionable rather than aspirational.

## What To Include

A practical CLAUDE.md covers these areas:

### Project Context

```markdown
## Project
This is the order management service for ACME Corp's e-commerce platform.
It handles order creation, payment processing, inventory reservation,
and fulfillment coordination.

Stack: .NET 8, EF Core, PostgreSQL, RabbitMQ, deployed on AWS ECS.
```

### Coding Conventions

```markdown
## Conventions
- Use record types for DTOs, classes for entities
- Follow the CQRS pattern with MediatR for all endpoints
- All database changes require EF Core migrations
- Error responses must use ProblemDetails (RFC 9457)
- No direct SQL — use EF Core or Dapper with parameterized queries
```

### Testing Expectations

```markdown
## Testing
- All new endpoints require integration tests in tests/Integration/
- Use Testcontainers for database tests
- Run: dotnet test --filter "Category=Integration"
- Aim for happy path + at least 2 error scenarios per endpoint
```

### Review Standards

```markdown
## Review Standards
From our playbook governance:
- All AI-assisted code requires human review before merge
- Security-sensitive changes (auth, data access, payments) require
  Security Auditor review
- Infrastructure changes require DevOps review
```

### MCP and Tool Guidance

```markdown
## Available Tools
- GitHub MCP: use for PR summaries and issue lookup (read-only)
- Context7: use to verify current library API syntax before suggesting code
- Terraform MCP: use for plan review only (never apply)
```

### What NOT To Do

```markdown
## Guardrails
- Never commit secrets, API keys, or connection strings
- Never modify production configuration or infrastructure directly
- Never bypass the CI pipeline or branch protection rules
- Never generate code that handles payment processing without explicit review
```

## Mapping Playbook Principles to CLAUDE.md

| Playbook Principle | CLAUDE.md Translation |
|---|---|
| Human accountability remains explicit | "All changes require a named human reviewer before merge" |
| Context quality drives output quality | Document project structure, conventions, and common patterns |
| Security and privacy are design constraints | List data handling rules, secret management, and access boundaries |
| AI output is reviewed like any other work | Reference branch protection, required reviews, and CI checks |
| Automation should be observable | Document logging, tracing, and audit expectations |

## Example: Complete CLAUDE.md

```markdown
# ACME Order Service

## Project
Order management microservice for ACME e-commerce.
Handles: order creation, payment coordination, inventory reservation,
fulfillment handoff.

## Stack
- .NET 8 Minimal APIs with MediatR
- EF Core 8 with PostgreSQL
- RabbitMQ for async messaging
- AWS ECS for deployment
- Terraform for infrastructure

## Conventions
- Endpoints: POST/GET /api/orders, follow REST conventions
- Validation: FluentValidation in Features/{Feature}/Validators/
- Errors: Always return ProblemDetails with correlation IDs
- Logging: Use structured logging with ILogger, include correlation ID
- Migrations: dotnet ef migrations add {Name} --project src

## Testing
- Integration tests in tests/Integration/ using Testcontainers
- Run: dotnet test --filter "Category=Integration"
- Every endpoint needs: happy path, validation error, not found

## Security
- JWT auth via IdentityProvider (see src/Auth/Config.cs)
- All endpoints require [Authorize] unless explicitly [AllowAnonymous]
- Never log PII or payment data
- Rate limiting: 100 req/min per user on write endpoints

## Infrastructure
- Terraform in infra/ with workspace per environment
- Review plans before apply — never auto-apply to production
- State backend: S3 with DynamoDB locking

## Guardrails
- Do not modify infra/ without DevOps review
- Do not change auth configuration without Security review
- Do not commit .env files or connection strings
- Do not generate payment processing code without explicit approval
```

## Where To Place It

- **Repository root**: `CLAUDE.md` — applies to the entire project
- **Subdirectories**: `src/api/CLAUDE.md` — applies when working in that subdirectory
- **User-level**: `~/.claude/CLAUDE.md` — applies to all your projects (personal preferences)

Claude Code reads all applicable CLAUDE.md files, with more specific ones taking precedence.

## Relationship to AITMPL

AITMPL templates define one-off or recurring tasks. CLAUDE.md defines persistent project context. They complement each other:

- **CLAUDE.md** = "Here's how this project works and what rules apply"
- **AITMPL template** = "Here's the specific task I want you to do right now"

A good CLAUDE.md makes every AITMPL template more effective because the AI already understands the project context.

## Keeping It Current

CLAUDE.md should evolve with the project. Update it when:

- Conventions change (new patterns, deprecated approaches)
- New tools or integrations are approved
- Review standards are updated
- Common mistakes need to be prevented
- New team members would benefit from the context

Treat CLAUDE.md as engineering documentation, not a one-time setup task.

## Related Pages

- [Claude Code](claude-code.md) — the tool that reads CLAUDE.md
- [AITMPL](aitmpl.md) — task templates that complement project context
- [User Level Setup](user-level-setup.md) — personal configuration across projects
- [Governance](../01-governance/governance.md) — the principles CLAUDE.md should encode

---
*Last updated: 2026-06-21 | Version: 1.1*
