```
.b-brand-slider {
  &__e-slide {
    width: calc(25% - 32px);
    /=/ Динамическая ширина элемента с учетом отступов
  }
  &__e-slide:nth-child(4n) {
    width: calc(25%); 
    /=/ Отменяем "отступ" у последнего в ряде
  }
  &__e-wrapper {
    gap: 16px 32px;
    margin: 0 0 16px 16px;
    display: flex;
    flex-wrap: wrap;
  }
}
```

---

```
width: calc(100% - 20px);
/=/ Вычисление ширины как 100% минус 20px

font-size: calc(16px + 2vw);
/=/ Вычисление размера шрифта как 16px плюс 2vw

margin: calc(10px / 2) auto;
/=/ Вычисление отступов как 10px деленное на 2, с автоматической центровкой
```
