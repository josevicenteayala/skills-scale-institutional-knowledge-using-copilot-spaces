# OctoAcme — Stakeholder Update Template

## Purpose
Provide a consistent format for regular and milestone-based stakeholder communications. The **Stakeholder Communication Lead** owns this template and is responsible for cadence and distribution.

## Communication Cadence

| Update type | Frequency | Owner | Channel |
|---|---|---|---|
| Weekly status | Every week | Stakeholder Communication Lead | Email / Slack |
| Milestone summary | At each milestone | Stakeholder Communication Lead + Project Manager | Email + meeting |
| Release announcement | At each release | Stakeholder Communication Lead + Release Manager | Email / status page |
| Incident notification | As needed (within 30 min of P1) | Stakeholder Communication Lead | Slack + email |
| Post-incident summary | Within 48 h of resolution | Stakeholder Communication Lead + Security Champion | Email |

---

## Weekly Status Update

**Subject:** `[OctoAcme] Weekly Status — Week of <DATE>`

---

**Project:** \<Project Name\>
**Date:** \<YYYY-MM-DD\>
**Status:** 🟢 On Track / 🟡 At Risk / 🔴 Off Track

### Summary
\<2–3 sentence plain-language summary of where the project stands this week.\>

### Progress This Week
- \<Completed item 1\>
- \<Completed item 2\>

### Planned for Next Week
- \<Upcoming item 1\>
- \<Upcoming item 2\>

### Risks & Blockers
| Risk / Blocker | Impact | Owner | Mitigation |
|---|---|---|---|
| \<description\> | High / Med / Low | \<Name\> | \<Plan\> |

### Decisions Needed
- \<Decision 1 — by whom, by when\>

### Metrics Snapshot *(optional)*
| Metric | Target | Actual |
|---|---|---|
| \<metric name\> | \<target\> | \<actual\> |

---

## Milestone Summary

**Subject:** `[OctoAcme] Milestone Complete — <MILESTONE NAME>`

---

**Project:** \<Project Name\>
**Milestone:** \<Milestone name\>
**Completed:** \<YYYY-MM-DD\>

### What Was Delivered
\<Brief description of milestone outcomes.\>

### Key Metrics
\<How did actuals compare to success targets?\>

### Lessons Learned / Adjustments
\<Any process or scope changes going forward?\>

### Next Milestone
**Name:** \<Next milestone\>
**Target date:** \<YYYY-MM-DD\>
**Focus areas:** \<summary\>

---

## Release Announcement

**Subject:** `[OctoAcme] Release — <VERSION> is live`

---

**Release:** \<Version / name\>
**Released:** \<YYYY-MM-DD HH:MM UTC\>
**Environment:** \<Production / Staging\>

### What's New
- \<Feature or fix 1\>
- \<Feature or fix 2\>

### Known Issues
- \<Any known limitations or in-flight fixes\>

### Migration / Action Required
\<Steps users or operators need to take, or "No action required."\>

### Rollback Plan
\<Reference to rollback procedure if needed, or "N/A — no breaking changes."\>

### Support Contact
\<Who to contact with questions or issues.\>

---

## Incident Notification (P1/P2)

**Subject:** `[OctoAcme][INCIDENT] <Short description> — <STATUS>`

---

**Severity:** P1 / P2
**Detected:** \<YYYY-MM-DD HH:MM UTC\>
**Status:** Investigating / Mitigating / Resolved

### Summary
\<What is impacted and who is affected?\>

### Actions Being Taken
- \<Step 1\>
- \<Step 2\>

### Estimated Resolution
\<ETA or "Unknown — updates every 30 minutes."\>

### Next Update
\<YYYY-MM-DD HH:MM UTC or "Upon resolution."\>

*Owned by: Stakeholder Communication Lead in coordination with Release Manager / Security Champion*

---

## Related Documents
- [Roles & Personas](./octoacme-roles-and-personas.md)
- [Risk Management & Communication](./octoacme-risks-and-communication.md)
- [Release Readiness Checklist](./octoacme-release-readiness-checklist.md)
