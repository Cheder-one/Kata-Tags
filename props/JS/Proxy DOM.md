объект `Proxy` - позволяет создавать ловушки для объектов, функций классов, позволяя перехватывать и изменять их поведение.  

### _Proxy для реактивности DOM_

**Реактивность** - способность программных компонентов (переменных, объектов или данных) `автоматически реагировать на изменения` в системе и `обновлять` свое `состояние`.

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reactivity with Proxy</title>
</head>
<body>

    <div id="app">
        <p>Counter: <span id="counter"></span></p>
        <button onclick="increment()">Increment</button>
    </div>

    <script>
        function createReactiveObject(target, onChange) {
            return new Proxy(target, {
                set(obj, prop, value) {
                    obj[prop] = value;
                    onChange();
                    return true;
                }
            });
        }

        /=/ Исходное состояние
        const state = createReactiveObject({
            counter: 0
        }, updateDOM);

        /=/ Функция обновления DOM
        function updateDOM() {
            document.getElementById('counter').innerText = state.counter;
        }

        /=/ Функция увеличения счетчика
        function increment() {
            state.counter++;
        }

        /=/ Инициализация DOM
        updateDOM();
    </script>

</body>
</html>
```

В этом примере создается объект `state`, который является реактивным с использованием `Proxy`. Когда значение свойства изменяется (в данном случае, `counter`), функция `updateDOM` вызывается `для обновления` соответствующего `элемента DOM`.

