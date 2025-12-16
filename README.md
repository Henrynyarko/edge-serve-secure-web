# EdgeServe Secure Web Platform

**Production-grade static delivery built with security, performance, and operational clarity.**

## What This Platform Demonstrates
- Secure static hosting with private cloud storage
- HTTPS-only access
- Automated CI/CD deployment via GitHub Actions
- Operational visibility and logging
- Versioned object storage for safe rollback

## Architecture Overview
Users → HTTPS GCS URL → Private GCS Bucket

- Users access content via HTTPS endpoint.
- GCS bucket is private; only accessible via IAM roles.
- Error pages served via `error.html`.
- Versioning enabled on bucket for safe rollback.
- Conceptually ready for CDN and Load Balancer integration.

## Security Posture
- Bucket is private; access granted via IAM only.
- All traffic encrypted in transit (HTTPS).
- Versioning enabled for all objects.
- Deployment uses a service account with minimal permissions.
- Secrets stored securely in GitHub Actions (`GCP_SA_KEY` & `GCP_PROJECT_ID`).

## Deployment / CI-CD
- GitHub Actions workflow deploys `site/` folder to GCS.
- Automatic sync triggered on push to `main` branch.
- Deployment verified by listing bucket contents.
- Optional: notifications on failure.

## Operational Observability
- GCS access logs enabled for auditing.
- Versioned objects allow rollback to previous state.
- Optional: Cloud Monitoring dashboards for metrics.

## Quick Demo
![EdgeServe Demo](site/assets/images/demo.png)
URL: `https://storage.googleapis.com/edge-serve-secure-web-prod/index.html`

## Next Steps / Enhancements
- Integrate Cloud CDN or Load Balancer for global performance.
- Add Cloud Monitoring dashboards for latency/error tracking.
- Configure automated notifications for deployment status.
