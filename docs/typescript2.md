---
id: typescript2
title: Functions, Objects, etc
---

## Функции

Про функции можно прочесть [тут](https://www.typescriptlang.org/docs/handbook/functions.html).
Стоит обратить внимание на следующий кейс:

```typescript
let myFunc: (firstArg: string) => void;

function oldFunc(name: string): void {
    alert('hey');
};

myFunc = oldFunc;
```

## Объекты

Типизация объектов довольно простая:

```typescript
let user: { name: string, age: number} = {
    name: 'David',
    age: 23
}
```

При добавлении нового поля в объекте следует добавить поле в тип объекта во избежании ошибки