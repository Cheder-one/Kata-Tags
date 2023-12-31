## _Блок, Элемент, Модификатор_

`БЭМ` - Компонентный подход к веб-разработке.

В его основе лежит принцип разделения интерфейса на независимые блоки.
Он позволяет эффективно разрабатывать интерфейсы любой сложности и повторно использовать существующий код, избегая «Copy-Paste».

**БЭМ-сущность** - собирательное для блоков, элементов и модификаторов.

## _Блок - Функционально независимый компонент страницы_

### _Особенности Блоков_

1. Название `блока` характеризует смысл.
   - «Что это?» — «меню»: menu, «кнопка»: button.
2. Блоку не следует задавать внешнюю геометрию.
   - У блока не должно быть `отступов`, `границ`, влияющих на размеры и `позиционирования (position:...)`. 
       Это позволит свободно переносить переиспользуемый элемент в любое окружение.
3. В блоке могут содержаться только те элементы, которые принадлежат данному родительскому блоку.
4. Для селекторов необходимо использовать `.class`, и не использовать селекторы по тегам или id.

```
/=/ Верно. Семантически осмысленный блок `error`
<div class="error">
  Error #404
</div>

/=/ Неверно. Описывается внешний вид
<div class="red-text">
  Error #404
</div>
```

### _Вложенность Блоков_

- Блоки можно вкладывать друг в друга.
- Блок может быть без элементов

---

## _Элемент - Составная часть блока_

**Элемент не может использоваться отдельно от блока.**

### _Особенности Элементов_

1. Название `элемента` характеризует смысл
   - «Что это?» — «меню»: menu, «кнопка»: button.
2. Структура полного имени элемента соответствует схеме: `имя-блока__имя-элемента`.
   - Имя элемента отделяется от имени блока двумя подчеркиваниями (`__`).

```
  /=/ Блок search-form
  <form class="search-form">
	  /=/ Элемент input блока search-form
	  <input class="search-form__input">
	
	  /=/ Элемент button блока search-form
	  <button class="search-form__button">
		  Найти
	  </button>
  </form>
```

### _Вложенность Элементов_

1. Элементы можно вкладывать друг в друга.
2. Элемент — всегда часть блока, а не другого элемента.
   - В названии элемента **нельзя** прописывать иерархию от другого элемента `block__elem1__elem2 (нет)`.

-> Правильная иерархия элементов в блоках:

```
  <form class="search-form">
    <div class="search-form__content">
      <input class="search-form__input">
      <button class="search-form__button">Найти</button>
    </div>
  </form>
```

### _Принадлежность Элементов_

Элемент — всегда часть блока и не должен использоваться отдельно от него.

-> Верно:
```
<div class="block">
  <div class="block__element">Элемент блока</div>
</div>
```

-> Неверно:
```
<div class="block">Содержимое родительского Блока</div>

<div class="block__element">Элемент блока</div>
```

### _Необязательность Элементов_

Элемент — необязательный компонент блока. Не у всех блоков должны быть элементы.

```
<div class="search-form"> /=/ Блок `search-form`
  <input class="input">   /=/ Блок `input`

  <button class="button"> /=/ Блок `button`
	  Найти
	</button>
</div>
```

### _Что выбрать `Блок` или `Элемент`?_

-  Не знаешь что делать - бей на Блоки. Бить на Блоки - это хорошая практика
-  Используй префиксы,для визуального выделения структуры `.b- .l- `

```
<div class="b-block">

	<div class="b-block1">
		<div class="b-block1__elem">...</div>
	</div>
	
</div>
```

1. Создавайте блок
   - Если фрагмент кода может использоваться повторно и не зависит от реализации других компонентов страницы. (Переиспользуемый)
2. Создавайте элемент
   - Если фрагмент кода не может использоваться самостоятельно, без родительской сущности. (Спецефический UI)
---

В БЭМ-методологии различие между блоками и элементами определяется по их функциональной роли и отношению к другим элементам. Вот несколько способов, как можно понять, что элементы:

1. **Смысловая зависимость**: Элементы обычно являются частями блока и зависят от него смыслово. Если элемент не имеет смысла без родительского блока, то это скорее всего элемент. Например, кнопка внутри меню (`m-top-menu__button`) зависит от самого меню, и без меню она не имеет смысла.
2. **Иерархическое отношение**: Если элемент находится внутри блока и используется для структурирования контента этого блока, то это скорее всего элемент. Элементы помогают оформить внешний вид или структуру блока, но сами по себе не представляют отдельных компонентов.
3. **Префикс в имени класса**: Согласно соглашениям БЭМ, элементы обычно именуются с использованием двойного подчеркивания после имени блока. Например, `m-top-menu__button`. Если у класса есть такой префикс, это указывает на то, что это элемент.
4. **Особенности дизайна и структуры**: Элементы могут иметь уникальные стили, которые отличают их от других блоков на странице. Они также могут иметь ограниченную область действия внутри блока и не пересекаться с другими блоками.
5. **Ответ на вопрос "Что это?"**: Если вы задаете вопрос "Что это?" элементу и ответ звучит как "Это часть блока...", то скорее всего это элемент.

