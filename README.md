Squashing Commits
=================

A Github Action to squash the last x commits, in your own repo and to the desired branch.

Table of contents
=================

*[Prerequisites](#prerequisites) \
*[Usage](#usage)

## Prerequisites

There are a couple of inputs needed to be considered before using this GA.
The user should specify the following parameters:
1.  Number of commits (can be any value >=2). This means that the last i.e 2 commits will be merged into one.
2. User_email -> This is needed to configure GIT
3. User_name -> This is needed to configure GIT
4. Repo_name -> The repository where you need to squash commits. It should be in the format of organization/repo i.e finderly/web
5. Target branch -> This parameter defines the branch we want to target to squash the commits.

## Usage

uses: finderly/squashing-commits@v1 \
with: \
   &nbsp;&nbsp; no_commits: 2 \
   &nbsp;&nbsp; user_email: "tools+github-shpock-ci@shpock.com" \
   &nbsp;&nbsp; user_name: "shpock-ci" \
   &nbsp;&nbsp; target_branch: "staging" \
   &nbsp;&nbsp; repo_name: "finderly/web" \
   &nbsp;&nbsp; github_token: ${GITHUB_TOKEN}