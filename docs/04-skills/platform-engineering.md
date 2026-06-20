# Platform Engineering

!!! info "Skill Type: **Technical Capability**"
    This skill represents a reusable technical domain competency. The [Platform Architect](../03-agents/platform-architect.md) agent decides what capabilities the platform needs; this skill helps implement them. The [DevOps Engineer](../03-agents/devops-engineer.md) agent also draws on this skill for operational workflows.

The Platform Engineering skill supports reusable delivery systems, developer experience improvements, service templates, deployment standards, and internal platform capabilities.

## When To Use

Use this skill when a team needs a repeatable path for building, deploying, observing, or operating software. It is also useful when a one-off workflow should become a shared engineering capability.

## Capabilities

- Design paved-road workflows for common engineering tasks.
- Improve CI/CD, environment provisioning, and developer onboarding.
- Define service templates, golden paths, and operational standards.
- Identify automation opportunities that reduce manual coordination.
- Balance standardization with team autonomy.

## Inputs

Provide current pain points, existing workflows, technology constraints, team topology, compliance requirements, support model, and examples of successful or failed delivery patterns.

## Expected Output

A useful platform engineering response should include a capability proposal, ownership model, adoption path, risks, support expectations, and measurable success criteria.

## Example Prompt

```
Design a golden path for new microservice onboarding that includes:
- Repository template with CI/CD, Dockerfile, and Helm chart
- One-command local development setup
- Automated deployment to dev environment on first push
- Observability baseline (logging, metrics, health checks)
- Documentation template for the service's README

Include: ownership model, support expectations, and adoption metrics.
```

## Review Notes

Good platform work reduces cognitive load. Review whether the proposal is maintainable, documented, observable, secure by default, and valuable enough for teams to adopt willingly.

## External References

- [CNCF Platforms Working Group](https://tag-app-delivery.cncf.io/wgs/platforms/)
- [Backstage documentation](https://backstage.io/docs/)
- [DORA Research Program](https://dora.dev/)
- [Internal Developer Platform](https://internaldeveloperplatform.org/)
- [Humanitec Platform Engineering](https://humanitec.com/platform-engineering)

## Third-Party Repositories

- [backstage/backstage](https://github.com/backstage/backstage)
- [crossplane/crossplane](https://github.com/crossplane/crossplane)
- [argoproj/argo-cd](https://github.com/argoproj/argo-cd)
- [fluxcd/flux2](https://github.com/fluxcd/flux2)
- [Humanitec-DemoOrg/reference-architectures](https://github.com/Humanitec-DemoOrg/reference-architectures)

---
*Last updated: 2026-06-21 | Version: 1.1*
