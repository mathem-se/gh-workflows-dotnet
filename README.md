# gh-workflows-dotnet
 
### Pull requests

Add the following file `.github/workflows/pull-request.yml` to your project with this content:

```yaml
name: Pull request
on: [pull_request]

jobs:
  PR:
    uses: mathem-se/gh-workflows-dotnet/.github/workflows/pr.yml@@main
    with:
      CHECK_IAM: false #if you don't want to check lint (defaults to true)
```

### Deploy to AWS with SAM

Add the following file `.github/workflows/deploy.yml` to your project with this content:

```yaml
name: Deploy to AWS
on:
  push:
    branches: [main, master, develop]

permissions:
  id-token: write
  contents: read

jobs:
  Deploy:
    uses: mathem-se/gh-workflows-dotnet/.github/workflows/deploy.yml@main
    with:
      domain: <repo name> #change value
      team: <team name> #change value
    secrets:
      AWS_CICD_ACCOUNT: ${{ secrets.AWS_CICD_ACCOUNT }}
      AWS_CICD_API_URL: ${{ secrets.AWS_CICD_API_URL }}
      AWS_CICD_API_REGION: ${{ secrets.AWS_CICD_API_REGION }}
```