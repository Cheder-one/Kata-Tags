`Прототипная модель` в `JavaScript` - это способ создания объектов, основанных на других объектах. 

- Любой объект имеет `__proto__`. Но не имеет `prototype`
	- `__proto__` дочернего `объекта` `ссылается` на родительский `prototype` и `равен` ему

- Любой `объект` создается с помощью `Class` или `function` (не `arrow`!)
	- Встроенные и Кастомные `прототипы`(`конструкторы`) имеют `prototype`
	- `prototype` ни на кого `не ссылаются` и `не равны` `XXX.prototype !== XXX.prototype`
	- `Class` - синт. сахар и на самом деле являются `function`. Следовательно и создаются внутри `JavaScript` через `function`

### _Как выглядят прототипы?_

```
/=/ Конструктор родительского прототипа
function Component(name) {
  this.name = name;
}

/=/ Добавляем методы и свойства к прототипу
Component.prototype.sayHello = function() {
	return `Hello, ${this.name}!`
};

/=/ Позволяет экземплярам, созданным с помощью `Component()`, наследовать его методы и свойства.
let component1 = new Component("Компонент 1");
let component2 = new Component("Компонент 2");

/=/ Кастомный прототип
console.log(Component.prototype);
----------------------------------

/=/ Встроенные прототипы
console.log(Object.prototype); /=/ Встроенные прототип Объекта
console.log(Promise.prototype);
console.log(Function.prototype);
console.log(Boolean.prototype);
console.log(Number.prototype);
console.log(String.prototype);
console.log(Array.prototype);

Object.prototype /-идентичны-/ Object.create(Object.prototype)
```

### _Примеры сравнения `prototype` и `__proto__`_

```
({}).prototype === {}.__proto__; /=/ false
/=/ У обычного объекта `{}` нет свойства `prototype`.
Object.prototype === {}.__proto__; /=/ true
/=/ Тк `{}` создан от прототипа `Object.prototype`.
/=/ Следовательно в своем `__proto__` носит ссылку на родительский `prototype`

function ITKamasutra() {}
ITKamasutra.prototype === ITKamasutra.__proto__; /=/ false
/=/ `ITKamasutra` создан от `прототипа` Function
/=/ Следовательно в своем `ITKamasutra.__proto__` будет ссылаться на `Function.prototype`
/=/ Function.prototype === ITKamasutra.__proto__; /=/ true

function ITIncubator() {}
function ITKamasutra() {}
ITIncubator.__proto__ === ITKamasutra.__proto__; /=/ true
/=/ Их `__proto__` ссылаются на родительский прототип - Function.prototype
/=/ ITKamasutra.__proto__ === Function.prototype /=/ true
ITIncubator.prototype === ITKamasutra.prototype; /=/ false
/=/ ITIncubator и ITKamasutra это два разных класса
/=/ Следовательно они считаются двумя разными родительскими прототипами

let Component = () => undefined;
Component.prototype === Object.prototype; /=/ false
/=/ arrow-function `не может` выступать `конструктором` и создавать `объекты`
/=/ Следовательно `не имеет` `prototype`. `Component.prototype` /=/ undefined
let Component2 = function () {};
Component2.prototype === Object.prototype; /=/ false
/=/ Но даже так, `Component` был бы `равен только` `Function.prototype`

let age = 18;
age.prototype === Number.prototype; /=/ false
/=/ `age` это `не конструктор` и `не имеет` `prototype`
/=/ age.prototype /=/ undefined
age.__proto__ === Number.prototype; /=/ true
/=/ `Число` создается от прототипа `Number`, поэтому переменная с ним === `Number.prototype`
/=/ Оно не создается через new Number(18). Но когда мы обращаемся к `переменной` как к `объекту` через точку, то `временно` создается `объект` с помощью `new Number()`

class Hacker {}
Hacker.__proto__ === Function.prototype; /=/ true
/=/ `Классы` - синт. сахар и внутри являются `функциями`  создаются от `Function.prototype`

function ITIncubator() {}
ITIncubator.__proto__ === ITIncubator.prototype; /=/ false
/=/ Тк `ITIncubator.__proto__` создан от прототипа `Function`
/=/ Следовательно ITIncubator.__proto__ === Function.prototype
```

---
## _prototype_

- `prototype` - существует только у `function` и `Class`
- `__proto__` - существует у всех `объектов`

**Прототип объекта** - это объект, который используется в качестве `шаблона` для создания других `объектов`.

### _Добавление свойств и методов в родительский прототип_

