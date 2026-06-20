# Ownership Matrix

Clear ownership prevents AI-assisted delivery from becoming ambiguous. The matrix below identifies who is typically accountable for common responsibilities. Organizations can adapt the roles to match their structure.

| Area | Accountable Role | Supporting Roles | Expected Outcome |
| --- | --- | --- | --- |
| AI usage policy | Engineering leadership | Security, legal, platform engineering | Approved policy and risk boundaries |
| Tool approval | Platform engineering | Security, procurement, architecture | Approved tools and documented access model |
| Data classification | Security | Data owners, engineering teams | Clear guidance for what data can be used |
| Agent definitions | Architecture | Engineering teams, platform engineering | Consistent role descriptions and workflows |
| Skill definitions | Domain owners | Senior engineers, platform engineering | Reusable guidance for specialized work |
| MCP integrations | Platform engineering | Security, tool owners | Secure, documented integrations |
| Code changes | Feature team | Reviewers, architects, QA | Reviewed and tested implementation |
| Infrastructure changes | Platform or service owner | Security, DevOps, architecture | Least-privilege, validated deployment changes |
| Documentation quality | Documentation owner | Engineering teams, product owners | Accurate and maintainable public content |
| Incident response | Operations owner | Engineering, security, platform | Human-led incident handling with auditable support |

## Decision Rights

AI systems may assist with analysis and drafting, but they do not own decisions. Product owners approve scope, engineering owners approve implementation, architects approve cross-system design, security owners approve risk exceptions, and operations owners approve production procedures.

## Review Expectations

Each AI-assisted change should have a named human owner. That owner is responsible for confirming that the output is accurate, secure, tested, and aligned with project standards.

For low-risk documentation edits, a lightweight review may be enough. For production code, infrastructure, authentication, authorization, data handling, or operational workflows, teams should require stronger review and validation.

---
*Last updated: 2026-06-21 | Version: 1.1*