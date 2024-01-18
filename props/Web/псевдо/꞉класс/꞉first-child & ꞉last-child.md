Псевдокласс `first-child` позволяет выбрать первый дочерний элемент родителя, а `last-child `— последний дочерний элемент. 

```
.prices-slider__slide-item-container:first-child {
	background-color: rebeccapurple;
}
.prices-slider__slide-item-container:nth-child(1) { /=/ Аналогично
	background-color: rebeccapurple;
}
```

```
<li class="prices-slider__slide swiper-slide">
  <div class="prices-slider__slide-item-container"> <!-- Окрасит этот --->
    <h3 class="prices-slider__slide-subtitle"
      >Ремонтные услуги</h3
    >
    <span>Тестирование с выдачей технического заключения</span>
  </div>
  <div class="prices-slider__slide-item-container-wrapper">
    <div class="prices-slider__slide-item-container"> <!-- Окрасит этот --->
      <h3 class="prices-slider__slide-subtitle">Цена</h3>
      <span>Бесплатно</span>
      <h3 class="prices-slider__slide-subtitle">Срок</h3>
      <span>30-120 мин</span>
    </div>
    <div class="prices-slider__slide-item-container"> <!-- Не Окрасит --->
      <a class="prices-slider__slide-order">
        <span class="prices-slider__order-item">Заказать</span>
        <img
          class="prices-slider__order-item"
          src="./app/assets/img/ic/goside.svg"
          alt="go side"
        />
      </a>
    </div>
  </div>
</li>
```

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
