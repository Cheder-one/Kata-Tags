С помощью него можно трансформировать псевдомассив элементов, в массив:

```
const divs = document.querySelector('div'); /=/ Псевдомассив
const nodes = [...divs]; /=/ Массив

nodes.map(el => console.log(el)) /=/ Можем применять не только forEach()
```

### _...rest-operator_

```
const numbers = [1, 2, 3, 4, 5]
const [a, b, ...other] = numbers
```

```
function sum(a, b, ...rest) {
  console.log(rest); /=/ [ 3, 4, 5 ]
	return a + b + rest.reduce((acc, el) => acc + el);
}

const nums = [1, 2, 3, 4, 5]
sum(...nums); /=/ 15
```

### _Деструктуризация_
![[destructuring]]