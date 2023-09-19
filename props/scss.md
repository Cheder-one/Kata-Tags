### *@extend*

Позволяет наследовать стили из одного селектора и применять их к другому селектору.

```
.button-base {
  padding: 10px 20px;
  background-color: #3498db;
  color: #fff;
}

.primary-button {
  @extend .button-base;
}
.secondary-button {
  @extend .button-base;
  background-color: #e74c3c;
}
```


1. **Переменные**: Вы можете определять переменные для хранения значений, таких как цвета, размеры и шрифты, что делает код более читаемым и облегчает изменение стилей на всем сайте. Пример:

   ```
   $primary-color: #3498db;
   $font-family: "Helvetica, Arial, sans-serif";

   body {
     font-family: $font-family;
     background-color: $primary-color;
   }
   ```

2. **Вложенность**: SCSS позволяет вкладывать селекторы внутри других селекторов, что делает код более структурированным и удобным для чтения:

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

3. **Миксины**: Миксины позволяют определить набор стилей и повторно использовать их в разных селекторах. Это полезно для создания кастомных стилей, которые могут быть использованы в нескольких местах. Пример:

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

4. **Функции**: SCSS предоставляет встроенные функции для выполнения операций над значениями, такие как `darken`, `lighten`, `rgba`, `mix` и другие. Эти функции облегчают манипулирование цветами и другими свойствами.

   ```
   .button {
     background-color: darken($primary-color, 10%);
     color: lighten($primary-color, 20%);
   }
   ```

5. **Импорт файлов**: Вы можете разделить свой CSS на несколько файлов и затем импортировать их в одном месте, что улучшает организацию кода и управление проектом.

   ```
   // В основном файле стилей
   @import 'variables';
   @import 'buttons';
   @import 'forms';
   ```

6. **Условные операторы**: SCSS поддерживает условные операторы `@if`, `@else if` и `@else`, которые позволяют вам создавать более динамические стили в зависимости от условий.

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

