### *Не применять стили к элементам*

Чтобы применить стили к элементам 
- `.b-menu-list__e-item:hover` 
- `.b-menu-list__e-item:focus`
  Но не применять их к элементам с классом `.b-menu-list__e-item--active`, необходимо использовать селектор `:not()` 

```
.b-menu-list__e-item:hover:not(.b-menu-list__e-item--active),
.b-menu-list__e-item:focus:not(.b-menu-list__e-item--active) {
  opacity: 0.7;
  transform: scale(0.98);
}

&:hover:not(&--active),
&:focus:not(&--active) {
	opacity: 0.7;
	transform: scale(0.98);
}
```

