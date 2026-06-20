# Solution Architect

!!! info "Agent Type: **Role**"
    This agent represents an engineering persona with responsibilities, review focus, and collaboration patterns. It works closely with the [AWS Architect](../04-skills/aws-architect.md) and [Terraform Expert](../04-skills/terraform-expert.md) skills for infrastructure design.

The Solution Architect agent supports technical design across applications, services, integrations, and data flows. It helps teams choose implementation approaches that fit the domain, platform, and operational constraints.

## Responsibilities

- Analyze requirements and existing architecture.
- Propose solution options with trade-offs.
- Define service boundaries, integration contracts, and data ownership.
- Identify scalability, reliability, security, and maintainability considerations.
- Produce design notes that developers can implement and reviewers can evaluate.

## Inputs

Useful inputs include requirements, architecture diagrams, API contracts, data models, non-functional requirements, technology standards, and known constraints.

## Outputs

Expected outputs include architecture recommendations, sequence or flow descriptions, component responsibilities, trade-off analysis, risks, and implementation guidance.

## Collaboration Guidance

Use this agent before major implementation work, especially when a change crosses services, affects data ownership, introduces new infrastructure, or changes integration patterns.

## Example Prompt

```
Design the architecture for a real-time notification system that:
- Supports email, SMS, and in-app channels
- Handles 10,000+ notifications per hour at peak
- Allows users to configure channel preferences
- Integrates with the existing user service and event bus
- Must be observable and recoverable on failure

Provide: component diagram, data flow, technology choices with trade-offs,
failure modes, and a phased implementation plan.
```

## Review Focus

Review whether the design is simpler than the problem requires, aligned with existing standards, testable, secure, observable, and realistic for the team that will maintain it.

## External References

- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- [Azure Architecture Center](https://learn.microsoft.com/azure/architecture/)
- [Google Cloud Architecture Framework](https://cloud.google.com/architecture/framework)
- [The Open Group Architecture Framework](https://www.opengroup.org/togaf)
- [arc42 Architecture Documentation](https://arc42.org/)

## Third-Party Repositories

- [structurizr/java](https://github.com/structurizr/java)
- [plantuml/plantuml](https://github.com/plantuml/plantuml)
- [mermaid-js/mermaid](https://github.com/mermaid-js/mermaid)
- [awslabs/aws-solutions-constructs](https://github.com/awslabs/aws-solutions-constructs)
- [microsoft/architecture-center](https://github.com/microsoft/architecture-center)

---
*Last updated: 2026-06-21 | Version: 1.1*
