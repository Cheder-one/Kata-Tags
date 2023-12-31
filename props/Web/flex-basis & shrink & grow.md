### *flex- basis*

`flex-basis` - определяет _**начальный размер**_ элемента внутри контейнера по главной оси

1. `auto` -  естественный размер элемента или размер, указанный через другие свойства (например, `width` или `height`), если они установлены. _(по умолчанию)_
2. `flex-basis` может быть задан в разных единицах измерения (например, пикселях, процентах или em) или ключевых словах (например, `auto`, `content`, `initial`, `inherit`).
3. `flex-basis` можно комбинировать с `flex-grow` и `flex-shrink`, чтобы более точно управлять размерами элементов внутри контейнера.

```
.container {
  display: flex;
}

.item {
  flex-basis: 100px; /* Начальный размер элемента 100 пикселей */
  flex-grow: 1; /* Элемент может увеличивать размер */
  flex-shrink: 1; /* Элемент может уменьшать размер */
}
```

-> В этом примере `flex-basis` устанавливает начальный размер элемента в `100px`. 
`flex-grow: 1` Если контейнер имеет свободное пространство, элемент будет увеличивать свой размер пропорционально другим элементам внутри контейнера. 
`flex-shrink: 1` Если контейнер слишком узкий, элемент будет уменьшаться в размере вместе с другими элементами с установленным `flex-shrink`.

### *Пропорция увеличения/уменьшения элемента `grow`/`shrink`* 
### *flex-grow (расти)*

`flex-grow` определяет, насколько элемент может увеличивать свой размер относительно других элементов внутри контейнера.

- Значение по умолчанию: 0.
- Если все элементы в контейнере имеют `flex-grow: 1`, то они будут равномерно занимать доступное пространство и увеличиваться в размере пропорционально.
- Если одному элементу установить `flex-grow: 2`, а другим - `flex-grow: 1`, то первый элемент будет занимать вдвое больше доступного пространства.

### *flex- shrink (сжатие)*

`flex-shrink` определяет, насколько элемент может уменьшать свой размер относительно других элементов внутри контейнера.

- Значение по умолчанию: 1.
- Если у элементов установлено `flex-shrink: 1`, и контейнер становится слишком узким, все элементы будут уменьшаться в размере пропорционально.
- Если у одного элемента установить `flex-shrink: 0`, то этот элемент не будет уменьшаться в размере, пока другие элементы будут уменьшаться.

```
.container {
  display: flex;
}

.item {
  flex-grow: 1; /* Все элементы равномерно увеличиваются */
  flex-shrink: 1; /* Все элементы равномерно уменьшаются */
}
.item:nth-child(2) {
  flex-grow: 2; /* Второй элемент увеличивается вдвое сильнее */
}
.item:nth-child(3) {
  flex-shrink: 0; /* Третий элемент не уменьшается вообще */
}
```

