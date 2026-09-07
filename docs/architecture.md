# How the Portal fits together

Paramount Portal is the mobile-facing layer of a club data system. The operational model brings source evidence, athlete context, and team information together; the PWA provides a focused way for athletes and coaches to use that information.

The [system diagram](../README.md#system-architecture) shows the conceptual flow. The operational data system and the frontend foundation are distinct: the current PWA uses synthetic content, and its protected live-data connection is the next phase.

## Seven connected responsibilities

| Layer | What it contributes |
| --- | --- |
| **Source ingestion** | Controlled retrieval of authoritative competition, record, qualification, and club-related information. Source context matters when interpreting what a result means. |
| **Validation and reconciliation** | Checks completeness and consistency, matches evidence to the appropriate athlete context, and makes proposed changes reviewable. Incomplete evidence must not silently become an authoritative update. |
| **Operational Airtable model — The Platform** | Organizes athlete profiles, competition history, training PRs, qualification and record context, membership context, and team views for club operations. |
| **Monitoring and integrity controls** | Tracks retrieval outcomes and exceptions, holds incomplete evidence back from downstream changes, and supports intentional, validated production writes. Automated tests protect important boundaries. |
| **Protected API and application boundary** | The planned bridge to the Portal: authenticate the user and provide only the information that user is permitted to see. Provider credentials remain outside the browser. This live-data connection is not part of the current preview. |
| **Mobile-first PWA** | The built Home, Platform, Team, and Profile surfaces, responsive navigation, and installable/offline shell foundation. Offline shell behavior does not imply offline access to private athlete data. |
| **External service integrations** | PushPress, TrainHeroic, and Telegram have launcher positions in the design. Reviewed destinations and any authenticated handoffs remain future work. Ring the PR Bell also needs authorized submission and persistence before it can record a PR. |

## Tools with clear roles

**Airtable** is the operational data layer. **Cloudflare** supports retrieval/runtime services and the hosting/API foundation. **GitHub** preserves reviewable implementation changes and automated validation. **ChatGPT** supports analysis, orchestration, and human decision support; **Codex** supports implementation and testing.

Together, these roles connect data maintenance to the athlete experience while keeping production changes controlled. The preview demonstrates the interface without granting access to the operational system.

## What coaches can assess today

The synthetic preview makes the information layout, navigation, athlete profile, and four Team board concepts reviewable. **Records in Reach remains under construction**: its intended comparison of athlete performance with applicable records and standards is not a live calculation in the preview.

Live authentication, permission-scoped data access, working external handoffs, and PR Bell persistence are next-phase work. No deployment, real athlete data, or operational credentials are included in this showcase.
