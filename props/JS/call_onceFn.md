
**-> Реализация вызова функции только единожды:**

```
function once(func) {
  let isOnce = true;

  return function (...args) {
    if (isOnce) {
      isOnce = false;
      return func.apply(this, args);
    }
  };
}
==/OR/==
function once(func) {
  let isOnce = true;

  return function (...args) {
    if (isOnce) {
      isOnce = false;
      return func(...args);
    }
  };
}


const fn = (a, b, c) => {
  return a + b + c;
};

const onceF = once(fn);
onceF(1, 2, 3); /=/ 6
onceF(1, 2, 3); /=/ undefined
```
