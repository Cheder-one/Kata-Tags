### _Debounce_

**Debounce** — `кд` для срабатывания последнего вызова, `сброс кд` при нажатии.
Функция будет выполнена только тогда, когда после последней попытки вызова прошло определённое время. Задержка начинает заново отсчитываться с каждой новой попыткой вызова.
Например если повесить `debounce` на `onscroll` с временем `100ms`, то функция выполнится через `100ms` после прекращения `скрола`.

![[Pasted image 20231102105801.png]]

```
const debounce = (fn, debounceTime) => {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => { fn.apply(this, args) }, debounceTime);
  };
};
```

```
let counter = 0;
const fn = () => {
  counter++;
};

const debounce = (fn, debounceTime) => {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => { fn.apply(this, args) }, debounceTime);
  };
};

const debouncedFn = debounce(fn, 200);

setTimeout(debouncedFn, 0);
setTimeout(debouncedFn, 100);
setTimeout(debouncedFn, 200);
setTimeout(debouncedFn, 300);
setTimeout(debouncedFn, 400);

setTimeout(function () {
  console.log(counter); // 1
}, 1000);
```

### _Throttling_

**Throttling** — `кд` между вызовами (проредить вызовы)
Функция будет выполняться не чаще одного раза в указанный период, даже если она будет вызвана много раз в течение этого периода.
Например если повесить `throttle` на `onscroll` с временем `100ms`, то функция будет выполнятся каждые `100ms` пока происходит скролинг.

![[Pasted image 20231102105840.png]]

**-> Простая версия**

```
let counter = 0;
const fn = () => {
  counter++;
};

const throttle = (fn, throttleTime) => {
  let isReady = true;

  return function (...args) {
    if (!isReady) {
      return;
    } else {
      fn.apply(this, args);
      isReady = false;
    }
    setTimeout(() => {
      isReady = true;
    }, throttleTime);
  };
};

const throttledFn = throttle(fn, 500);
/=/ функция может быть вызвана не чаще, чем раз в 500 мс

const intervalId = setInterval(throttledFn, 100);
setTimeout(() => clearInterval(intervalId), 1000); 
/=/ удаляем интервал через 10 вызовов

setTimeout(function () {
  console.log(counter); /=/ 2
}, 1100);
```

**-> Полная версия с последим вызовом**

```
let counter = 0;
const fn = () => {
  counter++;
};

const throttle = (fn, throttleTime) => {
  let isReady = true;
  let lastArgs = null;
  let lastThis = null;

  return function wrapper(...args) {
    if (!isReady) {
      lastArgs = args;
      lastThis = this;
      return;
    } else {
      fn.apply(this, args);
      isReady = false;
    }

    setTimeout(() => {
      isReady = true;

      if (lastArgs) {
        wrapper.apply(lastThis, lastArgs);
        lastArgs = null;
        lastThis = null;
      }
    }, throttleTime);
  };
};

const throttledFn = throttle(fn, 500);
/=/ функция может быть вызвана не чаще, чем раз в 500 мс

const intervalId = setInterval(throttledFn, 100);
setTimeout(() => clearInterval(intervalId), 1000); 
/=/ удаляем интервал через 10 вызовов

setTimeout(function () {
  console.log(counter); /=/ 3
}, 1100);
```
