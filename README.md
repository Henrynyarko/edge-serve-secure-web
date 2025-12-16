# EdgeServe Secure Web Platform

**Production-grade static delivery built with security, performance, and operational clarity.**

## What This Platform Demonstrates
- Secure static hosting with private cloud storage
- Global CDN-backed delivery
- HTTPS-only access
- Automated CI/CD deployment
- Operational visibility and logging

## Architecture Overview
Users → Cloud CDN (HTTPS) → Load Balancer → Private GCS Bucket
                                          │
                                          └─ Logging & Monitoring

## Security Posture
- Bucket is private; access via IAM only
- All traffic encrypted in transit (HTTPS)
- Versioning enabled for all objects
- Secrets stored securely in GitHub Actions

## Deployment / CI-CD
- GitHub Actions workflow deploys `site/` to GCS
- Automatic sync on push to `main`
- Deployment verified via bucket listing
- Notifications on failure (optional)

## Operational Observability
- GCS access logs enabled
- Versioned objects for rollback
- Optional: Cloud Monitoring dashboards

## Quick Demo
URL: `https://storage.googleapis.com/edge-serve-secure-web-prod/index.html`

