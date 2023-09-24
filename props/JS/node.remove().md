
```
<div id="main">
  <p class="text" data-id="1">Первый абзац</p>
	<p class="text" data-id="2">Второй абзац</p>
</div>
```

```
const p = document.querySelector("p");
p.remove(); /=/ Удалит первый абзац
```

### *Динамическое удаление*

```
var list = document.querySelector('.todo-list');
var items = list.children

var toggleEmptyListMessage = function () {
  console.log(items);
  if (items.length === 0) {
    console.log('Все цели выполнены!');
  }
};

var addCheckHandler = function (item) {
  var checkbox = item.querySelector('.todo-list-input');
  checkbox.addEventListener('change', function () {
    item.remove();
    toggleEmptyListMessage();
  });
};

for (var i = 0; i < items.length; i++) {
  addCheckHandler(items[i]);
}
```

