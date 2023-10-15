Свойство `arguments` является устаревшим. 
Вместо него можно использовать `spread-operator` `...`, который преобразует аргументы функции в настоящий массив.

```
function sum(...args) {
  let total = 0;
  for (let i = 0; i < args.length; i++) {
    total += args[i];
  }
  return total;
}

console.log(sum(1, 2, 3)); // Выведет: 6
console.log(sum(4, 5, 6, 7)); // Выведет: 22
```