### *Шаблоны. Тег `<template>`*

Предназначен для быстрого создания будущих элементов, чтобы не делать это вручную через JS.
Тогда далее останется только подправить содержимое под каждый элемент. 

Каждому тегу `template` назначают уникальный атрибут `id` , тк шаблонов может быть много. 
Поиск `template` так же совершают через `id`

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
const taskTemplate = 
	document.querySelector("#task-template").content;

/=/ Выдаст: (DocumentFragment)  
#document-fragment 
  <li class="todo-list-item">  
    <label>  
      <input type="checkbox" class="todo-list-input"/>  
      <span>  
    </label>  
  </li>
```

```
const newItemTemplate = 
	taskTemplate.querySelector(".todo-list-item");

/=/ Выдаст: (HTMLLIElement)  
<li class="todo-list-item"> 
  <label>  
    <input type="checkbox" class="todo-list-input"/>  
    <span>  
  </label>  
</li>
```
