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

## Platform-Specific Setup

### macOS

```bash
# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Git (if not already present)
brew install git

# Install Node.js (for MCP servers)
brew install node

# Configure Git identity
git config --global user.name "Your Name"
git config --global user.email "you@company.com"
git config --global init.defaultBranch main
git config --global pull.rebase true

# Install Claude Code
npm install -g @anthropic-ai/claude-code
claude auth login
```

### Linux (Ubuntu/Debian)

```bash
# Update package manager
sudo apt update

# Install Git
sudo apt install git

# Install Node.js
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs

# Configure Git identity
git config --global user.name "Your Name"
git config --global user.email "you@company.com"
git config --global init.defaultBranch main
git config --global pull.rebase true

# Install Claude Code
npm install -g @anthropic-ai/claude-code
claude auth login
```

### Windows

```powershell
# Install Git (via winget or download from git-scm.com)
winget install Git.Git

# Install Node.js
winget install OpenJS.NodeJS.LTS

# Configure Git identity
git config --global user.name "Your Name"
git config --global user.email "you@company.com"
git config --global init.defaultBranch main
git config --global pull.rebase true
git config --global core.autocrlf true

# Install Claude Code
npm install -g @anthropic-ai/claude-code
claude auth login
```

Use Git Bash or WSL2 for the best experience with AI-assisted tools on Windows.

## Verification Checklist

After setup, verify each tool works:

```bash
# Git
git --version                    # Expected: git version 2.x
git config user.name             # Expected: your name
git config user.email            # Expected: your email

# Node.js (for MCP servers and Claude Code)
node --version                   # Expected: v18+ or v20+
npm --version                    # Expected: 9+ or 10+

# Claude Code
claude --version                 # Expected: version number
claude auth status               # Expected: authenticated

# Repository access
git ls-remote origin             # Expected: list of refs (not an auth error)

# Claude Code (if installed)
claude --version                 # Expected: version number
```

If any command fails, check the error message and refer to the troubleshooting section below.

## Recommended Local Workflow

1. Clone the repository using the approved remote.
2. Install project dependencies using the documented package manager.
3. Confirm that local build and test commands work before making changes.
4. Configure approved MCP servers only when needed for the task.
5. Start AI-assisted work with a clear objective and repository context.
6. Review all file changes before committing.

## Environment Hygiene

Keep local environments predictable. Avoid storing secrets in shell history, prompts, screenshots, or shared transcripts. Prefer environment variables, managed secret stores, and short-lived credentials. Remove unused tokens and rotate credentials according to organizational policy.

```bash
# Check for secrets in shell history (examples)
history | grep -i "api_key\|password\|token\|secret"

# Remove a token from Git config
git config --global --unset credential.helper

# Check environment variables for leaked tokens
env | grep -i "token\|key\|secret"
```

## Personal Configuration

Developers may customize editor settings, aliases, and local prompts, but shared project behavior should be documented in the repository. If a personal setup becomes essential for repeated team work, convert it into team documentation or automation.

## Troubleshooting

When a tool behaves unexpectedly, verify the working directory, branch, active virtual environment, installed dependencies, authentication state, and network access. Capture enough detail for support without exposing secrets.

| Problem | Check |
|---|---|
| Git auth fails | `git config credential.helper`, token expiry, SSH key |
| MCP server won't start | Node.js version, npm cache, environment variables |
| Build fails | Working directory, branch, installed dependencies |
| Claude Code can't read files | Working directory, file permissions, `.gitignore` |
| Network errors | VPN, proxy settings, firewall rules |

## Related Pages

- [Claude Code](claude-code.md) — the primary AI tool to set up
- [CLAUDE.md](claude-md.md) — project instructions for AI
- [MCP Setup](mcp.md) — external integrations
- [Git Daily Usage](git-daily-usage.md) — common Git commands
- [AI Troubleshooting](ai-troubleshooting.md) — when things go wrong
- [Junior Developer Quick Start](junior-developer-quickstart.md) — your safe first path

---
*Last updated: 2026-06-21 | Version: 1.3*