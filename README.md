# CI/CD Pipeline: GitHub Actions + AWS S3 + CloudFront

Automated deployment pipeline that deploys a static website to AWS S3 and invalidates the CloudFront cache on every push to `main`.

## Live Deployment

This pipeline deploys to: **[aws-static-website](https://github.com/joegreenwoodtech/aws-static-website)** — view the live site at [d3uwqyk78lbrx7.cloudfront.net](https://d3uwqyk78lbrx7.cloudfront.net).

## Architecture

`Push to main → GitHub Actions Runner → AWS S3 (sync) → CloudFront (invalidate) → Live Site`

Full deployment completes in under 15 seconds.

## Pipeline Steps

1. **Checkout** — Runner pulls latest code from the repository
2. **Configure AWS credentials** — Authenticates using GitHub Secrets
3. **Sync to S3** — Uploads changed files, removes deleted files
4. **Invalidate CloudFront** — Clears CDN cache so visitors see new content

## AWS Services Used

- **S3** — Static file hosting
- **CloudFront** — Global CDN for HTTPS delivery
- **IAM** — Least-privilege service account for pipeline authentication

## Security

- AWS credentials stored as GitHub Secrets — never in code
- IAM user scoped to only S3 and CloudFront permissions
- No console access for the deployment user

## Key Files

- `.github/workflows/deploy.yml` — Pipeline definition
- `src/` — Website source files deployed to S3

## Related Projects

Part of a four-project AWS portfolio:

- 🚀 **[aws-cicd-pipeline](https://github.com/joegreenwoodtech/aws-cicd-pipeline)** *(this repo)* — GitHub Actions automation
- 📦 **[aws-static-website](https://github.com/joegreenwoodtech/aws-static-website)** — S3 + CloudFront static hosting (this pipeline's deployment target)
- 🌐 **[aws-ec2-rds-webapp](https://github.com/joegreenwoodtech/aws-ec2-rds-webapp)** — 3-tier web application on EC2 + RDS
- 🏗️ **[terraform-vpc-ec2](https://github.com/joegreenwoodtech/terraform-vpc-ec2)** — Reusable VPC + EC2 module in Terraform

## Author

**Joe Greenwood**
AWS Cloud Practitioner
[GitHub](https://github.com/joegreenwoodtech)
