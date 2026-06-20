# Adoption Roadmap

AI engineering adoption should progress through deliberate stages. The roadmap below helps teams move from experimentation to reliable, governed delivery.

## Stage 1: Foundation

Establish basic readiness before broad rollout. Define approved tools, publish data handling guidance, identify pilot teams, create starter documentation, and agree on review expectations.

Success looks like a small group of teams using AI safely with clear boundaries and visible feedback loops.

### Metrics

| Metric | Target | How to Measure |
|---|---| --- |
| Tool approval coverage | 100% of approved tools documented | Checklist in governance doc |
| Data handling guidance published | Yes/No | Document review status |
| Pilot teams identified | 2-3 teams | Team roster |
| Review expectations agreed | Yes/No | Signed-off governance doc |
| Developer awareness | >80% of pilot team | Survey or kickoff attendance |

## Stage 2: Guided Pilots

Run focused pilots that produce measurable learning. Select use cases such as documentation generation, test creation, codebase analysis, or backlog refinement. Track cycle time, review quality, rework, and developer satisfaction.

Success looks like evidence that AI improves specific workflows without reducing quality or control.

### Metrics

| Metric | Target | How to Measure |
|---|---| --- |
| Cycle time (selected workflows) | 15-30% improvement | PR creation to merge time |
| Review quality | No increase in post-merge defects | Defect tracking per sprint |
| AI-assisted PR ratio | >30% of pilot team PRs include AI output | PR labels or metadata |
| Developer satisfaction | >7/10 | Survey after 4 weeks |
| Rework rate | <10% of AI-generated output rejected | Reviewer feedback tracking |
| Security incidents from AI | Zero | Incident reports |

## Stage 3: Team Enablement

Scale the practices across more teams. Provide onboarding material, standardize agent workflows, create a support channel, add CI checks, and maintain a catalog of approved MCP integrations.

Success looks like teams adopting shared patterns rather than inventing isolated approaches.

### Metrics

| Metric | Target | How to Measure |
|---|---|---|
| Teams onboarded | >50% of engineering teams | Team adoption tracker |
| Onboarding time | <1 day from setup to first AI-assisted PR | Onboarding completion tracking |
| Shared workflow adoption | >70% of teams using standard templates | Template usage analytics |
| CI integration coverage | AI checks active on >50% of repos | CI configuration audit |
| MCP integrations cataloged | All approved integrations documented | Catalog completeness |
| Support channel response time | <4 hours for blocking issues | Support ticket tracking |

## Stage 4: Integrated Delivery

Integrate AI into everyday engineering workflows such as code review preparation, design exploration, test planning, release notes, and operational documentation.

Success looks like AI becoming a normal part of delivery while human review and ownership remain clear.

### Metrics

| Metric | Target | How to Measure |
|---|---|--- |
| AI-assisted PR ratio | >60% of all PRs | PR labels or CI metadata |
| Review turnaround time | 20-40% improvement | PR review start to approval time |
| Documentation coverage | >80% of APIs and runbooks current | Doc freshness audit |
| Release note automation | Automated for all releases | Release pipeline tracking |
| Test coverage trend | Stable or improving | Coverage reports per sprint |
| Governance compliance | >95% of changes pass governance checks | CI governance check pass rate |

## Stage 5: Continuous Improvement

Treat AI engineering as a managed capability. Retire ineffective workflows, promote successful patterns into templates, update governance, and invest in higher-quality context.

Success looks like a learning system: better context produces better output, better output improves delivery, and delivery feedback improves the playbook.

### Metrics

| Metric | Target | How to Measure |
|---|---|--- |
| Workflow effectiveness score | Regular review and retirement of underperforming workflows | Quarterly workflow audit |
| Template library growth | Net positive addition of validated templates | Template catalog tracking |
| Playbook freshness | All pages reviewed at least quarterly | Last-reviewed dates |
| Context quality score | CLAUDE.md coverage across all active repos | Repo audit |
| Cost per AI-assisted PR | Stable or decreasing | API usage / PR count |
| Team autonomy index | Teams self-serve without platform team involvement >80% of the time | Support ticket analysis |

### Advancement Criteria

Use these thresholds to decide when to move between stages:

| Transition | Criteria |
|---|---|
| Stage 1 → 2 | Governance approved, pilot teams identified, tools documented |
| Stage 2 → 3 | Pilot metrics meet targets for 4+ weeks, no security incidents |
| Stage 3 → 4 | >50% of teams onboarded, shared workflows adopted, CI checks active |
| Stage 4 → 5 | >60% AI-assisted PR ratio, governance compliance >95%, stable metrics for 8+ weeks |
| Ongoing | Quarterly review of all metrics, playbook updates, and workflow effectiveness |

---
*Last updated: 2026-06-21 | Version: 1.1*