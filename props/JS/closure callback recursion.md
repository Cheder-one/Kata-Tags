### _Отличие Замыкания, Колбэка и Рекурсии_

## _Функция_

Функция - это код функции + ее окружение (доступные данные в момент запуска ее кода)

```
function shell() {
  let x = 0;
  return function (text) {
    return `${text} ${++x}`;
  };
}

const nestedFn = shell(); /=/ Мы вызвали `shell()`, оболочка отпала и в руках
															остался только возврат. А возврат это внутренняя
															анонимная функция `function (text)`.

nestedFn("x ==="); // x === 1
nestedFn("x ==="); // x === 2
nestedFn("x ==="); // x === 3
```

### _Размещение`closure` вне функции_

Попытка размещения `closureFn` вне ее оболочки, но с вызовом ее внутри `shell()`

```
const closureFn = (text, x) => {
  return `${text} ${++x}`;
};

function shell(text) {
  let x = 0;
  return closureFn(text, x); /=/ Возвращает результат работы функции: "x === 1"
}

const nestedFn = shell("x ===");
/=/ При вызове оболочки, сразу вернет результат дочерних функций.
/=/ Вернет не функцию, а "x === 1"

nestedFn(); /=/ Поэтому вызвать не получится: "nestedFn is not a function"
```

Реализация вызова дочерних функций только по их вызову:

```
const closureFn = (text, x) => {
  return `${text} ${++x}`;
};

function shell(text) {
  let x = 0;
  return () => closureFn(text, x); // Добавили "() =>". Возвращает [λ]
}

const nestedFn = shell("x ==="); // Вернет функцию [λ] (референс)
nestedFn(); // x === 1
```

### _Создать локальную область видимости_:

```
(function () {
  let x = 0;

  const nestedFn = (text) => {
    return `${text} ${++x}`;
  };

  nestedFn("x ==="); // x === 1
})();
```

---
## _Сlosure_

![[closure]]

---
## _Callback_

![[callback]]

## _Recursion_

![[recursion]]
