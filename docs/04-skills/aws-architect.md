# AWS Architect

!!! info "Skill Type: **Technical Capability**"
    This skill represents a reusable technical domain competency. Agents invoke it when cloud architecture expertise is needed. The [Solution Architect](../03-agents/solution-architect.md) agent typically drives decisions; this skill provides the AWS-specific knowledge.

The AWS Architect skill supports design and review of cloud solutions on Amazon Web Services. It focuses on secure, reliable, cost-aware, and operable architectures that align with the AWS Well-Architected Framework and organizational standards.

## When To Use

Use this skill for new AWS workloads, migration planning, infrastructure reviews, account strategy, networking decisions, deployment patterns, and production readiness assessments.

## Capabilities

- Evaluate architecture against reliability, security, cost, performance, and operations concerns.
- Recommend service choices based on workload requirements.
- Review IAM, networking, encryption, logging, and backup patterns.
- Draft deployment, monitoring, and disaster recovery guidance.
- Identify risks in infrastructure-as-code templates and cloud designs.

## Inputs

Provide workload goals, expected traffic, compliance needs, data classification, availability requirements, existing AWS accounts, network topology, and infrastructure templates when available.

## Expected Output

A useful AWS architecture response should include the recommended design, key trade-offs, security and reliability considerations, cost drivers, operational requirements, and validation steps.

## Example Prompt

```
Review this AWS architecture for a customer-facing web application:
- ALB in public subnets, EC2 in private subnets
- RDS PostgreSQL in isolated subnets
- S3 for static assets with CloudFront
- SES for transactional email

Evaluate against the Well-Architected Framework. Focus on:
- IAM least privilege and secret management
- Public attack surface and network exposure
- Backup, recovery, and multi-AZ resilience
- Cost optimization opportunities
- Operational readiness (monitoring, alerting, runbooks)
```

## Review Notes

Pay close attention to IAM scope, public exposure, secret storage, region selection, data retention, backup coverage, and monitoring. Avoid service recommendations that solve a theoretical problem while adding unnecessary operational burden.

## External References

- [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- [AWS Architecture Center](https://aws.amazon.com/architecture/)
- [AWS Prescriptive Guidance](https://docs.aws.amazon.com/prescriptive-guidance/)
- [AWS Identity and Access Management Documentation](https://docs.aws.amazon.com/iam/)
- [AWS Reliability Pillar](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/welcome.html)

## Third-Party Repositories

- [aws/aws-cdk](https://github.com/aws/aws-cdk)
- [aws-samples/aws-cdk-examples](https://github.com/aws-samples/aws-cdk-examples)
- [awslabs/aws-solutions-constructs](https://github.com/awslabs/aws-solutions-constructs)
- [aws/aws-cli](https://github.com/aws/aws-cli)
- [awsdocs/aws-doc-sdk-examples](https://github.com/awsdocs/aws-doc-sdk-examples)

---
*Last updated: 2026-06-21 | Version: 1.1*
