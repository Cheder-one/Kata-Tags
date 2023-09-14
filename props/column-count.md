Позволяет разбить блок с текстом на несколько колонок.

Чтобы сэкономить место на экране, но при этом сделать текст читабельным, можно разбить один сплошной блок текста на несколько колонок, как это делается в газетах.

<div style="
	padding: 20px;
  column-count: 2;
  color: black;
  background-color: rgba(240, 240, 240, 0.85);">
<p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Obcaecati quam quis ipsum dolorum voluptates ratione officia fugiat sit reiciendis ipsam necessitatibus suscipit non nostrum, distinctio rerum molestias nobis dolor unde et? Ducimus quibusdam, libero pariatur vitae architecto ratione aspernatur natus. Impedit nesciunt error consequatur quasi sit eius nostrum.</p>
</div>

### *column-width*

Свойство `column-width` задаёт минимальную желаемую ширину колонки. 
Если свойство `column-count` ещё не было задано, браузер автоматически поделит текст на такое количество колонок, чтобы они уместились во всю доступную ширину.

Следует отметить, что если одиночная строка может включать от `45` до `75` символов, чтобы быть читабельной, то для колонок текста рекомендуется придерживаться ширины, включающей `40-50` символов.

### *column-gap*

<div style="
	padding: 20px;
	column-gap: 300px;
  column-count: 2;
  color: black;
  background-color: rgba(240, 240, 240, 0.85);">
<p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Obcaecati quam quis ipsum dolorum voluptates ratione officia fugiat sit.</p>
</div>


