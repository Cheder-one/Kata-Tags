Метод `fetch()` позволяет получать данные по сети `асинхронно`.
Возвращает `Promise`. Когда он выполнится, получим ответ `response` 

```
let promise = fetch(url, [options])
```

```
const getAllTodoes = () => {
	fetch('https://jsonplaceholder.typicode.com/todos', {
		method: 'GET', /=/ GET, POST, DELETE...

		headers: { 'Content-Type': 'application/json' } 
	  /=/ При `POST` указываем серверу формат в котором отправляем данные

    body: JSON.stringify(body), 
    /=/ При `POST` конвертируем объект в JSON (иначе будет [object Object])  
	})
}
```

Без `options` это простой `GET-запрос`, скачивающий содержимое по адресу `url`.

- У `fetch`, у его тела ответа, имеются встроенные `методы` для `получения` и `конвертации` тела ответа, например `response.json()`. Можем вызвать `единожды`. Тоже возвращает `Promise`.
- Так же у `fetch`-ответа имеются св-ва:
	-  **`status`** – код статуса `HTTP-запроса`, например `200`.
	- **`ok`** – логическое значение: будет `true`, если код `HTTP-статуса` в диапазоне` 200-299`.

```
const requestURL = "https://jsonplaceholder.typicode.com/users";  
  
function sendRequest(url, method, header = null, body = null) {  
	const options = {
    method,
    headers: {
      'Content-Type': 'application/json',
      ...header,
    },
    body: bodyData ? JSON.stringify(bodyData) : null 
    /=/ При `POST` конвертируем объект в JSON (иначе будет [object Object])    
  };
  
  return fetch(url, options)  /=/ Возвращает Promise  
    .then(response => {  
      if (response.ok) {  
        return response.json() /=/ Встроенный метод конвертации ответа в JSON  
      }  
      
      return response.json().then(error => {  
        const err = new Error('Что-то пошло не так')  
        err.data = error  
        throw err  
      })  
    })  
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
---

```
const getAllTodoes = () => {
	fetch('https://jsonplaceholder.typicode.com/todos', {
	method: 'GET', /=/ GET, POST, DELETE..
})
	.then((responseValue) => {
		if (!responseValue.ok) { /=/ Eсли HTTP-статус в диапазоне 200-299
			/=/ ok - произошел ли запрос успешно
			throw new Error('Ошибка запроса');
			/=/ throw - выбрасывает ошибку и переводит в блок .catch()
		}
		return responseValue.json(); /=/ Декодирование запроса
	})
	.then((todoes) => {
		/=/ Передаем дальше декодированный запрос
		todoes.forEach((el, i, arr) => {
			const todoHTML = createTodoElement(el.title);
			dataContainer.append(todoHTML);
		});
	})
	.catch((error) => {
		console.log('error:', error);
	})
	.finally(() => {
		toggleLoader();
	})
};
getAllTodoes()
```

-> `try..catch`
```
const url = `https://api.github.com/users`;

async function fetchData() {
	try {
	  const response = await fetch(url);
    const jsonData = await response.json();

    outputTable(jsonData);
	} catch (err) {
		console.error(err);
  } finally {
		const loader = document.getElementById("loader");
    loader.style.display = "none";
  }
}

fetchData()
```

### _Структура API клиента_

```
class SwapiService   {
  #apiBase = 'https://swapi.dev/api/';

  async getResources(url) {
    const response = await fetch(`${this.#apiBase}${url}`);

    if (!response.ok) {
      throw new Error(
        `Could not fetch ${url}, received ${response.status}`
      );
    }
    return await response.json();
  }

  getAllPeople = async () => {
    const people = await this.getResources('people/');
    return people.results;
  };

  getAllPerson = async (id) => {
    return this.getResources(`people/${id}`);
  };
 
}

const swapi = new SwapiService();

swapi.getAllPeople().then((body) => {
  console.log(body);
});

export default SwapiService;
```

### _Заголовки ответа_

Заголовки ответа хранятся в похожем на `Map` объекте `response.headers`.
Это не совсем `Map`, но мы можем использовать такие же методы, как с `Map`, чтобы получить заголовок по его имени или перебрать заголовки в цикле:

``` 
let response = await fetch(
	'https://api.github.com/repos/javascript-tutorial/en.javascript.info/commits'
);

/=/ Получить один заголовок
console.log(response.headers.get('Content-Type')); /=/ application/json harset=utf-8

/=/ Перебрать все заголовки
for (let [key, value] of response.headers) {
  console.log(`${key} = ${value}`);
}
```

### _POST-запрос_

Код отправляет объект `user` как `JSON`:
``` 
let user = {
  name: 'John',
  surname: 'Smith'
};

let response = await fetch('/article/fetch/post/user', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json;charset=utf-8'
  },
  body: JSON.stringify(user)
});

let result = await response.json();
console.log(result.message);
```

Заметим, что так как тело запроса `body` – строка, то заголовок `Content-Type` по умолчанию будет `text/plain;charset=UTF-8`.

Но, так как мы посылаем `JSON`, то используем параметр `headers` для отправки вместо этого `application/json` - правильный `Content-Type` для `JSON`.

### _[Отправка изображения](https://learn.javascript.ru/fetch#otpravka-izobrazheniya)_

Мы можем отправить `бинарные` данные при помощи `fetch`, используя объекты `Blob` или `BufferSource`.

