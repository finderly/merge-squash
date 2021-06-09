Merging & Squashing Commits
=================

A Github Action to merge & to squash the last x commits, in your own repository and to the desired branch.

Table of contents
=================

*[Prerequisites](#prerequisites) \
*[Usage](#usage) \
*[Merging & Squashing commits](#merging-and-squashing-commits)

## Prerequisites

There are a couple of inputs needed to be considered before using this GA.
The user should specify the following input parameters:
1. no_commits (can be any int >=2). This means that the last i.e 2 commits will be merged into one.
2. user_email -> This is needed to configure GIT
3. user_name -> This is needed to configure GIT
4. repo_name -> The repository where you need to squash commits. It should be in the format of organization/repo i.e finderly/web
5. from_branch -> This parameter defines the branch from which we want to merge.
6. target branch -> This parameter defines the branch we want to target to merge and squash commits.
7. github_token -> The personal access token to authenticate

# Usage
## Merging and Squashing commits 
**In this action, you can choose or combine between:** \

### Squash commits
```yaml
uses: finderly/merge-squash/squashing@v1.0.0
with:
  no_commits: 2
  user_email: "tools+github-shpock-ci@shpock.com"
  user_name: "shpock-ci"
  target_branch: "staging"
  repo_name: "finderly/web"
  github_token: ${{ github.token }}
```

### Sync branches

```yaml
name: Sync multiple branches
on:
  push:
    branches:
      - '*'
jobs:
  sync-branch:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master

      - name: Merge master -> staging
        uses: finderly/merge-squash@v1.0.0
        with:
          type: now
          from_branch: master
          target_branch: staging
          github_token: ${{ github.token }}

      - name: Merge current branch -> master
        uses: finderly/merge-squash@v1.0.0
        with:
          type: now
          target_branch: master
          github_token: ${{ github.token }}
```

### Squash and merge commits
```yaml
      - name: Merge master -> stagging
        uses: finderly/merge-squash@feature/adding-sq-merge
        with:
          type: now
          from_branch: master
          target_branch: staging
          github_token: ${{ github.token }}
      - name: Squashing commits
        uses: finderly/merge-squash/squashing@feature/adding-sq-merge
        with:
          target_branch: staging
          no_commits: 1
          user_email: "tools+github-shpock-ci@shpock.com"
          user_name: "shpock-ci"
          repo_name: "finderly/web"
          github_token: ${{ github.token }}
```