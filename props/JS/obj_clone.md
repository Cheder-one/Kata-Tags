## _Поверхностное копирование_

### _Object.assign()_

```
Object.assign(target, source1, source2, sourceN)
```

- Чем ближе к концу в цепочке передаваемый obj, тем его значения приоритетней при создании нового объекта. И при `мердже` они переназначат возможные идентичные значения более раннестоящих `source`

```
const obj1 = {
  name: "Katelyn"
};
const obj2 = {
  name: "Larry",
  age: 20
};

const newObj = Object.assign({}, obj2, obj1); /=/ { name: 'Katelyn', age: 20 }
```

### _Объединение Объектов_

Достаточно лишь `...rest` и `Object.assign()` для `merge` объектов

```
const merge = (...arr) => {
  return Object.assign(...arr);
};

merge(
  {
    name: "John",
    age: 22
  },
  {
    surname: "Klein",
    age: 20,
    profession: "student"
  },
  {
    profession: "frontend developer",
    country: "USA"
  }
);

// {
//   name: 'John',
//   surname: 'Klein',
//   age: 20,
//   profession: 'frontend developer',
//   country: 'USA',
// }
```

## _Глубокое копирование_

### _JSON.parse(JSON.stringify(obj))_

- `JSON.stringify(obj)` - позволяет сравнивать объекты
- Самый простой подход, но такой метод не копирует функции и ссылки и непроизводителен

У этого метода есть ограничение — копируемые данные должны быть сериализуемы.

- Несериализуемые данные: примитив `undefined`, `функция`, `symbol` - при вызове `JSON.stringify()` получаем `undefined`
- Массивы и объекты - сериализуемы.
  Что будет если у них в качестве ключа или значения будут несериализуемые данные?
  - для массивов: такие значения будут превращены в null;
  - для объектов: такие значения будут опущены, а если symbol является ключом объекта, то он будет проигнорирован, даже при использовании функции replacer.

```
const obj = {
  foo: 'Hello',
  bar: {
    baz: 'World'
  }
};

const deepCopy = JSON.parse(JSON.stringify(obj));

console.log(deepCopy);
```

### _Spread-operator_

```
const obj = {
  foo: 'bar',
  nested: {
    prop: 'value'
  }
};

/=/ Глубокое копирование объекта
const copy = { ...obj, nested: { ...obj.nested } };

/=/ Изменение значения в копии объекта
copy.nested.prop = 'new value';

console.log(obj); /=/ { foo: 'bar', nested: { prop: 'value' } }
console.log(copy); /=/ { foo: 'bar', nested: { prop: 'new value' } }
```

### _structuredClone() - global function_

![[window.structuredClone()]]

### _\_.cloneDeep(obj) - lodash_

```
var objects = [{ 'a': 1 }, { 'b': 2 }];
var deep = _.cloneDeep(objects);

console.log(deep[0] === objects[0]); /=/ false
```

### _Spread-operator + Рекурсия_

Обратите внимание, что второй подход с использованием рекурсии может не справиться с некоторыми сложными типами данных, такими как функции или экземпляры классов, и может привести к ошибкам.

```
function deepCopy(obj) {
  if (typeof obj !== 'object' || obj === null) {
    return obj;
  }

  const copiedObj = Array.isArray(obj) ? [] : {};

  for (let key in obj) {
    if (obj.hasOwnProperty(key)) {
      copiedObj[key] = deepCopy(obj[key]);
    }
  }

  return copiedObj;
}

const originalObj = { a: 1, b: { c: 2 } };
const copiedObj = deepCopy(originalObj);

console.log(originalObj);  // { a: 1, b: { c: 2 } }
console.log(copiedObj);    // { a: 1, b: { c: 2 } }

// Изменяем скопированный объект
copiedObj.a = 100;
copiedObj.b.c = 200;

console.log(originalObj);  // { a: 1, b: { c: 2 } }
console.log(copiedObj);    // { a: 100, b: { c: 200 } }
```
