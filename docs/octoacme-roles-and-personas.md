# OctoAcme Personas

This document defines typical roles and responsibilities used in OctoAcme project docs and exercises.

---

## Developers

### Role Summary
Developers design, build, test, and deliver software components. They collaborate with product and project leads to implement features that meet acceptance criteria and quality standards.

### Responsibilities
- Implement features and fixes to meet acceptance criteria
- Write and maintain tests and documentation
- Participate in design and code reviews
- Assist in estimating and planning work
- Help identify technical risks and propose mitigations

### Goals
- Deliver reliable, maintainable code
- Reduce cycle time from idea to production
- Maintain high test coverage and observability

### Typical Communication
- Daily standups and sprint planning
- PR descriptions and code review comments
- Technical design docs when needed

---

## Product Managers

### Role Summary
Product Managers define what should be built to deliver customer and business value. They own the product vision, prioritize the backlog, and measure outcomes.

### Responsibilities
- Define problem statements and success metrics
- Prioritize the roadmap and backlog
- Collaborate with stakeholders and engineering on trade-offs
- Validate solutions through user research and metrics

### Goals
- Maximize customer value and impact
- Make clear, data-driven prioritization decisions
- Ensure product-market fit and usability

### Typical Communication
- Weekly alignment with PM and engineering leads
- Roadmap updates and stakeholder briefings
- Acceptance criteria and feature specs

---

## Project Managers

### Role Summary
Project Managers coordinate delivery activities, manage schedules, risks, and communications. They enable the team to deliver on commitments efficiently.

### Responsibilities
- Create and maintain project plans and timelines
- Manage risks, dependencies, and resource constraints
- Facilitate meetings (kickoff, planning, retrospectives)
- Ensure consistent project documentation and status reporting
- Coordinate cross-team and stakeholder communication

### Goals
- Deliver projects on time and within scope
- Minimize unplanned work and escalations
- Maintain transparency and alignment across stakeholders

### Typical Communication
- Weekly status updates and stakeholder reports
- Risk registers and decision logs
- Coordination via project boards and meeting facilitation

---

## Release Manager

### Role Summary
The Release Manager oversees the end-to-end deployment and release process. They coordinate cross-functional readiness, maintain release schedules, and ensure that rollback plans and post-release checks are executed reliably.

### Responsibilities
- Own the release calendar and communicate deployment windows to all stakeholders
- Gate releases against pre-release requirements (CI pass, security scans, release notes)
- Coordinate with Product Managers and Developers on scope freeze and timeline
- Maintain and rehearse rollback plans; trigger incident response when needed
- Track post-release metrics and close the release cycle after verification

### Goals
- Ship releases on schedule with minimal unplanned risk
- Ensure every deployment has a documented rollback path
- Drive continuous improvement in release reliability and speed

### Typical Communication
- Release readiness meetings before each deployment window
- Go/no-go decision emails or channel messages to the delivery team
- Post-release summary to stakeholders and support

### Interactions / Handoffs
- **← Developers**: Receives merged, CI-passing code and completed release notes
- **← Product Managers**: Receives scope sign-off and feature flag configuration
- **→ Project Managers**: Provides release status and any timeline changes to update stakeholder reports
- **→ Stakeholder Communication Lead**: Hands off post-release summary for stakeholder broadcast
- **→ Support**: Notifies support team of release scope and known issues; coordinates incident triage if needed

---

## Stakeholder Communication Lead

### Role Summary
The Stakeholder Communication Lead manages the flow of project information to internal and external stakeholders. They ensure the right people receive timely, accurate updates and that communication channels stay uncluttered and consistent.

### Responsibilities
- Maintain stakeholder maps and communication plans from initiation through release
- Author and distribute regular status updates (weekly summaries, milestone briefings)
- Own status dashboards and project one-pagers as living documents
- Facilitate alignment meetings when decisions or escalations require stakeholder input
- Archive communication artifacts for audit and retrospective reference

### Goals
- Keep all stakeholders informed without information overload
- Reduce escalations caused by communication gaps
- Create reusable communication templates that improve consistency

### Typical Communication
- Weekly status email or message using the [Stakeholder Update Template](./octoacme-stakeholder-update-template.md)
- Ad-hoc incident or blocker notifications within agreed SLA
- Milestone and release announcements

