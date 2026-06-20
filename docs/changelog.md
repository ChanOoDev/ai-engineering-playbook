# Changelog

All notable changes to the AI Engineering Playbook are documented here. The playbook follows [Semantic Versioning](https://semver.org/).

## [1.6.0] - 2026-06-21

### Added

- **MkDocs and GitHub Pages Guide** (`02-platform-setup/mkdocs-github-pages-guide.md`) — single reference for MkDocs configuration, local development, Markdown extensions, Mermaid diagrams, GitHub Pages deployment pipeline, adding pages/sections, and troubleshooting.
- **Spec-Driven SDLC** (`07-spec-driven-sdlc/spec-driven-sdlc.md`) — full specification-driven software development lifecycle with AI assist. Covers 8 phases, Mermaid diagrams, agent mapping, 10 pros and 10 cons, when-to-use guide, and a full walkthrough example.
- **Configuration Reference** (`02-platform-setup/configuration-reference.md`) — unified reference for all components across all 4 configuration levels (user, project, directory, task/session). Includes precedence rules, decision matrix, and setup checklists.
- **Glossary** (`glossary.md`) — 27 term definitions including CI/CD, IAM, PR, Deployment, RBAC, SDLC, User Story, agent, skill, MCP, AITMPL, ADR, and more.
- **Junior Developer Quick Start** (`02-platform-setup/junior-developer-quickstart.md`) — 9-step safe first path, "What Not To Use AI For" warning list, safe toolkit table, and when-to-stop guidance.
- **AI Troubleshooting** (`02-platform-setup/ai-troubleshooting.md`) — 10 common problems junior developers encounter with causes, fixes, and prevention.
- **Git Daily Usage** (`02-platform-setup/git-daily-usage.md`) — 100+ Git commands, branch strategy diagrams (GitHub Flow, Git Flow, Trunk-Based), git bisect, .gitignore basics, and AI-assisted Git usage.
- **First AI-Assisted PR** (`02-platform-setup/first-ai-assisted-pr.md`) — step-by-step workflow with Mermaid diagram, PR checklist, and cross-links.
- **Agent and Skill Selection Guide** (`03-agents/agent-skill-selection.md`) — task mapping table, precedence order, scope boundaries, handoff diagram, and review questions.
- **CLAUDE.md guidance page** (`02-platform-setup/claude-md.md`) — how to encode playbook governance into Claude Code's project context with complete example.
- **CI/CD Integration page** (`02-platform-setup/ci-cd-integration.md`) — patterns for AI-assisted CI checks, PR summary generation, governance enforcement, and full pipeline example.
- **Filled artifact examples** in Reference Project Implementation Guide — completed project brief, requirement, ADR, test plan, security review, and deployment runbook.
- **Junior Developer Path** on the homepage — 6-step reading list for developers new to AI-assisted delivery.
- **Taxonomy badges** on all 8 agent pages and 6 skill pages — clarifies Role, Capability, or Orchestrator with cross-references.
- **Example prompts** to all 8 agent pages, all 6 skill pages, and all 5 MCP pages.
- **Example configurations** to all 5 MCP pages — JSON config snippets for Claude Code.
- **Metrics and advancement criteria** to the Adoption Roadmap — concrete KPIs per stage.
- **MCP permission profiles** — read-only, review/comment, sandbox write, production read, production write.
- **CI hardening guidance** — prompt injection risk, diff limits, advisory review behavior.
- **First implementation slices** for all reference projects — sample backlog items, acceptance criteria, and review checklists.
- **Metadata footers** (last updated, version) to all content pages.

### Changed

- Expanded User Level Setup — added macOS/Linux/Windows setup commands, Claude Code install, verification checklist, environment hygiene commands, troubleshooting table, and cross-links.
- Expanded Adoption Roadmap with per-stage metrics tables and advancement criteria.
- Added cross-references between related agents and skills.
- Added cross-links to all three reference project pages linking agent/skill names to their dedicated pages.
- Added inline template example to AITMPL page.
- Updated home page reading path to include first PR workflow, agent/skill selection, and reference project implementation guide.
- Added MCP config example and validation commands to MCP Setup page.
- Added install commands, CLAUDE.md cross-link, and permission modes table to Claude Code page.
- Added severity rubric (critical/high/medium/low) with definitions, examples, and required actions to Security Auditor agent.
- Added multi-framework example prompts (Python/FastAPI, Node/Express) to Backend Developer agent — now supports .NET, Python, and Node.js.
- Replaced SpecFlow Orchestrator BDD-focused external references with orchestration-relevant references (GitHub Projects, Team Topologies, DORA, Backstage, ArgoCD).
- Added glossary terms: Deployment, RBAC, SDLC, User Story (27 total).

### Fixed

- Fixed MCP Setup patterns table — added Setup Guide column linking to dedicated pages, marked Kubernetes/Vercel as team-documented.
- Fixed Implementation Guide — replaced Kubernetes MCP references with Docker MCP.
- Fixed Terraform/AWS MCP — updated example config packages to correct package names with registry links.
- Fixed CI/CD Integration — replaced placeholder `...` in Full Pipeline example with real working steps.
- Fixed SpecFlow Orchestrator — added clarifying note that the name refers to specification-driven delivery, not the BDD framework.
- Fixed markdown spacing after Mermaid blocks in `first-ai-assisted-pr.md`, `implementation-guide.md`, `mcp.md`, and `agent-skill-selection.md`.
- Fixed GitHub Pages deployment workflow — switched to peaceiris/actions-gh-pages@v4 with explicit permissions.
- Fixed AI Troubleshooting — safer advice for reverting AI changes (check diff first, stash if needed, warn about losing uncommitted work).

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
*Last updated: 2026-06-21 | Version: 1.6*
