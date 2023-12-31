## *По главной оси выравнивание Flex-элементов*

`justify-content`:
- `flex-start` — флекс-элементы располагаются в начале главной оси (по умолчанию — слева);
- `flex-end` — флекс-элементы располагаются в конце главной оси (по умолчанию — справа);
- `center` — флекс-элементы располагаются в центре главной оси;
- `space-between` — свободное пространство распределяется между флекс-элементами, при этом первый и последний элемент прижимаются к краям флекс-контейнера.
- `space-around` — свободное пространство распределяется вокруг флекс-элементов;

```
.container {
  display: flex;
  justify-content: center;
}
```

```
<div class="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
</div>
```

### *Горизонтальное выравнивание `Block` и `Grid` элементов*

```
.grid-container {
  display: grid;
  justify-content: start;
}
```

- `flex-start` - выравнивание элементов по горизонтали в начале контейнера.
- `flex-end` - выравнивание элементов по горизонтали в конце контейнера.
- `center` - выравнивание элементов по горизонтали по центру.
- `space-between` - равномерное распределение элементов по горизонтали с промежутками между ними.
- `space-around` - равномерное распределение элементов по горизонтали с промежутками как до, так и после элементов.
