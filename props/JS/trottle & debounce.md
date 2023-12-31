### _Debounce_

**Debounce** — `кд` для срабатывания последнего вызова, `сброс кд` при нажатии.
Функция будет выполнена только тогда, когда после последней попытки вызова прошло определённое время. Задержка начинает заново отсчитываться с каждой новой попыткой вызова.
Например если повесить `debounce` на `onscroll` с временем `100ms`, то функция выполнится через `100ms` после прекращения `скрола`.

![[Pasted image 20231102105801.png]]

```
const debounce = (fn, delay) => {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => { fn.apply(this, args) }, delay);
  };
};
```

```
let counter = 0;
const fn = () => {
  counter++;
};

const debounce = (fn, delay) => {
  let lastTimer;
  return function (...args) {
    clearTimeout(lastTimer);
    lastTimer = setTimeout(() => { fn.apply(this, args) }, delay);
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

```
 const useDebounce = (fn, delay) => {
  const timerRef = useRef(null);

  useEffect(() => {
    return () => {
      clearTimeout(timerRef.current);
    };
  }, []);  /=/ Clear the timer when the component unmounts
  

  return function debouncedFn(...args) {
    clearTimeout(timerRef.current);
    timerRef.current = setTimeout(() => {
      fn.apply(this, args);
    }, delay);
  };
};
```

```
class Debounce {
  constructor(fn, delay) {
    this.timerRef = null;
    this.fn = fn;
    this.delay = delay;
  }

  debouncedFn(...args) {
    clearTimeout(this.timerRef);

    this.timerRef = setTimeout(() => {
      this.fn.apply(this, args);
    }, this.delay);
  }

  clearTimer() {
    clearTimeout(this.timerRef);
  }

  componentWillUnmount() {
    this.clearTimer();
  }
}
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

const throttle = (fn, delay) => {
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
    }, delay);
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

const throttle = (fn, delay) => {
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
    }, delay);
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
