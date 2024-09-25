---
title: Git
name: git
date: 2024-09-08
draft: false
tags:
  - git
share: "true"
---

![](/img/git-2.png)

# GIT CHEAT SHEET
## CREATE
- Clone an existing repository:
  ```bash
  $ git clone ssh://user@domain.com/repo.git
  ```
- Create a new local repository:
  ```bash
  $ git init
  ```

## LOCAL CHANGES
- Changed files in your working directory:
  ```bash
  $ git status
  ```
- Changes to tracked files:
  ```bash
  $ git diff
  ```
- Add all current changes to the next commit:
  ```bash
  $ git add .
  ```
- Add some changes in `<file>` to the next commit:
  ```bash
  $ git add -p <file>
  ```
- Commit all local changes in tracked files:
  ```bash
  $ git commit -a
  ```
- Commit previously staged changes:
  ```bash
  $ git commit
  ```
- Change the last commit (do not amend published commits!):
  ```bash
  $ git commit --amend
  ```

## COMMIT HISTORY
- Show all commits, starting with the newest:
  ```bash
  $ git log
  ```
- Show changes over time for a specific file:
  ```bash
  $ git log -p <file>
  ```
- Who changed what and when in `<file>`:
  ```bash
  $ git blame <file>
  ```

## BRANCHES & TAGS
- List all existing branches:
  ```bash
  $ git branch -av
  ```
- Switch HEAD branch:
  ```bash
  $ git switch <branch>
  ```
- Create a new branch based on your current HEAD:
  ```bash
  $ git branch <new-branch>
  ```
- Create a new tracking branch based on a remote branch:
  ```bash
  $ git checkout --track <remote/branch>
  ```
- Delete a local branch:
  ```bash
  $ git branch -d <branch>
  ```
- Mark the current commit with a tag:
  ```bash
  $ git tag <tag-name>
  ```

## UPDATE & PUBLISH
- List all currently configured remotes:
  ```bash
  $ git remote -v
  ```
- Show information about a remote:
  ```bash
  $ git remote show <remote>
  ```
- Add new remote repository, named `<remote>`:
  ```bash
  $ git remote add <shortname> <url>
  ```
- Download all changes from `<remote>`, but don't integrate into HEAD:
  ```bash
  $ git fetch <remote>
  ```
- Download changes and directly merge/integrate into HEAD:
  ```bash
  $ git pull <remote> <branch>
  ```
- Publish local changes on a remote:
  ```bash
  $ git push <remote> <branch>
  ```
- Delete a branch on the remote:
  ```bash
  $ git push <remote> --delete <branch>
  ```
- Publish your tags:
  ```bash
  $ git push --tags
  ```

## MERGE & REBASE
- Merge `<branch>` into your current HEAD:
  ```bash
  $ git merge <branch>
  ```
- Rebase your current HEAD onto `<branch>` (do not rebase published commits!):
  ```bash
  $ git rebase <branch>
  ```
- Abort a rebase:
  ```bash
  $ git rebase --abort
  ```
- Continue a rebase after resolving conflicts:
  ```bash
  $ git rebase --continue
  ```
- Use your configured merge tool to solve conflicts:
  ```bash
  $ git mergetool
  ```
- Use your editor to manually solve conflicts and (after resolving) mark file as resolved:
  ```bash
  $ git add <resolved-file>
  $ git rm <resolved-file>
  ```

## UNDO
- Discard all local changes in your working directory:
  ```bash
  $ git reset --hard HEAD
  ```
- Discard local changes in a specific file:
  ```bash
  $ git checkout HEAD <file>
  ```
- Revert a commit (by producing a new commit with contrary changes):
  ```bash
  $ git revert <commit>
  ```
- Reset your HEAD pointer to a previous commit...and discard all changes since then:
  ```bash
  $ git reset --hard <commit>
  ```
- ...and preserve all changes as unstaged changes:
  ```bash
  $ git reset <commit>
  ```
- ...and preserve uncommitted local changes:
  ```bash
  $ git reset --keep <commit>
  ```
