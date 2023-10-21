```
Object.create(proto[, propertiesObject])
```

```
o = {};
/=/ Эквивалентно этому:
o = Object.create(Object.prototype);

o = new Constructor();
/=/ Эквивалентно этому:
o = Object.create(Constructor.prototype);
```

### _Пример создания через Object.create()_

```
const person = Object.create(

  /=/ Создаем прототип с методом calculateAge()
  {
    calculateAge() {
      console.log("Age:", new Date().getFullYear() - this.birthYear);
    },
  },
  
  /=/ Определяем свойства объекта и их характеристики
  {
    name: {
      value: "Vladilen",      /=/ Значение свойства name
      enumerable: true,       /=/ Разрешает итерироваться
      writable: true,         /=/ Разрешает изменять value
      configurable: true,     /=/ Можно удалять поля объекта
    },
    birthYear: {
      value: 1993,
      enumerable: false,
      writable: false,
      configurable: false,
    },
    
    age: { 
    /=/ Например, нам нужно вычислить возраст на основе года рождения
      get() {
        return new Date().getFullYear() - this.birthYear;
      },
      set(value) {
        document.body.style.background = "red";
        console.log("Set age", value);
      },
    },
  }
);
```

### _property-descriptors_
#property-descriptors [[Object.defineProperties()]]
- `enumerable: true` - Разрешает итерироваться по элементам
- `writable: true` - Разрешает изменять `value` полей объекта
- `configurable: true` - Разрешает `delete` поля объекта

