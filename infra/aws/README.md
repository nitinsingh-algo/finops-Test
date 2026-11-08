# AWS deploy plan for `finops-test`

Target: **ECS Fargate + ALB**
Repository: `nitinsingh-algo/finops-Test`

## Make it live

1. Create a GitHub Actions secret `AWS_ROLE_ARN` from `terraform output github_actions_role_arn`.
2. Set repository variable `AWS_REGION`.
3. Merge `.github/workflows/deploy.yml` and `infra/aws/` (this apply step wrote them into the isolated clone).
4. First apply can also be local: `cd infra/aws && terraform init && terraform apply`.
5. The live URL is `terraform output live_url` after apply.

OIDC is used so long-lived AWS keys never go in the repo.
