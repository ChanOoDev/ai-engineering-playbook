# User Level Setup

User-level setup prepares an individual developer environment for AI-assisted engineering. The goal is to provide a consistent, secure baseline without requiring every developer to become an expert in every integration.

## Baseline Requirements

Developers should have:

- Access to approved AI tools and accounts.
- A supported terminal and shell environment.
- Git configured with the correct identity.
- Required language runtimes and package managers.
- Repository access through approved authentication.
- Secret scanning and credential hygiene practices.
- Local documentation build tools when working on docs.

## Recommended Local Workflow

1. Clone the repository using the approved remote.
2. Install project dependencies using the documented package manager.
3. Confirm that local build and test commands work before making changes.
4. Configure approved MCP servers only when needed for the task.
5. Start AI-assisted work with a clear objective and repository context.
6. Review all file changes before committing.

## Environment Hygiene

Keep local environments predictable. Avoid storing secrets in shell history, prompts, screenshots, or shared transcripts. Prefer environment variables, managed secret stores, and short-lived credentials. Remove unused tokens and rotate credentials according to organizational policy.

## Personal Configuration

Developers may customize editor settings, aliases, and local prompts, but shared project behavior should be documented in the repository. If a personal setup becomes essential for repeated team work, convert it into team documentation or automation.

## Troubleshooting

When a tool behaves unexpectedly, verify the working directory, branch, active virtual environment, installed dependencies, authentication state, and network access. Capture enough detail for support without exposing secrets.

---
*Last updated: 2026-06-21 | Version: 1.1*