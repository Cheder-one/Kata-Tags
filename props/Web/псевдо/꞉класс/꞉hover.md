### _Как с помощью CSS создаются выпадающие меню?_

```
li.top ul.submenu {
  display: none;
}
li.top:hover ul.submenu {
  display: block;
}
```

Первое правило прячет список-подменю. Второе правило гласит: «если на верхний пункт меню, в котором находится подменю, наведут курсор, то надо показать подменю». Вот так всё просто.

Общий принцип такой: родительский элемент реагирует на наведение мыши и изменяет свойства элементов-потомков. То есть всё работает на контекстных селекторах вида селектор1:hover селектор2.

### *:hover и :focus*

Необходимо использовать стилизование сразу для двух типов действий. 
Так будут охвачены все виды тачпадов и устройств 

