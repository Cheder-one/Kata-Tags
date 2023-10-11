- `value = ++count` - **префикс**ный инкремент 
  (возвращает новое значение переменной после увеличения)
- `value = count++` - **постфикс**ный инкремент 
  (возвращает старое значение переменной перед увеличением)

```
let value = 5;
let newValue = ++value;
console.log(newValue); /=/ Вывод: 6
console.log(value); /=/ Вывод: 6

value = 5;
newValue = value++;
console.log(newValue); /=/ Вывод: 5
console.log(value); /=/ Вывод: 6
```
 