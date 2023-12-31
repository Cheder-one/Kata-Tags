Функция которая передается в качестве аргумента другой функции и вызывается ею.

```
 function add(a, b, callback) {
     const result = a + b; /=/ Вычисляем результат
     callback(result); /=/ Вызываем колбэк с результатом
 }
 function print(x) {
     console.log(x); /=/ Выводим x
 }

 add(2, 3, print); /=/ 5
 /=/ Передаем print в качестве колбэка для add
```

## _Асинхронный callback_

Колбэк позволяет «запланировать» действие, которое будет совершено после выполнения какого-то другого, возможно длительного действия.

Колбэк (`callback`) переводится как «Перезвоните». Действительно, принцип работы `колбэков` схож с заказом обратного телефонного звонка. Представьте, что вы звоните оператору для заказа пиццы, но срабатывает автоответчик, где приятный голос просит оставаться на линии, пока не освободится оператор, или предлагает заказать обратный звонок. Когда оператор освободится — он перезвонит и примет заказ.

Это прекрасная аналогия для понимания принципов работы `колбэков` и `асинхронности`.

- Вместо ожидания ответа оператора, мы можем заказать обратный звонок и заниматься другими делами. Как только оператор освободится, произойдёт колбэк (нам перезвонили), мы сможем выполнить задуманное — заказать пиццу.

### _Синхронный cb_

```
/=/ Приготовление пиццы. Длительный процесс
const newPizza = makePizza('pepperoni');

/=/ Читаем книгу пока готовят пиццу
readBook(); // На самом деле читаем только после приготовления

/=/ Съедаем пиццу
eatPizza(newPizza);
```

### _Aсинхронный cb_

```
const makePizza = function (title, pizzaCb) {
 console.log(`Заказ «${title}» получен. Начинаем готовить…`);
 setTimeout(pizzaCb, 3000);
}

const readBook = function () {
 console.log('Читаю книгу «Колдун и кристалл»…');
}

const eatPizza = function () {
  console.log('Ура! Пицца готова, пора подкрепиться.');
}

makePizza('Пеперонни', eatPizza);
readBook();

/=/ Заказ на приготовление пиццы «Пепперони» получен. Начинаем готовить…
/=/ Читаю книгу «Колдун и кристалл»…
// Здесь будет пауза
/=/ Ура! Пицца готова, пора подкрепиться.
```

---
## _Пример использования callbackMe_

**-> Не сработает**
```
const fn = () => {
  x = 0;

	setTimeout(function () {
    return (x = 1);
  }, 1000);
};
fn(); /=/ undefined
```

**-> Сработает**
```
const fn = (callback) => {
  x = 0;
  setTimeout(function () {
    x = 1;
    callback(x);
  }, 1000);
};

const callbackMeX = (value) => {
  console.log(value); /=/ 1
};

fn(callbackMeX);
```

### _Более сложный и реальный пример_

```
let fileSizes = {
  testFile1: 65,
  testFile2: 48
};

function getFileSize(filename, getSize) {
  setTimeout(() => getSize(fileSizes[filename]), Math.random() * 500);
}

function sumFileSizes(filename1, filename2, getFilesSum) {
/=/ Variant 1 (more detaliled)
//  getFileSize(filename1, callWhenFirstGet);
//
//  function callWhenFirstGet(file1Size) {
//    getFileSize(filename2, callWhenSecondGet);
//
//    function callWhenSecondGet(file2Size) {
//      getFilesSum(file1Size + file2Size);
//    }
//  }

/=/ Variant 2 (ordinary callback-hell)
  getFileSize(filename1, (file1Size) => {
    getFileSize(filename2, (file2Size) => {
      getFilesSum(file1Size + file2Size);
    });
  });
}

sumFileSizes("testFile1", "testFile2", (sum) => {
  return sum; // 113
});
```

