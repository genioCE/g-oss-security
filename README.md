# g-oss-security

Vault + Keycloak + OPA (policy-as-code).

## Run
```bash
cp .env.example .env
docker compose up -d
```
- Vault (dev): http://localhost:8200 (token: root)
- Keycloak: http://localhost:8089
- OPA: http://localhost:8181
