# AI Troubleshooting

This page covers common problems junior developers encounter when using AI-assisted workflows, and how to fix them.

## AI Changed Too Many Files

**What happened:** You asked AI for help and it modified files unrelated to your task.

**Why it happens:** The prompt was too broad, didn't specify scope, or the AI inferred changes it thought were helpful.

**How to fix:**

1. First, review what changed: `git diff` or `git diff --stat`
2. If you have other uncommitted work you want to keep, stash it: `git stash`
3. Revert only the AI changes: `git restore .` (discards all uncommitted changes)
4. If you stashed work, restore it: `git stash pop`
5. Add explicit scope to your prompt: "Only modify files in src/Services/Orders/"
6. Re-run with the narrower prompt
7. Review the diff before committing — every file should be explainable

**Warning:** `git restore .` discards ALL uncommitted changes, not just AI-generated ones. Always check `git status` and `git diff` first to make sure you won't lose work you care about.

**Prevention:** Always tell AI what NOT to change. Example: "Do not modify test files, configuration, or unrelated services."

## AI Ignored Project Conventions

**What happened:** The AI generated code that doesn't match your project's patterns, naming, or structure.

**Why it happens:** The repository doesn't have a `CLAUDE.md` file, or it's incomplete. The AI has no way to know your conventions unless you document them.

**How to fix:**

1. Check if `CLAUDE.md` exists in the repository root
2. If it doesn't, ask your team lead about creating one
3. If it does, check whether the convention you need is documented
4. For now, manually adjust the generated code to match conventions
5. Suggest adding the missing convention to `CLAUDE.md`

**Prevention:** See [CLAUDE.md](claude-md.md) for guidance on documenting project conventions.

## Tests Fail After AI Changes

**What happened:** You accepted AI-generated code and now tests are failing.

**Why it happens:** The AI introduced a regression, broke an assumption, or changed behavior without realizing existing tests depended on it.

**How to fix:**

1. Read the failing test output carefully — what assertion failed?
2. Compare the AI's changes to the test expectations
3. If the AI's code is wrong, fix it or revert and try again
4. If the test is wrong (the AI improved the behavior), update the test with a clear explanation
5. Run tests again to confirm

**Prevention:** Always run tests before committing. If you don't know the test command, ask your team or check the project README.

## I Don't Understand the Generated Code

**What happened:** AI wrote code that looks correct but you can't explain what it does or why.

**Why it happens:** The AI used a pattern, library, or approach you haven't seen before.

**How to fix:**

1. Do not merge code you cannot explain
2. Ask the AI to explain the code: "Explain what this function does, line by line"
3. If the explanation makes sense, add a comment to the code explaining the approach
4. If you're still unsure, ask a senior teammate to review with you
5. Learn the pattern for next time

**Prevention:** Start with simple tasks. Build up to complex ones as you gain experience.

## MCP Access Failed

**What happened:** The AI tool can't connect to GitHub, AWS, or another external system.

**Why it happens:** The token is expired, the permissions are wrong, the network is blocked, or the MCP server isn't configured.

**How to fix:**

1. Check if your MCP token is still valid (GitHub tokens expire)
2. Verify the token has the right scopes (read-only for most workflows)
3. Check if you're on the right network (VPN, corporate firewall)
4. Try a simple read-only operation first: "List my recent PRs"
5. Ask your team lead if the MCP integration is approved for your project

**Prevention:** See [MCP Setup](mcp.md) for configuration guidance. Always start with read-only access.

## Reviewer Rejected AI-Generated Code

**What happened:** Your reviewer found issues in the code you submitted.

**Why it happens:** The AI generated code with bugs, security issues, style violations, or missing tests. You accepted it without thorough review.

**How to fix:**

1. Read every review comment carefully
2. Understand WHY the reviewer flagged each issue — don't just fix blindly
3. Fix the issues manually or with AI help, but verify each fix
4. Re-request review
5. Note the patterns that were wrong so you can catch them next time

**Prevention:** Review every line of AI-generated code as if a junior developer wrote it. Because one did — the AI is your junior pair programmer, not your senior reviewer.

## I Accidentally Pasted Sensitive Data

**What happened:** You pasted customer data, secrets, credentials, or other sensitive information into an AI prompt.

**Why it happens:** It's easy to copy-paste context without thinking about what's in it.

**How to fix:**

1. Stop immediately — do not continue the session
2. If you pasted a secret or credential: **rotate it immediately** (generate a new one, invalidate the old one)
3. Inform your team lead or security contact
4. Do not try to "undo" the paste — the data may already be in logs
5. Document what happened and what was rotated

**Prevention:**

- Never paste real customer data into prompts — use synthetic or redacted examples
- Never paste API keys, passwords, tokens, or connection strings
- Before pasting, ask: "Would I put this in a public Slack channel?"
- If you need to reference sensitive data, describe it without the actual values

## AI Output Looks Plausible But Is Wrong

**What happened:** The AI generated code, documentation, or analysis that looks reasonable but is factually incorrect.

**Why it happens:** AI can "hallucinate" — generate confident-sounding output that doesn't match reality. This is especially common with library APIs, version-specific behavior, and infrastructure details.

**How to fix:**

1. Verify the output against the actual codebase, documentation, or tests
2. Use Context7 MCP to check current library documentation
3. Run the code — does it actually work?
4. If the output is wrong, tell the AI what's actually true and ask it to try again
5. Don't trust "it looks right" — trust "it works and I understand why"

**Prevention:** Always verify AI output. Use tests, documentation, and your own judgment as ground truth.

## Build Fails After AI Changes

**What happened:** The project won't build or deploy after accepting AI-generated changes.

**Why it happens:** Missing dependency, syntax error, configuration change, or incompatible version.

**How to fix:**

1. Read the build error output carefully — what's the first error?
2. Fix that error — later errors are often cascading
3. If the error is in AI-generated code, revert that specific change and try again
4. If the error is a missing dependency, check if the AI added an import for a package not in your project
5. Run the build locally before pushing

**Prevention:** Run the build command before committing. If you don't know it, check the project README or ask your team.

## Related Pages

- [Junior Developer Quick Start](junior-developer-quickstart.md) — your safe first path
- [First AI-Assisted PR](first-ai-assisted-pr.md) — your first workflow
- [CLAUDE.md](claude-md.md) — project instructions for AI
- [MCP Setup](mcp.md) — external integration configuration
- [Governance](../01-governance/governance.md) — the rules that protect you

---

*Last updated: 2026-06-21 | Version: 1.1*
