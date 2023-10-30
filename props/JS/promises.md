```
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = {
        name: "John",
        age: 30
      };
      resolve(data); /=/ Возвращаем успешный результат
      /=/ или reject("Ошибка получения данных");
    }, 2000);
  });
}
/=/ Исполнитель должен вызвать что-то одно: `resolve` или `reject`.
/=/ Состояние промиса может быть изменено только один раз.

fetchData()
  .then(data => {
    console.log("Данные получены:", data);
  })
  .catch(error => {
    console.error("Ошибка:", error);
  });
```

---
1. Создание промиса:
   - `Promise.resolve(value)`: Создает успешно завершенный промис с указанным значением.
   - `Promise.reject(reason)`: Создает промис, завершенный с ошибкой, с указанной причиной.

```
new Promise(function (resolve, reject) {
  resolve(someSynchronousValue);
}).then(/* ... */);

/=/ То же самое гораздо короче:

Promise.resolve(someSynchronousValue).then(/* ... */);
```
---
2. Выполнение асинхронной операции:
   - `new Promise((resolve, reject) => { /* асинхронный код */ })`: Создает новый промис, который может быть разрешен (resolve) или отклонен (reject) в зависимости от результата асинхронной операции.
---
3. Обработка результата(`потребители`):
   - `.then(onFulfilled, onRejected)`: Метод для добавления обработчиков успешного завершения и ошибки к промису.
   - `.catch(onRejected)`: Обработка только ошибок, эквивалентно `.then(null, onRejected)`.
---
3. Очистка: `finally`
   - Выполнится в любом случае, когда промис завершится: успешно или с ошибкой. Идея `finally` состоит в том, чтобы настроить обработчик для выполнения очистки/доведения после завершения предыдущих операций. Например, остановка индикаторов загрузки, закрытие больше не нужных соединений и т.д.
---
4. Выполнение асинхронных операций последовательно:
   - `Promise.all(iterable)`: Возвращает промис, который разрешается, когда все промисы из итерируемого объекта завершаются успешно.
   - `Promise.race(iterable)`: Возвращает промис, который разрешается, как только один из промисов из итерируемого объекта завершается (успешно или с ошибкой).

```
const promise1 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'Promise 1');
});
const promise3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 300, 'Promise 2');
});

Promise.race([promise1, promise2, promise3])
  .then((value) => {
    console.log(value); /=/ Output: "Promise 1"
  })
  .catch((error) => {
    console.error(error);
  });
```
---
5. Управление ошибками:
   - `Promise.allSettled(iterable)`: Возвращает промис, который разрешается после завершения всех промисов в итерируемом объекте, независимо от результата (успешно или с ошибкой).
   - `Promise.any(iterable)`: Возвращает промис, который разрешается после завершения первого успешного промиса в итерируемом объекте.
   - `Promise.prototype.finally(onFinally)`: Позволяет выполнить определенные действия после завершения промиса, независимо от его успешного завершения или ошибки.

### _forEach() с Промисами_

**-> Верно**
```
db.allDocs({include_docs: true})
  .then(function (result) {
    var arrayOfPromises = result.rows.map(function (row) {
      return db.remove(row.doc);
    });
    return Promise.all(arrayOfPromises);
  })
  .then(function (arrayOfResults) {
    /=/ Вот теперь все документы точно удалены!
  });
```

**-> Ошибка**
```
/=/ Я хочу применить remove() ко всем документам
db.allDocs({include_docs: true})
  .then(function (result) {
    result.rows.forEach(function (row) {
      /=/ Метод remove возвращает promise
      db.remove(row.doc);
    });
  })
  .then(function () {
    /=/ А здесь я наивно уверен, что все документы уже удалены!
  });
```

### _Promise.race `mini-polyfil`_

```
function promiseRace(promises) {
  return new Promise((resolve, reject) => {
    promises.forEach((item) => {
      item
        .then((res) => resolve(res))
        .catch((rej) => reject(rej));
    });
  });
}

const secondPromise = new Promise((resolve, reject) => {
  setTimeout(() => reject("error 200"), 200);
  // setTimeout(() => resolve(200), 200);
});
const thirdPromise = new Promise((resolve, reject) => {
  setTimeout(() => resolve(100), 100);
  // setTimeout(() => reject('error 100'), 100)
});
const firstPromise = new Promise((resolve, reject) => {
  setTimeout(() => reject("error 300"), 300);
  // setTimeout(() => resolve(300), 300);
});

promiseRace([firstPromise, secondPromise, thirdPromise]); /=/ 100
```
#promise_rase #polyfil

Для каждого `промиса` из массива, вызывается метод `then`/`catch` для обработки ошибки промиса. Если один из промисов выполняется или отклоняется первым, то вызывается соответствующий обработчик (`resolve` или `reject`).

Так как `resolve`/`reject` для одного `промиса` могут вызываться только `единожды`, а `thirdPromise` выполняется быстрее всех остальных промисов, то он будет первым, кто вызовет метод `resolve` нового промиса. Следовательно и вернется только он.
