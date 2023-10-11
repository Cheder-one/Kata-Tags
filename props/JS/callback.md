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
