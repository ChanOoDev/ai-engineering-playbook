# Changelog

All notable changes to the AI Engineering Playbook are documented here. The playbook follows [Semantic Versioning](https://semver.org/).

## [1.3.0] - 2026-06-21

### Added

- **Glossary** (`glossary.md`) — 19 term definitions covering all operating terms a junior developer will encounter (agent, skill, MCP, AITMPL, ADR, approval gate, permission profile, etc.).
- **Junior Developer Quick Start** (`02-platform-setup/junior-developer-quickstart.md`) — 9-step safe first path, "What Not To Use AI For" warning list, safe toolkit table, and when-to-stop guidance.
- **AI Troubleshooting** (`02-platform-setup/ai-troubleshooting.md`) — 10 common problems junior developers encounter with causes, fixes, and prevention.
- **Git Daily Usage** (`02-platform-setup/git-daily-usage.md`) — 100+ Git commands organized by task, branch strategy diagrams (GitHub Flow, Git Flow, Trunk-Based), common workflows, and AI-assisted Git usage.
- **Filled artifact examples** in Reference Project Implementation Guide — completed project brief, requirement, ADR, test plan, security review, and deployment runbook using Product Management as the domain.
- **Junior Developer Path** on the homepage — 6-step reading list for developers new to AI-assisted delivery.
- **Cross-links** from onboarding pages to related governance, agent, skill, and troubleshooting pages.

### Changed

- Fixed markdown spacing after Mermaid blocks in `first-ai-assisted-pr.md`, `implementation-guide.md`, `mcp.md`, and `agent-skill-selection.md`.

## [1.2.0] - 2026-06-21

### Added

- First AI-Assisted PR guide for developer onboarding and low-risk first contributions.
- Agent and Skill Selection Guide to map common delivery tasks to agents, skills, and MCP integrations.
- MCP permission profiles covering read-only, review/comment, sandbox write, production read, and production write access.
- Scope and precedence guidance for agents, skills, MCP configuration, and reference project workflows.
- CI hardening guidance for AI-assisted pipeline checks, prompt injection risk, diff limits, and advisory review behavior.
- First implementation slices, sample backlog items, acceptance criteria, and review checklists for all reference projects.

### Changed

- Updated the home page reading path to include the first PR workflow, agent/skill selection, and reference project implementation guide.

## [1.1.0] - 2026-06-21

### Added

- **CLAUDE.md guidance page** (`02-platform-setup/claude-md.md`) — how to encode playbook governance into Claude Code's project context.
- **CI/CD Integration page** (`02-platform-setup/ci-cd-integration.md`) — patterns for AI-assisted CI checks, PR summary generation, and governance enforcement.
- **Changelog** (`changelog.md`) — this file.
- **Taxonomy badges** on all agent and skill pages — clarifies whether a page describes a Role, Capability, or Orchestrator, with cross-references between related agents and skills.
- **Example prompts** to all 8 agent pages, all 6 skill pages, and all 5 MCP pages — concrete prompt templates showing how to use each agent, skill, and integration.
- **Example configurations** to all MCP pages — JSON config snippets for Claude Code integration.
- **Metrics and advancement criteria** to the Adoption Roadmap — concrete KPIs per stage with measurement approaches and stage-transition thresholds.

### Changed

- Expanded Adoption Roadmap with per-stage metrics tables covering cycle time, review quality, developer satisfaction, security incidents, and governance compliance.
- Added cross-references between related agents and skills (e.g., Backend Developer ↔ .NET Enterprise API, Platform Architect ↔ Platform Engineering).

## [1.0.0] - 2026-06-01

### Added

- Initial playbook structure with 6 sections: Governance, Platform Setup, Agents, Skills, MCP, Reference Projects.
- 8 agent role definitions: Backend Developer, Frontend Developer, DevOps Engineer, Security Auditor, System Analyst, Solution Architect, Platform Architect, SpecFlow Orchestrator.
- 6 skill definitions: AWS Architect, Terraform Expert, Platform Engineering, GitHub Spec Kit, .NET Enterprise API, React Enterprise.
- 5 MCP integration guides: GitHub, Context7, Terraform, AWS, Docker.
- 3 reference projects: Product Management, Authentication & RBAC, AWS EC2 Hosted App.
- MkDocs Material theme with GitHub Pages deployment.
- Governance framework with introduction, policies, ownership matrix, and adoption roadmap.

---
*Last updated: 2026-06-21 | Version: 1.3*
