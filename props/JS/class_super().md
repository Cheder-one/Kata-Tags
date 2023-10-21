```
class Animal {
  static type = "ANIMAL";

  constructor(options) {
    this.name = options.name;
    this.age = options.age;
    this.hasTail = options.hasTail;
  }

  voice() {
    console.log("I am Animal!");
  }
}
```

-> Поле `color` не создастся, тк оно не указано в `constructor` дочернего `экземпляра`.

```
class Cat extends Animal {
  static type = "CAT";
}

const cat = new Cat({ /=/ Создание нового экземпляра
  name: "Cat",
  age: 7,
  hasTail: true,
  color: "black", /=/ Не создастся, тк не указано ни в одном `constructor`
});

cat.color /=/ undefined
```

### _`constructor` дочернего экземпляра_

Для создания `constructor` в дочернем экземпляре, необходимо перенести поля из `constructor` родительского класса.

Это реализуется с помощью `super()` в дочернем `constructor`, который вызывает родительский `constructor`.

- Если `родительский` `constructor` принимает `аргументы`, то `дочерний` метод `super()`, так же должен передавать `аргументы` для заполнения полей объекта.
- Если мы `перетерли` родительские `поля` дочерними, но хотим обратиться к ним, то можно обратиться к `super` как к свойству объекта. Например: `super.voice()`

```
class Cat extends Animal {
  static type = "CAT";

  constructor(options) {
    super(options);
    this.color = options.color;
  }
		  
	/=/ Дочерний метод более приоритетный чем родительский
	voice() { 
		console.log("I am Cat!");
		super.voice() /=/ Вызывает родительский метод
	}
}

const cat = new Cat({
  name: "Cat",
  age: 7,
  hasTail: true,
  color: "black",
});

cat.color /=/ black
```

