# AWS EC2 Hosted App

The AWS EC2 Hosted App reference project demonstrates how AI-assisted engineering can support a conventional application deployment on Amazon EC2 while maintaining security, observability, and operational discipline.

## Scenario

A web application runs on EC2 instances behind a load balancer, with managed storage, secure networking, automated deployment, monitoring, and backup procedures. This pattern is useful for teams modernizing existing applications or running workloads that are not yet containerized.

## Architecture Pattern

A typical implementation includes:

- Application Load Balancer for public traffic.
- EC2 instances in private subnets.
- Auto Scaling group or documented capacity plan.
- Security groups with minimal inbound access.
- IAM roles for instance permissions.
- Systems Manager for access and operations.
- CloudWatch logs, metrics, alarms, and dashboards.
- Managed database or external service dependencies.
- Infrastructure-as-code for repeatable provisioning.

## AI-Assisted Workflow

The AWS Architect can review the cloud design. The Terraform Expert can implement or inspect infrastructure-as-code. The DevOps Engineer can define deployment and rollback workflows. The Security Auditor can review IAM, network exposure, encryption, and operational access.

## Documentation Outputs

Useful documentation includes architecture overview, deployment runbook, environment variables, scaling assumptions, monitoring guide, backup and restore procedure, and incident response notes.

## Quality Considerations

Review patching strategy, instance access, public exposure, TLS configuration, secret handling, backup coverage, deployment rollback, and alarm thresholds. EC2 deployments are operationally flexible, but they require clear ownership.

## First Implementation Slice

Start with a non-production deployment slice: provision the network, load balancer, EC2 instance or Auto Scaling group, Systems Manager access, basic logs, and a documented rollback path.

### Sample Backlog

| Item | Outcome |
| --- | --- |
| Define environment and network boundaries | Approved subnet, routing, and exposure model |
| Provision compute and load balancing | Application is reachable through the load balancer |
| Configure instance access | Operations use Systems Manager instead of public SSH |
| Add CloudWatch logging and alarms | Basic operational visibility exists |
| Document deployment and rollback | Team can repeat or undo the deployment |

### Acceptance Criteria

- EC2 instances do not require public SSH access.
- Security groups allow only required inbound and outbound traffic.
- Application health checks pass through the load balancer.
- Logs and basic alarms are available in the target account.
- Deployment and rollback steps are documented and rehearsed in non-production.

### Review Checklist

- Confirm IAM role scope is least privilege.
- Confirm TLS, secret handling, and patching strategy are documented.
- Confirm backup and restore assumptions for stateful dependencies.
- Confirm production deployment requires a separate approval gate.
## Extension Ideas

Teams can extend this project with blue-green deployments, automated AMI builds, centralized logging, vulnerability scanning, autoscaling policies, disaster recovery plans, or gradual migration to containers.

---
*Last updated: 2026-06-21 | Version: 1.1*