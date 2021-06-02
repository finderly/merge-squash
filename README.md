Squashing Commits
=================

A Github Action to squash the last x commits, in your own repo and to the desired branch.

Table of contents
=================

* [Prerequisites](#prerequisites)
* [Usage](#usage)

## Prerequisites

There are a couple of inputs needed to be considered before using this GA.
The user should specify the following parameters:
1. `no_commits`: Number of commits (can be any value >=2). This means that the last i.e 2 commits will be merged into one.
2. `user_email`: This is needed to configure GIT
3. `user_name`: This is needed to configure GIT
4. `repo_name`: The repository where you need to squash commits. It should be in the format of organization/repo i.e finderly/web
5. `target_branch`: This parameter defines the branch we want to target to squash the commits.

## Usage

```yaml
uses: finderly/squashing-commits@v1 \
with: \
  no_commits: 2 \
  user_email: "tools+github-shpock-ci@shpock.com" \
  user_name: "shpock-ci" \
  target_branch: "staging" \
  repo_name: "finderly/web" \
  github_token: ${{ github.token }}
```
