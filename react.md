# React

### Запуск нового проекта

1\) Инициализируем npm в папке:

```text
npm init -y
```

2\) Настроим typescript в связку к nodejs. Для этого в dev-dependencies установим:

```text
yarn add -D @types/node typescript
```

3\) Установим шаблон tsconfig -а:

```text
npx tsconfig.json
```

4\) Прописываем скрипты для запуска ноды на typescript. Тут два варианта.

Первый вариант использовать пакет ts-node:

```text
yarn add -D ts-node
```

и в скриптах в package.json прописать:

```text
"scripts": {
    "start": "ts-node src/index.ts"
}
```

Минусы этого варианта в долгой сборке. На проде проекта не очень годится. Второй вариант:

```text
"scripts": { "watch": "tsc -w", "start": "node src/index.js" }
```

