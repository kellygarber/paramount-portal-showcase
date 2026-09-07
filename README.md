# PARAMOUNT PORTAL

**One team. One front door.**

A mobile-first athlete and team platform for Paramount Barbell Club, designed to combine the athlete experience, coaching information, competition history, records, qualifications, training PRs, membership context, and team analytics in one interface.

**Foundation preview:** the PWA shell, design, and navigation are built. Every athlete name, performance value, and team entry shown below is synthetic. Live data and authentication are the next phase.

## The mobile experience

| Home · the club front door | The Platform · the athlete hub |
| :---: | :---: |
| <img src="assets/home-mobile.png" width="300" alt="Demo Home with The Platform and four club-tool launchers"> | <img src="assets/platform-mobile.png" width="300" alt="Synthetic Platform overview with profile, competition, performance, and team cards"> |

## What makes it different

The Portal goes beyond browsing USAW records. It is **federation/source-aware and club-centered**: the underlying data system reconciles multiple authoritative sources into a controlled athlete and team model, retaining the context needed to interpret results, qualifications, and records.

That model brings competition evidence together with training, membership context, and club priorities. The Portal is the athlete-facing experience being built on top of it.

## Athlete experience

| Area | Experience represented in the design |
| --- | --- |
| Personal profile | An athlete snapshot with competition bests, next competition, and meet history. |
| Training PRs | A dedicated view of personal bests across training movements. |
| Qualifications and record matches | Places to follow qualification progress and compare performance with relevant records. |
| Club tools | PushPress, TrainHeroic, and Telegram launchers for membership/community, training, and team communication. Destinations remain placeholders in this preview. |
| Ring the PR Bell | A workflow concept for recording and celebrating a training PR. The shell action does not save or submit a record. |

These screens demonstrate the intended experience using sample content; they do not read athlete records or verify eligibility.

## Team experience

Four boards give the team its own space:

| Board | Purpose and status |
| --- | --- |
| **Current Records** | A synthetic preview of club record holders. |
| **Perfect 6/6** | A sample board recognizing perfect meets. |
| **Bomb Squad** | A reserved board for a team tradition; its final rules and live membership are not represented here. |
| **Records in Reach — UNDER CONSTRUCTION** | Intended to identify realistic record opportunities by comparing athlete performance against applicable record standards and records. The visible rows are placeholders, not computed opportunities. |

| Team · all four boards | Profile · the athlete snapshot |
| :---: | :---: |
| <img src="assets/team-mobile.png" width="300" alt="Synthetic Team screen showing Current Records, Perfect 6/6, Bomb Squad, and Records in Reach"> | <img src="assets/profile-mobile.png" width="300" alt="Demo athlete profile with competition bests, next competition, and training PRs"> |

**Records in Reach is under construction.** All four boards in this screenshot contain anonymous demo placeholders.

## System architecture

The Portal belongs to a larger integrated data system. This diagram shows the conceptual path, including the planned live-data connection:

```mermaid
flowchart TD
    A[External authoritative sources] --> B[Controlled retrieval and reconciliation]
    B --> C["Airtable operational data model — The Platform"]
    C -. "Planned live-data connection" .-> D["Protected application / API layer — next phase"]
    D -.-> E[Paramount Portal PWA]
    E --> F[Athletes and coaches]
```

**Airtable** supports the operational model. **Cloudflare** provides the runtime and hosting foundation. **GitHub** supports reviewable engineering changes and automated validation. **ChatGPT** supports analysis and orchestration, with **Codex** supporting implementation and testing.

The built PWA currently uses static demo content. Read the [concise architecture overview](docs/architecture.md) for the responsibilities of each layer.

## Data integrity and engineering

- **Reconciled evidence:** source information is checked and reconciled before it informs athlete and team data.
- **Reviewable changes:** important updates can be inspected, with production writes intentionally controlled and validated.
- **Fail-closed decisions:** incomplete evidence is held back from downstream changes rather than treated as a complete result.
- **Automated protection:** tests and validation check structural integrity, security boundaries, and PWA behavior.
- **Private by design:** private athlete records and credentials are intentionally excluded from source control. This showcase contains documentation and synthetic screenshots only.

## One front door, room to grow

<img src="assets/sign-in-mobile.png" width="300" alt="Sign-in design explicitly stating that authentication is not connected, with a demo preview button">

The sign-in screen establishes the intended entry experience. Authentication is not connected, and the demo does not collect credentials.

<details>
<summary><strong>Explore the desktop layouts</strong></summary>

### Home

![Desktop Home with The Platform and club tools](assets/home-desktop.png)

### Athlete profile

![Synthetic desktop athlete profile with training PRs, records, and meet history](assets/profile-desktop.png)

</details>

## Current status

| Component | Status |
| --- | --- |
| PWA shell, design, and navigation | **Built** — responsive mobile and desktop surfaces, app manifest, and offline shell foundation. |
| Synthetic preview | **Built** — static demo content, with no live athlete reads or writes. |
| Protected live-data and authentication layer | **Staged / next phase** — the preview is not connected to live data or authentication. |
| Records in Reach | **Under construction** — board concept visible; live opportunity calculations are not implemented in this preview. |
| External launchers and PR Bell submission | **Placeholder / concept** — reviewed destinations and authorized persistence remain future work. |

This private showcase is a design and architecture review, with no application deployment or live service access.
