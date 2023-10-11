Список `immutable` (неизменяемых) и `mutable` (изменяемых) типов:

Mutable (изменяемые):
- Объекты (Objects)
- Массивы (Arrays)
- Функции (Functions)
- Классы (Classes)
- Множества (Sets)
- Словари (Maps)
- Буферы (Buffers)

Immutable (неизменяемые):
- Строки (Strings)
- Числа (Numbers)
- Булевы значения (Booleans)
- Undefined
- Null

---
Необходимо стремиться трансформировать `mutable` элементы в `immutable`, используя создание новой глубокой копии ссылочного элемента, а не мутировать исходный

- Пример неизменяемости (`immutable`) - `Pure`:

```
/=/ Создание неизменяемого объекта
const person = {
  name: 'John',
  age: 30
};

/=/ Создание нового объекта с обновленным свойством
const updatedPerson = {
  ...person,
  name: 'Jane'
};

console.log(person.name); /=/ 'John'
console.log(updatedPerson.name); /=/ 'Jane'
```

- Пример мутирования и изменяемости (`mutable`):
```
/=/ Создание изменяемого объекта
const person = {
  name: 'John',
  age: 30
};

/=/ Изменение исходного обьекта
person.name = 'Jane';

console.log(person.name); /=/ Выведет 'Jane'
```