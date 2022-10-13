# October 2022 MICA Challenge

## Part one: basics

The goal of this week's exercise is to

- Fork this repo to your own GitHub account
- Create a branch for your change with a name of your choice
- Make the change: add a textfile to the repo with your name as file title and your email as content
- Add, commit & push those changes back to GitHub (in the right branch)
- Create a pull request towards the original repo to have your file included

## Part two: GitHub Actions

The goal of the GitHub Actions exercise is to

- Add a workflow to your fork of this repo
- The workflow should run when you push to a branch of your choice (can be main/master)
- The worklflow should have two jobs
    - The jobs should run on Ubuntu runners
    - The jobs should be dependent on each other
- In your steps, use at least one script and an action
- Test the workflow by committing to the chosen branch
- Optional:
    - make the workflow manually executable from the GitHub website
    - in the script, write your GitHub id to standard output (see [Default Environment Variables](https://docs.github.com/en/actions/learn-github-actions/environment-variables#default-environment-variables)) 


Tips:
- the script can be as simple as `echo Hello World`
- the action can be a checkout action or any other action; see [GitHub Marketplace](https://github.com/marketplace?type=actions) for inspiration


