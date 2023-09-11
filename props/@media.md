## _Адаптивный макет сайта_

Рассмотрим пример адаптивного макета, состоящего из 2 блоков, который на разных устройствах выглядит по-разному.

- на смартфонах и планшетах (устройствах с очень маленьким размером экрана) блоки должны располагаться вертикально, т.е. один под другим;
- на ноутбуках (устройствах со средним размером экрана) блоки должны располагаться горизонтально (1 блок - 33.3%, 2 блок - 66.7%);
- на десктопах (устройствах с большим размером экрана) тоже горизонтально, но с другими размерами (1 блок - 25%, 2 блок - 75%)

![[Pasted image 20230909012310.png]]

```
<style>
  body {
    margin: 0;
  }

  .container {
    display: flex;
    flex-wrap: wrap;
  }

  .aside, .main {
    width: 100%;
    min-height: 1px;
  }

  @media (min-width: 992px) {
    .aside {
      flex: 0 0 33.333333%;
      max-width: 33.333333%;
      order: 1;
    }
    .main {
      flex: 0 0 66.666667%;
      max-width: 66.666667%;
      order: 2;
    }
  }

  @media (min-width: 1400px) {
    .aside {
      flex: 0 0 25%;
      max-width: 25%;
    }
    .main {
      flex: 0 0 75%;
      max-width: 75%;
    }
  }
</style>

<div class="container">
  <main class="main">
    MAIN
  </main>
  <aside class="aside">
    ASIDE
  </aside>
</div>
```

---

## _CSS медиа-запросы (media queries)_

Медиа-запросы (media queries) – позволяют управлять стилями элементов в зависимости от значений технических параметров устройств.

### _Подключение `viewport`_

Но при создании адаптивных веб-страниц также необходимо обратить внимание на метатег `viewport`. Данный тег обеспечивает корректное отображение адаптивных дизайнов сайтов на экранах устройств, имеющих высокую плотность пикселей. Иными словами, он устанавливает соответствие между CSS и физическим разрешением веб-страницы.

Подключение метатега `viewport` к странице осуществляется так:

```
<meta name="viewport" content="width=device-width, initial-scale=1">
```

### _Синтаксис_

![[Pasted image 20230909013703.png]]

-> Пример медиа-запроса с комбинированием нескольких условий:

```
@media screen and (min-width: 992px) and (max-width: 1199.98px) {
	...
}
```

```
.some-element {
  /=/ Стили для общих элементов
	/=/ которые применяются как на mobile, так и на desktop устройствах
}

/=/ Стили для мобильных устройств (меньше 768px)
@media screen and (max-width: 768px) {
  /=/ Скрыть элемент на мобильных устройствах
  .mobile-hidden-element {
    display: none;
  }

  .mobile-specific-element {
    /=/ Стилизация элемента, специфичная для мобильных устройств
  }
}

/=/ Стили для desktop устройств (больше 768px)
@media screen and (min-width: 769px) {
  /=/ Скрыть элемент на desktop устройствах
  .desktop-hidden-element {
    display: none;
  }

  .desktop-specific-element {
    /=/ Стили для desktop элементов
  }
}
```

### _Типы устройств_

В `@media` можно указывать определённые типы устройств:

- `all` – для всех;
- `print` – для принтеров и в режиме предварительного просмотра страницы перед печатью;
- `screen` – для устройств с экранами;
- `speech` – для программ чтения с экрана.

Например, первый `@media` только для экранов:

```
@media screen { ... }
```

```
@media screen, print { ... }
```

### _Логические операторы_

Логические операторы `and`/ `,` / `not` / `only (устарело)` предназначены для создания сложных медиа-запросов.

### _and_

Оператор `and` используется для объединения нескольких условий.
Результат будет `true`, когда каждое из них будет истинным.

Например, следующий `@media` будет применяться только при выполнении всех трёх условий (это `экран`, `width >= 1200px` и ориентация `landscape`):

```
@media screen and (min-width: 1200px) and (orientation: landscape) {
	...
}
```

### _, (запятая)_

Применение стилей, когда необходимо лишь выполнение **одного** из указанных условий.
(аналог "или" `||`)

В этом примере стили будут применяться к странице в двух случаях.
Когда `width >= 544px` или ориентация `portrait`.

```
@media (min-width: 544px), (orientation: landscape) {
	...
}
```

### _not_

Ключевое слово `not` используется для отрицания.

#### _`not` в комбинации с`and`:_

При использовании `not` с `and` отрицание работает для всего медиа-запроса.
При этом, когда указываем `not` **необходимо обязательно задавать тип устройства**.

-> Например, применим стили только в том случае, когда:

- **не** (`экран` и` width >= 411px` и `height >= 731px`).

```
@media not screen and (min-width: 411px) and (min-height: 731px) {
	...
}
```

#### _`not` в комбинации с`,`:_

При использовании `not` в выражении с `запятой` он добавляет отрицание только для этой части.

-> Например, применим стили когда **истинно** следующее условие:

- **не** `экран` **или** **не** `width >= 411px`.

