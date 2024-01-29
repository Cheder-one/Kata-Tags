## _Сброс перед началом верстки_

```
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

```
html, 
body {
	margin: 0;
	padding: 0;
}
ul, ol {
  list-style: none;
}
```

### *Задать border-box*

```
html {
  box-sizing: border-box;
}
*, *:before, *:after {
  box-sizing: inherit;
}
```

### *Обнулить все стили*

Cбросит все стили по умолчанию кнопки:
```
button {
  all: initial;
}
```

```
* {
  margin: 0;
  padding: 0;
}

html {
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: inherit;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  all: unset;
}

button,
a {
  all: unset;
  cursor: pointer;
}

input,
textarea {
  all: unset;
  box-sizing: border-box;
  // padding-left: 16px;
}

ul,
ol,
li {
  list-style: none;
}

// ::-webkit-scrollbar {
//   height: 3px;
// }
```

```
/* reset.css */

/* Resetting margins, paddings, and borders */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Resetting typography */
body, h1, h2, h3, p, ul, ol {
  font-family: inherit;
  font-size: 100%;
  font-weight: inherit;
  margin: 0;
  padding: 0;
  border: 0;
  vertical-align: baseline;
}

/* Other reset styles go here */
```