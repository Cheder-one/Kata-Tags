## _Подключение веб-шрифтов_

**! Внимание**
**Перед подключением необходимо распаковать zip**
В стандартном подходе для подключения шрифтов веб-браузеры поддерживают форматы `.ttf`, `.otf`, `.woff` и `.woff2`.

---

Подключение производится с помощью CSS-правила `@font-face`.
Читается как `«эт-правило font-face»`.

```
@font-face {
    font-family: "Roboto";
    src:
        local("Roboto Regular"),
        url("roboto.woff") format("woff");
}
```

```
@font-face {
	font-family: "TT Lakes";
	src: url("./assets/font/TTLakes/TTLakes-Regular.ttf") format("truetype");
}
```

### _Применение шрифта_

```
body > h1 {
  color: #1b1c21;
  font-family: TT Lakes Bold;
  font-size: 28px;
  font-style: normal;
  font-weight: 700;
  line-height: 40px;
  letter-spacing: -0.6px;
}
body > div {
  color: #1b1c21;
  font-family: TT Lakes;
  font-size: 14px;
  font-style: normal;
  font-weight: 400;
  line-height: 18px;
  letter-spacing: 0.2px;
}
```