### Interactions / Handoffs
- **← Project Managers**: Receives status, risks, and decisions to include in stakeholder updates
- **← Release Manager**: Receives post-release summaries for broadcast
- **← Product Managers**: Receives roadmap and feature context for stakeholder briefings
- **→ All stakeholder groups**: Delivers updates, action items, and decisions

---

## QA Automation Engineer

### Role Summary
The QA Automation Engineer designs, implements, and maintains automated test suites that give the team fast, reliable quality signals. They partner with Developers and the broader QA function to close coverage gaps and prevent regressions.

### Responsibilities
- Design and implement automated test frameworks (unit, integration, end-to-end)
- Maintain test reliability and reduce flakiness to keep CI pipelines trustworthy
- Review PRs for test coverage and flag gaps in acceptance criteria coverage
- Collaborate on Definition of Done to include automation requirements
- Identify and recommend tooling improvements to reduce manual QA effort

### Goals
- Achieve and maintain agreed test coverage targets
- Detect regressions as early as possible in the development cycle
- Reduce time-to-feedback so Developers can iterate quickly

### Typical Communication
- PR review comments on test coverage and automation quality
- Weekly coverage report shared with the delivery team
- Escalation to Project Manager when coverage drops below agreed thresholds

### Interactions / Handoffs
- **← Developers**: Reviews PRs and receives feature branches for test authoring
- **← Product Managers**: Receives acceptance criteria to translate into automated tests
- **→ Release Manager**: Confirms automated test suite passes as part of release gate; see [Quality & Security Gates](./octoacme-quality-and-security-gates.md)
- **→ Project Managers**: Reports test coverage status and quality risks

---

## Security Champion

### Role Summary
The Security Champion promotes secure-by-default practices across the project lifecycle. They are an embedded advocate—not a gatekeeper—who helps the team identify and address security risks early and consistently.

### Responsibilities
- Conduct or coordinate threat modeling during design and planning
- Review code and configurations for common vulnerabilities (OWASP Top 10, secrets in code, dependency risks)
- Maintain the security section of the risk register
- Monitor security scan results in CI and triage alerts promptly
- Coordinate incident response for security-related production issues
- Run periodic security awareness sessions with the team

### Goals
- Shift security left so issues are caught before production
- Maintain a clean security posture with no unresolved critical vulnerabilities at release
- Build team security literacy over time

### Typical Communication
- Async comments on PRs flagging security concerns
- Security risk updates in the weekly delivery sync
- Incident communications for security events, following escalation paths in [Risk Management & Communication](./octoacme-risks-and-communication.md)

### Interactions / Handoffs
- **← Developers**: Reviews PRs and security scan results; provides remediation guidance
- **← Project Managers**: Receives risk register context; escalates unresolved security risks
- **→ Release Manager**: Signs off on security scan results as a release gate; see [Quality & Security Gates](./octoacme-quality-and-security-gates.md)
- **→ Stakeholder Communication Lead**: Provides security incident summaries for stakeholder communications

---

## RACI-like Ownership by Lifecycle Phase

The table below shows **who owns what** across the project lifecycle. Use it to clarify accountability at handoff points.

| Phase | Accountable | Responsible | Consulted | Informed |
|---|---|---|---|---|
| **Initiation** | Product Manager | Project Manager | Stakeholder Communication Lead | All stakeholders |
| **Planning** | Project Manager | Product Manager, Developers | Security Champion, QA Automation Engineer | Release Manager, Stakeholder Communication Lead |
| **Execution** | Project Manager | Developers, QA Automation Engineer | Security Champion, Product Manager | Release Manager, Stakeholder Communication Lead |
| **Release** | Release Manager | Developers, QA Automation Engineer, Security Champion | Project Manager, Product Manager | Stakeholder Communication Lead, Support |
| **Retrospective** | Project Manager | All team members | Product Manager | Stakeholders (summary only) |

> **Key:** Accountable = final decision maker; Responsible = does the work; Consulted = provides input before decisions; Informed = notified of outcomes.

---

## How these personas are used in the exercise
- Use these persona definitions to frame scenarios and sample interactions in the Skills Exercise.
- Each persona can be used as a persona prompt for Copilot Spaces to shape role-specific guidance.
- For templates and checklists that operationalize these roles, see the related docs listed below.

## Related Documents
- [Release Readiness Checklist](./octoacme-release-readiness-checklist.md)
- [Stakeholder Update Template](./octoacme-stakeholder-update-template.md)
- [Quality & Security Gates](./octoacme-quality-and-security-gates.md)

