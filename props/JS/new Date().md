### _instanceof_

Позволяет проверить, принадлежит ли объект к определённому классу или является экземпляром определённого типа данных.

```
function checkDate(input) {
  if (input instanceof Date) {
    console.log('Входной параметр является объектом Date');
  } else {
    console.log('Входной параметр не является объектом Date');
  }
}

const input1 = new Date();
const input2 = '2021-01-01';

checkDate(input1); // Входной параметр является объектом Date
checkDate(input2); // Входной параметр не является объектом Date
```

-> Example: Classes
```
class Person {
  constructor(name) {
    this.name = name;
  }
}

const person = new Person('John');

console.log(person instanceof Person); // true
console.log(person instanceof Object); // true (все объекты в JavaScript также являются экземплярами Object)
console.log(person instanceof Date); // false
```

### _Invalid Date - isNaN()_

Вы можете идентифицировать `Invalid Date` с помощью метода `isNaN()`. 
Если преобразование с помощью `new Date()` прошло неудачно, `isNaN()` вернет `true`.  

```
const date = new Date();
if (isNaN(date)) {
  console.log('Преобразование не удалось');
} else {
  console.log('Преобразование прошло успешно');
}
```

### _.getTime() - от UNIX до new Date() _

В этом примере переменная `milliseconds` будет содержать количество миллисекунд, прошедших с полуночи 1 января 1970 года (также известной как "UNIX-эпоха") до текущего момента времени.

```
const date = new Date();
const milliseconds = date.getTime();
	
console.log(milliseconds);
```

### _new Date(null)_

`new Date(null)` -  вернёт количество миллисекунд, прошедшее с `01.01.1970`

### _Вычислить разницу между датами_

```
const date1 = new Date('2021-01-01');
const date2 = new Date('2021-02-01');

const differenceInMs = Math.abs(date2 - date1;
const differenceInDays = Math.ceil(differenceInMs / (1000 * 60 * 60 * 24));
```