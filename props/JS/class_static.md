`Статические поля` используются для хранения данных, которые являются общими для всех экземпляров класса.
Но при необходимости, могут быть перетерты в дочерних `экземплярах`

```
class Animal {
  static type = "ANIMAL";
}

class Cat extends Animal {
  // static type = "CAT";
}
Cat.type; /=/ ANIMAL

class Cat2 extends Animal {
  static type = "CAT";
}
Cat2.type; /=/ CAT
```

### _Применение static_

- Общие данные:
```
class Counter {
  static count = 0;

  static increment() {
    Counter.count++;
  }
}

Counter.increment(); /=/ Counter.count = 1
Counter.increment(); /=/ Counter.count = 2

В этом примере статическое поле count используется для отслеживания количества вызовов метода increment().
```

- Константы:
```
class Math {
  static PI = 3.14159;
}
console.log(Math.PI); /=/ Вывод: 3.14159

В этом примере статическое поле PI используется для хранения значения числа Пи.
```

- Глобальное состояние:
```
class Logger {
  static logLevel = "info";

  static setLogLevel(level) {
    Logger.logLevel = level;
  }

  static log(message) {
    if (Logger.logLevel === "info") {
      console.log(message);
    }
  }
}

Logger.log("This is an informational message"); 
/=/ Вывод: This is an informational message

Logger.setLogLevel("error");
Logger.log("This is an informational message"); 
/=/ Ничего не выводится, так как уровень журналирования установлен на "error"

В этом примере статическое поле logLevel используется для хранения уровня журналирования, и методы setLogLevel() и log() используют это поле для фильтрации и вывода сообщений.
```

- Утилитарные методы:
  (без необходимости создания объекта)
```
class MathUtils {
  static add(a, b) {
    return a + b;
  }

  static multiply(a, b) {
    return a * b;
  }
}

console.log(MathUtils.add(2, 3)); /=/ Вывод: 5
console.log(MathUtils.multiply(2, 3)); /=/ Вывод: 6

В этом примере статические методы add() и multiply() используются для выполнения математических операций без необходимости создания объекта класса MathUtils.
```

