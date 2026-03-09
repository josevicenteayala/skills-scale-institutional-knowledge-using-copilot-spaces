# OctoAcme — Quality & Security Gates

## Purpose
Define the quality and security checkpoints that code must pass before moving between pipeline stages (build → test → release). Clear gate ownership reduces ambiguity at handoff points and prevents defects and vulnerabilities from reaching production.

## Gate Overview

```
 Commit → [ Gate 1: Build & Unit Test ] → Merge → [ Gate 2: Integration & Security Scan ] → Release Candidate → [ Gate 3: Release Readiness ] → Production
```

---

## Gate 1 — Build & Unit Test
**Trigger:** Every commit / PR open  
**Owner:** **QA Automation Engineer** (automated); **Developers** (remediation)

| Check | Pass Criteria | Fail Action |
|---|---|---|
| Build compiles without errors | Exit code 0 | Block merge; Developer fixes |
| Unit tests pass | 0 failures | Block merge; Developer fixes |
| Linting / code style | 0 errors (warnings allowed) | Block merge; Developer fixes |
| Test coverage | Meets project threshold (e.g., ≥ 80%) | Flag for QA Automation Engineer review |

**Handoff:** Gate 1 pass → PR can be reviewed and merged.

---

## Gate 2 — Integration & Security Scan
**Trigger:** Merge to main / release branch  
**Owner:** **Security Champion** (security checks); **QA Automation Engineer** (integration tests)

| Check | Pass Criteria | Fail Action |
|---|---|---|
| Integration tests pass | 0 failures | Block promotion; QA Automation Engineer triages |
| SAST (static analysis) | No critical/high findings unresolved | Security Champion triages and remediates |
| Dependency vulnerability scan | No critical CVEs unresolved | Security Champion approves exception or fix |
| Secrets / credential scan | No secrets detected in code or configs | Block promotion; Developer rotates credentials immediately |
| Container / IaC scan (if applicable) | No critical findings | Security Champion reviews |

**Handoff:** Gate 2 pass → build artifact promoted to staging / release candidate.

---

## Gate 3 — Release Readiness
**Trigger:** Release candidate declared; before production deployment  
**Owner:** **Release Manager** (overall); see [Release Readiness Checklist](./octoacme-release-readiness-checklist.md)

| Check | Pass Criteria | Owner |
|---|---|---|
| Staging smoke tests | All critical paths pass | QA Automation Engineer |
| Security sign-off | Security Champion confirms Gate 2 findings resolved | Security Champion |
| Product sign-off | Product Manager confirms acceptance criteria met | Product Manager |
| Release notes & rollback plan | Documented and reviewed | Release Manager |
| Stakeholder communication ready | Update drafted and staged | Stakeholder Communication Lead |

**Handoff:** Gate 3 pass → Release Manager declares GO; production deployment proceeds.

---

## Escalation Paths

| Situation | Escalate to | SLA |
|---|---|---|
| Flaky test blocking Gate 1 | QA Automation Engineer | Same sprint |
| Critical security finding | Security Champion → Project Manager | 24 hours |
| Integration test environment down | Project Manager | 4 hours |
| Gate 3 no-go decision | Project Manager + Product Manager | Before deployment window |

---

## Quality Metrics to Track

- **Gate 1 pass rate:** % of PRs that pass on first run (target ≥ 90%)
- **Gate 2 mean time to green:** Average time from merge to passing Gate 2 (target < 30 min)
- **Defect escape rate:** Bugs found in production vs. caught in gates (target: trend down quarter-over-quarter)
- **Open critical/high security findings:** Count of unresolved findings at any given time (target: 0 at release)

Review metrics in the weekly delivery sync and retrospectives.

---

## Related Documents
- [Release Readiness Checklist](./octoacme-release-readiness-checklist.md)
- [Execution & Tracking](./octoacme-execution-and-tracking.md)
- [Release & Deployment Guide](./octoacme-release-and-deployment.md)
- [Roles & Personas](./octoacme-roles-and-personas.md)
