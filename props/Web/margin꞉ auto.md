## *Выравнивание Flex по осям X/Y.  Блочное выравнивание по X*


### *Блочный бокс:*
В блочном боксе автоматические внешние отступы сверху и снизу не работают
######
![Схема выравнивания по горизонтали](https://htmlacademy.ru/assets/courses/359/img/scheme7.svg)

### *Flex-контейнер:*
Но во флекс-контейнере `margin: auto` позволяет сдвинуть флекс-элемент к верхней или нижней границе. 
Или даже отцентрировать элемент по вертикали, если задать верхний и нижний отступ одновременно.
######
![Схема выравнивания по вертикали](https://htmlacademy.ru/assets/courses/359/img/scheme8.svg)

Если указать для `margin` два значения, то первое применится к внешним отступам по вертикали, а второе — к внешним отступам по горизонтали.

Выравнивание для flex-контейнеров:
```
.box {
	margin: 0 auto; (По горизонтали)
}
.box {
	margin: auto 0; (По вертикали)
}
```