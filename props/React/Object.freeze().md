```
const obj = {
  prop: 42,
};

Object.freeze(obj);

obj.prop = 33;
// Throws an error in strict mode

console.log(obj.prop);
// Expected output: 42
```

-> `Immutable.js`
```
const { Map } = require('immutable');

/=/ Создаем неизменяемый объект
const user = Map({
  name: 'John',
  age: 30,
  email: 'john@example.com'
});

/=/ Вносим изменения в объект
const updatedUser = user.set('age', 31);

/=/ Выводим обновленный объект
console.log(user.toJS()); 
/=/ { name: 'John', age: 30, email: 'john@example.com' }
console.log(updatedUser.toJS()); 
/=/ { name: 'John', age: 31, email: 'john@example.com' }
```

В этом примере мы создаем неизменяемый объект `user` с помощью метода `Map` из библиотеки `Immutable.js`. Затем мы вносим изменение в возраст пользователя, используя метод `set`, который возвращает новый объект с обновленным значением. Исходный объект `user` остается неизменным.

Обратите внимание, что методы `Immutable.js` не изменяют исходный объект, а возвращают новый объект с обновленными значениями. Это позволяет нам сохранить неизменяемость исходного объекта и создать новые объекты с обновленными значениями при необходимости.