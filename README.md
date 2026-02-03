# csv-import-pipeline

Serverless CSV ingestion pipeline built using AWS SAM and deployed automatically with GitHub Actions CI/CD using secure OIDC authentication (no AWS keys).

---

## Overview

This project demonstrates real-world Cloud/DevOps engineering practices:

- Infrastructure as Code (AWS SAM / CloudFormation)
- CI/CD automation with GitHub Actions
- Keyless authentication using OIDC
- Least-privilege IAM
- Serverless architecture

Every push to `main` automatically deploys the stack to AWS.

---

## Architecture

GitHub Push
   ↓
GitHub Actions
   ↓
SAM Build
   ↓
CloudFormation Deploy
   ↓
Lambda updated automatically

---

## Project Structure

csv-import-pipeline/
│
├── template.yaml # Infrastructure definition
├── hello_world/ # Lambda source code
├── events/ # Sample test events
├── .github/workflows/
│ └── deploy.yml # CI/CD pipeline
└── README.md


---

## CI/CD

Deployments are fully automated.

Workflow:


##.github/workflows/deploy.yml

On every push:
1. Assume AWS role (OIDC)
2. Build with SAM
3. Deploy with CloudFormation

No manual console steps required.

---

## Local Development

### Build


#sam build


 Test locally

##sam local invoke HelloWorldFunction --event events/event.json

 Start local API

##sam local start-api

---

 Manual Deploy (optional)

##sam deploy --guided


---

## Security

- No stored AWS keys
- OIDC authentication only
- Temporary credentials
- Least-privilege IAM


##sam delete --stack-name csv-import-dev



Built a serverless CI/CD pipeline using AWS SAM and GitHub Actions with OIDC authentication to automatically deploy infrastructure on every commit.

