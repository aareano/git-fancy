# git-fancy

How to be fancy with git.

##### Table of Contents

<!-- MarkdownTOC autolink="true" -->

- [Stage whitespace changes](#stage-whitespace-changes)
- [Add changes to previous commit](#add-changes-to-previous-commit)

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
