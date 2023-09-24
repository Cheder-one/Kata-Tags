По умолчанию градиент идет сверху вниз

```
background-image: linear-gradient(yellow, green);
```

### _Направление градиента_

Направления: `top`, `bottom`, `left`, `right`.

Направление градиента располагается перед списком цветов и включает в себя частицу `to`
Она была добавлена в синтаксис для улучшения читабельности и наглядности:

-> Жёлто-зелёный градиент слева направо

```
background-image: linear-gradient(to right, yellow, green);
```

### _Градиенты по диагоналям_

Градиенты можно направлять по диагонали, из угла в угол.
Для этого нужно комбинировать `top`, `bottom` и `left`, `right`.

-> Градиент, идущий из левого нижнего **_в правый верхний угол_**:

```
background-image: linear-gradient(to right top, yellow, green);
```

- В диагональных градиентах после `to` нужно указывать конечный угол, следовательно начальный - прямо-противоположный ему и будет определен автоматически

### _Градиенты под углом_

```
background-image: linear-gradient(90deg, yellow, green);
background-image: linear-gradient(-135deg, yellow, green);
```

![[Pasted image 20230914124344.png]]

```
.leaf-top-left {
  background-image: linear-gradient(135deg, #ff0000, #000000);
}
.leaf-top-right {
  background-image: linear-gradient(225deg, #00ff00, #000000);
}
.leaf-bottom-right {
  background-image: linear-gradient(315deg, #ffff00, #000000);
}
.leaf-bottom-left {
  background-image: linear-gradient(45deg, #ff00ff, #000000);
}
```

### _Диагонали против градусов_

- Градусные градиенты **_не_** зависят от формы контейнера
- Диагональные градиенты зависят от формы контейнера. Диагональные градиенты всегда остаются привязанными к своим углам.

```
													диагональный | градусный градиент
											(из угла в угол) | (не зависит от высоты контейнера)
```

