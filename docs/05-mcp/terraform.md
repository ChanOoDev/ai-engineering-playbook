# Terraform MCP

A Terraform MCP integration helps AI tools inspect infrastructure-as-code context, provider documentation, modules, plans, and related operational data. It can improve infrastructure review when paired with strict permission boundaries.

## Common Use Cases

- Explain Terraform modules and resource relationships.
- Review plans for replacements, deletions, or risky changes.
- Look up provider resource documentation.
- Diagnose validation, formatting, provider, or state-related errors.
- Generate safer module documentation and usage examples.

## Setup Considerations

Prefer read-only access for most workflows. If a tool can run plans or applies, separate sandbox, non-production, and production permissions clearly. Production apply operations should remain explicitly human-approved.

Document backend configuration, workspace naming, provider versions, and environment conventions so the AI tool can reason about the infrastructure safely.

## Security Guidance

Terraform often contains sensitive values, IAM permissions, network exposure, and environment topology. Avoid exposing state files, secrets, private endpoints, or customer-specific data unless the integration and workflow are approved for that data.

## Validation

A safe validation sequence is:

1. Read Terraform files from a sandbox repository.
2. Run formatting or validation only if allowed.
3. Generate a plan in a non-production environment if credentials permit.
4. Confirm that destructive actions are clearly identified and not applied automatically.

## Example Configuration

A typical Claude Code MCP configuration for Terraform:

```json
{
  "mcpServers": {
    "terraform": {
      "command": "npx",
      "args": ["-y", "@anthropic/terraform-mcp-server"],
      "env": {
        "TF_WORKSPACE": "${TF_WORKSPACE}"
      }
    }
  }
}
```

## Example Prompts

**Reviewing a plan for risks:**

```
Review the Terraform plan output for the staging environment. Identify:
- Any resources being replaced or destroyed
- IAM policy changes that expand permissions
- Security group changes that open new ingress ports
- State movements that require careful ordering
```

**Explaining module relationships:**

```
Explain the module structure in modules/vpc/. Show me how the subnets,
route tables, and NAT gateways are connected, and identify any
dependencies on modules/security/.
```

## Operating Model

Terraform MCP should support review and understanding. It should not become an unattended deployment mechanism. Keep human approval, change windows, and rollback plans in the operational workflow.

## External References

- [Terraform Documentation](https://developer.hashicorp.com/terraform/docs)
- [Terraform Registry](https://registry.terraform.io/)
- [Terraform Plan Command](https://developer.hashicorp.com/terraform/cli/commands/plan)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- [OpenTofu Documentation](https://opentofu.org/docs/)

## Third-Party Repositories

- [hashicorp/terraform](https://github.com/hashicorp/terraform)
- [hashicorp/terraform-provider-aws](https://github.com/hashicorp/terraform-provider-aws)
- [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
- [opentofu/opentofu](https://github.com/opentofu/opentofu)
- [gruntwork-io/terratest](https://github.com/gruntwork-io/terratest)

---
*Last updated: 2026-06-21 | Version: 1.1*
