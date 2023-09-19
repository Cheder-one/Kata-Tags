Красная строка. Улучшает читабельность / украшает большие тексты.

`text-indent` - устанавливает отступ для первой строки блока текста.

При задании значения в процентах, отступ первой строки вычисляется в зависимости от ширины блока.

-> Каждый абзац (`<p>`) будет иметь отступ первой строки в размере 50 пикселей.

```
p {
  text-indent: 50px;
}
```

### _Скрытие текста / Создание замещающего элемента_

```
<div class="paginator">
	<a class="prev disabled" href="#prev">Назад</a>
	<a class="current" href="#1">1</a>
	<span>&hellip;</span>
	<a href="#100">100</a>
	<a class="next" href="#next">Вперёд</a>
</div>
```

![[Pasted image 20230919164947.png]]

```
.paginator .prev {
  margin-right: 20px;

  text-indent: -1000px;

  background-image: url("arrows.png");
  background-repeat: no-repeat;
  background-position: 0 0;
}
```


