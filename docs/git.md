---
id: git
title: Git
---

## Squash commits

* ```git rebase -i HEAD~2```
* ```git push origin +master```

## Склонировать код из пулл реквеста (ветку)

```cli
git checkout -t origin/rkupov.VIDEOUI-9760.related-right
```

## Удалить ветку

* ```git branch -d branch_name``` - локально
* ```git branch -D branch_name```

## Задать имя и почту в локальном конфиге можно вот так:

* ```git config --local user.name "John Doe"```
* ```git config --local user.email johndoe@example.com```
