### *Переопределить положение <mark style="background: #FFF3A3A6;">элемента</mark> на поперечной/вертикальной оси*

`align-self` переопределяет положение для **элемента** в контейнере `Grid` или `Flex`, которое ранее было задано для **контейнера** с помощью  `align-items`.

- В Grid оно выравнивает элемент вертикально . 
- В Flexbox оно выравнивает элемент по поперечной оси.

Значения у этого свойства такие же, как у `align-items`: `stretch` (по умолчанию), `flex-start`, `flex-end` и `center`.

### *Разница `align-self` и `align-items`*

Основная разница между `align-self` и `align-items`:
- `align-self`**применяется к отдельному элементу внутри контейнера** и переопределяет его вертикальное выравнивание
- `align-items` **устанавливается на сам контейнер** и определяет вертикальное выравнивание всех его элементов.
 
```
.container {
  display: flex;
  align-items: center; /* Вертикальное центрирование всех элементов в контейнере */
}

.item {
  align-self: flex-start; 
  /* Переопределение вертикального выравнивания для конкретного элемента */
}

```
