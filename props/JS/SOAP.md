`SOAP` - `протокол обмена структурированными сообщениями`. Формат только `XML`.
`SOAP` - `протокол`, поэтому задает строгую структуру. `REST` же это набор `рекомендаций`.

- `REST` это множество дверей(`endpoint-ов`), в которые мы можем постучать.
- `SOAP` это скорее одно окно, в которое мы должны передать название процедуры которое хотим выполнить.

![[Pasted image 20231115231653.png]]

`SOAP` имеет `строгую структуру`:
- `Envelope` - определяет начало и конец сообщения. По нему клиент понимает когда сообщение полностью получено.
- `Header` - что-то вроде заголовков в `HTTP` запросе(отправить `токен`, указать тип `формата` сообщения и прочая `доп. инфа`)
- `Body` - полезные данные сообщения.

![[Pasted image 20231115231909.png]]

