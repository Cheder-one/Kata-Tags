- В JS все является объектами (даже `string`)
- Любой объект имеет `__proto__`
- Любой объект создается с помощью `Class` или `function` (не `arrow`!)
  - `Классы` - синт. сахар и на самом деле внутри создаются через `function`

---

## _prototype_

- `prototype` - существует только у `function` и `Class`
- `__proto__` - существует у всех `объектов`

**Прототип объекта** - это объект, который используется в качестве `шаблона` для создания других `объектов`.

### _Применение prototype_

При добавлении `метода` или `свойства` к `прототипу` родительскому `конструктору`, эти `методы` и `свойства` становятся доступными через `__proto__` для объектов, созданных с использованием этой `функции-конструктора`.

---

```
class Samurai {}             /=/ Class - имеет prototype
function Component() {}      /=/ function - имеет prototype
const API = function () {};  /=/ function - имеет prototype
const arrowFn = () => {};    /=/ arrow fn - НЕ имеет prototype

console.log(Samurai.prototype);
console.log(Component.prototype);
console.log(API.prototype);

console.log(Object.prototype); /=/ Встроенные Class - имеют prototype
console.log(Promise.prototype);
console.log(Function.prototype);
console.log(Boolean.prototype);
console.log(Number.prototype);
console.log(String.prototype);
console.log(Array.prototype);
```

- Каждый `prototype` - это независимый `Объект`.
  Поэтому:
  - `Number.prototype !== String.prototype`
  - `API.prototype !== Component.prototype`
  - `Samurai.prototype !== Object.prototype`

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

- `__proto__` есть у всех объектов. Является `внутренним(скрытым)` свойством объекта.
- `__proto__` ссылается на `прототип` своего объекта.

**А если проще**: `__proto__` отражает доступные `методы` и `значения` для "дочернего" `объекта` который был создан от родительского `конструктора`.

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
### _.get/setPrototypeOf()_

Вместо использования `__proto__`, рекомендуется использовать методы

- `Object.getPrototypeOf()` - метод для получения прототипа объекта.
- `Object.setPrototypeOf()` - метод для установки/изменения прототипа объекта.
- `Object.create()`-  создает новый объект с указанным прототипом.


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
```

---

У одинаковых по типу объектов `__proto__` равны.

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
/=/ Созданы от конструктора `new Object`
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

## _Итерация только по собственным свойствам объекта_

### _obj.hasOwnProperty(key)_

С помощью `.hasOwnProperty()` и `for...in` можно обойти свойства объекта, исключая свойства полученные от `Object.prototype`.
Возвращает `true`, если у `obj` есть собственное, не унаследованное свойство с именем `key`.

```
const obj = {
  prop1: 'value1',
  prop2: 'value2'
};

/=/ Добавляем свойство в прототип объекта
Object.prototype.prop3 = 'value3';

/=/ Используем for...in для обхода свойств объекта
for (let key in obj) {
  /=/ Проверяем, принадлежит ли свойство объекту
  if (obj.hasOwnProperty(key)) {
		console.log(`${key}: ${obj[key]}`);
	}
}
```

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
