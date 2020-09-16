---
id: typescript2
title: 'Functions, Objects, etc'
---

# typescript2

## Функции

Про функции можно прочесть [тут](https://www.typescriptlang.org/docs/handbook/functions.html). Стоит обратить внимание на следующий кейс:

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

## Классы

Типы свойств класса можно определить в самом классе:

```typescript
class User {
    name: string;
    age: number;
    nickName: string;

    constructor(name: string, age: number, nickName: string) {
        this.name = name;
        this.age = age;
        this.nickName = nickName;
    }
}
```

Ключевые слова **public**, **protected**, **private** и **readonly**

```typescript
class User {
    public name: string;
    private age: number = 20; // дефолтное значение
    protected nickName: string;
    readonly pass: number;

    constructor(name: string, age: number, nickName: string) {
        this.name = name;
        this.age = age;
        this.nickName = nickName;
        this.pass = pass;
    }
}

const nikita = new User('Nikita', 21, 'dev', 123);

nikita.name; // 'Nikita'
nikita.age;  // Prop 'age' is protected and only accssible within class 'User' and its subclasses
nikita.nickName; // Prop 'nickName' is private and only accssible within class 'User'
nikita.pass = 42; // Cannot assign to 'pass' because it is a read-only property
```

При инициализации дефолтного значения, добавлять инициализацию в сам конструктор не обязательно. Минимизировать количество строк кода в записи выше можно следующим образом:

```typescript
class User {

    constructor(
        public name: string,
        private age: number = 20, // дефолтное значение
        protected nickName: string,
        readonly pass: number
    ){}
}
```

## Свойства-акссесоры. get и set

Варианты получения доступа до приватного поля age:

```typescript
// Get access to private property
class User {

    private age: number = 20;

    constructor(public name: string) {}

    setAge(age: number) {
        this.age = age;
    }

    set myAge(age: number) {
        this.age = age;
    }
}

const samedi = new User('Samedi');

samedi.setAge(30); // 30
samedi.myAge = 31; // 31
```

