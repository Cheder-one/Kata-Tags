Вендорные префиксы - это приставки перед селекторам или другими сущностями в CSS, позволяющие браузерам внедрять экспериментальные функции до того, как они полностью стандартизированы и готовы для использования. 
Так же используются для большей совместимости при специфичных стилях для браузера.

- `-webkit-` — Safari, Chrome, Opera 15+ и другие на основе движка WebKit или Blink.
- `-moz-` — Firefox и браузеры на движке Gecko.
- `-o-` — Opera 12 и раньше, на движке Presto.
- `-ms-` — Internet Explorer и старый Microsoft Edge 12–18.

В последнее время в CSS появляется много новых очень мощных псевдоклассов. 
Например, стилизовать плейсхолдер в поле ввода можно при помощи такого кода:

```
input::-webkit-input-placeholder {
  color: #bada55;
}
input:-moz-placeholder {
  color: #bada55;
}
input::-moz-placeholder {
  color: #bada55;
}
input:-ms-input-placeholder {
  color: #bada55;
}
input::-ms-input-placeholder {
  color: #bada55;
}
input::placeholder {
  color: #bada55;
}
```
