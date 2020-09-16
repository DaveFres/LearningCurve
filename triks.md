---
description: 'Интересные приемы, которые мне встречались'
---

# Triks

1. **Предыстория:**  Необходимо было проверить корректность работы модального окна обратной связи. При успешной отправке обратной связи модальное окно должно закрываться. Если произошла ошибка модальное окно оставляем открытым.  **Проблема:**  Хотим в redux саге падать с ошибкой после первого успешного запроса. То есть в первый заход в сагу мы работаем нормально, а при втором заходе в сагу хотим упасть. Аналогично наоборот. Падаем только в первый заход в redux сага.  Как это реализовать?  **Решение:** Использовать замыкание. ****

```javascript
// Падаем после первого успешного выполнения
const something = (function() {
    const executed = false;
    return function() {
        if (!executed) {
            executed = true;
        } else {
            throw new Error('');
        }
    };
})();

something(); // "do something" happens
something(); // nothing happens
```

```javascript
// Падаем только в первый раз
const something = (function() {
    const executed = false;
    return function() {
        if (!executed) {
            executed = true;
            throw new Error('');
        }
    };
})();

something(); // "do something" happens
something(); // nothing happens
```

