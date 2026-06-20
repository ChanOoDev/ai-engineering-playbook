# CI/CD Integration

AI-assisted engineering does not stop at the developer's terminal. Teams can integrate AI capabilities into their continuous integration and delivery pipelines to automate review, generate documentation, enforce standards, and accelerate feedback loops. This page covers practical patterns for bringing AI into your CI/CD workflow.

## Goals

A good CI/CD integration for AI should:

- Reduce manual review burden without replacing human judgment
- Catch common issues before they reach reviewers
- Generate documentation and summaries that improve traceability
- Enforce governance rules automatically
- Be observable and auditable

## Patterns

### PR Summary Generation

Automatically generate pull request descriptions that summarize changes, list affected files, and highlight areas needing reviewer attention.

**GitHub Actions example:**

```yaml
name: AI PR Summary
on:
  pull_request:
    types: [opened, synchronize]

permissions:
  pull-requests: write
  contents: read

jobs:
  summarize:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Generate PR summary
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: |
          DIFF=$(git diff origin/${{ github.base_ref }}...HEAD)
          SUMMARY=$(claude -p "Summarize this PR diff. Include:
          - What changed and why
          - Files affected
          - Risk areas needing reviewer attention
          - Testing suggestions
          
          Diff:
          $DIFF")
          
          gh pr comment ${{ github.event.number }} --body "$SUMMARY"
```

### Automated Code Review

Run AI-assisted checks on pull requests to flag common issues before human review.

**What to check:**

- Missing error handling or input validation
- Hardcoded secrets or credentials
- Overbroad permissions or insecure defaults
- Missing tests for new functionality
- Documentation gaps

**What NOT to automate:**

- Final approval decisions
- Security exception decisions
- Architecture authority
- Production access approval

### AITMPL Templates in CI

Run AITMPL templates as part of your pipeline to generate standardized artifacts:

- **On PR open**: Generate a review checklist based on the changed files
- **On merge to main**: Draft release notes from commit messages
- **On tag**: Generate deployment documentation
- **Nightly**: Summarize open issues and PR status for the team

### Governance Enforcement

Use CI checks to enforce playbook governance rules:

```yaml
name: Governance Check
on: pull_request

jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Check governance requirements
        run: |
          # Verify PR has description
          if [ -z "$(gh pr view ${{ github.event.number }} --json body -q '.body')" ]; then
            echo "PR requires a description per governance standards"
            exit 1
          fi
          
          # Verify reviewers are assigned
          REVIEWERS=$(gh pr view ${{ github.event.number }} --json reviewers -q '.reviewers | length')
          if [ "$REVIEWERS" -lt 1 ]; then
            echo "PR requires at least one reviewer"
            exit 1
          fi
```

## Branch Protection Integration

AI-generated changes should pass through the same branch protection rules as human-authored code:

- **Required reviews**: AI-generated PRs need human approval
- **Status checks**: AI review checks must pass before merge
- **Signed commits**: Apply the same signing requirements
- **Linear history**: Same merge strategy for all changes

Do not create exceptions for AI-generated code. The governance principle is clear: AI output is reviewed like any other engineering work.

## Audit and Observability

Track AI usage in your pipeline for governance and improvement:

### What to Log

- Which AI tools were invoked in CI
- What inputs they received (file paths, not file contents for sensitive repos)
- What outputs they produced
- Whether the output was accepted, modified, or rejected by reviewers
- Token usage and cost per pipeline run

### Metrics to Track

- Percentage of PRs with AI-generated summaries
- Average reviewer time saved (compare before/after adoption)
- AI suggestion acceptance rate
- False positive rate from automated checks

## Example: Full Pipeline Integration