```
@media not screen, not (min-width: 411px) {
	...
}
```

### _Медиа-характеристики_

Каждая характеристика в `@media` должна быть заключена в круглые скобки.

Применяться стили указанные в `@media` будут также как раньше, т.е. только в том случае, когда результат вычисления **всего выражения** будет являться истиной.

### _width - ширина экрана в`viewport`_

-> Например, применим CSS только для `viewport` с `шириной 320px`.

```
@media (width: 320px) { ... }
```

#### _Диапазон ширины `min-width` и `max-width`_

Для определения диапазона можно использовать `min-width` и `max-width`.

-> Например, `@media` для ширины `viewport` от `576px` до `1200px`:

```
@media (min-width: 576px) and (max-width: 1199.98px) { ... }
```

Для ширины больше `768px`:

```
@media (min-width: 768px) { ... }
```

Если нужно меньше `1400px`:

```
@media (max-width: 1399.98px) { ... }
```

### _Условия высоты `height` `min-height` `max-height`_

Для задания условий в отношении высоты `viewport` можно использовать `height`, `min-height` и `max-height`.

-> Например, `@media` для высоты viewport больше `720px`:

```
@media (min-height: 720px) { ... }
```

### _orientation - альбомная/портретная_

С помощью `orientation` можно установить те или иные стили в зависимости от того, в каком режиме (альбомном или портретном) отображается сайт.

-> Например, в зависимости от `orientation` `viewport` будем отображать разные картинки:

```
@media (orientation: landscape) {
  .cover { background: url(bg-l.png) no-repeat; }
}

@media (orientation: portrait) {
  .cover { background: url(bg-p.png) no-repeat; }
}
```

### _aspect-ratio - соотношение сторон_

Характеристики `aspect-ration`, `min-aspect-ratio` и `max-aspect-ratio` позволяют задавать стили в зависимости от соотношения сторон `viewport`.

```
/* Minimum aspect ratio */
@media (min-aspect-ratio: 9/16) {
  .header {
    background-color: #0dcaf0;
  }
}

/* Maximum aspect ratio */
@media (max-aspect-ratio: 16/9) {
  .header {
    background: #ffc107;
  }
}

/* Exact aspect ratio */
@media (aspect-ratio: 1/1) {
  .header {
    background: #6c757d;
  }
}
```

### _resolution - плотность пикселей_

Характеристики `resolution`, `min-resolution` и `max-resolution` можно использовать, когда нужно задать стили в зависимости от плотности пикселей устройства.

-> Например, установим другой размер шрифта для устройств с плотностью пикселей на дюйм более `150dpi`:

```
/* Default */
p {
  font-size: 16px;
}

/* Minimum resolution */
@media (min-resolution: 150dpi) {
  p {
    font-size: 14px;
  }
}
```

Стили для печати страницы с плотностью пикселей больше `300dpi`:

```
@media print and (min-resolution: 300dpi) { ... }
```

## _Активация таблиц стилей в зависимости от условий `@media`_

При подключении таблицы стилей можно с помощью атрибута `media` установить медиа-запросы и тем самым определить условия, когда они должны использоваться.

```
<link
  rel="stylesheet"
  media="screen and (max-width: 991.98px)"
  href="/assets/mobile.css"
>
<link
  rel="stylesheet"
  media="screen and (min-width: 992px)"
  href="/assets/desktop.css"
>
```

Кроме `<link>`, их также можно использовать в `@import`:

```
@import url(mobile.css) screen and (max-width: 991.98px);
@import url(desktop.css) screen and (min-width: 992px);
```

### _Медиа-запрос в JS `matchMedia()`_

`matchMedia()` является методом объекта `window`.

```
const mediaQuery = window.matchMedia('(min-width: 768px)');
if (mediaQuery.matches) {
  alert('Документ соотвествует медиа-запросу!');
}
```

-> Например, установим цвет фона `<body>` в зависимости от ширины области просмотра:

```
if (window.matchMedia('screen and (width >= 768px)').matches) {
  document.body.style.backgroundColor = 'black';
} else {
  document.body.style.backgroundColor = 'yellow';
}
```

**! НО** этот код выполнится один раз и при изменении размера области просмотра цвет фона `<body>` не обновится.

Если нам нужно реагировать на изменения статуса медиа-запроса, то можно воспользоваться методом `addListener()`. Этот метод принимает функцию обратного вызова, которая будет вызываться каждый раз при изменении статуса медиа-запроса:

```
const mediaQuery = window.matchMedia('screen and (width >= 768px)');

const handleBreakpointChange = (e) =>{
  document.body.style.backgroundColor = e.matches ? 'black' : 'yellow';
}

mediaQuery.addListener(handleBreakpointChange);

handleBreakpointChange(mediaQuery);
```

Теперь функция `handleBreakpointChange` будет вызываться каждый раз при изменении статуса медиа-запроса.

Удаления добавленного обработчика осуществляется с помощью метода `removeListener()`:

Например, эту возможность можно применить для асинхронной загрузки картинок в зависимости от того какой размер viewport имеет устройство (браузер).