## _Модификатор - Определяет внешний вид, состояние, и поведение блока/элемента._

### _Особенности Модификаторов_

1. Название модификатора должно характеризовать:
   - Внешний вид: «какой размер?», «какая тема?» — «размер»: `size_s`, «тема»: `theme_islands`
   - Состояние: «чем отличается от прочих?» — «отключен»: `disabled`, «фокусированный»: `focused`
   - Поведение: «что делает?», «как ведет себя?», «как взаимодействует с пользователем?» — «направление»: `directions_left-top`.
2. Имя модификатора отделяется от имени блока или элемента одним подчеркиванием (`_`) или `--`.
   - `имя-блока_модификатор `
   - `имя-блока__имя-элемента_модификатор`
   - `имя-блока__имя-элемента--mod-name--mod-val`

### _Типы Модификаторов_

### *Булевый*

   - Считается, что булевый модификатор в сущности, означает `true`.
       Например, «отключен»: `disabled`.

```
<form class="search-form search-form_focused">
	<input class="search-form__input">

	<button
		class="search-form__button search-form__button_disabled"
	>
		Найти
	</button>
</form>
```

### *Модификатор со значением`key-value`*

   - Используют, когда важно значение модификатора.
       Например, «меню с темой оформления islands»: 
       `menu_theme_islands`/`menu--theme--islands`
  
```
<form class="search-form search-form_theme_islands">
	<input class="search-form__input">
	
	<button class="search-form__button search-form__button--size--m">
		Найти
	</button>
</form>
```

## *Принципы работы с модификаторами*

### *Модификатор нельзя использовать самостоятельно*

- Модификатор не может использоваться в отрыве от `модифицируемого-блока` или `элемента` 
- Модификатор должен `изменять вид`, `поведение` или `состояние` сущности, а не заменять ее.

-> Верно:
```
<form class="search-form search-form_theme_islands">
	<input class="search-form__input">
	
	<button class="search-form__button">Найти</button>
</form>
```

-> Неверно *(пропущен сам класс блока `search-form`)*
```
<form class=" search-form_theme_islands">
	<input class="search-form__input">
	
	<button class="search-form__button">Найти</button>
</form>
```

## *Микс - объединение 2х и более CSS селекторов в одном блоке.*

Микс (mix) - это механизм, который позволяет применять стили из одного блока или элемента к другому блоку или элементу. 
Использование миксов позволяет избегать дублирования стилей и создавать более удобный и поддерживаемый код.

Комбинация возможна в любом сочетании: 
- БЭМ-блок + БЭМ-элемент
- БЭМ-блок + БЭМ-блок
- БЭМ-элемент + БЭМ-элемент.
```
<div class="page-header">
  <div class="page-header__nav-wrap">...</div>
  <a class="btn  page-header__btn" href="/buy">...</a>
</div>
```

```
<div class="*slider*">
  <div class="promo  slider__inner">
    <div class="promo__item  *slider*__item"> 
      /=/ Миксование элементов только внутри родителя.
    </div>
  </div>
</div>
```


-> Пример использования миксов для применения общего стиля `border` к элементам `<button>` и `<input>`:

```
.shared-style {
  border: 1px solid #ccc;
  padding: 5px;
}

.button {
  background-color: blue;
  color: white;
}
.input {
  background-color: white;
  color: black;
}
```

```
<button class="button shared-style">My Button</button>
<input class="input shared-style">
```

В этом примере `@include shared-style` используется для применения общих стилей, включая `border`, к блокам `.button` и `.input`. 
Теперь оба элемента будут иметь одинаковый стиль `border`, а также свои собственные уникальные стили.

---
Миксы позволяют:
- Совмещать стили нескольких элементов без дублирования кода; 
- Создавать новые компоненты интерфейса на основе имеющихся.

```
<div class="about">
	<div class="title about__title">
	  ...
	</div>

	<div class="subtitle about__subtitle">
	  ...
  </div>
</div>

    * About - родительский Блок
    * Title и Subtitle - отдельные Блоки, которые вложены в Блок `About`
    * К которым добавлены кастомные стили Элементов 
	    about__title и about__subtitle из Блока About
```

Данный подход позволяет задавать ситуативное позиционирование Блоков `Title, Subtitle` в родительском Блоке `About`. Таким образом, блок можно использовать в любом другом окружении.

- Это происходит через передачу стилистических классов Блокам, в то время как эти классы `(элементы с этими классами)` относятся к Блоку `About`.
- Тем самым происходит некое представление Блоков `Title, Subtitle` как дочерних Элементов `About`.  
- Это позволяет все так же сохранить переиспользуемость Блоков `Title, Subtitle`. 
  И одновременно смочь адаптировать их в нужный контекст, без потери их универсальности
  
### *Пример записи стилей для БЭМ*

