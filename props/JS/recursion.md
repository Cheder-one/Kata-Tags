Функция которая вызывает сама себя с новыми аргументами.

```
function factorial(n) {
    if (n === 0) {
            return 1; /=/ Базовый случай
    } else {
        return n * factorial(n - 1);
        /=/ Рекурсивный вызов с меньшим аргументом
    }
}

console.log(factorial(5)); /=/ 120
```

### _Пройти по Объекту в глубь и отсортировать его_

```
const obj = {
  a: {
    b: {
      e: {
        num: 1
      },
      d: "string",
      c: 1
    }
  }
};

function processObject(obj) {
  /=/ Обработка текущего объекта

  /=/ Рекурсивный вызов для вложенных объектов
  for (let key in obj) {
    const isObject = typeof obj[key] === "object" && obj[key] !== null;

    if (isObject) {
	   obj[key] = processObject(obj[key]) /=/ !Важно не забывать сохранять результат
																					рекурсии обратно в исходный объект `obj` 
	  };
  }

	return Object.fromEntries(Object.entries(obj).sort());
}

processObject(obj); /=/ { a: { b: { c: 1, d: 'string', e: { num: 1 } } } }
```
