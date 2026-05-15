# Karmada Graduation Application Review Notes

## Overview

Review of the Karmada Graduation Application ([#1572](https://github.com/cncf/toc/issues/1572)), based on the CNCF TOC [process documentation](https://github.com/cncf/toc/blob/main/process/README.md), the [DD guide](https://github.com/cncf/toc/blob/main/operations/dd-toc-guide.md), and the application content.

## Current Status

| Field | Value |
|-------|-------|
| Applied | Mar 26, 2025 by @RainbowMango (Hongcai Ren) |
| Triaged | Sep 3, 2025 by @jeremyrickard — confirmed sufficient for DD |
| Assigned | Feb 23, 2026 to @chadbeaudin and @abebars|
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

1. **Strong adoption signal** — 30+ production adopters across diverse industries (finance/ICBC, travel/Trip.com, social/Xiaohongshu, video/Bilibili, cloud/Huawei, Bloomberg).

1. **Security posture is solid** — Third-party audit completed January 2025 with all findings (1 high, 1 medium, 2 low, 2 informational) resolved. OpenSSF Best Practices badge achieved. Clear vulnerability reporting process.

1. **Maintainer diversity** — 8 maintainers from 6 organizations (Huawei, ByteDance, Moore Threads, DaoCloud, ICBC, VIPKID) with a documented 50% cap rule. This is a meaningful improvement from the 2023 review which flagged Huawei-heavy maintainership.

1. **Release maturity** — Regular 3-month release cadence, semantic versioning, clear support policy (3 most recent minor releases, ~9 months of patches), well-documented artifacts and platform support.

1. **Rich ecosystem integration** — Documented integrations with Argo CD, Flux, Istio, Kyverno, Velero, Prometheus, Submariner, Gatekeeper, and others.

## Areas Requiring Attention / Potential Blockers

1. **GTR not yet complete** — PR #2133 is in review.

1. **Maintainer lifecycle demonstration is thin** — Only one example provided (adding Xiao Zhang). The maintainer lifecycle process is documented, but the offboarding path has not been demonstrated. The 2023 governance review flagged 4 inactive maintainers (@mrlihanbo, @carmark, @zoroyouxi, @lfbear).  They should be moved to emeritus.I

1. **Adopter interview section still templated** — The application's Adoption section still has `$COMPANY/$INDUSTRY` and `MONTH YEAR` placeholders. These will be filled by the TOC sponsor after conducting interviews, but the 7 adopters submitted via the form need to be contacted.

[DD TOC Guide](https://github.com/cncf/toc/blob/main/operations/dd-toc-guide.md):

### 1. Kick-off meeting

Schedule with @RainbowMango. Use the kick-off template (already adapted in `karmada-kickoff-notes.md`).

### 2. Verify governance review findings are resolved

Cross-reference the 2023 review's must-fix items against current state of the repos. Key checks:

- `MAINTAINERS.md` — are inactive members removed?
   - [Comment](https://github.com/cncf/toc/issues/1572#issuecomment-4451663241) made on DD issue.
- `CODE_OF_CONDUCT.md` — is there now a single canonical CoC?
  - CoC issue has been rectified.  Now one CoC pointing to CNCF CoC
- `OWNERS` files — are they consistent across repos?
  - [Comment](https://github.com/cncf/toc/issues/1572#issuecomment-4452003587) regarding inconsistent OWNERS

### 3. GTR coordination

GTR was completed by @brandtkeller PR [#2133](https://github.com/cncf/toc/pull/2133)
- GTR Q&A [here](https://github.com/brandtkeller/toc/blob/1769_karmada_technical_review/projects/karmada/tech-review/2026-04-21.md)

Area(s) of concern.  
  - "These certificates are stored in Kubernetes ConfigMaps or Secrets, and are manually provisioned and rotated by cluster administrators."  
    - This could be fairly labor intensive if a project is using Karmada to manage dozens of clusters.
  - Upgrade->downgrade->upgrade was not tested.
    - This is not significant, but worth investigating.

### 4. Adopter interviews

Reached out to the submitted adopters. Per the guide, aiming for 3-5 interviews across different industries or use cases. Will use the [adopter questions template](https://github.com/cncf/toc/blob/main/operations/toc-templates/template-adopter-questions.md).

- Bloomberg (finance, Western company — good diversity signal)
- Trip.com (travel, migration from KubeFed story)
- Xiaohongshu or Bilibili (large-scale Chinese internet) (TODO)

### 5. Security audit review

Review the [OSTIF audit report](https://github.com/karmada-io/community/blob/main/security-team/assessments/OSTIF-Karmada-Report.pdf) to confirm all critical/high findings resolved. Check for any operational security recommendations that should be noted in the DD.

### 6. Licensing check

Per the DD guide, verify compliance with CNCF licensing policy (Apache 2.0 for the main project, check dependencies).

## Process Timeline Considerations

- Application filed: Mar 2025
- Triaged: Sep 2025
- Assigned to @chadbeaudin: Feb 23, 2026 (added Ahmed Bebars as shadow May 14, 2026)
- Current date: May 7, 2026
- Target: Complete DD, interviews, internal review, then public comment + vote

## Summary

The Karmada graduation application is **substantively complete and well-prepared**. The project has clearly matured since incubation (Dec 2023) with improved governance, a completed security audit, strong adoption growth, and maintained release cadence. The main process gaps are the in-progress GTR (PR #2133) and confirming resolution of the 2023 governance review findings. Neither appears to be a fundamental blocker — they are execution items. The adoption signal is strong for graduation level.
