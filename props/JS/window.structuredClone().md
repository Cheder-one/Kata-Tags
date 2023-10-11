
Поддержка начинается с `Node 17`

Метод `structuredClone()` используется для создания глубоких копий объектов, включая все их вложенные объекты, массивы, примитивы и другие типы данных. 
Он работает с объектами, которые могут содержать циклические ссылки и встроенные объекты, такие как `Date`, `RegExp`, `Map` и `Set`.

```
const obj = {
  name: 'Alice',
  age: 30,
  address: {
    city: 'New York',
    country: 'USA'
  }
};

const newObj = window.structuredClone(obj);

/=/ Изменение значения в новом объекте
newObj.address.city = 'San Francisco';

console.log(obj.address.city); /=/ Выведет 'New York'
console.log(newObj.address.city); /=/ Выведет 'San Francisco'
```
