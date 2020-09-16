---
id: typescript
title: Basic types
---

# typescript

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

