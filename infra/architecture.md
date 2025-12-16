# EdgeServe Secure Web Platform – Architecture

## Traffic Flow
Users → HTTPS GCS URL → Private GCS Bucket

- Users access content via HTTPS endpoint.
- GCS bucket is private; only accessible via IAM roles.
- Error pages served via `error.html`.
- Versioning enabled on bucket for safe rollback.

## Security Decisions
- Cloud Storage bucket is private.
- Public access is disabled.
- HTTPS enforced via managed certificates.
- Deployment uses a service account with minimal permissions.
- Secrets stored securely in GitHub Actions (`GCP_SA_KEY` & `GCP_PROJECT_ID`).

## CI/CD Pipeline
- GitHub main branch push triggers workflow.
- GitHub Actions authenticates GCP service account.
- Static site from `site/` folder synced to GCS bucket.
- Deployment verified by listing bucket contents.
- Failures can be reported via notifications.

## Observability & Monitoring
- GCS access logs enabled for auditing.
- Versioned objects allow rollback to previous state.

## Non-Goals
- No backend APIs or dynamic compute.
- No authentication or user management.
- No database or server-side processing.

## Deployment Notes
- All static assets (`css`, `js`, `images`) deployed to GCS.
- CI/CD workflow ensures automated, secure deployment.
