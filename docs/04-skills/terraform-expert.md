# Terraform Expert

!!! info "Skill Type: **Technical Capability**"
    This skill represents a reusable technical domain competency. Agents invoke it when infrastructure-as-code expertise is needed. The [DevOps Engineer](../03-agents/devops-engineer.md) and [Platform Architect](../03-agents/platform-architect.md) agents commonly use this skill.

The Terraform Expert skill supports infrastructure-as-code design, implementation, review, and troubleshooting. It helps teams write Terraform that is understandable, reusable, secure, and safe to operate.

## When To Use

Use this skill for module design, provider configuration, state management, plan review, refactoring, drift investigation, and infrastructure change validation.

## Capabilities

- Review Terraform for correctness, maintainability, and least privilege.
- Propose module boundaries and variable interfaces.
- Diagnose plan errors, provider issues, and state conflicts.
- Improve naming, tagging, outputs, and environment separation.
- Document safe apply and rollback procedures.

## Inputs

Provide Terraform files, provider versions, plan output, error logs, target environment, state backend details, and the intended infrastructure change.

## Expected Output

A useful Terraform response should include specific file-level recommendations, risk notes, validation commands, and any migration steps required to avoid destructive changes.

## Example Prompt

```
Review the Terraform plan output in plan.txt for this infrastructure change.
Flag:
- Any resource replacements or deletions
- IAM policy changes that expand permissions
- Security group changes that open new ports
- State movements that could cause downtime
- Secrets or sensitive values in variables or outputs

For each issue, explain the risk and suggest a safer alternative.
```

## Review Notes

Always inspect resource replacement, deletion, provider version changes, IAM policies, security group exposure, state movement, and secrets in variables or outputs before applying changes.

## External References

- [Terraform Documentation](https://developer.hashicorp.com/terraform/docs)
- [Terraform Registry](https://registry.terraform.io/)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
- [OpenTofu Documentation](https://opentofu.org/docs/)
- [Terratest Documentation](https://terratest.gruntwork.io/docs/)

## Third-Party Repositories

- [hashicorp/terraform](https://github.com/hashicorp/terraform)
- [hashicorp/terraform-provider-aws](https://github.com/hashicorp/terraform-provider-aws)
- [terraform-aws-modules/terraform-aws-vpc](https://github.com/terraform-aws-modules/terraform-aws-vpc)
- [gruntwork-io/terratest](https://github.com/gruntwork-io/terratest)
- [opentofu/opentofu](https://github.com/opentofu/opentofu)

---
*Last updated: 2026-06-21 | Version: 1.1*
