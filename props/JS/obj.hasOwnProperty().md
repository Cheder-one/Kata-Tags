Проверяет на наличие ключа, но значение может быть `null`

```
const object1 = {};
object1.property1 = 42;
object1.property2 = null;


console.log(object1.hasOwnProperty('property1'));
/=/ Expected output: true

console.log(object1.hasOwnProperty('property2'));
/=/ Expected output: true

console.log(object1.hasOwnProperty('42'));
/=/ Expected output: false
```

