# git-fancy

How to be fancy with git. I'll add to this as I encounter fanciness.

##### Table of Contents

<!-- MarkdownTOC autolink="true" -->

- [Stage whitespace changes](#stage-whitespace-changes)
- [Add changes to previous commit](#add-changes-to-previous-commit)
- [Stage changes one piece at a time](#stage-changes-one-piece-at-a-time)
- [Delete stale remote-tracking branches](#delete-stale-remote-tracking-branches)
- [Move your changes on `master` to another branch](#move-your-changes-on-master-to-another-branch)

<!-- /MarkdownTOC -->

## Stage whitespace changes

```bash
$ git add -A
$ git diff --cached -w | git apply --cached -R
```

## Add changes to previous commit

```bash
$ git commit -a --amend --no-edit
```

## Stage changes one piece at a time

```bash
$ git add -p
```

## Delete stale remote-tracking branches

Deletes all stale remote-tracking branches under `<name>`. These stale
branches have already been removed from the remote repository referenced by
`<name>`, but are still locally available in `remotes/<name>`.

```bash
$ git remote prune <name> [--dry-run]
```

## Move your changes on `master` to another branch

If you've pushed all your code onto the `master` branch for whatever reason,
but now you want to move it to a different branch (presumably to open a pull
request against `master`). Here's what you do:

- Case 1, you want master to be empty when you open your PR:

```bash
$ git checkout master
$ git checkout -b my-feature-branch
$ git branch -D master
$ git checkout --orphan master
$ git rm -rf .
$ git commit --allow-empty -m "empty base commit"
$ git checkout my-feature-branch
$ git rebase master
$ git push -f origin master
$ git push origin my-feature-branch
```

- Case 2: you want master to be at a particular git hash when you open your PR:

```bash
$ git checkout master
$ git checkout -b my-feature-branch
$ git branch -D master
$ git checkout my-git-hash-or-branch-name
$ git checkout -b master
$ git checkout my-feature-branch
$ git rebase master
$ git push -f origin master
$ git push origin my-feature-branch
```

TODO: You can also accomplish this with cherry-picking and reseting.