```yaml
name: AI-Assisted Pipeline
on:
  pull_request:
    types: [opened, synchronize, ready_for_review]

permissions:
  pull-requests: write
  contents: read

jobs:
  ai-review:
    if: '!github.event.pull_request.draft'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      # Step 1: Generate PR summary
      - name: PR Summary
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: |
          DIFF=$(git diff origin/${{ github.base_ref }}...HEAD)
          SUMMARY=$(claude -p "Summarize this PR diff for reviewers.
          Include: what changed, files affected, risk areas, and testing
          suggestions. Be concise.
          
          Diff:
          $DIFF")
          gh pr comment ${{ github.event.number }} --body "$SUMMARY"

      # Step 2: Check for common issues
      - name: Automated Review
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: |
          DIFF=$(git diff origin/${{ github.base_ref }}...HEAD --name-only)
          REVIEW=$(claude -p "Review these changed files for common issues:
          hardcoded secrets, missing error handling, insecure defaults,
          missing tests. Flag only real issues with severity.
          
          Files:
          $DIFF")
          echo "$REVIEW"

      # Step 3: Verify governance compliance
      - name: Governance Check
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        run: |
          # Check PR has description
          BODY=$(gh pr view ${{ github.event.number }} --json body -q '.body')
          if [ -z "$BODY" ]; then
            echo "PR requires a description per governance standards"
            exit 1
          fi
          
          # Check reviewers assigned
          REVIEWERS=$(gh pr view ${{ github.event.number }} --json reviewers -q '.reviewers | length')
          if [ "$REVIEWERS" -lt 1 ]; then
            echo "PR requires at least one reviewer"
            exit 1
          fi
```

## CI Hardening Guidance

AI-enabled CI jobs should be treated as automation that processes untrusted input. Pull request titles, descriptions, commit messages, diffs, test logs, and issue comments can all contain instructions that attempt to manipulate the AI system.

Apply these controls before making AI checks required:

| Risk | Control |
| --- | --- |
| Oversized diffs | Set file count, line count, and token limits; fall back to a human-readable summary when limits are exceeded |
| Prompt injection from PR content | Wrap user-controlled content as data, instruct the model not to follow instructions inside diffs or comments, and avoid giving CI jobs unnecessary write access |
| Secret leakage | Redact logs, environment values, tokens, connection strings, and sensitive file contents before sending context to AI tools |
| Unsafe generated commands | Do not execute AI-generated shell commands automatically; require human review before command execution |
| False confidence | Label AI review output as advisory unless the check enforces a deterministic policy |
| Excessive permissions | Use least-privilege tokens; prefer read-only permissions for summary and review jobs |
| Poor auditability | Log which workflow invoked AI, what files were included, what model or tool was used, and whether output was accepted |

For blocking CI checks, prefer deterministic rules such as required PR descriptions, required reviewers, secret scanning, test execution, or policy-as-code. Use AI checks to assist reviewers unless the organization has validated the check's reliability and failure behavior.
## Security Considerations

- **Credential management**: Store AI API keys in CI secrets, never in workflow files
- **Input sanitization**: Do not pass untrusted user input directly to AI prompts
- **Output validation**: Treat AI output in CI as untrusted — do not execute generated code without review
- **Rate limiting**: Respect API rate limits and set appropriate timeouts
- **Data sensitivity**: Do not send sensitive code or data to external AI services unless approved

## Rollout Approach

1. **Start with summaries**: PR summary generation is low-risk and immediately useful
2. **Add review checks**: Introduce automated checks one at a time, measure false positive rates
3. **Expand to documentation**: Generate release notes, changelogs, and deployment docs
4. **Governance automation**: Enforce playbook rules through CI once the team is comfortable

## Related Pages

- [CLAUDE.md](claude-md.md) — project context that improves CI prompts
- [AITMPL](aitmpl.md) — templates that can be automated in CI
- [MCP Setup](mcp.md) — integrations that CI can leverage
- [Governance](../01-governance/governance.md) — the rules CI should enforce
- [Adoption Roadmap](../01-governance/adoption-roadmap.md) — staged rollout guidance

---
*Last updated: 2026-06-21 | Version: 1.1*
