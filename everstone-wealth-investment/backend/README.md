# Everstone backend integration plan

Status: planning document. No production backend is deployed.

## Current frontend
- `login.html` and `register.html` are visual previews only.
- Forms are disabled. They do not collect, transmit, or store credentials.
- No client accounts, balances, payment actions, or financial transactions exist.

## Production architecture
1. Use a maintained identity provider or audited authentication service. Require email verification, secure password hashing, MFA options, rate limits, session rotation, CSRF protection, and secure, HttpOnly, SameSite cookies.
2. Keep all secrets in the hosting provider's secret manager. Never put API keys, database credentials, signing keys, or privileged tokens in browser code or Git.
3. Use a managed PostgreSQL database with private networking, encrypted backups, least-privilege roles, and tested restore procedures.
4. Enforce server-side authorisation for every client and administrator operation. Do not trust role, user ID, balance, or transaction status supplied by the browser.
5. Before any regulated financial service, obtain jurisdiction-specific legal advice and required authorisations. Use appropriately authorised custody, banking, and payment providers.

## Suggested service boundaries
- Identity: account creation, verification, MFA, sessions, account recovery.
- Client profile: consent, verified contact details, privacy requests.
- Support: enquiries, case ownership, response history.
- Compliance: required due diligence, sanctions screening where applicable, complaints and retention.
- Ledger: immutable, double-entry journal; balanced postings; idempotency keys; reconciliation; maker-checker approvals.
- Reporting: read-only projections derived from reconciled ledger entries.
- Audit: append-only security and administrative events.

## Release gates
- Security and privacy threat model approved.
- Data protection and retention requirements documented.
- Access-control tests cover cross-client data isolation.
- Authentication, recovery, rate-limit, and session tests pass.
- Ledger invariants, reconciliation, duplicate-request and failure-recovery tests pass.
- Independent security review completed.
- Legal entity, product disclosures, permissions and provider contracts verified.

Do not enable deposits, withdrawals, investment execution, or balance editing until all relevant legal, provider, accounting, security, and operational controls are in place.
