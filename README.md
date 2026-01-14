# Immigration Justice Data Spine (starter)

A minimal starter for a persistent, auditable system-of-record for immigration cases and conviction–immigration nexus.
It includes a FastAPI backend and a React admin skeleton intended to be extended with strong audit, security, and ML/embedding features.

Status: prototype / starter — use for development and design exploration only.

## Features (starter)
- FastAPI backend with JSON REST endpoints
- React admin skeleton for basic CRUD
- Docker Compose for local development
- Plans for audit logging, role-based redaction, and vector search

## Quickstart (local)
Requirements: Docker & Docker Compose.

1. Clone the repo
2. Build and run:
   ```bash
   docker-compose up --build
   ```
3. Services
   - Backend: http://localhost:8000
   - Frontend: http://localhost:3000

## Development notes
- Harden authentication before production: secure password hashing, refresh tokens, session policies.
- Add database migrations (recommended: Alembic for SQLAlchemy).
- Implement audit logging triggers (DB-level or application-level) to ensure an immutable audit trail.
- Implement role-based redaction and field-level security for privacy-sensitive fields.
- Add scrapers or ETL worker services as separate processes to keep the API responsive.
- Consider pgvector + embeddings for KNN similarity search across documents/case histories.

## Recommended next steps (prioritized)
1. Authentication & session security (bcrypt/argon2, refresh tokens, MFA options)
2. Add Alembic migrations and a documented migration workflow
3. Implement audit log storage (append-only table, hashed chains, or external audit store)
4. Role-based access control and field-level redaction tests
5. Add unit & integration test coverage, CI pipeline
6. Pipeline for embeddings + pgvector for similarity/semantic search

## Environment & configuration suggestions
- Use a .env file for development with defaults committed to `.env.example`
- Important envs:
  - DATABASE_URL (Postgres)
  - SECRET_KEY (auth signing)
  - EMAIL_* (optional alerting)
- Use separate secrets management for production (Vault, cloud KMS, etc).

## Architecture & security considerations
- Keep scraping and heavy ML tasks in background workers to avoid blocking API.
- Limit PII exposure in logs and backups. Use field-level encryption or redaction where required.
- Prepare a data retention and deletion policy to comply with privacy/regulatory requirements.

## Contributing
Contributions welcome. Please open issues for design discussions and small PRs for features. For larger changes, open an issue first to discuss the approach.

## License
Add a license (e.g., MIT, Apache-2.0) — currently unspecified.
