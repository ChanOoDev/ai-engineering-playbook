# Governance

AI engineering governance defines how teams use AI safely, consistently, and productively. It should be lightweight enough to support delivery, but clear enough that teams understand what is approved, what requires review, and what is out of bounds.

## Objectives

- Establish approved AI tools, models, integrations, and usage patterns.
- Define how sensitive data and intellectual property are protected.
- Make accountability clear for AI-assisted work.
- Standardize review, testing, and release expectations.
- Provide a path for teams to propose new capabilities responsibly.

## Approved Use

Teams may use AI for code analysis, implementation assistance, test generation, documentation drafting, refactoring support, architecture exploration, and operational runbook creation when the work remains subject to normal engineering review.

High-impact decisions should not be delegated entirely to AI. Examples include production access approval, security exception approval, incident command decisions, vendor selection, legal interpretation, and final architectural authority.

## Data Handling

Teams should avoid submitting secrets, credentials, private keys, production customer data, regulated data, or confidential business material to tools that are not explicitly approved for that data class.

Repositories should use secret scanning, least-privilege access, dependency controls, and clear data classification guidance. When in doubt, engineers should redact or synthesize sensitive examples before sharing context with an AI system.

## Review Requirements

AI-assisted outputs must be reviewed according to the same standard as human-authored work. Code should pass automated tests, static analysis, security checks, and peer review. Documentation should be checked for accuracy, clarity, and alignment with current systems.

Reviewers should pay special attention to incorrect assumptions, missing edge cases, overbroad permissions, insecure defaults, outdated library usage, and plausible but unsupported technical claims.

## Traceability

Teams should preserve enough context to understand meaningful AI-assisted changes. Pull requests should explain the intent, summarize validation performed, and identify areas that need reviewer attention. For larger changes, design notes or decision records should capture assumptions and trade-offs.

## Control Framework

Enterprise AI engineering requires a small set of controls that can be understood, automated, and audited.

| Control Area | Required Practice | Evidence |
| --- | --- | --- |
| Human-in-the-loop review | All AI-assisted changes require a named accountable owner and normal peer review | Pull request reviewer, approval history, review comments |
| Prompt and template management | Shared prompts, AITMPL templates, skills, and CLAUDE.md files are version controlled | Repository history, template owner, review record |
| Secret handling | Secrets are never pasted into prompts, committed to repositories, or exposed in generated examples | Secret scanning results, CI logs, credential rotation records |
| Compliance requirements | Regulated data and customer data are used only with approved tools and data handling rules | Data classification, tool approval, exception records |
| Audit trail | Material AI-assisted work records intent, changed artifacts, validation, and reviewer decisions | PR description, CI output, release notes, decision records |
| Tool and model approval | New AI tools, models, MCP servers, and external catalogs are reviewed before team adoption | Approved tool catalog, risk review, renewal date |
| Cost and usage management | Token usage, subscription cost, and CI usage are monitored for high-volume workflows | Usage dashboard, budget alerts, quarterly review |

## Approval Gates

Use explicit approval gates when AI assistance touches high-risk areas:

| Gate | Applies To | Required Approval |
| --- | --- | --- |
| Architecture gate | Cross-service design, data ownership, major platform changes | Solution architect or architecture owner |
| Security gate | Authentication, authorization, secrets, encryption, customer data | Security owner or designated security reviewer |
| Infrastructure gate | Terraform, cloud resources, network exposure, production configuration | Platform or DevOps owner |
| Release gate | Production deployments, rollback plans, customer-facing changes | Release owner or service owner |
| Compliance gate | Regulated workflows, retention, audit, legal or contractual obligations | Compliance, legal, or data owner as appropriate |

AI may prepare evidence for a gate, but it may not approve the gate. Gate decisions should be visible in the normal system of record, such as a pull request, ticket, change record, or architecture decision record.

## Governance Cadence

A practical cadence is monthly review of tool usage and adoption feedback, quarterly review of approved tools and data policies, and semiannual review of reference architectures, agent definitions, and platform standards.

---
*Last updated: 2026-06-21 | Version: 1.1*