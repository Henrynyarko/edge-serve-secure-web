# EdgeServe Secure Web Platform – Architecture

## Traffic Flow
Users → HTTPS Load Balancer (CDN) → Private GCS Bucket
│
└─ Logging & Monitoring

- Users access content via HTTPS endpoint.
- CDN caches static content globally for performance and reduces latency.
- Load Balancer routes traffic to nearest edge location.
- GCS bucket remains private; only accessed via IAM roles.

## Scalability & Global Performance
- CDN allows edge caching for global users.
- Load Balancer ensures high availability and failover across regions.
- Future enhancement: deploy multi-region buckets for ultra-low latency.
- Versioning ensures safe rollback in case of content updates.

## Security Decisions
- Cloud Storage bucket is private.
- Public access disabled.
- HTTPS enforced via managed certificates.
- CDN shields origin from direct access.
- Deployment uses service account with minimal permissions.
- Secrets stored securely in GitHub Actions (`GCP_SA_KEY` & `GCP_PROJECT_ID`).

## CI/CD Pipeline
- GitHub main branch push triggers workflow.
- GitHub Actions deploys static content to GCS bucket.
- Deployment verified by listing bucket contents.
- Failures can trigger notifications.

## Observability & Monitoring
- GCS access logs enabled.
- Versioned objects allow rollback.
- Optional: Cloud Monitoring dashboards for latency, errors, and availability.

## Non-Goals
- No backend APIs or dynamic compute.
- No authentication or user management.
- No database or server-side processing.
