# Karmada Graduation Application Review Notes

## Overview

Review of the Karmada Graduation Application ([#1572](https://github.com/cncf/toc/issues/1572)), based on the CNCF TOC [process documentation](https://github.com/cncf/toc/blob/main/process/README.md), the [DD guide](https://github.com/cncf/toc/blob/main/operations/dd-toc-guide.md), and the application content.

## Current Status

| Field | Value |
|-------|-------|
| Applied | Mar 26, 2025 by @RainbowMango (Hongcai Ren) |
| Triaged | Sep 3, 2025 by @jeremyrickard — confirmed sufficient for DD |
| Assigned | Feb 23, 2026 to @chadbeaudin |
| Board Status | TOC DD Evaluation (in-progress) |
| GTR (PR #2133) | Draft, in progress by @brandtkeller — not yet merged |
| Governance Review | [#1791](https://github.com/cncf/toc/issues/1791) opened Jul 24, 2025 |

## Application Completeness Assessment (per DD Triage Guide)

| Area | Status | Notes |
|------|--------|-------|
| Adoption Assertion | ✅ Complete | 30+ public production adopters listed; 7 adopters submitted via interview form |
| General Technical Review | ⏳ In Progress | [#1769](https://github.com/cncf/toc/issues/1769) tracked; [PR #2133](https://github.com/cncf/toc/pull/2133) is draft |
| Governance Review | ⏳ Requested | [#1791](https://github.com/cncf/toc/issues/1791) opened Jul 24, 2025 |
| Vendor Neutrality | ✅ Asserted | Governance values, 50% maintainer cap rule, neutral channels |
| Documentation | ✅ Complete | Installation, tutorials, contributor guides all linked |
| Governance & Maintainers | ✅ Complete | All sub-criteria addressed with links |
| Contributors & Community | ✅ Complete | Ladder, channels, meetings, devstats all provided |
| Engineering Principles | ✅ Complete | Architecture, roadmap, release process documented |
| Security | ✅ Complete | Audit completed Jan 2025, all findings fixed, OpenSSF badge passing |
| Ecosystem | ✅ Complete | 12+ integrations documented, 30+ adopters |

## Strengths Observed

1. **Strong adoption signal** — 30+ production adopters across diverse industries (finance/ICBC, travel/Trip.com, social/Xiaohongshu, video/Bilibili, cloud/Huawei, Bloomberg). This significantly exceeds the 3-adopter minimum.

1. **Security posture is solid** — Third-party audit completed January 2025 with all findings (1 high, 1 medium, 2 low, 2 informational) resolved. OpenSSF Best Practices badge achieved. Clear vulnerability reporting process.

1. **Governance evolution since incubation** — The project addressed several findings from the 2023 governance review (inactive maintainers, CoC harmonization). They have added maintainership change rules, subproject documentation, roadmap change process, and a dependencies policy.

1. **Maintainer diversity** — 8 maintainers from 6 organizations (Huawei, ByteDance, Moore Threads, DaoCloud, ICBC, VIPKID) with a documented 50% cap rule. This is a meaningful improvement from the 2023 review which flagged Huawei-heavy maintainership.

1. **Release maturity** — Regular 3-month release cadence, semantic versioning, clear support policy (3 most recent minor releases, ~9 months of patches), well-documented artifacts and platform support.

1. **Rich ecosystem integration** — Documented integrations with Argo CD, Flux, Istio, Kyverno, Velero, Prometheus, Submariner, Gatekeeper, and others.

## Areas Requiring Attention / Potential Blockers

1. **GTR not yet complete** — PR #2133 is still in draft. Per the DD guide, the TOC member can review this themselves if the subproject has not picked it up, but it should be finalized before public comment. This is currently the most significant process gap.

1. **Governance Review (#1791) status unclear** — Opened July 2025 but no visible completion. The 2023 review by Bill Mulligan found "Mostly Satisfactory" with must-fix items. Need to verify those were resolved:
   - Were inactive maintainers moved to emeritus? (The application shows only 1 new maintainer added — @wawa0210 — but does not show removals)
   - Was the CoC harmonized to a single source?
   - Are OWNERS files now synchronized?

1. **Maintainer lifecycle demonstration is thin** — Only one example provided (adding Xiao Zhang). For graduation, the TOC typically wants to see both additions AND removals/emeritus transitions to demonstrate the lifecycle works in both directions. The 2023 governance review flagged 4 inactive maintainers (@mrlihanbo, @carmark, @zoroyouxi, @lfbear) — their status should be clarified.

1. **Adopter interview section still templated** — The application's Adoption section still has `$COMPANY/$INDUSTRY` and `MONTH YEAR` placeholders. These will be filled by the TOC sponsor after conducting interviews, but the 7 adopters submitted via the form need to be contacted.

## Recommendations for DD Execution

Based on the [DD TOC Guide](https://github.com/cncf/toc/blob/main/operations/dd-toc-guide.md):

### 1. Kick-off meeting

Schedule with @RainbowMango. Use the kick-off template (already adapted in `karmada-kickoff-notes.md`). Set expectations on timeline (~3+ months from assignment).

### 2. Verify governance review findings are resolved

Cross-reference the 2023 review's must-fix items against current state of the repos. Key checks:

- `MAINTAINERS.md` — are inactive members removed?
- `CODE_OF_CONDUCT.md` — is there now a single canonical CoC?
- `OWNERS` files — are they consistent across repos?

### 3. GTR coordination

Since @brandtkeller has the draft PR (#2133), coordinate with them on timeline. DD activities can proceed in parallel.

### 4. Adopter interviews

Reach out to the 7 submitted adopters. Per the guide, aim for 3 completed interviews minimum across different industries. Use the [adopter questions template](https://github.com/cncf/toc/blob/main/operations/toc-templates/template-adopter-questions.md). Notable adopters to prioritize for diversity:

- Bloomberg (finance, Western company — good diversity signal)
- Xiaohongshu or Bilibili (large-scale Chinese internet)
- Trip.com (travel, migration from KubeFed story)

### 5. Security audit review

Review the [OSTIF audit report](https://github.com/karmada-io/community/blob/main/security-team/assessments/OSTIF-Karmada-Report.pdf) to confirm all critical/high findings resolved. Check for any operational security recommendations that should be noted in the DD.

### 6. Licensing check

Per the DD guide, verify compliance with CNCF licensing policy (Apache 2.0 for the main project, check dependencies).

## Process Timeline Considerations

- Application filed: Mar 2025
- Triaged: Sep 2025
- Assigned to @chadbeaudin: Feb 23, 2026
- Current date: May 7, 2026
- **KubeCon EU 2026** — check if the 4-week freeze applies to your timeline
- Target: Complete DD, interviews, internal review, then public comment + vote

## Summary

The Karmada graduation application is **substantively complete and well-prepared**. The project has clearly matured since incubation (Dec 2023) with improved governance, a completed security audit, strong adoption growth, and maintained release cadence. The main process gaps are the in-progress GTR (PR #2133) and confirming resolution of the 2023 governance review findings. Neither appears to be a fundamental blocker — they are execution items. The adoption signal is strong for graduation level.
