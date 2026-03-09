# OctoAcme Project Management Docs

This folder is the central hub for OctoAcme's project management process documentation. It is maintained as part of the [skills-scale-institutional-knowledge-using-copilot-spaces](../) repository, which demonstrates how GitHub Copilot Spaces can be used to scale institutional knowledge across a team.

---

## What this repository contains

| Area | Description |
|---|---|
| `docs/` | Process documents that define how OctoAcme runs projects end-to-end |
| `.github/ISSUE_TEMPLATE/` | Templates for proposing new or updated process content |
| Root `README.md` | Exercise entry point for the Copilot Spaces skills exercise |

---

## How to propose updates

To add new content or update an existing process document, open an issue using the [**Add/Update Process Doc** template](../.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml). Follow the checklist in that template to ensure your proposal is reviewed and aligned with existing standards.

---

## OctoAcme Project Lifecycle

OctoAcme uses a phased delivery approach. Each phase has a dedicated guide linked below.

### 1. Initiation → [`octoacme-project-initiation.md`](octoacme-project-initiation.md)
Validate the project idea, align stakeholders, and define success criteria before committing to full planning. Key deliverable: **Project One-pager**.

### 2. Planning → [`octoacme-project-planning.md`](octoacme-project-planning.md)
Break work into shippable increments, estimate scope, document risks and dependencies, and define the **Definition of Done (DoD)**.

### 3. Execution & Tracking → [`octoacme-execution-and-tracking.md`](octoacme-execution-and-tracking.md)
Manage day-to-day progress via project boards, daily standups, and PR workflows. Escalate blockers through three levels (Team → PM → Sponsor).

### 4. Release & Deployment → [`octoacme-release-and-deployment.md`](octoacme-release-and-deployment.md)
Standardize releases (Patch / Minor / Major) with passing CI, drafted **release notes**, a rollback plan, and post-deploy verification before announcing.

### 5. Retrospective & Continuous Improvement → [`octoacme-retrospective-and-continuous-improvement.md`](octoacme-retrospective-and-continuous-improvement.md)
After each sprint, release, or incident, capture what went well, what can improve, and track 2–3 action items with clear owners and due dates.

---

## Risks & Communication → [`octoacme-risks-and-communication.md`](octoacme-risks-and-communication.md)

Maintain a **Risk Register** (ID, description, impact, likelihood, owner, mitigation, status) and provide weekly status updates using the standard template. Escalate security incidents to the Security on-call immediately.

---

## Roles & Personas → [`octoacme-roles-and-personas.md`](octoacme-roles-and-personas.md)

| Role | Primary responsibility |
|---|---|
| **Project Manager (PM)** | Coordinates delivery, schedules, risk, and communications |
| **Product Manager (PdM)** | Defines outcomes, prioritizes backlog, measures success |
| **Developers** | Implement features, write tests, participate in design and code reviews |
| **QA / Testing** | Validate quality and acceptance criteria |
| **Stakeholders** | Provide inputs and approvals |

---

## Key Artifacts & Cadences

| Artifact | Phase |
|---|---|
| Project One-pager | Initiation |
| Prioritized Backlog | Planning |
| Definition of Done (DoD) | Planning |
| Risk Register | Planning → Execution |
| Weekly Status Updates | Execution → Release |
| Release Notes | Release & Deployment |
| Retrospective Notes & Action Items | Retrospective |

**Recurring cadences:** daily standup · weekly PM + PdM sync · monthly stakeholder update · sprint demo/review

---

For a high-level overview of all processes in one place, see [`octoacme-project-management-overview.md`](octoacme-project-management-overview.md).
