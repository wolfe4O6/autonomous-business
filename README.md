# Autonomous Business

Working name for a desktop-controlled autonomous business experiment powered by Hermes Agent.

**Status: specification and planning only. No application, worker, purchasing integration, or installer has been implemented.**

## Intended experience
Install the desktop app → choose a Linux VPS, another computer, or this computer → connect an AI API and dedicated business accounts → set limits → start → receive verified daily reports. Routine operation should not require owner prompting.

Mac desktop first; Linux worker first; Linux desktop later. The owner wants to use a VPS initially, retain Closet Mac/local hosting options, and eventually use the desktop app on their Linux desktop.

## Design
- Custom application around a pinned Hermes runtime, not a large Hermes fork.
- One operator, an on-demand reviewer, and bounded specialist workers.
- Non-AI policy controller holds final authority over spending and sensitive actions.
- Owner controls: Pause, Intervene, Stop Spending, Emergency Stop.
- No promise of profit. All model and infrastructure costs count.

## Project documents
- [Product requirements](docs/product.md)
- [Architecture](docs/architecture.md)
- [Safety and purchasing](docs/safety.md)
- [Research and prior experiments](docs/research.md)
- [Implementation milestones](.hermes/plans/implementation.md)
- [Contribution boundaries](AGENTS.md)

## Planned repository layout
`apps/desktop/` — cross-platform desktop UI (Tauri is a candidate, not committed).

`services/control/` — authoritative business state, policy, scheduler, audit log.

`services/worker/` — Hermes adapter and role execution.

`packages/contracts/` — versioned API/event schemas.

`deploy/` — tested Linux deployment and later local-host setup.

These implementation directories will be created with their milestones, not filled with placeholder services.

## Development
No build or runtime command exists yet. Start with milestone 1: prove the supported Hermes execution route on Linux with a harmless end-to-end task. Never introduce real purchasing before policy and failure-path tests pass.

## Licensing
No project license selected yet. Hermes is MIT-licensed; retain upstream notices when distributing it. Audit bundled dependency licenses separately. No upstream source is vendored here.
