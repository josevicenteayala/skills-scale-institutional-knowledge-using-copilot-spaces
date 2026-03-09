# OctoAcme — Release Readiness Checklist

## Purpose
Provide a structured gate check before every release to confirm that code quality, security, communication, and operational readiness requirements are met. The **Release Manager** owns this checklist and collects sign-offs from each area.

## How to Use
1. Copy this checklist into the release tracking issue or PR.
2. Each owner completes their section and adds a ✅ comment with their name and date.
3. The Release Manager reviews all sections and declares go/no-go.
4. Archive the completed checklist alongside the release notes.

---

## 1. Code & Quality Readiness
> Owner: **QA Automation Engineer** (with Developers)

- [ ] All planned features and fixes are merged and linked to their tracking issues
- [ ] CI pipeline is passing (build, unit tests, integration tests)
- [ ] End-to-end / smoke tests have been run and are passing
- [ ] Test coverage meets or exceeds agreed threshold
- [ ] No open P1/P2 bugs targeted for this release
- [ ] Code reviewed and approved per PR policy
- [ ] Definition of Done verified for all included items

*See also: [Quality & Security Gates](./octoacme-quality-and-security-gates.md)*

---

## 2. Security Readiness
> Owner: **Security Champion**

- [ ] Security scans (SAST, dependency audit) have run and passed or findings triaged
- [ ] No critical or high CVEs unresolved in production dependencies
- [ ] Secrets and credentials confirmed out of source code and config
- [ ] Threat model reviewed if new attack surface was introduced
- [ ] Security Champion has signed off on this release

*See also: [Quality & Security Gates](./octoacme-quality-and-security-gates.md)*

---

## 3. Documentation & Communication Readiness
> Owner: **Stakeholder Communication Lead** (with Release Manager)

- [ ] Release notes drafted, reviewed, and ready to publish
- [ ] Stakeholder update prepared using the [Stakeholder Update Template](./octoacme-stakeholder-update-template.md)
- [ ] Support team notified of release scope and potential impact areas
- [ ] Migration steps or breaking-change guidance documented (if applicable)
- [ ] Internal status page / dashboard updated

---

## 4. Operational Readiness
> Owner: **Release Manager**

- [ ] Deployment window scheduled and communicated
- [ ] Staging deployment completed and verified
- [ ] Rollback / mitigation plan documented and rehearsed if needed
- [ ] On-call / incident response team notified of deployment
- [ ] Monitoring and alerting confirmed active for key signals
- [ ] Post-deploy verification steps documented

---

## 5. Stakeholder & Product Sign-off
> Owner: **Product Manager**

- [ ] Acceptance criteria confirmed met for all user-facing changes
- [ ] Product Manager has approved the release scope
- [ ] Any feature flags or phased rollout configuration confirmed

---

## Go / No-Go Decision

| Role | Sign-off | Notes |
|---|---|---|
| Release Manager | | |
| QA Automation Engineer | | |
| Security Champion | | |
| Product Manager | | |
| Project Manager | | |

> **Decision:** ☐ GO &nbsp;&nbsp; ☐ NO-GO
>
> **Release Manager signature:** _________________________________ &nbsp; **Date:** ___________

---

## Related Documents
- [Quality & Security Gates](./octoacme-quality-and-security-gates.md)
- [Stakeholder Update Template](./octoacme-stakeholder-update-template.md)
- [Release & Deployment Guide](./octoacme-release-and-deployment.md)
- [Roles & Personas](./octoacme-roles-and-personas.md)
