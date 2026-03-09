# OctoAcme — Risk Management & Communication

## Purpose
Explain how to identify, manage, and communicate risks and dependencies.

## Risk Register
Maintain a simple table with:
- ID
- Description
- Impact (High/Med/Low)
- Likelihood (High/Med/Low)
- Owner
- Mitigation plan
- Status

## Risk Lifecycle
- Identify: during planning and ongoing execution
- Assess: estimate impact and likelihood
- Mitigate: reduced via actions, contingency plans
- Monitor: review at weekly syncs and update status

## Stakeholder Communication
- Identify stakeholder groups and communication needs (e.g., engineering, sales, support)
- Provide regular updates (weekly or milestone-based)
- Use a single source of truth (project README or release doc) for status

## Communication Templates
Weekly Status Template:
- Progress this week:
- Next steps:
- Risks & blockers:
- Ask / decisions needed:

Incident Communication
- Triage summary
- Actions being taken
- Expected timeline
- Post-incident blameless retrospective scheduled

## Escalation Paths
- Team-level -> PM -> Product Lead -> Sponsor
- For security incidents, follow the security incident runbook and notify Security on-call

## Roles Involved
- **Project Manager** — maintains risk register; escalates to Product Lead and Sponsor
- **Stakeholder Communication Lead** — owns regular stakeholder updates and incident communications
- **Security Champion** — owns security risk entries in the register; leads security incident response
- **Product Manager** — consulted on risk trade-offs and priority decisions

## Related Templates
- [Stakeholder Update Template](./octoacme-stakeholder-update-template.md) — weekly status, incident, and milestone communication formats
- [Roles & Personas](./octoacme-roles-and-personas.md) — full role descriptions and RACI ownership table
