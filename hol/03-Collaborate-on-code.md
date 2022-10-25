# 🔨 Hands-on: Collaborate on code

In this hands-on lab you will learn how to collaborate on code using pull-requests. The exercise consists of the following parts:
- [Setting everything up](#setting-everything-up)
- [Working with codeowners](#working-with-codeowners)
- [Protecting the main branch](#protecting-the-main-branch)
- [Working locally](#working-locally)
- [Creating a pull request](#creating-a-pull-request)

## Setting everything up

### Enable GitHub Pages

> If you have enabled pages in the previous exercise you just have to change the folder from `/(root)` to `/docs`.

1. Enable GitHub Pages in [Settings | Pages](/../../settings/pages) for the `/docs` folder and the `main` branch. Open the pages URL and verify that the tetris game is visible but too slow.

### Review the issue to fix

1. Read the issue [🐞 Fix game](/../../issues/1) and see the instructions how to fix the game.

### Invite your co-worker and give them write permissions to your repo

Invite your co-worker and give them write permissions to your repo

<details><summary>Solution</summary>
  
1. Go to [Collaborators](/../../settings/access) and click `Add people`. Search for your partner and add them to your repo.

<img width="250" alt="image" src="https://user-images.githubusercontent.com/5276337/174008450-86231b45-6328-483e-a09d-3148a38d7f9d.png">

2. Your partner will receive a notification - but you can also copy the link for the invitation and send it directly.

<img width="500" alt="image" src="https://user-images.githubusercontent.com/5276337/174008524-d47ee1cd-4281-42e0-a38a-c3c13ee6f125.png">

3. Your partner has to accept the invitation.

<img width="250" alt="image" src="https://user-images.githubusercontent.com/5276337/174008624-58dbdbad-9a92-411c-a80c-f85d537b5696.png">

</details>

### Check your local git config

1. Check your local git config with `git config --global user.name` and `git config --global user.email`. 
2. If you don't want to expose your email on GitHub get the email from [Email settings](https://github.com/settings/emails) and configure name and email accordingly:

```console
git config --global user.name "<your name>"
git config --global user.email "<github-user-id>+<github-user-name>@users.noreply.github.com"
```

3. On windows you should also configure autocrlf: `git config --global core.autocrlf true`. This is normally done when you execute the git setup.

> Memory Tip: autocrlf stands for auto carriage return line feed.

## Working with codeowners

Make yourself the global `CODEOWNER` for all files - and your partner for all files in the folder `docs/`.

<details><summary>Solution</summary>
  
1. Create a [New file](/../../new/main) `CODEOWNERS`.
2. Add yourself as the global owner. Add this ti line 1: 
```
* @<your-github-username>
```
4. Make your partner the owner of the file in the `docs/` folder. Add this to line 2: 
```
docs/ @<your-partners-user-name>
```
5. Commit the file directly to `main`.

</details>

## Protecting the main branch

Protect the `main` branch and enforce reviews from code owners.
  
<details><summary>Solution</summary>
  
1. Create a new [Branch Protection Rule](/../../settings/branch_protection_rules/new)
2. Set the **Branch name pattern** to `main`.
3. 
  
<img width="412" alt="image" src="https://user-images.githubusercontent.com/5276337/174016555-804d5210-dfba-4f00-983a-1cb6e4de0ba0.png">

4. Check **Include administrators**
5. Click create

</details>
  
## Working locally

### Clone the repository

1. Copy the URL to the repository from [Code](/../../) to the clipboard:
<img width="500" alt="image" src="https://user-images.githubusercontent.com/5276337/173845095-c4fdc522-135a-4de3-80fc-6fef95fa7aee.png">

2. Clone the  repository and change into the new folder:

  <details><summary>Solution</summary>

  ```console
  git clone <paste URL>
  cd GitHubBootcamp
  ```
  </details>
  
### Create a local branch

Create new local branch `users/<user-name>/<issue-id>_fix-game` and switch to it.

<details><summary>Solution</summary>

Create the branch and switch to it:
```console
git branch users/<user-name>/1_fix-game
git switch users/<user-name>/1_fix-game
```
Or switch to a new branch: 
  
```console
git switch -c users/<user-name>/<issue-id>_fix-game
``` 
</details>
  
### Do changes to the file
  
1. Modify line 78 in [docs/index.html](../docs/index.html#L78) and modify the values like indicated in [🐞 Fix game](/../../issues/1).
2. Add your file to the index:
  ```console
  git add docs/index.html
  ```
3. Commit your changes:
  ```console
  git commit
  ```
4. In your editor, enter a title for the commit in line 1. Title should be smaller then 50 characters and written in imperative. What will happen, when this commit is applied. For example:
  ```
  Fix timing in docs/index.html
  ```
5. After a blank line add the body. Make sure to break your lines at 70 characters. Add a reference to the issue with a keyord that laters closes the issue (for example closes, fixes, resolves):
  ```
  
This commit fixes the timing error in docs/index.html by setting 
correct start and min properties for the speed object.

This commit fixes #1
  ```
  Safe the file and close the editor.
6. Push your changes:
  ```console
  git push --set-upstream origin users/<user-name>/1_fix-game
  ```
  
## Creating a pull request 

Before creating the pull request, ensure that in [Settings](/../../settings) all options for pull requests are enabled:
  
<img width="412" alt="image" src="https://user-images.githubusercontent.com/5276337/174024187-495607be-b1ad-4416-8631-54ce4592d16f.png">

  
Now create a pull request in draft mode. If you have the [GitHub CLI](https://cli.github.com/) installed, you can do it directly from the command line:

```console
gh pr create --fill --draft
```

Otherwise go to the pull request tab and click `Conpare and pull request`:
<img width="550" alt="image" src="https://user-images.githubusercontent.com/5276337/174023923-33c02817-861a-4006-bddc-41e6dbe3e692.png">

Note that the title and body of the commit are automatically added to the PR and that the codeowner was added as a reviewer:
  
<img width="550" alt="image" src="https://user-images.githubusercontent.com/5276337/174024753-30041e90-ef8d-433e-bea5-0107a3488a83.png">
  
Create the PR. The issue will be automatically linked. The PR is still in `draft` mode and your partner is not notified, yet. Mark it as ready to enter the the phase and collaborate using reviews:
  
<img width="550" alt="image" src="https://user-images.githubusercontent.com/5276337/174026618-7de907d9-eb74-46a3-93e8-10b9a66f4fe4.png">

## Summary
  
In this hands-on lab you've learned how to protect your branch, use codeowners, work locally, and create a pull request. 
Please continue with [Review code](04-Review-code.md)
