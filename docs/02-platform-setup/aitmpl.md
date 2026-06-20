# AITMPL

AITMPL is a pattern for reusable AI task templates. A template captures the intent, inputs, constraints, output format, and validation expectations for a repeated AI-assisted workflow. Templates reduce ambiguity and make AI usage easier to review, improve, and scale.

## Why Templates Matter

Ad hoc prompts are useful for exploration, but teams need repeatability for delivery work. Templates help teams standardize tasks such as code reviews, architecture analysis, test planning, documentation generation, security assessment, and release note drafting.

A good template makes the desired behavior explicit without over-prescribing implementation details.

## Template Structure

A practical AITMPL template includes:

- **Purpose** - what the template is for.
- **Inputs** - files, specifications, links, logs, or examples the user should provide.
- **Context** - system boundaries, domain assumptions, and relevant standards.
- **Instructions** - the task the AI should perform.
- **Constraints** - security, style, technology, or scope limits.
- **Output format** - the expected structure of the response or artifact.
- **Validation** - checks the user or AI should perform before accepting the result.

## Example Uses

- Generate an implementation plan from a product requirement.
- Review an infrastructure change for least privilege and operational risk.
- Draft API documentation from OpenAPI definitions and code examples.
- Produce a migration checklist from an architecture decision record.
- Summarize a pull request for reviewers.

## Authoring Guidance

Write templates in plain language. Keep them focused on one workflow. Include examples only when they clarify the expected output. Avoid embedding secrets or environment-specific values. Revisit templates after real use and incorporate lessons from review comments, defects, and user feedback.

## Governance

Templates that affect production systems, security review, compliance, or customer-facing documentation should have an accountable owner. Changes to those templates should be reviewed like other engineering standards.

## Installation

Some agents and skills referenced by this playbook can be installed from AITMPL. See the [AITMPL Installation Guide](aitmpl-installation.md) for prerequisites, direct installation commands, batch installation, dry runs, verification, and governance checks.

---
*Last updated: 2026-06-21 | Version: 1.1*
