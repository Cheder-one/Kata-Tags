Document Object Model или объектная модель документа

JavaScript особым образом воспринимает разметку: элементы здесь не строки, которые мы пишем в HTML-файлах, а `объекты`. 
При этом каждый объект связан с другими такими же объектами и знает о своём родителе, соседних объектах-элементах, вложенных объектах.

В каждом DOM-дереве есть `корневой объект`, из которого идут другие объекты. Он называется `document`. Этот `глобальный объект` доступен во всех программах, которые работают в браузере. 
Проще говоря, `document` — страница, которая содержит все элементы разметки (объекты).

### *DOM API*

`API` - это группа методов, которые позволяют взаимодействовать с какой-то частью программы или интерфейса. 
В случае с `DOM API` это все методы, которые позволяют что-то делать с `DOM-элементами`. (`querySelector`, `addEventListener` и тд)