-> Реализация кода выше через `Promise`
```
let fileSizes = {
  testFile1: 65,
  testFile2: 48
};

function getFileSize(filename, cb) {
  setTimeout(() => cb(fileSizes[filename]), Math.random() * 500);
}

async function sumFileSizes(filename1, filename2, cb) {
  try {
    const size1 = await new Promise((resolve) => {
      getFileSize(filename1, resolve);
    });
    const size2 = await new Promise((resolve) => {
      getFileSize(filename2, resolve);
    });

    return cb(size1 + size2);
  } catch (error) {
    console.log(error);
  }
}

sumFileSizes("testFile1", "testFile2", (sum) => {
  return sum; /=/ 113
});
```

### _Promise.all `polyfil`_
 
```
const users = [
  { id: 1, name: "John", age: 25 },
  { id: 2, name: "Jane", age: 30 },
  { id: 3, name: "Alex", age: 35 },
  { id: 4, name: "Sarah", age: 28 },
  { id: 5, name: "Michael", age: 32 }
];

class DB {
  constructor(users) {
    this.users = users;
  }
  getUsersIds(cb) {
    const ids = [2, 1, 5, 4, 3];
    setTimeout(() => {
      cb(ids);
    }, 200);
  }
  getUserInfo(id, cb) {
    const user = this.users.find((el) => el.id === id);
    setTimeout(() => {
      cb(user);
    }, Math.random() * 200);
  }
}

const db = new DB(users);
const getUserInfo = db.getUserInfo.bind(db);
const getUsersIds = db.getUsersIds.bind(db);

function getUsersInfo(onLoad) {
  getUsersIds((idArr) => {
    const usersArr = [];
    let count = 0;

    for (let i = 0; i < idArr.length; i++) {
      getUserInfo(idArr[i], (user) => {
 ->     usersArr[i] = user;
        usersArr.push(user); /=/ Так уже не сработает!

				count += 1; /=/ проверяет, количество завершенных асинхронных вызовов
        if (count === idArr.length) {
          onLoad(usersArr);
          return;
        }
      });
    }
  });
}

getUsersInfo((users) => {
  console.log(users);
});
```
#promise_all #polyfil

В данном примере происходит `асинхронный` вызов `коллбэков`.

Условие `++count === idArr.length` проверяет, количество завершенных асинхронных вызовов `getUserInfo`.
Каждый раз, когда асинхронный вызов `getUserInfo` завершается, `count` увеличивается на 1. Когда `count` становится равным `idArr.length`, это означает, что все асинхронные вызовы `getUserInfo` завершились, и функция `onLoad` вызывается с массивом `usersArr`.

- `usersArr.push(user)`
  При использовании `push()`, цикл все так же раздает всем `коллбэкам` `id` пользователей для поиска нужного юзера на сервере. Но ответ приходит у всех `коллбэков` по разному.
  Следовательно и `push()`, (который находится в теле `callback`) происходит в разное время. Найденный "через час" пользователь просто встанет в конец массива

- `usersArr[i] = user;`
  При использовании жесткого `назначения позиции` в `массиве`, цикл все так же раздает всем `коллбэкам` `id` пользователей для поиска нужного юзера на сервере. И ответ у всех коллбэков все так же приходит по разному.

Но в данном случае сработает `замыкание`, функция запомнит какую позицию мы назначили для данного элемента в массиве. Теперь, независимо от порядка срабатывания `коллбэка`, элементы запишутся в той очередности, в которой `итерировались` элементы `idArr`

### _Аналогично через `then`_

```
function promiseAll(promises) {
  if (!promises.length) {
    return Promise.resolve([]);
  }

  return new Promise((resolve, reject) => {
    const arr = [];
    let count = 0;

    for (let i = 0; i < promises.length; i++) {
      promises[i]
        .then((prom) => {
          arr[i] = prom;

          if (++count === promises.length) {
            resolve(arr);
            return;
          }
        })
        .catch(reject);
    }
  });
}

const firstPromise = new Promise((resolve) =>
  setTimeout(() => resolve(300), 300)
);
const secondPromise = new Promise((resolve) =>
  setTimeout(() => resolve(200), 200)
);
const thirdPromise = new Promise((resolve) =>
  setTimeout(() => resolve(100), 100)
);

promiseAll([firstPromise, secondPromise, thirdPromise]).then(console.log);
/=/ [300, 200, 100]
promiseAll([]).then(console.log);
/=/ Promise<[]>
```
#promise_all #polyfil
