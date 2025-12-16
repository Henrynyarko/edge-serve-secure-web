# EdgeServe Secure Web Platform – Architecture

## Traffic Flow
User → HTTPS Load Balancer (CDN) → Private GCS Bucket

## Security Decisions
- Cloud Storage bucket is private
- Public access is disabled
- HTTPS enforced via managed certificates
- CDN shields origin from direct access

## Non-Goals
- No backend APIs
- No authentication
- No dynamic compute
