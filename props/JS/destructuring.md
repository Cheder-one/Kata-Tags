```
function calcValues(a, b) {
	return [a + b, , a * b, a / b];
}

const [sum, sub = "Вычитания нет", , ...other] = calcValues(42, 10);
/=/ [ 52, , 420, 4.2 ]
console.log(sub) /=/ Вычитания нет
```

-> Example with Obj & Fn

```
const {
  name: firstName = 'Без имени',
  age,
  car = 'Машины нет',
  address: {city: homeTown, country}
} = person

// const {name, ...info} = person
// console.log(name, info)

function logPerson({name: firstName = '111', age}) {
  console.log(firstName + ' ' + age)
}
```
