
Стрелочные функции:

- Не имеют `this`.
- Не могут быть вызваны с `new` в качестве конструктора для нового объекта, тк не имеют своего `контекста`.
- У них также нет `super`
- Нет переменной `arguments`.

### _У стрелочных функций нет «this»_

Значение `this` у `arrow fn` берётся там где они были объявлены, берется снаружи.

-> Например, мы можем использовать это для итерации внутри `метода` объекта:
``` 
let group = {
  title: "Our Group",
  students: ["John", "Pete", "Alice"],

  showList() {
    this.students.forEach(
      student => console.log(this.title + ': ' + student)
    );
  }
};

group.showList();
```

Внутри `forEach` использована стрелочная функция, таким образом `this.title` в ней будет иметь точно такое же значение, как в методе `showList`: `group.title`.

---
Если бы мы использовали «обычную» функцию, была бы ошибка:

``` 
let group = {
  title: "Our Group",
  students: ["John", "Pete", "Alice"],

  showList() {
    this.students.forEach(function(student) {
      /=/ Error: Cannot read property 'title' of undefined
      console.log(this.title + ': ' + student)
    });
  }
};

group.showList();
```