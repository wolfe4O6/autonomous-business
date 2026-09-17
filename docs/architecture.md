# Architecture proposal

## Separation
Desktop client → authenticated control API → business service/policy controller → restricted tool brokers and Hermes worker.

The desktop is not the durable scheduler. Host-side services own execution and persisted state. The agent does not own or edit enforcement code, audit records, or sensitive service credentials.

## Components
- Desktop: onboarding, pairing, account consent, dashboard, intervention, reports. Tauri/shared web UI is a candidate; validate packaging and secure storage before commitment.
- Control service: durable task queue, operator lease, scheduling, owner policies, action authorization, financial reservations, audit trail, reports.
- Hermes adapter: version-pinned runtime, supported integration route proven in an early Linux spike. Profiles express operator/reviewer roles but are not security boundaries.
- Tool brokers: email, publishing, spending, and payment readback; scoped credentials never exposed as unrestricted agent secrets.
- Worker sandbox: browser, code, and artifacts isolated from owner files and control services. No privileged container, host-management socket, or host-admin credential.

## Agent roles
Operator owns strategy and execution. Reviewer assesses significant proposed actions and periodic business results, using source evidence rather than trusting operator claims. Temporary specialists have bounded tasks, time/cost limits, and narrow tools. Reviewer opinion never overrides deterministic policy. Do not run permanent group chats merely to create activity.

## Runtime loop
Event/timer → load authoritative state → claim one task → bounded execution → verify external effect → append result → schedule follow-up. Ordinary code checks whether work is due before making model calls. Retries are bounded; uncertain external effects are reconciled before retry.

## Platforms
Initial worker: compatible Linux VPS, with supported distro/architecture documented after tests. A versioned container deployment is a candidate. Mac local/Closet Mac hosting requires a separate isolation/runtime design and explicit machine authorization. Later Linux desktop packaging must be tested independently of headless Linux worker support.

## Persistence and remote control
Business state survives restart and UI disconnection. Use leases/locks to avoid duplicate operator execution. Owner control must have independent authentication and a durable audit event. Expiring action authorization and host-side watchdogs should fail closed for sensitive operations when control connectivity is lost. Define reconnection and stale-event behavior before deployment.

## Hermes strategy
Reuse provider/tool/session/profile capabilities through a narrow adapter; avoid an extensive fork. Verify exact supported APIs/CLI/extensions before implementation. Review upstream MIT notices and all bundled dependency licenses. No dependency is pinned yet because no executable integration has been proven.
