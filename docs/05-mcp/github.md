# GitHub MCP

A GitHub MCP integration allows AI tools to inspect repositories, issues, pull requests, reviews, branches, and workflow status through a structured interface. When approved for write actions, it may also create issues, comment on pull requests, or update repository content.

## Common Use Cases

- Summarize issues, pull requests, and review comments.
- Investigate failing checks and workflow logs.
- Prepare pull request descriptions and release notes.
- Connect implementation work with issue acceptance criteria.
- Review repository structure and project conventions.

## Setup Considerations

Use organization-approved authentication. Prefer fine-grained tokens, GitHub App permissions, or managed connectors over broad personal access tokens. Start with read-only access unless the workflow explicitly requires write actions.

Document the repositories, organizations, and scopes available to the integration. Avoid granting access to repositories that are unrelated to the supported workflow.

## Security Guidance

Review permissions carefully. Write access can create comments, issues, branches, or content depending on the connector. Administrative repository actions should remain outside normal AI-assisted workflows unless explicitly approved.

Do not expose secrets from workflow logs, repository settings, or private issue content in generated summaries.

## Validation

A safe validation sequence is:

1. List accessible repositories or read a known repository.
2. Read a harmless issue or pull request.
3. Confirm that the AI tool reports permission errors clearly for unauthorized resources.
4. Test write actions only in a sandbox repository when write access is approved.

## Example Configuration

A typical Claude Code MCP configuration for GitHub:

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_TOKEN}"
      }
    }
  }
}
```

Use a fine-grained personal access token with only the scopes your workflow needs. For read-only workflows, grant only `Contents: Read` and `Metadata: Read`. Store the token in an environment variable, never in the config file.

## Example Prompts

**Summarizing recent PR activity:**

```
Using the GitHub MCP, summarize the open pull requests in this repository.
For each PR, include: title, author, age, review status, and whether CI
is passing. Group by ready-to-merge vs. needs-action.
```

**Investigating a failing workflow:**

```
The CI workflow on PR #142 is failing. Use the GitHub MCP to:
1. Read the workflow run logs for the latest commit
2. Identify which step failed
3. Extract the relevant error output
4. Suggest a fix based on the error
```

**Preparing a PR description:**

```
Using the GitHub MCP, prepare a pull request description for the current
branch. Include:
- Summary of changes (from commit messages)
- Related issues (search for references in commits)
- Testing performed
- Deployment notes if applicable
```

## Operating Model

The GitHub MCP integration should make repository work easier to understand and coordinate. It does not replace maintainer review, branch protection, CI validation, or release approval.

## External References

- [GitHub REST API Documentation](https://docs.github.com/rest)
- [GitHub GraphQL API Documentation](https://docs.github.com/graphql)
- [GitHub Actions Documentation](https://docs.github.com/actions)
- [GitHub Webhooks Documentation](https://docs.github.com/webhooks)
- [GitHub Apps Documentation](https://docs.github.com/apps)

## Third-Party Repositories

- [github/github-mcp-server](https://github.com/github/github-mcp-server)
- [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
- [github/rest-api-description](https://github.com/github/rest-api-description)
- [octokit/octokit.js](https://github.com/octokit/octokit.js)
- [actions/starter-workflows](https://github.com/actions/starter-workflows)

---
*Last updated: 2026-06-21 | Version: 1.1*
