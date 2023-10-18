Возвращает `массив`из имен собственных `свойств` объекта. 

Собственные свойства объекта — это те, которые определены непосредственно в этом объекте и `не наследуются` от прототипа объекта. К свойствам объекта относятся как поля (объекты), так и функции.

-> Поиск только собственным свойствам объекта:
```
function isEmpty(obj) {
	return !Object.getOwnPropertyNames(obj).length;
}

const obj = Object.create(null);
isEmpty(obj); /=/ true
isEmpty({ prop: "value" }); /=/ false
```

-> Поиск по собственным + свойствам `__proto__` объекта 
```

```

-> Поиск по собственным + свойствам `__proto__` объекта (не корректное решение)
```
function isEmptyWithProtos(obj) {
	const proto = Object.getPrototypeOf(obj);
	return !Object.getOwnPropertyNames(proto).length
}

const protoObj = Object.create(null);
const obj2 = Object.create(protoObj);

isEmptyWithProtos(obj2); /=/ true
isEmptyWithProtos({}); /=/ false
```
