Метод `Object.defineProperties()` используется для `определения` или `изменения` одного или нескольких `свойств объекта`.

Это позволяет более точно управлять их характеристиками, такими как:
#property-descriptors
- доступность для чтения или записи (`writable`)
- наличие свойства (`enumerable`)
- возможность его конфигурации (`configurable`).
----

```
Object.defineProperties(obj, props)
```

- `obj` - `объект`, `свойства` которого нужно `определить` или `изменить`.
- `props` - `объект`, содержащий описания `свойств` для `определения` или `изменения`. 
  Каждое свойство объекта `props` должно иметь имя свойства, которое вы хотите определить, и конфигурацию этого свойства.

```
const person = {};

Object.defineProperties(person, {
  firstName: {
    value: 'John',
    writable: true,
    enumerable: true,
    configurable: true
  },
  lastName: {
    value: 'Doe',
    writable: true,
    enumerable: true,
    configurable: true
  }
});

console.log(person.firstName); /=/ Вывод: John
console.log(person.lastName); /=/ Вывод: Doe
```