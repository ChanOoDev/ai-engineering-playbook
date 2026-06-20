# Glossary

This glossary defines the operating terms used throughout the AI Engineering Playbook. If you are new to AI-assisted delivery, start here.

## A

**ADR (Architecture Decision Record)** — A document that captures a significant technical decision, the context that led to it, alternatives considered, and the consequences. ADRs help teams understand why a system was built a certain way.

**Agent** — An AI persona with defined responsibilities, review focus, and collaboration patterns. Agents represent engineering roles (like Backend Developer or Security Auditor) and guide how AI approaches a task. See [Agents](03-agents/backend-developer.md).

**AITMPL (AI Task Templates)** — Reusable prompt templates that capture the intent, inputs, constraints, and expected output for a repeated AI-assisted workflow. AITMPL reduces ambiguity and makes AI usage easier to review. See [AITMPL](02-platform-setup/aitmpl.md).

**Approval Gate** — A required human review point before work can proceed to the next stage. Examples: architecture review before implementation, security review before release, PR review before merge.

## C

**CLAUDE.md** — A special file in a repository that Claude Code reads automatically when it starts a session. It contains project-specific context, conventions, constraints, and guardrails. Think of it as the bridge between governance rules and the AI workflow. See [CLAUDE.md](02-platform-setup/claude-md.md).

## D

**Default-Deny** — A security pattern where all access is blocked unless explicitly granted. Used in authorization design: users cannot perform an action unless a policy specifically allows it.

## G

**Golden Path** — A recommended, well-supported way to accomplish a common engineering task. Platform teams build golden paths so developers don't have to solve the same problems repeatedly. Similar to "paved road."

## H

**Human-in-the-Loop** — A workflow pattern where AI drafts, analyzes, or generates output, but humans decide, review, and approve. The playbook requires human-in-the-loop for all AI-assisted work.

## L

**Least Privilege** — A security principle of granting only the minimum permissions needed for a task. Applied to MCP integrations, IAM roles, API access, and tool permissions.

## M

**MCP (Model Context Protocol)** — A standard way for AI tools to connect with external systems such as repositories, cloud platforms, documentation services, and databases. MCP gives AI agents structured, permissioned access to context and actions. See [MCP Setup](02-platform-setup/mcp.md).

## O

**Orchestrator** — An agent that coordinates multi-agent workflows. Unlike role agents (which represent a single engineering persona), orchestrators route work to other agents and maintain traceability across the delivery lifecycle. The SpecFlow Orchestrator is the playbook's primary orchestrator.

## P

**Paved Road** — Platform engineering term for a pre-built, supported workflow that teams can adopt instead of building from scratch. Similar to "golden path."

**Permission Profile** — The set of actions an MCP integration is allowed to perform. For example, a GitHub MCP integration might have read-only access to repositories but no write access.

## R

**Rollback** — Reverting a change to the previous known-good state. Every deployment should have a documented rollback procedure.

**Runbook** — Step-by-step operational instructions for a procedure such as deployment, incident response, or system recovery. See [Reference Project Implementation Guide](06-reference-projects/implementation-guide.md).

## S

**Scope** — The boundaries of what a task, agent, or change should affect. Narrow scope reduces risk. When asking AI for help, always define what should and should not be changed.

**Skill** — A reusable technical capability that an agent may invoke. Skills represent domain expertise (like .NET Enterprise API or AWS Architect) rather than delivery roles. See [Skills](04-skills/aws-architect.md).

## T

**Traceability** — The ability to follow a change from its origin (requirement or user story) through implementation, testing, review, and deployment. Good traceability means every change has a clear "why" and "who approved it."

## V

**Vertical Slice** — A small, end-to-end implementation that touches all layers of the system (frontend, backend, database, tests). Vertical slices are useful for proving a workflow works before scaling up.

---

*Last updated: 2026-06-21 | Version: 1.1*
