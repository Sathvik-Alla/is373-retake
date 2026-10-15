# is373-retake
IT373 Practical Test - Secure DigitalOcean Deployment and CI/CD


# IT373 Practical Test — Secure DigitalOcean Deployment and CI/CD

## Project Overview
This project demonstrates secure deployment of a Dockerized website to a DigitalOcean Ubuntu 24.04 server using GitHub Actions for automated CI/CD.

## Live Websites
- Production: https://is373-sathvik.duckdns.org
- QA: https://qa-is373-sathvik.duckdns.org

## GitHub Repository
https://github.com/Sathvik-Alla/is373-retake

## Technology Stack
- Ubuntu 24.04 LTS
- DigitalOcean Droplet
- Docker and Nginx
- GitHub Actions
- GitHub Container Registry (GHCR)
- Caddy reverse proxy
- DuckDNS
- HTTPS/TLS
- UFW firewall

## Security Configuration
- Non-root deployment user with sudo permissions
- SSH public-key authentication
- Root SSH login disabled
- SSH password authentication disabled
- UFW firewall enabled
- Only SSH, HTTP, and HTTPS ports allowed
- Deployment SSH private key stored in GitHub Actions Secrets
- Restricted passwordless sudo access for the deployment script
- Docker containers bound to localhost
- Automatic HTTPS through Caddy

## CI/CD Pipeline
The GitHub Actions workflow automatically builds a Docker image, publishes it to GHCR, and deploys it to the DigitalOcean server.

- Push to `qa`: deploy to QA
- Push to `main`: deploy to production

Deployment script: `/usr/local/sbin/it373-deploy`

Workflow file: `.github/workflows/deploy.yml`

## Deployment Environments
| Environment | Branch | Local Port | Version |
|---|---|---|---|
| Production | main | 8081 | 1.1 |
| QA | qa | 8082 | 1.1 |

## Testing and Verification
1. Successfully deployed the production website.
2. Successfully deployed the QA website.
3. Updated QA independently to Version 1.1.
4. Promoted the tested QA changes into production using a pull request.
5. Corrected the production environment label.
6. Verified both HTTPS websites.
7. Confirmed five successful GitHub Actions workflow runs.

## CI/CD Workflow History
- Run #1: Initial production deployment
- Run #2: Initial QA deployment
- Run #3: QA Version 1.1 update
- Run #4: QA-to-production promotion
- Run #5: Production environment label correction

## Conclusion
The project demonstrates secure server configuration, Docker containerization, automated CI/CD, separate QA and production deployments, and promotion of tested changes into production.
