### _Переменные_

Вы можете определять переменные для хранения значений, таких как цвета, размеры и шрифты, что делает код более читаемым и облегчает изменение стилей на всем сайте.

  ```
  $primary-color: #3498db;
  $font-family: "Helvetica, Arial, sans-serif";

  body {
    font-family: $font-family;
    background-color: $primary-color;
  }

.checkbox_wrapper {
  :global { /=/ Использование global 
    .ant-checkbox {
      border-color: #2196f3;
    }
	}
}
  ```

Вынос в переменные:
- цвета
- размеры шрифтов и интерлиньяж (все значения интерлиньяжа можно не выносить в переменные, а задавать его в отн. единицах)
- брейкпоинты.
- Для средних и крупных проектов определяйте в переменных цвета ссылок, бордюры, тени и прочие часто использующиеся величины.
- Если при стилизации конкретных блоков указываете размер шрифта через переменную, указывайте интерлиньяж тоже через переменную, или через мат. операцию (от базового интерлиньяжа или от размера шрифта), или в относительных единицах (em).
- Отделяйте смысловые блоки с переменными пустыми строками.
- Используйте БЭМ-именование для переменных.

```
$color-main:                  #0275d8;
$color-success:               #5cb85c;
$color-danger:                #d9534f;

$text-color:                  $gray-darkest;
$text-color--muted:           $gray;

$font-size:                   1.6rem;
$font-size--h1:               3rem;
$font-size--small:            0.75em;

$font-family:                 'Roboto', Arial, sans-serif;

$screen-xs:                   0;
$screen-sm:                   480px;
$screen-md:                   768px;
$screen-lg:                   992px;
$screen-xl:                   1200px;
```

### _Вложенность_

SCSS позволяет вкладывать селекторы внутри других селекторов, что делает код более структурированным и удобным для чтения:

  ```
  .container {
    padding: 20px;

    p {
      font-size: 16px;
    }
    a {
      color: $primary-color;
    }
  }
  ```

![[Pasted image 20230926235118.png]]

### _Наследование и Шаблоны_

Позволяет наследовать стили из одного селектора и применять их к другому селектору.
`Класс-шаблон` - особый тип классов, который выводится только при использовании расширения - это позволит сохранить ваш скомпилированный CSS чистым и аккуратным.

`|>` `SCSS`
```
/=/ This CSS will print because %message-shared is extended. 
%message-shared {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

/=/ This CSS won't print because %equal-heights is never extended.
%equal-heights {
  display: flex;
  flex-wrap: wrap;
}

.message {
  @extend %message-shared;
}

.success {
  @extend %message-shared;
  border-color: green;
}
```
`|>` `CSS`
```
.message, .success, .error, .warning {
  border: 1px solid #ccc;
  padding: 10px;
  color: #333;
}

.success {
  border-color: green;
}
```

### _Указание комбинированного класса_

SCSS позволяет вкладывать селекторы внутри других селекторов, что делает код более структурированным и удобным для чтения:

```
-> class="b-brand-slider swiper"

.b-brand-slider {
  &.swiper {
    //
  }
}
```

### _Миксины_

Миксины позволяют определить набор стилей и повторно использовать их в разных селекторах. Это полезно для создания кастомных стилей, которые могут быть использованы в нескольких местах. Пример:

  ```
  @mixin button($background, $color) {
    background-color: $background;
    color: $color;
    padding: 10px 20px;
  }

  .primary-button {
    @include button($primary-color, white);
  }
  .secondary-button {
    @include button(#e74c3c, white);
  }
  ```

```
@mixin slide-order-font {
  color: #fff;
  text-align: right;
  font-family: TT Lakes Bold;
  font-size: 12px;
  font-style: normal;
  font-weight: 700;
  line-height: 200%;
  letter-spacing: -0.15px;
  text-transform: uppercase;
}

.my-element {
  @include slide-order-font;
}
```

### _Функции_

SCSS предоставляет встроенные функции для выполнения операций над значениями, такие как `darken`, `lighten`, `rgba`, `mix` и другие. Эти функции облегчают манипулирование цветами и другими свойствами.

  ```
  .button {
    background-color: darken($primary-color, 10%);
    color: lighten($primary-color, 20%);
  }
  ```

### _Импорт файлов_

Вы можете разделить свой CSS на несколько файлов и затем импортировать их в одном месте, что улучшает организацию кода и управление проектом.

  ```
  // В основном файле стилей
  @import 'variables';
  @import 'buttons';
  @import 'forms';
  ```

![[Pasted image 20230926234811.png]]

### _Условные операторы_

 SCSS поддерживает условные операторы `@if`, `@else if` и `@else`, которые позволяют вам создавать более динамические стили в зависимости от условий.

  ```
  $theme: light;

  .navbar {
    @if $theme == light {
      background-color: white;
      color: black;
    } @else if $theme == dark {
      background-color: black;
      color: white;
    }
  }
  ```

### _Математические операторы_

![[Pasted image 20230926233712.png]]

![[calc()]]
