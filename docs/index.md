# AI Engineering Playbook

The AI Engineering Playbook is a practical guide for teams adopting AI-assisted software delivery. It explains how to govern AI use, configure the development platform, define agent responsibilities, apply reusable skills, connect Model Context Protocol (MCP) servers, and learn from reference projects.

The playbook is written for engineering leaders, platform teams, architects, developers, security reviewers, and delivery teams that want to use AI systems with clarity, accountability, and repeatable engineering practices.

## What You Will Find

- **Governance** - operating principles, ownership, review expectations, and adoption planning.
- **Platform Setup** - guidance for configuring Claude Code, AITMPL, MCP, and user-level tooling.
- **Agents** - role definitions for common AI-assisted engineering contributors.
- **Skills** - reusable capability profiles for architecture, infrastructure, API, frontend, and specification work.
- **MCP** - setup and usage guidance for common MCP integrations.
- **Reference Projects** - example project patterns that show how the playbook can be applied.

## Recommended Reading Path

1. Start with [Introduction](01-governance/introduction.md) to understand the operating model.
2. Review [Governance](01-governance/governance.md) and [Ownership Matrix](01-governance/ownership-matrix.md) before enabling team-wide use.
3. Configure the tooling in [Platform Setup](02-platform-setup/claude-code.md).
4. Use the [Agents](03-agents/backend-developer.md) and [Skills](04-skills/aws-architect.md) sections to define delivery workflows.
5. Connect approved integrations through the [MCP](05-mcp/github.md) guidance.
6. Adapt patterns from the [Reference Projects](06-reference-projects/product-management.md).

## Local Commands

```bash
mkdocs serve
mkdocs build
```

Use `mkdocs serve` for local editing and `mkdocs build` to validate the generated site before publishing.