`Object.is()`: Сравнивает значения объектов и возвращает `true`/`false`. Этот метод обрабатывает некоторые специальные случаи, такие как сравнение `NaN` и `-0`.

```
const obj1 = { name: 'Alice' };
const obj2 = { name: 'Alice' };

console.log(obj1 == obj2); /=/ false
console.log(Object.is(obj1, obj2)); /=/ false

const obj3 = { name: 'Bob' };
const obj4 = obj3;

console.log(obj3 == obj4); /=/ true
console.log(Object.is(obj3, obj4)); /=/ true

```