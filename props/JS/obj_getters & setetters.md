Геттеры (`getters`) и сеттеры (`setters`) - это специальные `методы` в объектах, которые позволяют управлять доступом к их свойствам.

Обращение происходит как к `полю`, а не к как `методу`

- `get()` - должен возвращать какое-то значение.
- `set(value)` 

``` 
let obj = {
  get propName() {
    /=/ Геттер, срабатывает при чтении obj.propName
  },

  set propName(value) {
    /=/ Сеттер, срабатывает при записи obj.propName = value
  }
};
```

### _Умные геттеры/сеттеры_

``` 
let user = {
  get name() {
    return this._name;
  },

  set name(value) {
    if (value.length < 4) {
      console.log("Имя слишком короткое, должно быть более 4 символов");
      return;
    }
    this._name = value;
  }
};

user.name = "Pete";
console.log(user.name); // Pete

user.name = ""; // Имя слишком короткое...
```

-> Example 2
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

