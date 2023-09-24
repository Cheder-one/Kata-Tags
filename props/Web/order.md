## *Изменяет визуальный порядок элементов на странице*

**! Свойство `order` работает только в Grid и Flex-контейнерах.**

По умолчанию, элементы имеют порядковый номер 0, и они располагаются в порядке, определенном в HTML-разметке.

```
.container {
  display: flex;
}

.item:nth-child(3) {
  order: -1;
}
.item:nth-child(2) {
  order: 1;
}
.item:nth-child(1) {
  order: 2;
}
```

```
<div class="container">
  <div class="item">Первый элемент</div>
  <div class="item">Второй элемент</div>
  <div class="item">Третий элемент</div>
</div>

```
