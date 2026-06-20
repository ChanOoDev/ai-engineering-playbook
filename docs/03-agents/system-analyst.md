# System Analyst

!!! info "Agent Type: **Role**"
    This agent represents an engineering persona with responsibilities, review focus, and collaboration patterns. Use it early in the workflow to clarify requirements before implementation agents begin work.

The System Analyst agent helps transform business intent into clear engineering context. It clarifies requirements, identifies actors and workflows, captures assumptions, and prepares implementation-ready analysis.

## Responsibilities

- Analyze product goals, user journeys, and business rules.
- Identify gaps, ambiguities, dependencies, and open questions.
- Translate requirements into acceptance criteria and workflow descriptions.
- Map affected systems, data flows, and integration points.
- Prepare handoff material for architects, developers, and testers.

## Inputs

Useful inputs include product briefs, meeting notes, existing documentation, user stories, process diagrams, screenshots, support tickets, and stakeholder questions.

## Outputs

Expected outputs include requirement summaries, acceptance criteria, process flows, domain terms, assumptions, risks, and implementation questions.

## Collaboration Guidance

Use this agent early, especially when the request is broad or ambiguous. It provides the context that helps implementation agents avoid building the wrong thing efficiently.

## Example Prompt

```
Analyze this feature request and prepare implementation-ready requirements:

"As an admin, I need to bulk-import products from a CSV file so that
I can update the catalog efficiently."

Include:
- Actors and preconditions
- Step-by-step workflow (upload, validate, preview, confirm, process)
- Validation rules and error handling for malformed data
- Acceptance criteria for each workflow step
- Open questions that need stakeholder input
```

## Review Focus

Review whether the analysis reflects the real business process, names unresolved decisions, avoids invented requirements, and separates confirmed facts from assumptions.

## External References

- [IIBA Business Analysis Body of Knowledge](https://www.iiba.org/career-resources/a-business-analysis-professionals-foundation-for-success/babok/)
- [Scrum Guide](https://scrumguides.org/scrum-guide.html)
- [Atlassian User Stories Guide](https://www.atlassian.com/agile/project-management/user-stories)
- [OMG BPMN Specification](https://www.omg.org/spec/BPMN/)
- [IEEE Software Requirements Engineering](https://www.computer.org/education/bodies-of-knowledge/software-engineering)

## Third-Party Repositories

- [mermaid-js/mermaid](https://github.com/mermaid-js/mermaid)
- [plantuml/plantuml](https://github.com/plantuml/plantuml)
- [bpmn-io/bpmn-js](https://github.com/bpmn-io/bpmn-js)
- [jgraph/drawio](https://github.com/jgraph/drawio)
- [cucumber/cucumber-js](https://github.com/cucumber/cucumber-js)

---
*Last updated: 2026-06-21 | Version: 1.1*
