# Configuration Reference

This page is the single reference for how skills, agents, MCP servers, commands, hooks, settings, and CLAUDE.md are configured at every level. Use it to understand where configuration lives, who owns it, and how precedence works.

## The 4 Levels

Configuration in Claude Code operates at 4 levels. More specific levels override broader ones.

```
┌─────────────────────────────────────────────┐
│  4. Task/Session  (most specific)           │  ← current prompt, template, or flag
│  ┌─────────────────────────────────────────┐│
│  │  3. Directory  (.claude/ in subdir)     ││
│  │  ┌─────────────────────────────────────┐││
│  │  │  2. Project  (.claude/ in root)     │││
│  │  │  ┌─────────────────────────────────┐│││
│  │  │  │  1. User  (~/.claude/)          ││││  ← personal defaults
│  │  │  └─────────────────────────────────┘│││
│  │  └─────────────────────────────────────┘││
│  └─────────────────────────────────────────┘│
└─────────────────────────────────────────────┘

Precedence: Task > Directory > Project > User
```

### Level 1: User

**Location:** `~/.claude/`

**Scope:** You personally, across all projects.

**Who manages:** You (the individual developer).

**Purpose:** Personal preferences, default agents, personal MCP connections, editor settings.

```
~/.claude/
├── CLAUDE.md              # Personal preferences and defaults
├── agents/                # Personal agents
├── skills/                # Personal skills
├── mcps/                  # Personal MCP connections
├── commands/              # Personal commands
├── hooks/                 # Personal hooks
├── settings/              # Personal settings
└── config.json            # Personal configuration
```

**Example CLAUDE.md:**
```markdown
# My Preferences
- Prefer concise responses with code examples
- Always show the diff before committing
- Use conventional commit messages
```

### Level 2: Project

**Location:** `<repo-root>/.claude/` and `<repo-root>/CLAUDE.md`

**Scope:** Everyone working on this repository.

**Who manages:** The team (committed to repo, reviewed like code).

**Purpose:** Project conventions, approved agents, team skills, project MCP servers, CI/CD hooks.

```
project-root/
├── CLAUDE.md                  # Project conventions and guardrails
└── .claude/
    ├── agents/                # Project-approved agents
    ├── skills/                # Project-specific skills
    ├── mcps/                  # Project MCP server configs
    ├── commands/              # Project commands
    ├── hooks/                 # Project hooks (pre-commit, etc.)
    ├── settings/              # Project settings
    └── config.json            # Project configuration
```

**Example CLAUDE.md:**
```markdown
# ACME Order Service
Stack: .NET 8, EF Core, PostgreSQL, deployed on AWS ECS.
Run: dotnet test --filter "Category=Integration" before committing.
All endpoints require [Authorize] unless explicitly [AllowAnonymous].
```

### Level 3: Directory

**Location:** `<subdirectory>/.claude/` and `<subdirectory>/CLAUDE.md`

**Scope:** Only when working in that subdirectory.

**Who manages:** The team or subteam owning that directory.

**Purpose:** Directory-specific conventions, agents for that layer, skills for that domain.

```
project-root/
├── CLAUDE.md                      # Project-level (broader)
└── src/
    ├── api/
    │   ├── CLAUDE.md              # API-specific conventions
    │   └── .claude/
    │       ├── agents/            # Agents for API work
    │       └── skills/            # Skills for API work
    └── ui/
        ├── CLAUDE.md              # UI-specific conventions
        └── .claude/
            ├── agents/            # Agents for UI work
            └── skills/            # Skills for UI work
```

**Example `src/api/CLAUDE.md`:**
```markdown
# API Layer
- Use Minimal APIs with MediatR
- All validation via FluentValidation
- Run: dotnet test --filter "Category=Integration"
```

**Example `src/ui/CLAUDE.md`:**
```markdown
# UI Layer
- React 18 with TypeScript
- Components in src/components/ui/
- Run: npm run test:components
```

### Level 4: Task/Session

**Location:** Not stored in files — passed at invocation time.

**Scope:** Only the current task or session.

**Who manages:** The individual developer (ephemeral, not persisted).

**Purpose:** One-off instructions, AITMPL templates, CLI flags, inline prompts.

**Examples:**
- AITMPL template: "Review this PR for security issues"
- Inline prompt: "Fix the bug in src/orders/create.ts"
- CLI flag: `claude --model claude-sonnet-4-6`
- Session instruction: "Use the Security Auditor agent for this review"

## Component Reference

### CLAUDE.md

| Level | Path | Purpose |
|-------|------|---------|
| User | `~/.claude/CLAUDE.md` | Personal preferences across all projects |
| Project | `<repo>/CLAUDE.md` | Project conventions, commands, guardrails |
| Directory | `<subdir>/CLAUDE.md` | Directory-specific conventions |
| Task | Inline in prompt | One-off instructions for current task |

**Precedence:** All applicable CLAUDE.md files are loaded. More specific ones override broader ones.

**Documentation:** [CLAUDE.md](claude-md.md)

### Agents

| Level | Path | Purpose |
|-------|------|---------|
| User | `~/.claude/agents/` | Personal agents you use across projects |
| Project | `<repo>/.claude/agents/` | Team-approved agents for this project |
| Directory | `<subdir>/.claude/agents/` | Agents specific to this layer/domain |
| Task | Inline prompt instruction | "Use the Backend Developer agent" |

**Install command:**
```bash
# Project-level (default)
npx claude-code-templates@latest --agent development-team/frontend-developer

# User-level
npx claude-code-templates@latest --agent development-team/frontend-developer --directory ~/.claude
```

**Documentation:** [Agents](../03-agents/backend-developer.md), [AITMPL Installation](aitmpl-installation.md)

