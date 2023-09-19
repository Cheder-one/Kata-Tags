
- Переменные: Вы можете определить переменные для использования повторно в вашем коде стилей. 

```
$primary-color: #ff0000;
$font-size: 14px;

body {
  color: $primary-color;
  font-size: $font-size;
}
```

- Вложенность: Sass позволяет вам вкладывать правила стилей внутри других правил, что делает код более читаемым и структурированным.

```
nav {
  ul {
    margin: 0;
    padding: 0;

    li {
      display: inline-block;
    }
  }
}
```

- Миксины: Миксины позволяют вам определить набор стилей, которые могут быть повторно использованы в разных местах.

```
@mixin button($bg-color) {
  background-color: $bg-color;
  color: #fff;
  padding: 10px;
  border-radius: 5px;
}

.button-primary {
  @include button(#ff0000);
}

.button-secondary {
  @include button(#00ff00);
}
```

- Импорт файлов: Вы можете импортировать другие Sass файлы в основной файл стилей, чтобы разделить код на модули и улучшить организацию.

```
@import 'variables';
@import 'button';
@import 'navbar';
```

- Функции: Sass предоставляет набор встроенных функций, которые могут быть использованы для выполнения различных операций со значениями стилей.

```
.container {
  width: percentage(0.5); // 50%
  height: round(1.5); // 2
  color: darken(#ff0000, 10%); // #cc0000
}
```

