### *Шаблоны. Тег `<template>`*

Предназначен для быстрого создания будущих элементов, чтобы не делать это вручную через JS.
Тогда далее останется только подправить содержимое под каждый элемент. 

Каждому тегу `template` назначают уникальный атрибут `id` , тк шаблонов может быть много. 
Поиск `template` так же совершают через `id`

```
<template id="">
  <h1>Hello, world!</h1>
</template>
```

```
const taskTemplate = document.querySelector("#task-template");

/=/ Выдаст: (HTMLTemplateElement)  
<template id="task-template"> 
  #document-fragment  
    <li class="todo-list-item">  
      <label>  
        <input type="checkbox" class="todo-list-input"/>  
        <span>  
      </label>  
    </li>  
</template>
```
### *document-fragment. Контент тега `<template>`*

`document-fragment`:
- Хранилище содержимого тега `template`. 
- Скрывает разметку которая находится внутри тега `template`. 

Если искать элементы через `querySelector` и другие методы поиска внутри `template`, то мы не получим нужные нам элементы. 
Элементы лежат в свойстве `content` тега `template`. Это свойство и содержит `document-fragment`, внутри которого уже можно искать привычными методами поиска.

```
const taskTemplate = document.querySelector("#task-template").content;

/=/ Выдаст: (DocumentFragment)  
#document-fragment 
  <li class="todo-list-item">  
    <label>  
      <input type="checkbox" class="todo-list-input"/>  
      <span>  
    </label>  
  </li>
```

-> Конечный вариант
```
const taskTemplate = document.querySelector("#task-template").content;

const newItemTemplate = taskTemplate.querySelector(".todo-list-item");

/=/ Выдаст: (HTMLLIElement)  
<li class="todo-list-item"> 
  <label>  
    <input type="checkbox" class="todo-list-input"/>  
    <span>  
  </label>  
</li>
```

---

```
const slidesData = [
  {
    service: "Диагностика",
    price: "Бесплатно",
    duration: "30 мин"
  },
  {
    service: "Замена дисплея",
    price: "1 000 ₽",
    duration: "30-120 мин"
  },
  {
    service: "Замена полифонического динамика",
    price: "1 000 ₽",
    duration: "30-120 мин"
  }
];

const clonedSlides = [];
const template = document.querySelector(".prices-slider__template").content;
const slidesTemplate = template.querySelector(".prices-slider__slide");
const slideText = slidesTemplate.querySelectorAll(".prices-slider__slide-item");

slidesData.forEach(({ service, price, duration }) => {
  slideText[0].textContent = service;
  slideText[1].textContent = price;
  slideText[2].textContent = duration;

  const clonedSlide = slidesTemplate.cloneNode(true);
  clonedSlides.push(clonedSlide);
});

const pricesSlider = document.querySelector(".prices-slider__wrapper");

clonedSlides.forEach((slide) => {
  pricesSlider.append(slide);
});
```