Action to detect if any open Dependabot alerts are in the list of CISA KEV CVEs and fail the workflow.

 :warning: WARNING: THIS WILL MAKE DEPENDABOT ALERT DATA VISIBLE TO ANYONE WITH REPOSITORY READ ACCESS

```yml
name: 'Dependabot KEV Action'
on: [push]

jobs:
  dependabot-kev-action:
    name: 'CISA KEV Compliance Check'
    runs-on: ubuntu-latest
    steps:
      - name: 'KEV Policy'
        uses: felickz/dependabot-kev-action@main
        env:
            GITHUB_TOKEN: ${{ secrets.DEPENDABOT_KEV_GITHUB_TOKEN }}
```

## Required Credentials
* [GITHUB_TOKEN](https://docs.github.com/en/actions/security-guides/automatic-token-authentication#permissions-for-the-github_token) 
   * Classic Tokens
      *  repo scope or security_events scope. For public repositories, you may instead use the public_repo scope.
   * Fine-grained personal access token permissions
      * Read-Only - [Dependabot Alerts](https://docs.github.com/en/rest/overview/permissions-required-for-fine-grained-personal-access-tokens?apiVersion=2022-11-28#vulnerability-alerts)

