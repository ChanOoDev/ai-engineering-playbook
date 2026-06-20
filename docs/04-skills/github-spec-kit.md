# GitHub Spec Kit

!!! info "Skill Type: **Technical Capability**"
    This skill represents a reusable technical domain competency. It is commonly used by the [SpecFlow Orchestrator](../03-agents/specflow-orchestrator.md) agent to convert requirements into GitHub-native work items.

The GitHub Spec Kit skill supports specification-driven delivery using GitHub issues, pull requests, projects, discussions, and repository documentation. It helps teams maintain traceability from idea to implementation.

## When To Use

Use this skill when turning requirements into GitHub-native work items, preparing pull request structure, organizing project boards, or connecting documentation with implementation tasks.

## Capabilities

- Convert requirements into clear issues and acceptance criteria.
- Propose labels, milestones, and project board structure.
- Draft pull request descriptions and review checklists.
- Link decisions, tasks, tests, and documentation updates.
- Summarize implementation progress for stakeholders.

## Inputs

Provide feature briefs, existing issues, repository conventions, release targets, team workflow rules, and any required templates.

## Expected Output

A useful response should include issue breakdowns, acceptance criteria, dependency notes, pull request guidance, and traceability links or placeholders.

## Example Prompt

```
Convert this feature brief into GitHub issues with acceptance criteria:

"We need to add multi-tenant support to the reporting service. Each tenant's
data must be isolated. Reports should be filterable by tenant. Admins can
manage tenant settings."

Break into issues with: title, description, acceptance criteria, labels,
milestone assignment, and dependency notes between issues.
```

## Review Notes

GitHub workflows should make delivery clearer, not busier. Review whether issues are actionable, pull request guidance is specific, and project structure reflects how the team actually works.

## External References

- [GitHub Issues Documentation](https://docs.github.com/issues)
- [GitHub Pull Requests Documentation](https://docs.github.com/pull-requests)
- [GitHub Projects Documentation](https://docs.github.com/issues/planning-and-tracking-with-projects)
- [GitHub Actions Documentation](https://docs.github.com/actions)
- [GitHub Flavored Markdown Spec](https://github.github.com/gfm/)

## Third-Party Repositories

- [github/docs](https://github.com/github/docs)
- [github/rest-api-description](https://github.com/github/rest-api-description)
- [github/github-mcp-server](https://github.com/github/github-mcp-server)
- [actions/starter-workflows](https://github.com/actions/starter-workflows)
- [github/issue-metrics](https://github.com/github/issue-metrics)

---
*Last updated: 2026-06-21 | Version: 1.1*
