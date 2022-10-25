# 🔨 Hands-on: My first workflow

In this hands-on lab your will create your first GitHub Actions Workflow and learn how you can use Actions to automate tasks in your software development lifecycle. If you like more background information, please refer to the [GitHub Actions](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions) pages on GitHub Docs. Good luck! 👍

This hands on lab consists of the following steps:
- [Creating a repository](#creating-a-repository)
- [Creating the workflow](#creating-the-workflow)
- [Viewing your workflow results](#viewing-your-workflow-results)

## Creating a repository

Go to [Code](/../../) tab of this repository and click `Use this template`:

<img width="400" alt="2022-09-18_11-24-58" src="https://user-images.githubusercontent.com/5276337/190895393-6fa0fad9-e05c-4fea-8126-a291b087d663.png">

Select your GitHub user as the owner and name the repository. Leave the repo public to have unlimited action minutes: 

<img width="400" alt="2022-09-18_11-25-57" src="https://user-images.githubusercontent.com/5276337/190895398-751a1ec9-c1cf-497f-beb7-a6b53d4d911e.png">

Continue now in the new repository.

## Creating the workflow

Go to **Actions** | [New Workflow](/../../actions/new) and click on [set up a workflow yourself](/../../new/main?filename=.github%2Fworkflows%2Fmain.yml&workflow_template=blank).

1. Rename the file `main.yml` in the `.github/workflows` directory to `github-actions-demo.yml`.
<img width="400" alt="image" src="https://user-images.githubusercontent.com/5276337/174096754-4e2d7219-9caf-42e8-bfd9-c190762886d3.png">

2. Remove the template content - we want to create the workflow from scratch.
3. Click <kbd>Ctrl</kbd>+<kbd>Space</kbd> and select name as the first element:

<img width="400" alt="image" src="https://user-images.githubusercontent.com/5276337/174097468-8be92e37-7948-4895-b5ed-20a22c5773bc.png">

4. Set the workflow name to `GitHub Actions Demo`:

```YAML
name: GitHub Actions Demo
```

5. Add the triggers to the worklow with the help of <kbd>Ctrl</kbd>+<kbd>Space</kbd> and the documentation. We want the workflow to trigger:
  - on every push to the `main` branch, but not when there are changes to files in the `.github` folder.
  - on every pull request with `main` as the base branch
  - Every sunday at 6:15 UTC
  - Manually

<details>
  <summary>Solution</summary>
  
```YAML
on:
  push:
    branches: [ main ]
    paths-ignore: [.github/**]
  pull_request:
    branches: [ main ]
  schedule:
    - cron: '15 6 * * 0'
  workflow_dispatch:
```
  
</details>

6. Create a job `Build` that runs on the latest Ubuntu image on GitHub hosted runners. Check the documentation of the [virtual environments](https://github.com/actions/virtual-environments/) what label to use and what version it is. The job should do the following things:
  - Output the name of the event that triggered the workflow
  - Output the name of the branch that the repository is currently referencing
  - List all files in the repository 

<details>
  <summary>Solution</summary>
  
```YAML
jobs:
  Build:
    runs-on: ubuntu-latest
    steps:
      - run: |
          echo "🎉 The job was triggered by event: ${{ github.event_name }}"
          echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ."
        
      - uses: actions/checkout@v3.0.2

      - name: List files in the repository
        run: |
          echo "The repository ${{ github.repository }} contains the following files:"
          tree
```
  
</details>

7. Commit the workflow file - and trigger the workflow manually. It should not run automatically if your path filter works. Got to [Action](/../../Actions),  select [GitHub Actions Demo](/../../actions/workflows/github-actions-demo.yml) and `Run workflow`: 

<img width="600" alt="image" src="https://user-images.githubusercontent.com/5276337/174105162-19f33fd1-8533-4860-9279-88fabec84451.png">


## Viewing your workflow results

1. Click on your workflow run:

<img width="600" alt="image" src="https://user-images.githubusercontent.com/5276337/174105747-0e205e0d-37cc-464c-905b-5b29be74fc75.png">
 
2. Click on the job 'Build':

<img width="400" alt="image" src="https://user-images.githubusercontent.com/5276337/174105990-a1c204c6-fb7d-44a4-9343-6982899edb25.png">

3. Expand `Set up job` and note the log woth line number (line numbers are links). Check the information about the virtual environment and included software:

<img width="600" alt="image" src="https://user-images.githubusercontent.com/5276337/174106759-c2a8f933-74cf-42a4-899b-b29dc67eccd7.png">

4. Expand your jobs and check that the output was correct.

<img width="400" alt="image" src="https://user-images.githubusercontent.com/5276337/174107136-af9187c1-dbee-4109-9ddc-f2abd4830282.png">

5. Verify you other triggers by modifying the [README.md](README.md) file:
  - Modify and commit: triggers build (`push`)
  - Modify and add `[skip ci]` (not triggering the workflow):  
  <img width="350" alt="image" src="https://user-images.githubusercontent.com/5276337/174110845-93d4a38a-9c8a-4336-9b6a-9089ea9a1cfd.png"> 
  
  - Modify and create pull request (trigger: `pull_request`)

## Summary

In this hands-on you've learned to create you first workflow with triggers, jobs, steps, and expressions. Next you will write your [first GitHub Action](06-My-first-action.md).
