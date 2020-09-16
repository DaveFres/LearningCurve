---
id: git
title: Git
---

# Git

## Squash commits

* `git rebase -i HEAD~2`
* `git push origin +master`

## Склонировать код из пулл реквеста \(ветку\)

```text
git checkout -t origin/<branch_name>
```

## Удалить ветку

* `git branch -d branch_name` - локально
* `git branch -D branch_name`

## Задать имя и почту в локальном конфиге можно вот так:

* `git config --local user.name "John Doe"`
* `git config --local user.email johndoe@example.com`

## Замержить ветку от ветки, после того, как первую ветку замержили в master

`git rebase --onto master feature_branch dependent_feature`

Полный ответ смотри [тут](https://stackoverflow.com/questions/22593087/merging-a-branch-of-a-branch-after-first-branch-is-squashed-when-merged-to-maste)

