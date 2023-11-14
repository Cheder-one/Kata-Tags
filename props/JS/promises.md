`Promise` - это специальный `объект` который уведомляет `запрашивающие` части о результате выполненного кода, когда тот будет готов. 

``` 
let promise = new Promise(function(resolve, reject) {
  // функция-исполнитель(executor) / "певец"
});
```

- Конструктор `new Promise` принимает в себя - `функцию-исполнитель`(`executor`)
- В данной `функции` находится `создающий код`, который `когда-нибудь` создаст `результат`. 
- Её аргументы: `resolve` и `reject` – это колбэки, которые предоставляет сам JavaScript. Наш код – только внутри исполнителя.

Итак, `исполнитель` запускается автоматически, он должен `выполнить работу`, а затем вызвать `resolve` или `reject`.

### _Внутренние св-ва объекта `promise`_

У объекта `promise`, возвращаемого конструктором `new Promise`, есть внутренние `свойства`:

1. `state`(`состояние`)
	- Изначально `"pending"`(`ожидание`), затем меняется:
	  - На `"fulfilled"` при вызове `resolve`(`выполнено успешно`) 
	  - Или `"rejected"` при вызове `reject`(`выполнено с ошибкой`)
2. `result`(`результат`) — вначале `undefined`, далее изменяется:
	- На `value` при вызове `resolve(value)` 
	- Или `error` при вызове `reject(error)`.

```
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const data = { name: "John", age: 30 };
      resolve(data); /=/ Возвращаем успешный результат
      // Или reject("Ошибка получения данных");
    }, 2000);
  });
}
/=/ Исполнитель должен вызвать что-то одно: `resolve` или `reject`.

fetchData()
  .then(data => {
    console.log("Данные получены:", data);
  })
  .catch(error => {
    console.error("Ошибка:", error);
  });
```

### _Потребители: then, catch_

Объект `Promise` служит `связующим звеном` между `исполнителем` и `функциями-потребителями`, которые получат либо `результат`, либо `ошибку`. 
- `Функции-потребители` могут быть `зарегистрированы` (`подписаны`) с помощью методов  `.then` и `.catch`.
- Данные 


### _Очистка: finally_

- Обработчик, вызываемый из `finally`, не имеет аргументов.
- Обработчик `finally` ничего не возвращает. Единственным `исключением` из этого правила является случай, когда обработчик `finally` выдает ошибку. Тогда выполнение переходит к ближайшему обработчику ошибок.
- Обработчик `finally` «`пропускает`» `результат` или `ошибку` дальше, к последующим обработчикам.

``` 
new Promise((resolve, reject) => {
  setTimeout(() => resolve("value"), 2000);
})
  .finally(() => console.log("Промис завершён")) /=/ срабатывает первым
  .then(result => console.log(result)); /=/ <-- .then показывает "value"
```

``` 
new Promise((resolve, reject) => {
  throw new Error("error");
})
  .finally(() => console.log("Промис завершён")) /=/ Срабатывает первым
  .catch(err => console.log(err));  /=/ <-- .catch показывает ошибку
```

---
Создание промиса:
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
Выполнение `асинхронных` операций `последовательно`:
   - `Promise.all(iterable)`: Возвращает промис, который разрешается, когда все промисы из итерируемого объекта завершаются успешно.
   - `Promise.race(iterable)`: Возвращает промис, который разрешается, как только один из промисов из итерируемого объекта завершается (`успешно` или с `ошибкой`).

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

### _Внутреннее строение Promise_

```
class MyPromise {  
  constructor(executor) {  
    this.state = "pending"; // состояние промиса  
    this.value = undefined; // значение промиса (результат выполнения или ошибка)  
    this.callbacks = []; // массив колбэков, ожидающих выполнения промиса  
  
    const resolve = (value) => {  
      if (this.state === "pending") {  
        this.state = "fulfilled";  
        this.value = value;  
        this.callbacks.forEach((callback) => callback.onFulfilled(value));  
      }  
    };  
  
    const reject = (reason) => {  
      if (this.state === "pending") {  
        this.state = "rejected";  
        this.value = reason;  
        this.callbacks.forEach((callback) => callback.onRejected(reason));  
      }  
    };  
  
    try {  
      executor(resolve, reject);  
    } catch (error) {  
      reject(error);  
    }  
  }  
  
  then(onFulfilled, onRejected) {  
    return new MyPromise((resolve, reject) => {  
      const handleCallback = () => {  
        try {  
          if (this.state === "fulfilled") {  
            if (typeof onFulfilled === "function") {  
              const result = onFulfilled(this.value);  
              resolve(result);  
            } else {  
              resolve(this.value);  
            }  
          } else if (this.state === "rejected") {  
            if (typeof onRejected === "function") {  
              const result = onRejected(this.value);  
              resolve(result);  
            } else {  
              reject(this.value);  
            }  
          }  
        } catch (error) {  
          reject(error);  
        }  
      };  
      if (this.state === "pending") {  
        this.callbacks.push({  
          onFulfilled: handleCallback,  
          onRejected: handleCallback  
        });  
      } else {  
        setTimeout(handleCallback, 0);  
      }  
    });  
  }  
  
  catch(onRejected) {  
    return this.then(null, onRejected);  
  }  
  
  static resolve(value) {  
    return new MyPromise((resolve) => resolve(value));  
  }  
  
  static reject(reason) {  
    return new MyPromise((resolve, reject) => reject(reason));  
  }  
  
  static all(promises) {  
    return new MyPromise((resolve, reject) => {  
      const results = [];  
      let completedCount = 0;  
  
      const checkCompletion = () => {  
        if (completedCount === promises.length) {  
          resolve(results);  
        }  
      };  
  
      promises.forEach((promise, index) => {  
        promise  
          .then((result) => {  
            results[index] = result;  
            completedCount++;  
            checkCompletion();  
          })  
          .catch(reject);  
      });  
    });  
  }  
}
```