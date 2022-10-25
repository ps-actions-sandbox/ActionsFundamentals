# 🔨 Hands-on: Review code 

In this hands-on lab you will learn how to perform reviews of code, make suggestions, and approve pull requests. The module consists of the following parts:
- [Open pull the request and add a single comment](#open-pull-the-request-and-add-a-single-comment)
- [Incorporate the changes and set PR to autocomplete](#incorporate-the-changes-and-set-pr-to-autocomplete)
- [Performing a review](#performing-a-review)
- [Reconciling your local repository](#reconciling-your-local-repository)

> **Note**:  
> ⚡ In this this exercise you have to work together with the same partner that you added as a reviewer to your PR in 
> [Collaborate on code](03-Collaborate-on-code.md). The first part is in the repo of your partner. The second one in 
> your own after the parter completed that aprt. The third one again in the repo of your partner. Make sure that you 
> always pick the right repository!

## Open pull the request and add a single comment

> **Note**:  
> ⚡ This part is done in the repo of your execise partner!

1. Open the PR of your partner - you should have received a notification. 
2. Go to the `Filles changed` tab and click line 78. Drag the mouse to line 79 - this will select two lines. 
3. Add a `suggestion` and increase the decrement to 0.006:

<img width="800" alt="image" src="https://user-images.githubusercontent.com/5276337/174055904-2816e258-a324-47ae-abb2-dd8a59c7d9d5.png">

## Incorporate the changes and set PR to autocomplete

> **Note**:  
> ⚡ This part is done in YOUR repo!

1. Go back to your repo and wait for your partner to complete the comment with the suggestion.
2. Open `Commit suggestion` and verify the commit message title and body. Click `Commit changes`:

<img width="600" alt="image" src="https://user-images.githubusercontent.com/5276337/174057058-c7f97db3-2527-4e8d-9062-77cea20a106c.png">

3. Note that the commit shows up under `commit` tab and contains your partner as a co-commiter:

<img width="212" alt="image" src="https://user-images.githubusercontent.com/5276337/174057445-eac26b99-14f3-4c7c-8a84-ac2225339249.png">

4. Now set `Enable auto-merge` to `Squash and merge` and enable it: 

<img width="600" alt="image" src="https://user-images.githubusercontent.com/5276337/174057550-cb5e5978-941b-4a48-b44b-cf46e58ae1f2.png">

5. Verify the commit message with all changes and the co-author information and confirm the auto-merge:

<img width="600" alt="image" src="https://user-images.githubusercontent.com/5276337/174057638-6398560f-9f8d-4312-80ab-81e9e2f022d6.png">

6. Check that **auto-merge** is enabled and head over to the repo of your partner:

<img width="600" alt="image" src="https://user-images.githubusercontent.com/5276337/174057729-fb6a4294-665c-4278-897c-fc4b152d578a.png">

## Performing a review

> **Note**:  
> ⚡ This part is done in the repo of your execise partner!

1. Open the PR again and note that the changes you had suggested are now visible. Add a new comment and this time start a review:

<img width="600" alt="image" src="https://user-images.githubusercontent.com/5276337/174058013-e31b2cae-fdef-477c-b8a1-79c69b1e8607.png">

2. You could add multiple comments and the indicator on the top of the PR will increase. If ready, finish the review and approve it:

<img width="400" alt="image" src="https://user-images.githubusercontent.com/5276337/174058197-375f9378-c7b1-442f-942b-1ee3fca21159.png">

3. Note that the PR gets automatically merged after you have approved the PR. Also the branch was deleted automatically. 

<img width="350" alt="image" src="https://user-images.githubusercontent.com/5276337/174058328-3e6a97be-4658-4d26-98b3-f5d4ed728342.png">


## Reconciling your local repository

Verify that your own pull request is also merged. Go back to your command line and clean up your local repo:

1. Switch to the main branch: 

```
git switch main
```

2. Pull the changes with `--prune` or `-p` to delete branches do not longer exist on the remote:

```
git pull --prune
```

The result should look like this: 

```console
$ git switch main
> Switched to branch 'main'
> Your branch is behind 'origin/main' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)
  
$ pull --prune
> From https://github.com/wulfland/GitHubBootcamp
>  - [deleted]         (none)     -> origin/users/wulfland/1_fix-game
> remote: Enumerating objects: 20, done.
> remote: Counting objects: 100% (20/20), done.
> remote: Compressing objects: 100% (14/14), done.
> remote: Total 14 (delta 10), reused 0 (delta 0), pack-reused 0
> Unpacking objects: 100% (14/14), 3.15 KiB | 247.00 KiB/s, done.
>    bbc4b93..57023b8  main       -> origin/main
> Updating d7076e3..57023b8
> Fast-forward
 docs/index.html               |  2 +-
 1 files changed, 1 insertions(+), 1 deletions(-)
```

3. Check that the issue was automatically closed when the PR was merged
4. Check that the bug was fixed and your game is working

## Summary

In this hands-on lab you've learned how to perform code reviews, make and incorporate suggestions, and approve pull requests.

You can now continue with [CI/CD and Automation](../README.md#part-4--cicd-and-automation).


