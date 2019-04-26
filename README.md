# git-fancy

How to be fancy with git. I'll add to this as I encounter fanciness.

##### Table of Contents

<!-- MarkdownTOC autolink="true" -->

- [Stage whitespace changes](#stage-whitespace-changes)
- [Add changes to previous commit](#add-changes-to-previous-commit)
- [Stage changes one piece at a time](#stage-changes-one-piece-at-a-time)
- [Delete stale remote-tracking branches](#delete-stale-remote-tracking-branches)

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
