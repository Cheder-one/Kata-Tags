Мониторит документ на соответствие текущих `@media-запросов`
- Не нуждается в ручном обновлении через слушатель `"resize"`

```
const mediaQuerySmall = window.matchMedia("(max-width: 767.9px)");
const mediaQueryLarge = window.matchMedia("(min-width: 768px)");

console.log(mediaQuerySmall.matches);
console.log(mediaQueryLarge.matches);
```

```
const mediaQuery = window.matchMedia('(max-width: 600px)');

function handleMediaChange(event) {
    if (event.matches) {
        console.log("Экран узкий (ширина меньше 600px)")
    } else {
        console.log("Экран широкий (ширина больше 600px)")
    }
}

// Добавляем слушатель события "change" для отслеживания изменений медиа-запроса
mediaQuery.addEventListener('change', handleMediaChange);

// Вызываем функцию обработчика в первый раз для начального состояния
handleMediaChange(mediaQuery);
```

### *window.innerWidth*

Возвращает внутреннюю ширину окна. Сюда входит ширина вертикальной полосы прокрутки, если она имеется.
- Нуждается в ручном обновлении через слушатель `"resize"`

```
const heightOutput = document.querySelector("#height");
const widthOutput = document.querySelector("#width");

function updateSize() {
  heightOutput.textContent = window.innerHeight;
  widthOutput.textContent = window.innerWidth;
}

updateSize();
window.addEventListener("resize", updateSize);
```


