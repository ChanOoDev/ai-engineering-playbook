# AWS MCP

An AWS MCP integration allows AI tools to inspect or interact with AWS resources through approved credentials and scoped permissions. This can accelerate cloud analysis, troubleshooting, and documentation, but it also introduces meaningful operational risk if not governed carefully.

## Common Use Cases

- Inspect resource configuration and relationships.
- Summarize logs, metrics, alarms, or deployment status.
- Review IAM policies and security group exposure.
- Assist with cost, reliability, and operational analysis.
- Draft runbooks based on actual cloud resources.

## Setup Considerations

Use least-privilege roles, short-lived credentials, and environment-specific access. Prefer read-only roles for analysis workflows. Separate production access from development and test environments.

Document account IDs, regions, role names, and approved commands or tools. Avoid relying on personal administrator credentials for AI-assisted work.

## Security Guidance

AWS integrations can expose sensitive infrastructure details and may perform real actions. Require explicit approval for write-capable tools such as deployment, resource mutation, IAM changes, or data access operations.

Never pass long-lived access keys into prompts or commit them to configuration files. Use approved credential providers and rotation policies.

## Validation

Validate access with a harmless identity or read-only call, then inspect a low-risk resource. Confirm that unauthorized actions fail and that the user can understand which account and role are active.

## Example Configuration

A typical Claude Code MCP configuration for AWS (read-only):

```json
{
  "mcpServers": {
    "aws": {
      "command": "npx",
      "args": ["-y", "@anthropic/aws-mcp-server"],
      "env": {
        "AWS_PROFILE": "readonly-dev",
        "AWS_REGION": "us-east-1"
      }
    }
  }
}
```

Use a read-only IAM role. Never use administrator credentials for AI-assisted work.

## Example Prompts

**Investigating resource configuration:**

```
Using the AWS MCP, inspect the EC2 instances in the staging account.
For each instance, show: ID, state, subnet, security groups, IAM role,
and whether it has a public IP. Flag any that deviate from our standard
(private subnet, no public IP, SSM access only).
```

**Reviewing IAM policies:**

```
Review the IAM policies attached to the lambda-prod-role. Identify any
overbroad permissions (e.g., Resource: *, Action: *). Suggest specific
least-privilege alternatives based on what the Lambda function actually does.
```

## Operating Model

AWS MCP should support informed human operators. Production-impacting changes should remain controlled by established deployment, change management, and incident response practices.

## External References

- [AWS CLI Documentation](https://docs.aws.amazon.com/cli/)
- [Boto3 Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html)
- [AWS CloudFormation Documentation](https://docs.aws.amazon.com/cloudformation/)
- [AWS Identity and Access Management Documentation](https://docs.aws.amazon.com/iam/)
- [Amazon CloudWatch Documentation](https://docs.aws.amazon.com/cloudwatch/)

## Third-Party Repositories

- [aws/aws-cli](https://github.com/aws/aws-cli)
- [boto/boto3](https://github.com/boto/boto3)
- [aws/aws-sdk-js-v3](https://github.com/aws/aws-sdk-js-v3)
- [awslabs/mcp](https://github.com/awslabs/mcp)
- [awsdocs/aws-doc-sdk-examples](https://github.com/awsdocs/aws-doc-sdk-examples)

---
*Last updated: 2026-06-21 | Version: 1.1*
