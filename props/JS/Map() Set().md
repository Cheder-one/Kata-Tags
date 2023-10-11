## _Map() – коллекция ключ/значение, как и `Object`_

Основное отличие - `Map` позволяет использовать ключи любого типа: `объекты`, `функци`, другие `Map()`

```
map => new Map([
  ["Hi", "Привет"],
  [42, "Автостопом по галактике"],
  [true, false],
  [{}, "Объект"],
  [function () {}, "Функция"]
]);
_____________________
map = new Map();
map.set("Hi", "Привет")
	 .set("42", "42")
	 .set(42, 42)

console.log(map); /=/ Map { 'Hi' => 'Привет', '42' => '42', 42 => 42 }
```

- `new Map()` – создаёт коллекцию.
- `map.set(key, value)` – добавляет элемент в коллекцию (заменяет на новый, если идентичный `key` уже существовал).
- `map.get(key)` – возвращает значение по ключу или `undefined`.
- `map.has(key)` – проверяет наличие `key`, возвращает `true`/`false.
- `map.delete(key)` – удаляет элемент (пару «ключ/значение») по ключу `key`.
- `map.clear()` – очищает коллекцию от всех элементов.
- `map.size` – возвращает текущее количество элементов.

### _Map() - итерируемый объект_

- `map.keys()` - возвращает ключи элемента
- `map.values()` - возвращает значения элемента
- `map.entries()` – возвращает итерируемый объект по парам вида `[ключ, значение]`, этот вариант используется по умолчанию в `for..of`.

```
[...map.entries()]; /=/ [	["Hi", "Привет"],	["42", "42"],	[42, 42] ];
```

### _`for of` перебор Map()_

```
for (let kv of map) {
	console.log(kv);
}

for (let [key, value] of map) {
	console.log(key, value);
}
```

### _`forEach` перебор Map()_

```
map.forEach((value, key, map) => {
	console.log(value, key, map);
});
```

### _Клонирование Map()_

```
const map2 = new Map(map1.entries());

console.log(map2); /=/ Map { 'Hi' => 'Привет', '42' => '42', 42 => 42 }
```

### _Деструктуризация `Map()` и его`key/value`_

`Map()` сохраняет порядок в котором мы добавляем элементы

```
const map = new Map();

map
	.set("HTML", "Hypertext Markup Language")
	.set("CSS", "Cascading Style Sheets")
	.set("JS", "JavaScript");

const [[key, value], second, third] = map;
console.log(key, value); // HTML Hypertext Markup Language
```

## _Set() – коллекция уникальных значений_

```
new Set(["HTML", "CSS", "JS"]); // Set { 'HTML', 'CSS', 'JS' }

new Set("HTML"); // Set { 'H', 'T', 'M', 'L' }
```

- `new Set(iterable)` – создаёт `Set` уникальных значений.
- `set.add(value)` – добавляет значение (если оно уже есть, то ничего не делает), возвращает тот же объект `set`.
- `set.delete(value)` – удаляет значение, возвращает `true` если `value` было в множестве на момент вызова, иначе `false`.
- `set.has(value)` – возвращает `true`, если значение присутствует в множестве, иначе `false`.
- `set.clear()` – удаляет все имеющиеся значения.
- `set.size` – возвращает количество элементов в множестве.

### _Клонирование Set()_

Тут оно проще чем в `Map()`

```
const set1 = new Set(["HTML"]);
const set2 = new Set(set1);
```
### _Итерирование по Set()_

- `[...set]` –  аналогичная замена методов ниже.
- `set.keys()` – возвращает перебираемый объект для значений
- `set.values()` – то же самое, что и `set.keys()`, присутствует для обратной совместимости с `Map`
- `set.entries()`  – возвращает перебираемый объект для пар вида `[значение, значение]`, присутствует для обратной совместимости с `Map`.

Метод `for of`:

```
let set = new Set(["апельсин", "яблоко", "банан"]);

for (let value of set) {
	console.log(value)
}
```

Метод `forEach`

```
set.forEach((value, valueAgain, set) => { 
  console.log(value);
});
```

### _Особенности и ошибки в Set()_

### _new Set(num)_

Тк конструктор `Set()`-а пытается вызвать специальный метод у аргумента, для получения перебираемого объекта.
У чисел нет такого метода, поэтому получаем ошибку.

```
new Set(42); /=/ number 42 is not iterable
const set = new Set([42]); /=/ Сработает
```

### _new Set({}).has({})_

Проверка на наличие выдаст `false`, тк ссылки объектов разные:

```
const set = new Set();

set.add({ className: "button" });
set.has({ className: "button" }); // false
```

Проверка на наличие будет работать корректно:

```
const set = new Set();
const buttonRef = { className: "button" }

set.add(buttonRef);
set.has(buttonRef); // true
```