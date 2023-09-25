### _Стилизация через атрибут_

```
[data-size="large"] {
  padding: 2rem;
	font-size: 125%;
}

button[data-type="download"] {...}
.card[data-pad="extra"] {...}
```

---
- Выбор элементов, у которых имеется указанный атрибут

```
[data-size] { }
```

- Выбор элемента, атрибут которого имеет заданное значение

```
[data-state="open"],
[aria-expanded="true"] { }
```

- Селектор "начинается с", использование которого приведёт к выбору элементов, атрибут которых содержит "3", а так же - что угодно другое, начинающееся с 3 - вроде "3.14"

```
[data-version^="3"] { }
```

```
/=/ Получите все элементы, у которых классы начинаются с "swiper"

var elementsWithSwiperClasses =
	document.querySelectorAll('[class^="swiper"]');
```

- Селектор "содержит" указывает на то, что заданная строка должна содержаться где-то в значении свойства

```
[data-company*="google"] { }
```

### _Использование в JavaScript_

- Получить data-атрибут элемента
```
<div 
	data-mobile="false" 
	class="b-brand-slider"
>
```
```
const slider = document.querySelector(".b-brand-slider");
console.log(slider.dataset.mobile); /=/ false
```

- Изменение data-атрибутов:
```
slider.dataset.mobile = true;
```

- Добавить data-атрибут:
```
element.dataset.myAttribute = 'значение';
```
