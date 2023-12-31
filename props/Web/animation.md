Описание CSS-анимации состоит из двух частей:

- набор ключевых кадров `keyframes`
- параметры самой анимации.

---
```
.selector {
  animation: [name] [duration] [timing-fn] [delay] [i-count] [direction] ;
}
.clouds {
  animation: move-clouds 5s linear infinite alternate;
}
```

- `animation-name`
- `animation-duration`
- `animation-timing-function` (`ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out`, `bezier`)
- `animation-delay`
- `animation-iteration-count` (`1`, `2.5`, `infinite`)
- `animation-direction` (`normal`, `reverse`, `alternate`, `alternate-reverse`)
- [[#_animation-fill-mode_]] (`none`,`forwards`,`backwards`,`both`)
- `animation-play-state` (`running`, `paused`)

```
.element {
    width: 100px;
    height: 100px;
    background-color: blue;
    animation: moveRight 2s ease-in-out infinite;
}

@keyframes moveRight {
    0% {
        transform: translateX(0);
    }
    50% {
        transform: translateX(200px);
    }
    100% {
        transform: translateX(0);
    }
}
```

---

-> Пример описания ключевых кадров анимации:

```
@keyframes stretching { /=/ Анимация с именем 'stretching'
  0% {
    width: 100px;
  }
  100% {
    width: 200px;
  }
}

.button {
  animation-name: stretching;
  animation-duration: 1s;
}
```

Этот код назначит анимацию `stretching` элементам с классом `button`. 
Элемент плавно увеличит ширину со `100px` до `200px` за `1` секунду, а затем вернётся в исходное состояние.

### _@keyframes: раскадровка_

`@keyframes` - механизм создания кадров анимации.

1. Объявляем анимацию с помощью `@keyframes` и задаем ей имя.

```
@keyframes slide-in {
	/=/ Здесь будут описаны ключевые кадры анимации
}
```

2. На `50% процентах` длительности анимации, элемент будет сдвинут на `100px` по горизонтали относительно его начальной позиции, а на `100% процентах` - на `200px`.

```
@keyframes slide-in {
  50% {
    transform: translateX(100px);
  }
  100% {
    transform: translateX(200px);
  }
}
```

3. Применяем собранную анимацию к элементу
   
```
.element {
  width: 50px;
  height: 50px;
  background-color: blue;
  animation-name: slide-in; /=/ Имя анимации, которую мы создали
  animation-duration: 2s; /=/ Продолжительность анимации
  animation-timing-function: linear; /=/ Функция времени (например, линейная)
  animation-iteration-count: infinite; /=/ Количество повторений (бесконечно)
}
```

### _@keyframes Ключевые и Промежуточные кадры_

`Начальный` и `конечный` кадры задаются с помощью

- `from` и `to`
- или значений `0%` и `100%`.

Промежуточные ключевые кадры задаются с помощью

- `процентов`.

-> Пример анимации из 4 кадров:

```
@keyframes coloring {
  from { background-color: red; }
  33%  { background-color: yellow; }
  66%  { background-color: green; }
  to   { background-color: blue; }
}
```

### _@keyframes: группировка кадров_

```
@keyframes stretching {
  0%,
  50% {
    width: 100px;
  }
  100% {
    width: 200px;
  }
}
```

Анимируемый элемент сначала изменит свою ширину до `100px` и останется в этом состоянии половину времени анимации. А за вторую половину времени он растянется от `100px` до `200px`.

### _Множественная анимация_

В этом примере две анимации (`moveLeft` и `changeColor`) назначены одному элементу с классом `.button`.
Первая анимация сдвигает кнопку влево, а вторая анимация меняет цвет фона кнопки.

```
.button {
  animation-name: moveLeft, changeColor;
  animation-duration: 2s, 2s;
  animation-timing-function: ease, linear;
  animation-iteration-count: infinite, infinite;
}
@keyframes moveLeft {
  0% { transform: translateX(0); }
  100% { transform: translateX(-100px); }
}
@keyframes changeColor {
  0% { background-color: red; }
  100% { background-color: blue; }
}
```

### _iteration-count_

Определяет количество раз, которое анимация будет воспроизведена перед завершением.

- Целые числа: Вы можете указать конкретное количество повторений анимации, например, `2` означает, что анимация будет воспроизведена два раза.
- Дробные числа: Можно использовать дробные числа для более точного контроля над числом повторений.
  Например, `1.5` означает, что анимация будет воспроизведена один раз и до половины следующей итерации.
- `infinite`: Анимация будет бесконечно повторяться до тех пор, пока она не будет явно остановлена.

```
.element {
  animation-name: fade;
  animation-duration: 3s;
  animation-iteration-count: 2.5;
  /=/ Анимация будет воспроизведена два раза и до половины третьей итерации
}
```

### _animation-direction_

Определяет как будет воспроизводиться анимация после завершения каждого цикла.

1. `normal`: Анимация воспроизводится в нормальном направлении (от начала к концу) при каждом цикле. _(по умолчанию)_
2. `reverse`: Анимация воспроизводится в обратном направлении (от конца к началу) при каждом цикле.
3. `alternate`: При повторении от `2 итераций >=`
    Анимация чередует направление между `normal` и `reverse` при каждом цикле.  
4. `alternate-reverse`: Анимация чередует направление между обратным и нормальным при каждом цикле, начиная с обратного направления. 
   То есть, первый цикл будет в `reverse` направлении, второй - в `normal`.

### _animation-delay_

Определяет задержку перед началом анимации

```
.bell {
  animation-name: ding;
  animation-duration: 1s;
}
.arrow-small {
  animation-name: rotate;
  animation-duration: 1s;
}

@keyframes rotate {
  to {
    transform: rotate(360deg);
  }
}
@keyframes ding {
  33% {
    transform: translateX(-15px);
  }
  66% {
    transform: translateX(15px);
  }
}
```

### _animation-fill-mode (режим заполнения анимации)_

Состояние элемента до и после анимации.
Определяет, какие стили будут применены к элементу до и после выполнения анимации.

- `none`: Без применения к элементу стилей. _(по умолчанию)_
- `forwards`: Элемент **_сохранит_** свое **_состояние после анимации_**.
- `backwards`: Элемент отобразит свое состояние до начала анимации.
- `both`: До начала анимации элементу присваивается состояние первого ключевого кадра, а после завершения — конечное состояние анимации сохраняется.

### _animation-play-state_

Дает возможность поставить анимацию «на паузу», а потом возобновить с места остановки.

- `running`
- `paused`

```
.robot-paused {
  animation-play-state: paused;
}
```

Класс `robot-paused` переключается при клике на роботов. При установке класса элементу, анимация приостанавливается до возобновления.
