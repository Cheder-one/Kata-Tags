Псевдокласс `first-child` позволяет выбрать первый дочерний элемент родителя, а `last-child `— последний дочерний элемент. 

---
**! Аналогично nth-child(). 
Обращаться нужно к искомому дочернему элементу, а не к родительскому контейнеру.**

```
.b-top-menu .b-top-menu__e-nav-icon:last-child {
	margin-right: 0;
}
==/OR/==
.b-top-menu {
	&__e-nav-icon:last-child {
		margin-right: 0;
	}
}
```

```
<div class="b-top-menu b-top-menu--box-model">
	<button class="b-top-menu__e-nav-icon">
		<img src="src/app/assets/img/ic/burger.svg" alt="sidebar" />
	</button>
	
	<div class="b-top-menu__e-divider"></div>
	
	<button class="b-top-menu__e-nav-icon">
		<img src="src/app/assets/img/ic/checkstatus.svg" alt="check status" />
	</button>
</div>
```

---

```
    <ul class="target">
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
    </ul> 

    li:first-child {
        background-color: red;
    }

    li:last-child {
        background-color: yellow;
    } 
```
