# GitHub Actions demo

Sample workflow:

```yaml
name: Mica Challenge Workflow

on:
 workflow_dispatch:
 push:
   branches: [main]

env:
  SERVER: server001
  CLOUD: Azure

jobs:
  job1:
    runs-on: ubuntu-latest
    name: Job Number One
    timeout-minutes: 360 # default is 360
    env:
      MESSAGE: Variable available to all steps in the job
    steps:
      - uses: actions/checkout@v3
      - id: step1
        name: Say Hello
        env:
          USERNAME: Geert
        run: |
          echo Hello $USERNAME, welcome to $CLOUD
          cat README.md
      - name: Print env vars
        # see https://docs.github.com/en/actions/reference/environment-variables#default-environment-variables
        run: |
          echo GITHUB_WORKFLOW: $GITHUB_WORKFLOW
          echo GITHUB_RUN_ID: $GITHUB_RUN_ID
          echo GITHUB_REPOSITORY: $GITHUB_REPOSITORY
          echo GITHUB_EVENT_NAME: $GITHUB_EVENT_NAME
          echo GITHUB_WORKSPACE: $GITHUB_WORKSPACE
          echo GITHUB_SHA: $GITHUB_SHA
          echo GITHUB_REF: $GITHUB_REF
          echo GITHUB_ACTOR: $GITHUB_ACTOR
  job2:
    # no name; name will be job id job2
    runs-on: ubuntu-latest
    needs: job1
    steps:
      - name: Hello from Job 2
        run:  | 
          echo Hello from Job 2
  job3:
    name: Job with expression
    # use github context in the expression; further below use the env var
    # note that expressions are in ${{ }}
    if: ${{ github.actor == 'gbaeke'}}
    runs-on: ubuntu-latest
    steps:
      - name: Hello from job 3 with expression
        run: echo Hello $GITHUB_ACTOR
```