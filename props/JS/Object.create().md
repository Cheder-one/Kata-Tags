```
Object.create(proto, propertiesObject)
```

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

### _getters/setters_

Геттеры (`getters`) и сеттеры (`setters`) - это специальные методы в объектах, которые позволяют управлять доступом к их свойствам.

Обращение происходит как к `полю`, а не к как `методу`
- `get()` - должен возвращать какое-то значение.
- `set(value)`

```
const person = {
  firstName: 'John',
  lastName: 'Doe',

  /=/ Геттер для получения полного имени
  get fullName() {
    return this.firstName + ' ' + this.lastName;
  },

  /=/ Сеттер для установки полного имени
  set fullName(value) {
    /=/ Разбиваем переданное значение на имя и фамилию
    const parts = value.split(' ');
    if (parts.length === 2) {
      this.firstName = parts[0];
      this.lastName = parts[1];
    } else {
      console.log('Неверный формат полного имени. Используйте "Имя Фамилия".');
    }
  }
};

/=/ Получение полного имени с использованием геттера
console.log(person.fullName); /=/ Выводит: "John Doe"

/=/ Установка полного имени с использованием сеттера
person.fullName = 'Alice Johnson';
console.log(person.firstName); /=/ Выводит: "Alice"
console.log(person.lastName); /=/ Выводит: "Johnson"
```

