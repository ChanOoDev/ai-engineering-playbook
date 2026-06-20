# SpecFlow Orchestrator

!!! warning "Agent Type: **Orchestrator**"
    This agent coordinates multi-agent workflows. It is not a single engineering role — it routes work to other agents and maintains traceability across the delivery lifecycle. Use it when a feature needs analysis, design, implementation, testing, and documentation in sequence.

The SpecFlow Orchestrator agent coordinates specification-driven delivery. It helps move from product intent to analysis, architecture, implementation, tests, documentation, and release readiness through an ordered workflow.

## Responsibilities

- Break broad requests into structured delivery stages.
- Route work to the right specialist agents or skills.
- Maintain traceability from requirement to implementation and validation.
- Identify missing context before implementation begins.
- Summarize progress, decisions, risks, and remaining work.

## Inputs

Useful inputs include product requirements, epics, feature briefs, acceptance criteria, architecture constraints, repository context, and delivery deadlines.

## Outputs

Expected outputs include delivery plans, task breakdowns, agent handoff notes, validation checklists, documentation outlines, and release readiness summaries.

## Collaboration Guidance

Use this agent for multi-step work that requires coordination. It is especially useful when a feature needs analysis, design, backend work, frontend work, tests, infrastructure, and documentation.

## Example Prompt

```
Coordinate the delivery of this feature: "Customer self-service password
reset with email verification."

Break this into stages:
1. System Analyst: clarify requirements and edge cases
2. Solution Architect: design the flow and security model
3. Backend Developer: implement the API and email integration
4. Frontend Developer: build the reset flow UI
5. Security Auditor: review before release
6. DevOps Engineer: add monitoring and alerting

For each stage, define the input needed, expected output, and handoff
criteria. Flag dependencies and risks.
```

## Review Focus

Review whether the orchestration keeps the work scoped, names dependencies clearly, and preserves accountability. The orchestrator should coordinate work, not hide uncertainty.

## External References

- [Cucumber Documentation](https://cucumber.io/docs/cucumber/)
- [Gherkin Reference](https://cucumber.io/docs/gherkin/reference/)
- [Reqnroll Documentation](https://docs.reqnroll.net/)
- [GitHub Projects Documentation](https://docs.github.com/issues/planning-and-tracking-with-projects)
- [Agile Alliance Acceptance Criteria](https://www.agilealliance.org/glossary/acceptance-criteria/)

## Third-Party Repositories

- [cucumber/cucumber-js](https://github.com/cucumber/cucumber-js)
- [cucumber/gherkin](https://github.com/cucumber/gherkin)
- [reqnroll/Reqnroll](https://github.com/reqnroll/Reqnroll)
- [SpecFlowOSS/SpecFlow](https://github.com/SpecFlowOSS/SpecFlow)
- [microsoft/playwright](https://github.com/microsoft/playwright)

---
*Last updated: 2026-06-21 | Version: 1.1*
