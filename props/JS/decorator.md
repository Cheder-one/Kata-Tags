В `JavaScript` `функция-декоратор` - это функция, которая используется для изменения поведения `другой функции` или `метода` без изменения его собственного `исходного кода`.

```
function uppercaseDecorator(targetFunction) {
/=/ контекст 1
  return function (...args) {
	/=/ контекст 2
    const result = targetFunction.apply(this, args); /=/ функция
    return result.toUpperCase();
	};
}

function sayHello(name) {
  return `Hello, ${name}!`;
}

const decoratedSayHello = uppercaseDecorator(sayHello);
decoratedSayHello("John"); /=/ Вывод: "HELLO, JOHN!"
```

В данном коде, выражение `targetFunction.apply(this, args)` будет ссылаться на `контекст 2`. То есть на контекст исполнения функции-обертки, которая возвращает функцию-декоратор.

---
```
class MyClass {
  constructor(name) {
    this.name = name;
  }

  sayHello() {
    return `Hello, ${this.name}!`;
  }
}

function myDecorator(constructor) {
  return function (...args) {
    const instance = new constructor(...args);
    // Добавьте здесь ваш код для декорирования экземпляра
    return instance;
  };
}

const DecoratedMyClass = myDecorator(MyClass);
const instance = new DecoratedMyClass("John");
instance.sayHello(); // Вывод: "Hello, John!"
```

```
/=/ Базовый класс
class Coffee {
  cost() {
    return 5;
  }
}

/=/ Декоратор для добавления сахара
function addSugar(coffee) {
  const cost = coffee.cost();
  coffee.cost = () => cost + 2;
}

/=/ Декоратор для добавления молока
function addMilk(coffee) {
  const cost = coffee.cost();
  coffee.cost = () => cost + 3;
}

const myCoffee = new Coffee();
console.log("Стоимость кофе без декораторов: $" + myCoffee.cost());

addSugar(myCoffee); /=/ Добавляем сахар
console.log("Стоимость кофе с сахаром: $" + myCoffee.cost());

addMilk(myCoffee); /=/ Добавляем молоко
console.log("Стоимость кофе с сахаром и молоком: $" + myCoffee.cost());
```
