# OctoAcme — Release & Deployment Guide

## Purpose
Standardize how OctoAcme releases features to production to reduce risk and improve observability.

## Release Types
- Patch: hotfixes addressing critical production issues
- Minor: incremental features and improvements
- Major: significant functionality or breaking changes

## Pre-release requirements
- All acceptance criteria met and PRs merged
- Passing CI and security scans
- Release notes drafted
- Rollback / mitigation plan documented
- Smoke tests prepared

## Deployment Checklist
- [ ] Deployment window scheduled (if needed)
- [ ] Backup or snapshot (if applicable)
- [ ] Deploy to staging and run smoke tests
- [ ] Deploy to production (automated pipeline preferred)
- [ ] Run post-deploy verifications
- [ ] Announce release to stakeholders and support

## Rollback & Incident Playbook
- If a deployment fails or causes a critical issue:
  - Trigger incident response and notify on-call
  - Rollback to last known-good release if necessary
  - Triage root cause and capture action items

## Release Notes Template
- Release name / number:
- Date:
- Summary:
- Notable changes:
- Migration steps (if any):
- Known issues:

## Roles Involved
- **Release Manager** — owns the deployment checklist, go/no-go decision, and post-release verification
- **QA Automation Engineer** — confirms automated tests pass before deployment
- **Security Champion** — signs off on security scan results
- **Stakeholder Communication Lead** — drafts and sends release announcement
- **Product Manager** — approves release scope

## Related Templates
- [Release Readiness Checklist](./octoacme-release-readiness-checklist.md) — structured sign-off across all readiness areas
- [Stakeholder Update Template](./octoacme-stakeholder-update-template.md) — release announcement format
- [Quality & Security Gates](./octoacme-quality-and-security-gates.md) — gate definitions and pass criteria
- [Roles & Personas](./octoacme-roles-and-personas.md) — full role descriptions and interactions