### Skills

| Level | Path | Purpose |
|-------|------|---------|
| User | `~/.claude/skills/` | Personal skills you use across projects |
| Project | `<repo>/.claude/skills/` | Team-approved skills for this project |
| Directory | `<subdir>/.claude/skills/` | Skills specific to this layer/domain |
| Task | Inline prompt instruction | "Use the .NET Enterprise API skill" |

**Install command:**
```bash
# Project-level (default)
npx claude-code-templates@latest --skill pdf-processing

# User-level
npx claude-code-templates@latest --skill pdf-processing --directory ~/.claude
```

**Documentation:** [Skills](../04-skills/aws-architect.md), [AITMPL Installation](aitmpl-installation.md)

### MCP Servers

| Level | Path | Purpose |
|-------|------|---------|
| User | `~/.claude/mcps/` | Personal MCP connections (your GitHub token, etc.) |
| Project | `<repo>/.claude/mcps/` | Project-approved MCP servers |
| Directory | `<subdir>/.claude/mcps/` | MCP servers for specific subsystems |
| Task | CLI flag or inline prompt | Temporary MCP usage for current task |

**Precedence:** User-level MCP cannot expand beyond project or organization policy. If a user-level config grants broader access, the narrower access applies.

**Documentation:** [MCP Setup](mcp.md)

### Commands

| Level | Path | Purpose |
|-------|------|---------|
| User | `~/.claude/commands/` | Personal slash commands |
| Project | `<repo>/.claude/commands/` | Team slash commands (e.g., `/test`, `/review`) |
| Directory | `<subdir>/.claude/commands/` | Directory-specific commands |
| Task | N/A | Commands are invoked, not configured per-task |

### Hooks

| Level | Path | Purpose |
|-------|------|---------|
| User | `~/.claude/hooks/` | Personal hooks (e.g., format on save) |
| Project | `<repo>/.claude/hooks/` | Project hooks (e.g., pre-commit lint, CI triggers) |
| Directory | `<subdir>/.claude/hooks/` | Directory-specific hooks |
| Task | N/A | Hooks are event-driven, not per-task |

### Settings

| Level | Path | Purpose |
|-------|------|---------|
| User | `~/.claude/settings/` | Personal tool settings |
| Project | `<repo>/.claude/settings/` | Project tool settings |
| Directory | `<subdir>/.claude/settings/` | Directory-specific settings |
| Task | CLI flags | Temporary overrides for current session |

### config.json

| Level | Path | Purpose |
|-------|------|---------|
| User | `~/.claude/config.json` | Personal configuration defaults |
| Project | `<repo>/.claude/config.json` | Project configuration |
| Directory | `<subdir>/.claude/config.json` | Directory-specific configuration |

## Precedence Rules

When configuration conflicts exist, more specific levels win:

| Conflict | Resolution |
|----------|------------|
| User says "verbose" / Project says "concise" | Project wins |
| Project says "use Agent A" / Directory says "use Agent B" | Directory wins |
| Directory says "run test X" / Task prompt says "run test Y" | Task wins |
| User MCP has write access / Project allows read-only | Project wins (narrower access) |
| Organization policy forbids action / Any level allows it | Organization wins (highest authority) |

**Important:** Organization security policy always overrides all 4 levels. No configuration level can grant access that organization policy forbids.

## Decision Matrix: Where to Put Configuration

| What | Where | Why |
|------|-------|-----|
| "I prefer concise responses" | User CLAUDE.md | Personal preference, all projects |
| "This project uses .NET 8" | Project CLAUDE.md | Project-specific, whole team needs it |
| "In src/api/, use MediatR" | Directory CLAUDE.md | Only applies to that layer |
| "Review this PR for security" | Task prompt | One-off, current task only |
| GitHub MCP connection | User or Project MCP | Depends on whether it's personal or team |
| Security Auditor agent | Project agents | Team needs it, commit to repo |
| My personal lint commands | User commands | Only I use them |
| Pre-commit test hook | Project hooks | Whole team should run it |

## Quick Setup Checklist

### For Individual Developers

- [ ] Set up `~/.claude/CLAUDE.md` with your preferences
- [ ] Install personal MCP servers you use across projects
- [ ] Configure personal commands and aliases
- [ ] Verify project CLAUDE.md exists before starting work

### For Teams

- [ ] Create `CLAUDE.md` at repo root with project conventions
- [ ] Add approved agents to `.claude/agents/`
- [ ] Add approved skills to `.claude/skills/`
- [ ] Configure project MCP servers in `.claude/mcps/`
- [ ] Add team commands (e.g., `/test`, `/review`) to `.claude/commands/`
- [ ] Add pre-commit and CI hooks to `.claude/hooks/`
- [ ] Document which components are approved and which require review

### For Platform Teams

- [ ] Publish organization-level approved MCP catalog
- [ ] Define security policy that overrides all configuration levels
- [ ] Provide starter CLAUDE.md templates for common project types
- [ ] Create AITMPL templates for recurring workflows
- [ ] Document the configuration hierarchy in your onboarding guide

## Related Pages

- [CLAUDE.md](claude-md.md) — how to write project instructions
- [MCP Setup](mcp.md) — MCP configuration and precedence
- [AITMPL](aitmpl.md) — task templates
- [AITMPL Installation](aitmpl-installation.md) — installing agents, skills, and MCPs
- [User Level Setup](user-level-setup.md) — developer environment setup
- [Junior Developer Quick Start](junior-developer-quickstart.md) — safe first path
- [Glossary](../glossary.md) — definitions of all terms

---

*Last updated: 2026-06-21 | Version: 1.3*
