Конструктор `Image()` создает новый экземпляр `HTMLImageElement`. Он функционально эквивалентен `document.createElement('img')`.

```
const myImage = new Image(100, 200);
myImage.src = "picture.jpg";

document.body.appendChild(myImage);
```
```
<img width="100" height="200" src="picture.jpg" />
```
---

Работает в `Webpack`
```
import Icon from './icon.png';

const myIcon = new Image();
myIcon.src = Icon;

element.appendChild(myIcon);
```

Работает в `React`
```
import logo from '../../assets/Logo.svg';

function Logo() {
  return <img src={logo} alt="logo" />;
}

export default Logo;
```

Переназначение изображения 
```
const parentElements = document.querySelectorAll(".parent-element");

parentElements.forEach((parentElement) => {
	parentElement.addEventListener("click", () => {
		const image = parentElement.querySelector("img");
		
		if (image) {
			image.src = "новый_путь_к_изображению.jpg";
		} else {
			const newImage = document.createElement("img");
			newImage.src = "путь_к_изображению.jpg";
			parentElement.appendChild(newImage);
		}
	});
});
```