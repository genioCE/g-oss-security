# g-oss-security · Identity, secrets & policy (Vault + Keycloak + OPA)

**Audience:** O&G CIOs/CTOs, CISOs, and platform/security owners  
**Goal:** Centralize secrets, enable SSO/OIDC, and express authorization as code.

---

## Executive summary
- **What it is:** **HashiCorp Vault** for secrets, **Keycloak** for OIDC/SAML SSO, and **OPA** (Open Policy Agent) for policy‑as‑code.  
- **What it replaces:** Scattered `.env` secrets, local users on every tool, expensive SSO add‑ons.

## Where it fits
```
(Users) -> Keycloak (OIDC) -> [Airflow/Trino/Superset/...]
(Services) -> Vault (dynamic creds) -> Databases/Object storage
(Authorization) -> OPA/Rego policies (allow/deny; data contracts)
```
This module underpins access to all other modules.

## Security & compliance
- **No secrets in repos.** Rotate with Vault.  
- **SSO everywhere.** Federate to corporate IdP (Keycloak as broker).  
- **Policy as code.** Approvals, dataset access, PII rules via OPA.  
- Map to internal controls (e.g., SOX change mgmt, least privilege, audit).

## KPIs for leadership
- Secrets in Vault vs. files, mean rotation time, % tools behind SSO, policy violations blocked by OPA.

## Quick start
```bash
cp .env.example .env
docker compose up -d
# Vault: http://localhost:8200  • Keycloak: http://localhost:8089  • OPA: http://localhost:8181
```
