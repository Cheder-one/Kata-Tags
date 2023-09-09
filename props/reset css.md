## *Сброс перед началом верстки *

Например чтобы обнулить внешние отступы у `<body>` и `<ul>` и точки
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

```
html {
  box-sizing: border-box;
}
*, *:before, *:after {
  box-sizing: inherit;
}
```

