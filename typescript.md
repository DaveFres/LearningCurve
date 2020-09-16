---
id: typescript
title: Basic types
---

# Typescript

Тип **Array**:

```typescript
let list: number[] = [1, 2, 3];

let list: Array<number> = [1, 2, 3];
```

Тип **Tuple**:

```typescript
// Multiple line
let x: [string, number];
x = ['hello', 12];

// One line
let y: [string, number] = ['hey', 10];

// Error case
x = [10, 'hello']; // Type string is not assignable to type 'number'
```

**Вопрос**: Что делать, если на вход поступает массив неизвестной длинны и типов?

Использовать тип `any`:

```typescript
// Any type for array
let y: [any, any] = [1, 'hello'];
let z: Array<any> = ['goodbye', 10];
```

Тип **never**:

```typescript
// Never type
// Function return error
const msg = 'hello';
const error = (msg: string): never => {
    throw new Error(msg);
};

// Function infiniteLoop
const infiniteLoop = (): never => {
    while (true) {

    }
};
```

**Пользовательский тип**:

```typescript
type Name = string | undefined; // Custom type creation

let id: Name; // Apply custom type

id = '42'; // No error
id = 10; // Type 'number' is not assignable to type 'string'
```

Тип **enum**:

Удобно использовать следующим образом:

```typescript
// Custom name for keys
enum links {
    youtube = 'https://youtube.com/',
    vk = 'https://vk.com/',
    facebook = 'https://facebook.com/'
}

// Using
links.vk       // 'https://vk.com/'
links.youtube  // 'https://youtube.com/'
```

Подробнее про enum смотреть [тут](https://www.typescriptlang.org/docs/handbook/basic-types.html#enum).



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

