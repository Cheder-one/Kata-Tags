Функция которая вызывает сама себя с новыми аргументами.

```
function countdown(i) {
  console.log(i)
  if (i <= 1) {  // base case
    return;  
  } else {       // recursive case
    countdown(i - 1)
  }
}
countdown(5);
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
	   obj[key] = processObject(obj[key]) 
	   /=/ !Важно сохранять результат рекурсии 
			   обратно в исходный объект `obj` 
	  };
  }

	return Object.fromEntries(Object.entries(obj).sort());
}

processObject(obj); /=/ { a: { b: { c: 1, d: 'string', e: { num: 1 } } } }
```