При добавлении `метода` или `свойства` к `прототипу` родительского `конструктора`, эти `методы` и `свойства` становятся доступными через `__proto__` для объектов, созданных с использованием этой `функции-конструктора`.

---

```
class Samurai {}             /=/ Class - имеет prototype
function Component() {}      /=/ function - имеет prototype
const API = function () {};  /=/ function - имеет prototype
const arrowFn = () => {};    /=/ arrow fn - НЕ имеет prototype

class Hacker {}
Hacker.__proto__ === Function.prototype; /=/ true

console.log(Samurai.prototype);
console.log(Component.prototype);
console.log(API.prototype);

/=/ Встроенные прототипы - имеют prototype
console.log(Object.prototype); /=/ Встроенные прототип Объекта
console.log(Promise.prototype);
console.log(Function.prototype);
console.log(Boolean.prototype);
console.log(Number.prototype);
console.log(String.prototype);
console.log(Array.prototype);
```

Например, `Object.prototype` является `прототипом` для всех `объектов` в `JavaScript`.  
Каждый `объект` в `JavaScript` наследует `свойства` и `методы` от `Object.prototype`.
Это означает, что вы можете использовать `свойства` и `методы`, определенные в `Object.prototype`, на любом `объекте`.

---

- Каждый `prototype` - это независимый `Объект`.
  Поэтому:
  - `Number.prototype !== String.prototype`
  - `API.prototype !== Component.prototype`
  - `Samurai.prototype !== Object.prototype`

---

### _Как работает поиск вызванных свойств объекта_

- Если `prototype` находит нужное поле к которому мы обращаемся - он его вызывает
- Если нет, то спускается вниз и обращается к локальному прототипу `__proto__` и ищет в нем
- Если свойство нигде не найдено, то `error`

Данный алгоритм демонстрирует, как `JavaScript` ищет `свойства объекта`, начиная с самого `объекта`, а затем спускаясь по цепочке `прототипов`, пока не найдет нужное `свойство` или не достигнет конца `прототипной цепочки`.

---

-> Создание поля для глобальной родительской сущности `Object`:

```
const person = new Object({
  name: "Maxim",
  age: 25,
  greet: function () {
    console.log("Greet!");
  }
});

Object.prototype.sayHello = function () {
  console.log("Hello!");
};
```

-> Создание поля для `__proto__` объекта:

```
let animal = {
  eats: true
};

let rabbit = {
  jumps: true
};

rabbit.__proto__ = animal; /=/ устанавливает `animal` как прототип для `rabbit`

console.log( rabbit.eats ); /=/ true
console.log( rabbit.jumps ); /=/ true
```

---

## _`__proto__`_

Обратите внимание, что `__proto__` — _не то же самое_, что внутреннее свойство `[[Prototype]]`. Это `геттер/сеттер` для `[[Prototype]]`

- `__proto__` есть у всех объектов. Является `внутренним(скрытым)` свойством объекта.
- `__proto__` ссылается на `прототип` своего объекта.

**Если проще**: `__proto__` отражает доступные `методы` и `значения` для "дочернего" `объекта` который был создан от родительского `конструктора`. А точнее ссылается на них.

-> Например:

```
const Fn = function (arg) {
  this.a = arg;
  /=/ Полю `a`, присваиваем переданное значение `agr`
};

Fn.prototype.b = 10;
/=/ Добавляем в родительский конструктор `Fn` (в частности в его prototype) свойство `b` со значением 10.

const instance1 = new Fn(3);
const instance2 = new Fn(5);
/=/  Создаем экземпляры от нашего кастомного конструктора `new Fn()`

instance1.__proto__ === instance2.__proto__; /=/ true
/=/ Экземпляры равны тк созданы от одинакового по типу родителя

instance1; /=/ Fn { a: 3 }
/=/ В исходных свойствах объекта (который был создан в качестве экземпляра объекта от родительского конструктора Fn), есть только переданное ему через аргументы значение, где  a === 3

instance1.__proto__; /=/ Fn { b: 10 }
/=/ При обращении к скрытому свойству объекта `__proto__`, получаем доступ к методам и свойствам, определенным родительском в прототипе, от которого был создан данный объект.

instance1.b; /=/ 10
/=/ Тк свойства `b` нет в обычных свойствах объекта, поиск спускается по прототипной цепочке ниже и осуществляет поиск там. Где он и находит наше значение - в `__proto__` объекта, значение которого он получил от своей родительской функции-конструктора, через которую был создан.

/=/ *instance - экземпляр
```

---

### _Методы прототипов_

Вместо использования `__proto__`, рекомендуется использовать методы

