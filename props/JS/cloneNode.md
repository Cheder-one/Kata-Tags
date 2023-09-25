Нельзя просто так взять один элемент и добавить его много раз на страницу. **Вставка шаблона сработает только один раз.**
Для этого существует **клонирование** `DOM-элементов`.

У метода `cloneNode` есть аргумент — булево значение.

- `false`, то будет скопирован сам элемент со своими классами и атрибутами, но без дочерних элементов.
- `true`, то клонируется сам элемент вместе со всеми вложенностями. Глубокое клонирование.

**!** Необходимо всегда передавать `true/false` во избежание непредсказуемого поведения.

```
element.cloneNode(true);
/=/ Полное клонирование потомков

element.cloneNode(false);
/=/ Вернёт склонированный элемент, но без вложенностей
```

### _Вставка множества клонированных элементов_

- Клонировать все элементы, находящиеся внутри тега `<template>`, вы можете использовать метод `cloneNode(true)`

```
const template = document.querySelector('template');
const clonedElements = template.content.cloneNode(true);
```
---
```
/=/ Контейнер для карточек
var pool = document.querySelector(".pool");

/=/ Получаем шаблон карточки
var template = 
	document.querySelector("#element-template").content;
var element = template.querySelector("div");

for (var i = 1; i <= 10; i++) {
  var clonedElement = element.cloneNode(true);
  clonedElement.children[0].textContent = i;

  pool.appendChild(clonedElement)
}
```

