- `Вышестоящие` слои могут `использовать` только `нижележащие` слои
- `Нижележащие` слои `не могут` использовать `вышестоящие`
- `Никто не может` использовать `элементы своего уровня`

![[Pasted image 20240313024420.png]]

- **UI** - Никакой бизнес логики, только элементы интерфейса

![[Pasted image 20240313025029.png]]

- **Components** (`например карточка товара, комментарий`)
  
![[Pasted image 20240313025150.png]]

- **Modules** - Внутри находится `вcе необходимое для работы этого модуля`

![[Pasted image 20240313025445.png]]

- **Pages** - Максимально тонкий. Собирает в себе несколько `Modules`

