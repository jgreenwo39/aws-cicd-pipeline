# CI/CD Pipeline: GitHub Actions + AWS S3 + CloudFront

Automated deployment pipeline that deploys a static website to AWS 
S3 and invalidates the CloudFront cache on every push to `main`.

## Architecture

## Pipeline Steps

1. **Checkout** - Runner pulls latest code from the repository
2. **Configure AWS credentials** - Authenticates using GitHub Secrets
3. **Sync to S3** - Uploads changed files, removes deleted files
4. **Invalidate CloudFront** - Clears CDN cache so visitors see new content

## AWS Services Used

- **S3** - Static file hosting
- **CloudFront** - Global CDN for HTTPS delivery
- **IAM** - Least-privilege service account for pipeline authentication

## Security

- AWS credentials stored as GitHub Secrets — never in code
- IAM user scoped to only S3 and CloudFront permissions
- No console access for the deployment user

## Key Files

- `.github/workflows/deploy.yml` — Pipeline definition
- `src/` — Website source files deployed to S3