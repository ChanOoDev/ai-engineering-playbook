# AITMPL Installation Guide

Some agents and skills in this playbook can be sourced from [AITMPL](https://aitmpl.com/), also documented as Claude Code Templates. AITMPL provides ready-to-use Claude Code components such as agents, skills, commands, MCP integrations, settings, hooks, and templates.

Use this guide to install AITMPL components into a project while keeping the governance, review, and security practices in this playbook intact.

## Prerequisites

Before installing components, confirm that the workstation has:

- Node.js 14 or later.
- Claude Code installed and authenticated.
- Git, when repository integration or version control workflows are required.
- Write access to the target project directory.
- Approval to install any component that can access external systems, credentials, or sensitive data.

## Recommended Installation Method

Use `npx` for most installations. This runs the current CLI without requiring a global package installation.

```bash
npx claude-code-templates@latest
```

The CLI opens an interactive selector for browsing and installing available components. This is the safest starting point when evaluating AITMPL for a project because it makes the selected components visible before installation.

## Install Individual Agents

Agents are installed into the project's `.claude/agents/` directory. Use direct installation when the component name is already known.

```bash
npx claude-code-templates@latest --agent development-team/frontend-developer
```

For project work, install only the agents the team expects to use. Avoid adding large collections of unused agents because they increase review surface and make local configuration harder to reason about.

## Install Individual Skills

Skills are installed into the project's `.claude/skills/` directory. Use skills for reusable capabilities that should be loaded when a task requires specialized knowledge or workflow instructions.

```bash
npx claude-code-templates@latest --skill pdf-processing
```

Review each installed skill before relying on it for production work. Skills can contain detailed instructions and supporting files, so treat them as executable process guidance rather than passive documentation.

## Batch Installation

For team onboarding or a known project stack, install multiple components in one command.

```bash
npx claude-code-templates@latest \
  --agent development-team/frontend-developer \
  --agent security/security-auditor \
  --skill pdf-processing \
  --mcp development/github-integration \
  --yes
```

Use `--yes` only when the selected components have already been reviewed. For first-time setup, prefer the interactive flow or a dry run.

## Dry Run

Use `--dry-run` to inspect planned changes before writing files.

```bash
npx claude-code-templates@latest \
  --agent development-team/frontend-developer \
  --dry-run
```

A dry run is recommended before adding components to shared repositories or onboarding scripts.

## Install To A Specific Directory

By default, components install into the current directory. Use `--directory` when preparing another project path.

```bash
npx claude-code-templates@latest \
  --directory /path/to/project \
  --agent development-team/frontend-developer
```

Run the command from a trusted shell and confirm the target directory before installation.

## Expected Project Structure

After installation, AITMPL components are stored under `.claude/` in the project.

```text
.claude/
|-- agents/
|-- commands/
|-- hooks/
|-- mcps/
|-- settings/
|-- skills/
`-- config.json
```

Commit project-level components only when the team has reviewed them and agreed they should be shared. Keep personal experiments out of shared repositories unless they are promoted through normal review.

## MCP Credentials

Some MCP components require environment variables such as tokens, database URLs, or cloud credentials. Store those values using the approved secret-management pattern for the project.

Do not commit `.env` files, personal access tokens, cloud access keys, database passwords, or other secrets. Prefer short-lived credentials and least-privilege access for any MCP component that can read or mutate external systems.

## Verification

Run the AITMPL health check after installation.

```bash
npx claude-code-templates@latest --health-check
```

Also verify manually that the expected files were installed:

```bash
ls .claude/
ls .claude/agents/
ls .claude/skills/
```

Restart Claude Code after installation so it reloads project configuration.

## Governance Checklist

Before adopting an AITMPL agent or skill for team use, confirm:

- The component purpose is clear and relevant to the project.
- The component instructions do not conflict with team standards.
- Any MCP or command dependency has an approved permission model.
- The component does not require committing secrets or private data.
- The owning team knows how to update, remove, or replace it.
- Generated outputs remain subject to normal engineering review.

## Third-Party Discovery Sources

Use third-party catalogs and repositories as discovery sources, not as automatic trust sources. Review every installed agent, skill, MCP server, command, hook, or template before using it in a shared project or production workflow.

### Skill Catalogs And Repositories

- [skills.sh](https://www.skills.sh/) - Open Agent Skills directory with install commands and a skills leaderboard.
- [Anthropic Agent Skills](https://github.com/anthropics/skills) - Public repository of example and production-inspired Claude skills.
- [Vercel Agent Skills](https://github.com/vercel-labs/agent-skills) - Vercel-maintained skill collection for web and frontend workflows.
- [Microsoft Azure Skills](https://github.com/microsoft/azure-skills) - Azure-focused skills and MCP server configurations.
- [CrewAI Skills](https://github.com/crewAIInc/skills) - CrewAI skill marketplace repository for Claude Code and compatible agent tools.

### Agent Catalogs And Framework Repositories

- [Agent.ai](https://agent.ai/) - Marketplace and professional network for discovering and building AI agents.
- [AITMPL Agents](https://aitmpl.com/agents/) - Claude Code Templates catalog for installing agent components.
- [Mastra Templates](https://mastra.ai/templates) - Starter templates for TypeScript agent projects.
- [CrewAI](https://github.com/crewAIInc/crewAI) - Open-source framework for role-based autonomous agent teams.
- [LangGraph](https://github.com/langchain-ai/langgraph) - Framework for building stateful, resilient agent workflows.

### MCP Registries, Courses, And Repositories

- [Official MCP Registry](https://github.com/modelcontextprotocol/registry) - Community-driven registry service for MCP servers.
- [Model Context Protocol Servers](https://github.com/modelcontextprotocol/servers) - Reference and community MCP server implementations.
- [Glama MCP Directory](https://glama.ai/mcp) - Searchable MCP directory for servers, connectors, clients, and tools.
- [MCP.so](https://mcp.so/) - Third-party marketplace and directory for MCP servers and clients.
- [Mastra MCP Course](https://mastra.ai/course) - Hands-on course for building agents with tools, memory, workflows, and MCP.

### Evaluation Guidance

For third-party sources, check the repository owner, license, commit activity, issue history, install script behavior, required secrets, dependency chain, and permission model. Prefer dry runs, sandboxed installs, and read-only credentials until the component has been reviewed.

## Troubleshooting

If `npx` is unavailable, install or update Node.js. If components do not appear in Claude Code, confirm the current working directory, inspect `.claude/`, restart Claude Code, and run the health check.

If an MCP component fails, check required environment variables, credential scope, network access, and the component's configuration file under `.claude/mcps/`.