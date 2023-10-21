**-> Example 1**

```
class EventEmitter {
  #listeners = {
    // eventName: [callback, callback, ...]
  };

  #getCallbacksFor(eventName) {
    return this.#listeners[eventName] ?? [];
  }
  #setCallbacksFor(eventName, listeners) {
    /=/ Проверка для избежания установки [eventName]: []
    if (listeners.length === 0) {
      delete this.#listeners[eventName];
    } else {
      this.#listeners[eventName] = listeners;
    }
  }

  subscribe(eventName, callback) {
    const subs = this.#getCallbacksFor(eventName);
    subs.push(callback);

    this.#setCallbacksFor(eventName, subs);

    return () => this.unsubscribe(eventName, callback);
  }

  unsubscribe(eventName, callback) {
    const subs = this.#getCallbacksFor(eventName)
		const filterSubs = subs.filter((func) => func !== callback);
		/=/ Может вернуть пустой []

		this.#setCallbacksFor(eventName, filterSubs);
  }

  dispatch(eventName, data) {
    /=/ Получаем массив коллбэков нужного event-а.
		const subs = this.#getCallbacksFor(eventName);
		subs.forEach((callback) => callback(data));
    /=/ Проходимся по всем callbacks и вызываем их с data.
  }
}


const eventEmitter = new EventEmitter();

/=/ Подписка на событие - "сделать то-то, когда..."
eventEmitter.subscribe("on", () => {
  console.log("Лампочка №1 включена");
});

const unsubLamp2 = eventEmitter.subscribe("on", () => {
  console.log("Лампочка №2 включена");
});

eventEmitter.subscribe("on", () => {
  console.log("Адронный коллайдер запущен");
});

/=/ Инициируем событие (например, когда была нажата кнопка)
/=/ Запустит все callbacks-функции которые были подписаны на событие 'on'
eventEmitter.dispatch("on");

unsubLamp2();
/=/ Вызываем `unsubscribe` через вернувшийся callback из `subscribe`

eventEmitter.dispatch("on");
/=/ Запустит только Лампочку №1 и Коллайдер
```

**-> Example 2**

```
class EventEmitter {
  constructor() {
    this.events = {};
  }

  emit(eventName, data) {
    const event = this.events[eventName];
    if( event ) {
      event.forEach(fn => {
        fn.call(null, data);
      });
    }
  }

  subscribe(eventName, fn) {
    if(!this.events[eventName]) {
      this.events[eventName] = [];
    }

    this.events[eventName].push(fn);
    return () => {
      this.events[eventName] = this.events[eventName].filter(eventFn => fn !== eventFn);
    }
  }
}
```

**-> Example 1.1 (Modified)**

```
class EventEmitter {
  constructor() {
    this.listeners = {};
    this.ranBefore = {};
  }

  getCallbacksFor(eventName) {
    return this.listeners[eventName] || [];
  }
  setCallbacksFor(eventName, listeners) {
    if (listeners.length === 0) {
      delete this.listeners[eventName];
    } else {
      this.listeners[eventName] = listeners;
    }
  }

  on(eventName, callback) {
    const subs = this.getCallbacksFor(eventName);
    subs.push(callback);

    this.setCallbacksFor(eventName, subs);

    return () => this.off(eventName, callback);
  }

  off(eventName, callback) {
    const subs = this.getCallbacksFor(eventName);
    const filterSubs = subs.filter((func) => func !== callback);

    this.setCallbacksFor(eventName, filterSubs);
  }

  once(eventName, callback) {
    const isOnce = !Object.keys(this.ranBefore).includes(eventName);
    if (isOnce) {
      const unsubEvent = this.on(eventName, callback);
      this.ranBefore = { [eventName]: unsubEvent };
    }
  }

  emit(eventName, args) {
    const subs = this.getCallbacksFor(eventName);
    subs.forEach((callback) => callback(args));

    const unsubOnceEvent = this.ranBefore[eventName];
    if (unsubOnceEvent) unsubOnceEvent();

    // return subs.map((callback) => callback(args));
  }
}

class BroadcastEventEmitter extends EventEmitter {
  getAllCallbacks() {
    return Object.values(this.listeners).flat();
  }

  emit(eventName, ...args) {
    let subs = this.getCallbacksFor(eventName);
    if (eventName === "*") subs = this.getAllCallbacks();

    subs.forEach((callback) => callback(...args));

    const unsubOnceEvent = this.ranBefore[eventName];
    if (unsubOnceEvent) unsubOnceEvent();

    // return subs.map((callback) => callback(args));
  }
}

// let h1 = document.querySelector("h1");
// let input = document.querySelector("input");
// let button = document.querySelector("button");

// let emitter1 = new EventEmitter();

// emitter1.on("event:name-changed", (data) => {
//   h1.innerHTML = `New value is: ${data.name}`;
// });

// button.addEventListener("click", () => {
//   emitter1.emit("event:name-changed", { name: input.value });
// });

//----------------------------

let emitter = new EventEmitter();

const multiplyTwo = (num, dick) => num * 2;
const multiplyThree = (num, duck) => num * 3;

const divideTwo = (num) => num / 2;
const divideThree = (num) => num / 3;

// Добавляем для события multiplication два обработчика
emitter.on("multiplication", multiplyTwo);
emitter.on("multiplication", multiplyThree);

// Вызываем событие multiplication, должны вызвать все обработчики для этого события - multiplyTwo и multiplyThree
emitter.emit("multiplication", 2);
// -> 4
// -> 6

// Удалим обработчик multiplyThree для события multiplication
emitter.off("multiplication", multiplyThree);

// Еще раз вызываем событие multiplication, теперь срабатывает только один обработчик multiplyTwo
emitter.emit("multiplication", 2);
// -> 4

// Создадим новое событие divideTwo и добавим два обработчика:
// divideTwo - срабатывает всегда, когда вызывается событие division (до тех пор, пока не удалим этот обработчик)
//  divideThree - сработает только ОДИН раз, во время первого ВЫЗОВА события division
emitter.on("division", divideTwo);
emitter.once("division", divideThree);

// Вызываем событие division - срабатывают обработчики divideTwo и divideThree
emitter.emit("division", 6);
// -> 3
// -> 2

// Вызываем еще раз событие division - срабатывает ТОЛЬКО обработчики divideTwo
emitter.emit("division", 6);
// -> 3

// Вызываем еще раз событие division - срабатывает ТОЛЬКО обработчики divideTwo
emitter.emit("division", 6);
// -> 3

//----------------------------
let broadcastEmitter = new BroadcastEventEmitter();

broadcastEmitter.on("multiplication", multiplyTwo);
broadcastEmitter.on("multiplication", multiplyThree);
broadcastEmitter.on("division", divideTwo);
broadcastEmitter.on("division", divideThree);

// Вызываем все события (multiplication и division) => все обработчики для всех событий будут вызваны.
// Для события multiplication - вызовутся обработчики multiplyTwo и multiplyThree.
// Для события division - вызовутся обработчики divideTwo и divideThree.
broadcastEmitter.emit("*", 6);
// -> 12
// -> 18
// -> 3
// -> 2
```
