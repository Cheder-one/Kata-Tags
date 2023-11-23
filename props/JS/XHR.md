`XMLHttpRequest` – это встроенный в браузер объект, который даёт возможность делать HTTP-запросы к серверу без перезагрузки страницы.

Несмотря на наличие слова `XML` в названии, `XMLHttpRequest` может работать с любыми данными, а не только с `XML`. Мы можем загружать/скачивать файлы, отслеживать прогресс и многое другое.

### _Основы_

`XMLHttpRequest` имеет два режима работы: `синхронный` и `асинхронный`.
Чтобы сделать `асинхронный` запрос, нам нужно выполнить три шага:

1. Создать `объект` запроса `XMLHttpRequest`
``` 
let xhr = new XMLHttpRequest(); 
/=/ Конструктор не принимает аргументов
```
___
2. Инициализировать и `конфигурировать` `соединение`.
``` 
xhr.open(method, URL, [async, user, password])
```

Вызов `open`, вопреки своему названию, не открывает соединение. Он лишь `конфигурирует` запрос, но непосредственно отсылается запрос только лишь после вызова `send`.

- `method` – HTTP-метод. Обычно это `GET` или `POST`.
- `URL` – куда отправляется запрос: `строка`, может быть и `объект URL`.
- `async` – если указать `false`, тогда запрос будет выполнен `синхронно`.
- `user`, `password` – логин и пароль для базовой `HTTP-авторизации` (если требуется).

___
3. Установить соединение и послать запрос.
```
xhr.send([body])
```

Необязательный параметр `body` содержит тело запроса. 
Некоторые типы запросов, такие как `GET`, не имеют тела. А некоторые, как, например, `POST`, используют `body`, чтобы отправлять `данные на сервер`. 

___
4. Слушать события на `xhr`, чтобы получить ответ.

Это обычные события 
- `load` – событие происходит когда `получен` какой-либо `ответ`(включая ответы с `HTTP-ошибкой`, например `404`).  (*общение с сервером успешно*)
- `error` – когда запрос не может быть выполнен, например, `нет соединения` или `невалидный URL`. (*общение с сервером не успешно*)
- `progress` – происходит периодически во время `загрузки` ответа, сообщает о `прогрессе`.

**_! Слушатель необходимо добавлять перед отправкой `send()`_**

``` 
xhr.onload = function() {
  console.log(`Загружено: ${xhr.status} ${xhr.response}`);
};

/=/ Происходит, только когда общение с сервером не успешно
xhr.onerror = function() { 
  console.log(`Ошибка соединения`);
};

/=/ Запускается периодически
xhr.onprogress = function(event) { 
  /=/ event.loaded - количество загруженных байт
  /=/ event.lengthComputable = равно true, если сервер присылает заголовок Content-Length
  /=/ event.total - количество байт всего (только если lengthComputable равно true)
  console.log(`Загружено ${event.loaded} из ${event.total}`);
};
```
---

```
const url = "https://jsonplaceholder.typicode.com/users";  
  
const xhr = new XMLHttpRequest();  
xhr.open("GET", url);  
  
xhr.onload = () => {  
  if (xhr.status === 200) {  
    const users = JSON.parse(xhr.response);  
    console.log(users);  
  }  
};  
	==/OR/==  
xhr.responseType = "json";  

xhr.onload = () => {  
  if (xhr.status >= 400) {  
		console.error(xhr.response);
  } else {  
    console.log(xhr.response);  
  }  
};  

xhr.send();
```

### _Реализация с Promise_

```
const requestURL = "https://jsonplaceholder.typicode.com/users";  
  
function sendRequest(method, url, body = null) {  
  return new Promise((resolve, reject) => {  
    const xhr = new XMLHttpRequest();  
  
    xhr.open(method, url);  
  
    xhr.responseType = "json";  
    xhr.setRequestHeader('Content-Type', 'application/json')  
    /=/ Явно указываем серверу формат в котором отправляем данные  
  
    xhr.onload = () => {  
      if (xhr.status >= 400) {  
        reject(xhr.response);  
      } else {  
        resolve(xhr.response);  
      }  
    };  
  
    xhr.onerror = () => {  
      reject(xhr.response);  
    };  
  
    // xhr.send(body); /=/ При отправке преобразуется в string. [object Object]  
    xhr.send(JSON.stringify(body));  
  });  
}  
  
// sendRequest("GET", requestURL)  
//   .then((data) => console.log(data))  
//   .catch((err) => console.log(err));  
  
const body = {  
  name: 'username',  
  age: 23  
}  
  
sendRequest("POST", requestURL, body)  
  .then((data) => console.log(data))  
  .catch((err) => console.log(err));
```

### _Метод для конвертации доступен единожды_

```
const requestURL = "https://jsonplaceholder.typicode.com/users";  
  
fetch(requestURL).then((response) => {  
  console.log(response.json()); /=/ <state>: "fulfilled"
  console.log(response.json()); /=/ TypeError: Response.json: Body has already been consumed.  
});
```

![[Pasted image 20231104215138.png]]
