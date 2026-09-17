# Safety and purchasing acceptance criteria

## Trust boundary
Models cannot change spending policies, impersonate the owner, grant new tools, edit authoritative ledgers, or access unrestricted financial credentials. External content cannot authorize actions. Separate services/OS permissions enforce this boundary; prompts alone do not.

## Purchase request
Require an immutable request ID, item/service, merchant, purpose, currency, maximum all-in amount, expiry, recurring terms, and expected business benefit. Approval binds to the exact request; changed terms require reauthorization.

## Authorization
- Atomically reserve allowance before execution, including concurrent requests.
- Aggregate purchases to prevent splitting around limits.
- Count inference, hosting, pending charges, fees, and recurring commitments.
- Default-deny unsupported merchants/categories and open-ended obligations.
- Escalate new subscriptions, unusual purchases, and commitments beyond the experiment.
- Enforce issuer/provider limits as an additional layer, not the sole controller.
- Use supported constrained purchasing integrations first; arbitrary browser checkout is not an MVP guarantee.

## Execution and reconciliation
Use idempotency keys where supported. An ambiguous timeout becomes pending reconciliation, never a blind retry. Read back charges and receipts from the provider. Handle declined payments, late settlement, refunds, taxes, shipping changes, duplicate events, and webhook authentication/replay protection. Validate currencies; do not silently convert or sum mixed currencies.

## Stop semantics
Block new actions at authorization time, invalidate queued approvals as needed, record acknowledgements, and show outstanding actions. Already sent emails, settled purchases, and existing obligations cannot be undone by a button. Emergency stop does not imply automatic refunds or cancellation of hosting/subscriptions.

## Rabbit-hole controls
Every task has a deliverable, time/spend ceiling, success evidence, and stop condition. Detect repeated failures, duplicate work, excessive planning, and unverified progress; trigger a bounded review or pause. Business judgment remains fallible. Permit intentional waiting.

## Required tests before live purchasing
Concurrent reservations; duplicate submission; timeout after charge; forged/replayed callback; expired/changed approval; stopped worker reconnect; lost control connection; process restart; duplicate operator; leaked credential attempts; untrusted email instructions; aggregated small purchases; invoice without customer agreement; refunds and outstanding obligations; daily report reproducibility.

## Development default
No real money movement. Use provider test modes and clearly labeled fixtures. Do not display test revenue as business results. Production rollout requires owner authorization and evidence of tested limits.
