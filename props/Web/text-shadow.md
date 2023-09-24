
```
text-shadow:  [x] [y] [blur] [color];
text-shadow:  30px 30px 5px #111111;
```

- свойство `text-shadow` применяется к тексту;
- форма тени повторяет форму текстовых символов;
- можно управлять смещением тени, её цветом, а также размытием;
- нельзя управлять растяжением текстовой тени;
- можно создавать множественные тени.

### *Эффект вдавленного текста*

Принцип эффекта таков: 
- Более тёмная тень смещается немного вверх и влево, а более светлая — вниз и вправо.

```
text-shadow:
  1px 1px 1px #111111,
  2px 2px 2px #222222;
```

### *Декоративная ретро-тень*

Тени смещены в одну сторону. 
 - Нижняя тень смещена чуть сильнее и её цвет отличается от цвета фона
 - Верхняя тень смещена слабее и цвет её совпадает с цветом фона. 
   Так получается интересный эффект обводки.

<h1 style='background-color: white;
	color: black;
	display: inline-block;
  text-shadow:
    2px 2px #e5d4c0,
    4px 4px rgba(0, 0, 0, 0.2);
  text-transform: uppercase;
  font-weight: normal;
  font-size: 55px;'>Я и объектив</h1>

---

<div class="square" style="
	display: inline-block;
	color: white;
  font-family: sans-serif;
  font-size: 72px;
  letter-spacing: 10px;
  text-align: center;
  text-transform: uppercase;"><span style="padding: 0 0 0 10px; border: 5px solid whitesmoke;">Warm</span>photo</div>

