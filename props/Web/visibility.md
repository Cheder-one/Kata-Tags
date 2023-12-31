### _Методы скрытия элементов визуально и/или для ридеров_

1. `display: none` и `hidden` - Элемент и все его потомки будут скрыты
   
2. `opacity: 0` - Элемент и все его потомки будут визуально скрыты. 
  - Доступен для ридеров и Tab (скрыт визуально)
   
3. `visibility: hidden/visible` - Элемент может быть скрыт частично/полностью, его потомки могут отображаться, если `visible`.
   - Когда используется `visibility: hidden` к родительскому элементу, все скрыто.
   - Когда к дочернему элементу этого родителя применен `visibility: visible`, этот дочерний элемент будет показан.

4. `aria-hidden` - удаляет элемент из дерева специальных возможностей 
  - Не скрывает элемент визуально, исключает ридеры

   Варианты использования `aria-hidden`:
   - Скрыть декоративный контент (иконки, изображения).
   - Скрыть дублированный текст.
   - Скрыть закадровый или свернутый контент.

```
<div aria-hidden="true">
  Этот элемент будет скрыт от ассистивных технологий.
</div>

<div aria-hidden="false">
  Этот элемент будет доступен для ассистивных технологий.
</div>
```