<div class="content" style="margin: auto; width: 350px;">
  <div class="gradient gradient-diagonal" style="width: 150px;
    height: 150px;
    box-shadow: 0 0 3px #333333; float: left;
    height: 300px;
    
    background-image: linear-gradient(to top right, #ff0000, #ffff00, #ff0000); 
  "></div>
  <div class="gradient gradient-degrees" style=" width: 150px;
    height: 150px;
    box-shadow: 0 0 3px #333333;  float: right;
    height: 300px;
    
    background-image: linear-gradient(45deg, #ff0000, #ffff00, #ff0000);
  "></div>
</div>

### _Равномерный многоцветный градиент_

В линейный градиент можно включать больше двух цветов. Для этого цвета просто перечисляются через запятую. Например, если задать такой CSS:

```
linear-gradient(to right, red, yellow, green)
```

### _Пропорции цветов и колорстопы_

По умолчанию цвета в градиентах распределяются равномерно, в одинаковых пропорциях.
Колорстоп указывает положение цвета в градиенте.

Колорстоп задаёт то место, где будет располагаться центральная (_\*\*самая насыщенная_\*\*) часть цвета.

![[Pasted image 20230914131911.png]]

### _Резкие переходы цветов_

Задаем для соседних цветов одну и ту же позицию.
В таком случае получится резкий переход цветов, так как они оба будут «вытекать» из одной точки в противоположных направлениях.

![[Pasted image 20230914132357.png]]

### _Переходы цветов в `%` и `px`_

Цветовые переходы градиента можно также задавать в пикселях. Работают они по аналогии с процентными переходами.
Отличие заключается в том, что процентные переходы зависят от размера элемента, а переходы в пикселях — нет.

### _Полупрозрачные градиенты_

`Alfa-канал` - отвечает за прозрачность 

- `rgba(255, 255, 255, 1)` — обычный белый цвет.
- `rgba(255, 255, 255, 0.5)` — наполовину прозрачный белый.
- `rgba(255, 255, 255, 0)` — полностью прозрачный цвет.

Также прозрачный цвет можно задать с помощью ключевого слова `transparent`.

### _Повторяющийся линейный градиент в `px`_

Помимо обычных градиентов существуют и повторяющиеся.
Их синтаксис полностью совпадает с синтаксисом обычных, только вместо `linear-gradient` пишется `repeating-linear-gradient`.

```
background: repeating-linear-gradient(
  to right,
  #FF5733,
  #FF5733 30px,
  #337DFF 30px,
  #337DFF 60px
);
/=/ Градиент двигается по горизонтали и повторяться каждые 30 пикселей
```

<body style=" 
						display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;">
    <div class="gradient-background" style="
    width: 300px;
		height: 200px;
     background: repeating-linear-gradient(to right, #FAD02E, #FAD02E 30px, #6BCDFF 30px, #6BCDFF 60px);
    ">
    </div>
</body>

Есть несколько тонкостей, которые нужно знать про повторяющиеся градиенты:

1. Размер фрагмента определяется по последнему колорстопу. 
   Чтобы повторение было видно, последний колорстоп должен быть меньше, чем размер элемента с градиентом.
2. Если первый и последний цвета градиента различаются, то будут видны резкие границы между повторяющимися фрагментами. 
   Чтобы от них избавиться, нужно задавать одинаковый первый и последний цвета.
3. Колорстопы в повторяющихся градиентах обычно задают в `px`, но можно использовать и проценты.

### _Множество градиентов_

CSS-градиенты — это особые фоновые изображения, и на них действуют все свойства для управления фонами: `background-position`, `background-size`, `background-repeat`.

В CSS можно задавать элементу сразу несколько фоновых картинок, перечисляя их через запятую:

```
background-image:
  url('img1.png'),
  url('img2.png'),
  url('img3.png');
```

Точно так же вместо картинок можно использовать градиенты:

```
 background-image:
    linear-gradient(135deg, white 25%, transparent 25%),
    linear-gradient(225deg, white 25%, transparent 25%),
    linear-gradient(45deg, white 25%, transparent 25%),
    linear-gradient(315deg, white 25%, transparent 25%);
```

### _`background-size` градиента_

В отличие от обычных изображений градиенты не имеют «собственного» размера, и их размер равен размеру элемента, в фоне которого они расположены.
Конечно, такое поведение не подходит для построения орнаментов.

<div class="pattern" style=' width: 200px;
  height: 200px;
  background-color: #333333;
  background-image:
    linear-gradient(135deg, white 25%, transparent 25%),
    linear-gradient(225deg, white 25%, transparent 25%),
    linear-gradient(45deg, white 25%, transparent 25%),
    linear-gradient(315deg, white 25%, transparent 25%);
  box-shadow: 1px 1px 3px #333333;'></div>

К счастью, мы можем задать размер для градиента с помощью свойства `background-size`.

```
background-size: 100px 200px;
```

Такая запись задаст _всем_ фоновым изображениям ширину `100px` и высоту `200px`.

<div class="pattern" style=' width: 200px;
  height: 200px;
  background-color: #333333;
  background-image:
    linear-gradient(135deg, white 25%, transparent 25%),
    linear-gradient(225deg, white 25%, transparent 25%),
    linear-gradient(45deg, white 25%, transparent 25%),
    linear-gradient(315deg, white 25%, transparent 25%);
    background-size: 100px 100px;
  box-shadow: 1px 1px 3px #333333;'></div>

### _Размер фона для каждого градиента_

```
 background-image:
    linear-gradient(135deg, white 25%, transparent 25%),
    linear-gradient(225deg, white 25%, transparent 25%),
    linear-gradient(45deg, white 25%, transparent 25%),
    linear-gradient(315deg, white 25%, transparent 25%);
```

```
background-size:
  100px 200px,
  200px 300px,
  300px 400px;
```
