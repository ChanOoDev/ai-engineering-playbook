# Claude Code

Claude Code is a command-line coding assistant that can inspect a repository, edit files, run commands, and help complete engineering tasks from inside the development workflow. In this playbook, Claude Code is treated as an AI engineering workstation: powerful, contextual, and subject to the same review standards as any other contributor.

## Recommended Use

Use Claude Code for tasks that benefit from direct repository context:

- Exploring unfamiliar codebases.
- Drafting or refactoring implementation changes.
- Generating tests and documentation.
- Investigating build, lint, or CI failures.
- Preparing pull request summaries and review notes.
- Applying structured engineering workflows from this playbook.

Claude Code is most effective when the user provides a clear goal, relevant constraints, and permission boundaries for file edits, commands, or external services.

## AI IDE Layer

Claude Code is one option in the broader AI IDE layer. Teams may also use tools such as Cursor, OpenCode, Windsurf, and Cline when they are approved for the same data and repository access model.

Evaluate AI IDEs using consistent criteria:

| Criterion | What To Check |
| --- | --- |
| Repository access | Which files can the tool read or modify, and can access be constrained? |
| Command execution | Does the tool require confirmation before running commands or making destructive changes? |
| Context handling | How does the tool load repository instructions, long context, and project memory? |
| Integration support | Does it support MCP, plugins, skills, hooks, or CI workflows? |
| Data protection | Where prompts, code snippets, telemetry, and logs are processed or stored |
| Enterprise controls | SSO, audit logs, policy management, network controls, and admin visibility |

Use the same governance principles regardless of IDE. The tool may change, but review, traceability, and human accountability do not.
## Installation

```bash
# Install via npm (requires Node.js 18+)
npm install -g @anthropic-ai/claude-code

# Verify installation
claude --version

# Authenticate
claude auth login

# Start a session in your project directory
cd /path/to/your/project
claude
```

For detailed setup, see the [Claude Code documentation](https://docs.anthropic.com/en/docs/claude-code).

## Project Configuration

Claude Code reads `CLAUDE.md` files automatically for project-specific context. See [CLAUDE.md](claude-md.md) for how to write project instructions that Claude Code follows.

```bash
# Check if your project has CLAUDE.md
ls CLAUDE.md

# If not, create one (see CLAUDE.md page for templates)
touch CLAUDE.md
```

Claude Code also reads configuration from `.claude/` for agents, skills, MCP servers, and settings. See [Configuration Reference](configuration-reference.md) for the full hierarchy.

## Setup Checklist

1. Install Claude Code: `npm install -g @anthropic-ai/claude-code`
2. Authenticate: `claude auth login`
3. Confirm repository access and local filesystem permissions.
4. Verify `CLAUDE.md` exists in the project root (create one if not — see [CLAUDE.md](claude-md.md)).
5. Configure any required MCP servers (see [MCP Setup](mcp.md)).
6. Validate: `claude -p "Read the README and summarize this project"`
7. Review data handling guidance before pasting sensitive material into a session.

## Working Pattern

A strong Claude Code workflow usually follows this sequence:

1. State the objective and success criteria.
2. Let the assistant inspect the repository before suggesting changes.
3. Ask for a concise plan when the task has meaningful scope or risk.
4. Allow edits only within the intended workspace.
5. Run relevant tests, builds, or linters.
6. Review the resulting diff before committing.

## Guardrails

Do not use Claude Code to bypass code review, approve production changes, expose secrets, or perform destructive actions without explicit confirmation. Treat generated output as a draft until it is validated by tests, reviews, and accountable owners.

**Hard boundaries:**

- Never paste secrets, credentials, or customer data into a session
- Never use Claude Code to approve your own PRs
- Never run destructive commands (`rm -rf`, `DROP TABLE`, `git push --force`) without human confirmation
- Never commit generated code you cannot explain to a reviewer
- Never use MCP write access unless explicitly approved by your team

**Permission modes:**

Claude Code has different permission levels for file edits and command execution. Use the most restrictive mode appropriate for the task:

| Mode | File Edits | Commands | Use When |
|------|-----------|----------|----------|
| Plan mode | Read only | Read only | Exploration, analysis, review |
| Auto-accept edits | Write allowed | Read only | Implementation with manual command control |
| Full auto | Write allowed | Write allowed | Trusted automation (use sparingly) |

Default to plan mode for exploration. Escalate to auto-accept only when you trust the scope. Avoid full auto for production work.

See [Governance](../01-governance/governance.md) for the full review and approval requirements.

## Troubleshooting

If Claude Code produces weak output, improve the context before retrying. Provide file names, relevant logs, acceptance criteria, examples of desired style, and constraints. If it cannot access files or tools, verify the working directory, permission profile, and configured integrations.

---
*Last updated: 2026-06-21 | Version: 1.1*