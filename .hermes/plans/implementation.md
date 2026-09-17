# Phased implementation plan

## Current state
Specification-only repository. No existing executable product, integrations, deployment, or CI claims. Proposed layout is in README.md. No changes to owner's existing Hermes installation or remote hosts are authorized by this plan.

## 1. Prove Linux Hermes execution
On an explicitly authorized disposable Linux environment, pin a runtime version and prove authenticated non-interactive inference, a harmless tool task, structured result capture, timeout/cancel behavior, cost visibility, and restart recovery. Record exact integration surface and dependencies. No customer contact or purchases.

## 2. Implement control domain with tests first
Durable tasks, operator lease, append-only audit events, owner directions, state transitions, and budget reservations. Prove concurrency and idempotency. Select storage and schemas based on deployment needs. Use clearly labeled test fixtures.

## 3. Connect one bounded operator
Add the adapter, restricted tools, task contracts, event-driven wake-ups, and a restart-safe loop. Complete a harmless artifact-producing task and verify it. Confirm closing/reopening a client cannot spawn duplicates.

## 4. Add reviewer and owner controls
Read-only reviewer at defined decision points, bounded specialists, Pause/Intervene/Stop Spending/Emergency Stop. Test lost connectivity, in-flight action reporting, policy tampering, and stale approvals.

## 5. Build Mac desktop onboarding and dashboard
Validate framework choice; implement existing-VPS connection/pairing first, secure key entry, readiness checks, real event stream, and evidence links. Exercise clean-machine installation, restart, credential failure, and unavailable worker. No fake live metrics.

## 6. Add dedicated business integrations
Prove email with owner-controlled recipients, publishing in a test workspace, and payment test-mode readback. Complete sandbox purchase/reconciliation tests before requesting live-money authorization. Record all provider limitations and required user consent.

## 7. Daily reports and bounded pilot
Generate reports from authoritative records. Test a complete controlled cycle: start, task, verified result, expense, intervention, restart, daily summary. Owner approves budget and any production actions separately.

## 8. Expand host/platform support
Test local Mac/Closet Mac isolation only with explicit permission; test Linux desktop packaging on owner's intended environment; verify supported Linux VPS distributions/architectures. Add provider-specific provisioning only after explicit cost consent and rollback design.

## Release acceptance
Supported clean installs; real inference and tools; persistent recovery; all safety tests; reconciled daily report; observed stop acknowledgements; signed/notarized Mac distribution as applicable; documented compatibility and known gaps. A health endpoint or mocked purchase is not end-to-end proof.