- `Object.getPrototypeOf(obj)` - метод для получения прототипа объекта.
- `Object.setPrototypeOf(obj)` - метод для установки/изменения прототипа объекта.
- `Object.create(obj)`-  создает новый объект с указанным прототипом.
- `obj.hasOwnProperty(key)` - используется для проверки наличия собственного (`непрототипного`) свойства с заданным именем `key` в объекте `obj`.
- `Object.getOwnPropertyNames(obj)` - возвращает `массив` со всеми свойствами (независимо от того, перечисляемые они или нет), найденными непосредственно в переданном объекте.

```
const obj = {};
const prototype = Object.getPrototypeOf(obj);
console.log(prototype); /=/ Object {}
```

```
const obj = {};
const prototype = { foo: 'bar' };
Object.setPrototypeOf(obj, prototype);
console.log(obj.foo); /=/ bar
```

```
const parentObj = {
	greet() {
		return "Привет от родительского объекта!";
	},
};
const childObj = Object.create(parentObj);

childObj.greet(); /=/ Привет от родительского объекта!
```

![[Object.getOwnPropertyNames()]]

### _Применение proto_

- Используется для поиска `свойств` и `методов`, если они не определены в самом объекте. Если `свойство` или `метод` не найден в объекте, JavaScript будет искать его в цепочке прототипов.

```
const person = {
  name: "Alice"
};
const student = {
  grade: "A"
};
student.__proto__ = person;
console.log(student.name); /=/ "Alice"

===/ v Корректная замена v /===

const person = {
  name: "Alice"
};

const student = Object.create(person)
console.log(student.name); // "Alice"
```

---

У одинаковых по `типу` объектов, `__proto__` равны.

Тк если `объект` был создан от одного и того же `конструктора`, то `__proto__` будет ссылаться на один и тот же `родительский прототип` от которого был создан.

```
const Fn = function (arg) {
	this.a = arg;
};

Fn.prototype.b = 10; /=/ Добавляем в родительский конструктор `Fn`
                     (в частности в его `prototype`) свойство `b` со значением 10.

const inst1 = new Fn(3);
const inst2 = new Fn(5);
/=/ Создаем экземпляры от нашего кастомного конструктора `new Fn()`

inst1.__proto__ === inst2.__proto__ /=/ true
/=/ Экземпляры равны тк созданы от одинакового по типу родителя
```

```
/=/ Созданы от конструктора(от встроенноего прототипа) `new Object`
let man = {} /=/ new Object
let man2 = {}
man.__proto__ === man2.__proto__ /=/ true

/=/ Созданы от конструктора `new Array`
let users = []
let cars = []
users.__proto__ === cars.__proto__ /=/ true

/=/ Это все типы конструктора `new Function`
class Channel {}
function () {}
let varFn = function() {}
let arrowFn () => {}
```

### _Итерация по свойствам Объекта_

Итерация может быть:

- по свойствам объекта + его унаследованным свойствам
- исключительно по собственным свойствам объекта

### _for..in - итерация по собственным + унаследованные_

```
let animal = {
  eats: true
};

let rabbit = {
  jumps: true,
  __proto__: animal
};

/=/ Object.keys() возвращает только собственные ключи
console.log(Object.keys(rabbit)); /=/ jumps

/=/ for..in проходит и по своим, и по унаследованным ключам
for(let prop in rabbit) console.log(prop); /=/ jumps, затем eats
```

Если унаследованные свойства нам не нужны, то мы можем отфильтровать их при помощи встроенного метода `obj.hasOwnProperty(key)`: он возвращает `true`, если у `obj` есть собственное, не унаследованное, свойство с именем `key`.

```
let animal = {
  eats: true
};

let rabbit = {
  jumps: true,
  __proto__: animal
};

for(let prop in rabbit) {
  let isOwn = rabbit.hasOwnProperty(prop);

  if (isOwn) {
		return `Our: ${prop}`; // Our: jumps
  } else {
		return `Inherited: ${prop}`; // Inherited: eats
  }
}
```

## _Итерация только по собственным свойствам объекта_

### _obj.hasOwnProperty(key)_

![[obj.hasOwnProperty(key)]]

### _Object.keys()_

`Object.keys()` возвращает только собственные ключи объекта

```
let animal = {
  eats: true
};
let rabbit = {
  jumps: true,
  __proto__: animal
};
===/ v Корректная замена v /===

let animal = {
  eats: true
};

/=/ Cоздаем новый объект с добавлением свойств их указанного прототипа
let rabbit = Object.create(animal);
rabbit.jumps = true;

Object.keys(rabbit); /=/ jumps
/=/ Возвращает только собственные ключи
```
