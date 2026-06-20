# Junior Developer Quick Start

This page is for developers who are new to AI-assisted delivery. It gives you a safe first path, tells you what to avoid, and connects you to the pages you need.

## Your First Week

Follow these steps in order. Each one builds on the last.

### Step 1: Learn the Terms

Read the [Glossary](../glossary.md). The playbook uses terms like agent, skill, MCP, AITMPL, and approval gate in specific ways. Understanding them will make every other page easier to follow.

### Step 2: Understand the Principles

Read the [Introduction](../01-governance/introduction.md). It explains why the playbook exists and the five principles that guide all AI-assisted work:

- Human accountability remains explicit
- Context quality drives output quality
- Security and privacy are design constraints
- AI output is reviewed like any other work
- Automation should be observable

### Step 3: Know the Rules

Read [Governance](../01-governance/governance.md). It defines what AI can be used for, what data you must not share, and how review works. This is not optional — it protects you and the team.

### Step 4: Set Up Your Environment

Follow [Claude Code](claude-code.md) to install the tool, then read [CLAUDE.md](claude-md.md) to understand how project instructions work. Ask your team lead if the repository has a CLAUDE.md file.

### Step 5: Learn the Workflow

Read [First AI-Assisted PR](first-ai-assisted-pr.md). It walks you through a complete low-risk workflow: selecting a task, asking AI for help, validating the output, and opening a PR for review.

### Step 6: Pick the Right Agent

Use the [Agent and Skill Selection Guide](../03-agents/agent-skill-selection.md) to choose the right agent for your task. When in doubt, start with the [Backend Developer](../03-agents/backend-developer.md) or [Frontend Developer](../03-agents/frontend-developer.md) agent.

### Step 7: Do Your First PR

Choose a **documentation-only** or **test-only** task for your first AI-assisted PR. Examples:

- Fix a typo or improve a README
- Add a missing test case for an existing function
- Update an API docstring to match the actual behavior
- Add a code comment explaining a complex block

Do not start with feature code, infrastructure, or anything touching auth or data.

### Step 8: Get Feedback

After your first PR is reviewed, ask your reviewer:

- Was my AI usage appropriate?
- Did I miss anything the AI generated?
- Was my PR description clear enough?
- What should I do differently next time?

### Step 9: Graduate to Code

After your first approved PR, try a small code change:

- A minor bug fix with a clear issue description
- Adding validation to an existing endpoint
- Refactoring a function with existing test coverage

Always run tests before committing. Always review the diff before opening the PR.

## What Not To Use AI For

!!! warning "Read this before your first session"

    These are hard boundaries for junior developers. As you gain experience, some of these may become appropriate with senior guidance. Until then, stay within these limits.

- **Do not** ask AI to change production infrastructure
- **Do not** paste customer data, secrets, or credentials into prompts
- **Do not** approve security findings yourself — ask the Security Auditor
- **Do not** merge generated code you cannot explain to a reviewer
- **Do not** use MCP write access unless explicitly approved by your team
- **Do not** delegate architecture decisions to AI — use it for analysis, not authority
- **Do not** skip tests because the code "looks right"
- **Do not** assume AI output is correct — verify it against the codebase and documentation
- **Do not** use AI to bypass code review or branch protection
- **Do not** commit generated code in large batches — keep diffs small and reviewable

## Your Safe Toolkit

As a junior developer, these are the tools and agents you should start with:

| Tool | When to Use |
|------|-------------|
| [Backend Developer](../03-agents/backend-developer.md) | Server-side implementation, API work, tests |
| [Frontend Developer](../03-agents/frontend-developer.md) | UI components, forms, accessibility |
| [System Analyst](../03-agents/system-analyst.md) | Clarifying requirements before you code |
| [GitHub MCP](../05-mcp/github.md) (read-only) | Looking up issues, PRs, and repo context |
| [Context7 MCP](../05-mcp/context7.md) | Checking current library documentation |

Avoid these until you have more experience or senior guidance:

| Tool | Why to Wait |
|------|-------------|
| [Security Auditor](../03-agents/security-auditor.md) | Needs security context to be useful |
| [DevOps Engineer](../03-agents/devops-engineer.md) | Infrastructure changes have high blast radius |
| [AWS MCP](../05-mcp/aws.md) / [Terraform MCP](../05-mcp/terraform.md) | Cloud access requires careful permission scoping |
| [SpecFlow Orchestrator](../03-agents/specflow-orchestrator.md) | Multi-agent coordination needs delivery experience |

## When To Stop And Ask For Help

Stop and ask a senior teammate when:

- The AI proposes changes you don't understand
- The task touches authentication, authorization, or data access
- Tests fail and you're not sure why
- The diff is much larger than you expected
- You're unsure if a change is safe to merge
- MCP exposes data or permissions you didn't expect
- You accidentally pasted sensitive data into a prompt

Asking for help is not a failure. It is the governance model working correctly.

## Related Pages

- [Glossary](../glossary.md) — definitions of all playbook terms
- [Governance](../01-governance/governance.md) — the rules you must follow
- [First AI-Assisted PR](first-ai-assisted-pr.md) — your first workflow
- [Agent and Skill Selection Guide](../03-agents/agent-skill-selection.md) — which agent to use
- [CLAUDE.md](claude-md.md) — project instructions for AI
- [AI Troubleshooting](ai-troubleshooting.md) — when things go wrong
- [MCP Setup](mcp.md) — external integrations

---

*Last updated: 2026-06-21 | Version: 1.1*
