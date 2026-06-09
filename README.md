# glab-groups-small

Thin GitHub Actions wrapper for the mixed small-organization mirror set.

## Scope

- Loads `gh-actions-cfg/glab-groups-small`
- Calls the reusable workflow in `glab-groups-shared@mcr/main`
- Uses the BWS target PAT secret `GL_PAT_GROUP_SMALL_SVC`
- Uses the shared GitHub App secrets `GH_ORG_READ_APP_ID` and
  `GH_ORG_READ_APP_PEM` for GitHub-source discovery and clone auth
- Mirrors the configured GitHub, GitLab, and cgit sources into managed target
  namespaces beneath `glab-forks`
- Runs deterministic mirror batch shards with five jobs max in parallel
- Schedules at minute 5 of hours 2, 8, 14, and 20 UTC
- Publishes discovery, plan, report, CSV, JSON, and Parquet artifacts for each run

## Validation

```sh
python3 -m unittest discover -s tests
```