```
<div class="about">
	<div class="title about__title">
	  ...
	</div>

	<div class="subtitle about__subtitle">
		...
	</div>
</div> 
```

-> CSS

```
.about {
	/* стили для блока .about */
}
.about__title {
	/* стили для элемента .about__title */
}
.about__subtitle {
	/* стили для элемента .about__subtitle */
}

.title {
	/* стили для блока .title внутри .about */
}
.subtitle {
	/* стили для блока .subtitle внутри .about */
}
```

-> SCSS *(требуется компиляция в `css`)*

```
.about {
  &__title {
	  /* стили для элемента .about__title */
  }
  &__subtitle {
	  /* стили для элемента .about__subtitle */
	}
	
  .title {
		/* стили для блока .title внутри .about */
	}
  .subtitle {
	  /* стили для блока .subtitle внутри .about */
	}
}
```

### *Сокращение записи селекторов*

```
.b-top-menu {
	&__e-nav-icon,
	&__e-divider {
		margin-right: 1rem;
	}

	&__e-logo {
		margin-right: auto;
	}
}
```
## *Файловая структура БЭМ*

Это Компонентный подход в организации проектов в файловой структуре. 

### *Nested-подход*

### *Особенности Nested:*

- Один `блок` — одна директория.
- Имена `блока` и его директории совпадают. 
  -> Например, блок `header` — директория `header/`, блок `menu` — директория `menu/`.
- Реализация блока разделяется на отдельные файлы-технологии. 
  -> Например, `header.css`, `header.js`.
- Директория блока является корневой для поддиректорий соответствующих ему элементов и модификаторов.
- Имена директорий элементов начинаются с двойного подчеркивания (`__`).
  -> Например, `header/__logo/`, `menu/__item/`.
- Имена директорий модификаторов начинаются с одинарного подчеркивания (`_`) или `two dashes`(`--`). 
  -> Например, `header/_fixed/`, `menu/--theme-islands/`.
- Реализации `элементов` и `модификаторов` разделяются на отдельные файлы-технологии. 
  -> Например, `header__input.js`, `header--theme-islands.css`.

```
search-form/
├── __input/
│   ├── search-form__input.css
│   └── search-form__input.js
├── __button/
│   ├── search-form__button.css
│   └── search-form__button.js
├── --theme/
│   ├── search-form--theme-islands.css
│   └── search-form--theme-lite.css
├── search-form.css
└── search-form.js
```

### *Flat-подход*

Упрощенная схема организации файловой структуры:
- Директории для `блоков` не используются.
- Опциональные `элементы` и `модификаторы` **могут быть реализованы в отдельных файлах или в основном файле блока**.

```
project/
└── common.blocks/
    ├── input_type_search.css         
    ├── input_type_search.js          
    ├── input__clear.js               
    ├── input.css
    ├── input.js
    ├── popup.css
    ├── popup.js
    └── popup.png
```

### *Flex-подход*

Максимально гибкая схема, является объединением двух схем `flat` и `nested`. Для блоков с разветвленной файловой структурой применяются правила схемы `nested`. Для простых блоков используется схема `flat`.

Особенности:

- Блоку соответствует отдельная директория.
- Элементы и модификаторы **могут быть реализованы в файлах блока или в отдельных файлах.**
	
### *Элементы и модификаторы в файлах блока:*

В этом случае стили и JavaScript для элементов и модификаторов могут быть включены непосредственно в файлы блока. 

```
blocks/
├── header/
│   ├── header.css       // Стили блока header
│   ├── header.js        // JavaScript для блока header
│   ├── logo.css         // Стили элемента logo
│   ├── logo.js          // JavaScript для элемента logo
│   ├── menu.css         // Стили элемента menu
│   ├── menu.js          // JavaScript для элемента menu
│   ├── header_dark.css  // Стили для модификатора dark блока header
│   ├── header_dark.js   // JavaScript для модификатора dark блока header
│   └── header.html      // HTML для блока header (если не встроен в шаблон)
```

### *Элементы и модификаторы в отдельных файлах:*

В этом случае стили и JavaScript для элементов и модификаторов могут быть размещены в отдельных файлах, которые находятся внутри директории блока.

```
blocks/
├── header/
│   ├── header.css       // Стили блока header
│   ├── header.js        // JavaScript для блока header
│   ├── header_dark.css  // Стили для модификатора dark блока header
│   ├── header_dark.js   // JavaScript для модификатора dark блока header
│   ├── header.html      // HTML для блока header (если не встроен в шаблон)
├── logo/
│   ├── logo.css         // Стили элемента logo
│   ├── logo.js          // JavaScript для элемента logo
├── menu/
│   ├── menu.css         // Стили элемента menu
│   ├── menu.js          // JavaScript для элемента menu
```

Выбор между этими двумя способами зависит от вашей организации проекта и ваших предпочтений по структуре файлов. Оба способа соответствуют методологии БЭМ, и вы можете выбрать тот, который лучше подходит вашей команде и проекту.