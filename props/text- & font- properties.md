### _text-decoration_

Свойство text-decoration — составное. Оно раскладывается на отдельные свойства:

### _text-decoration-line_

- `underline` — подчёркивание;
- `line-through` — зачёркивание;
- `overline` — надчёркивание;
- `none` — убирает вышеперечисленные эффекты.

### _text-decoration-style_

- `solid` — сплошная линия;
- `double` — двойная линия;
- `dotted` — точечная линия;
- `dashed` — пунктирная линия;
- `wavy` — волнистая линия.

### _text-decoration-color_

```
.text {
	text-decoration: underline;
	text-decoration-color: rgb(255, 0, 0, 0.5);
}
```

### _text-transform_

- `lowercase`: Весь текст в строчных буквах.
- `uppercase`: Весь текст в заглавных буквах.
- `capitalize`: Каждое слово начинается с большой буквы.
- `none`: Отменяет изменение регистра.

### _white-space_

- `nowrap` — схлопывает лишние пробелы и отображает весь текст одной строкой без переносов;
- `pre` — сохраняет пробелы и переносы как в исходном коде аналогично тегу `<pre>`;
- `pre-wrap` — работает как значение pre, но добавляет автоматические переносы, если текст не помещается в контейнер;
- `normal` — режим по умолчанию: лишние пробелы и переносы строк схлопываются, текст переносится, пробелы в конце строк удаляются.

### _font-style_

- `normal` — обычное начертание;
- `italic` — курсивное начертание;
- `oblique` — наклонное начертание (`oblique 30deg`)

### _font-size_

```
font-size: xx-small;
font-size: x-small;
font-size: small;
font-size: medium;
font-size: large;
font-size: x-large;
font-size: xx-large;
font-size: xxx-large;
```

### *font-weight*

```
font-weight: normal;
font-weight: bold;

font-weight: 100;
font-weight: 200;
font-weight: 300;
font-weight: 400; /* normal */
font-weight: 500;
font-weight: 600;
font-weight: 700; /* bold */
font-weight: 800;
font-weight: 900;
```

### *Составное свойство font*

    font: 16px/26px "Arial", sans-serif;

Браузер «расшифрует» в такой набор обычных свойств и их значений:

    font-size: 16px;                  /* было задано в font */
    line-height: 26px;                /* было задано в font */
    font-family: "Arial", sans-serif; /* было задано в font */

    font-weight: normal;              /* не было задано в font */
    font-style: normal;               /* не было задано в font */
    font-variant: normal;             /* не было задано в font */