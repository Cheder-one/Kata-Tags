<br/> - разрыв строки (Shift+Enter)
<p></p> - параграф, абзац (Enter)
<hr/> - горизонтальная линия (horizontal rule)
<span></span> - строчный элемент (выделяет выделенную строку без переноса)
<b> - Жирный текст
<strong> - Важный текст
font-weight: bold;
<i> - текст Курсив (наклонный)
<em> - текст Акцентирует внимание (наклонный)
<mark> - Маркированный текст
<small> - Небольшой текст
<del> - Удаленный (зачеркнутый) текст
<ins> - Вставленный (добавить) текст
<sub> - Подстрочный текст
<sup> - Надстрочный текст

<p contenteditable="true"> - делает параграф редактируемым

lorem20 - набор рыбьего текста 

<a href="">Наименование ссылки</a> - ссылка 
<a href="" target="_blank"> </a> - ссылка в новой вкладке
<img src="" alt=""> - тег для вставки URL или локального пути изображения. "alt" используется для написания текстового объяснения, в случае если фото будет недоступно
<_ target="_blank"> - открытие в новой вкладке
<a href="https://webref.ru"><img src="image/shark.jpg" alt=""></a> - ссылка в изображении

<ol></ol> - упорядоченная оболочка для пунктов списка
<ul></ul> - неупорядоченный, dots список 
<ol/<ul type="I/square"> Для изменения нумерации используют "type" 
<li></li> - сам список (пишется внутри <ul></ul> или <ol></ol>)

<li value="3"> -ставит значение 3 для нумерации строки
style= "list-style-type: disc/circle/square/decimal/georgian/trad-chinese-informal/kannada; "
---------
ul>li{Элемент $}*5 - Появится 5 строк с наименованием "Элемент".При добавлении "$", появится нумерация   

    const NavBar = () => {
        return (
            ul>(li>a)*4
        )
    };
     
    const NavBar = () => {
        return (
            <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
            </ul>
        )
    };

---------
<table></table> - оболочка для тегов таблицы
<thead></thead> - заголовок таблицы 
(столбцы именуются как <th></th>, а не как <td></td>. Но вкладываются все равно в <tr> <th></th> </tr>)
<tr></tr> - строка таблицы (table roll)
<th></th> - столбцы заголовка таблицы
<tbody></tbody> - основное тело таблицы
<tr></tr> - строка таблицы (table roll)
<td></td> - столбцы в теле таблицы (внутри тега <tr></tr>) (table data)

<form></form> - поле для ввода
<label for="логин">Логин</label> -  текст перед полем ввода. Тег "for" связывается с тегом "id" и при нажатии на текст выделяется форма.
<input type="text/password/email/number/range/date/color/message/" id="логин"> - что будет вводиться в поле ввода.

<section id="sex">
    <option value="Мужчина">м</option>
    <option value="Женщина">ж</option>
</section> - выпадающий из прошлого список
-------------------
/=/ Отличие label и name в ключах Объекта
---------
name - это уникальное имя, идентифицирующее элемент в списке или форме. 
Это имя может использоваться для доступа к элементу, изменения его значения или удаления из списка.

label - это описание элемента, которое обычно используется для отображения названия элемента на странице или в приложении. 
В массиве accountCardList label указывает на название элемента, которое будет отображаться на странице.

const [accountCardList, setAccountCardList] = useState([
    {
      name: "income",
      label: "Доход",
      dropDown: { label: "Дата", items: dropItems }
    }
  ]);

---------
<value=""> - атрибут тега, определяет что будет написано
<id=""> и <class=""> - "id" не должно повторяться, "class" может и используется для стилистики
<div></div> - блочный элемент (выделяет и переносит абзацем)
<header>/<footer>/<nav>/<article>/<section (группа для article)>/<aside (для меню слева-справа)> - это все замена <div> для правильной индексации и нормализации поиска сайта

<figure>
   <img src="" alt="">
   <figcaption>Подпись</figcaption> - связывает подпись с картинкой
</figure> 
<details>
   <summary></summary> - Описание и краткое заглавие выпадающего описания
</details>
_______________________________
/=/=/ Выделить текст при вставке в расширении
---------
    const logToInsert = `console.log(\${1:${text}});`;
    vscode.commands.executeCommand("editor.action.insertSnippet", { snippet: logToInsert });

text
  ? vscode.commands
      .executeCommand("editor.action.insertLineAfter")
      .then(() => {
        const logToInsert = `console.log(\${1:${text}})`;
        vscode.commands.executeCommand("editor.action.insertSnippet", {
          snippet: logToInsert,
        });
      })
  : vscode.window.activeTextEditor?.insertSnippet(new vscode.SnippetString('console.log($1)'));
_______________________________
CSS
   h1       {color: red}
-селектор {свойство: значение}
-свойство: функции (значение);
.class > p - обращение только к детям класса (не учитывая детей детей)
---------------------------------------------------------
font-family - выбор шрифта (Roboto,Times..)
font-size - размер текста
font-weight - толщина начертание шрифта (normal/400, bold/700)
text-transform: uppercase, capitalize
font-style: normal, italic, oblique 30deg
    - oblique наклоняет текст, что создает эффект похожий на курсив, но без изменения начертания шрифта
text-decoration: underline, overline, none
---------------------------------------------------------
width= "150" - устанавливает ширину элемента (ширину области)
word-spacing - расстояние между словами
letter-spacing - расстояние между символами
line-height - межстрочный интервал
text-decoration: underline; - подчеркивания, зачеркивания, none
<del></del> -зачеркнутый текст или (представляет диапазон текста, который был удалён из документа)
<ins></ins> - подчеркивание или (показывает что было добавлено в код)
opacity: 0.4 - непрозрачность элемента
---------------------------------------------------------
#ff0000 - красный; color: #00ff00 зеленый; color: #00ff00 синий;
color: rgba(0, 255, 0, 0.2) - цвета и прозрачность
-Дизайн цвета можно копировать с браузера с помощью пипетки из "Исследовать элемент"
---------------------------------------------------------
-CSS код можно писать как в  HTML в <head><style></style></head>
 Можно писать инлайн <header style="color: black;"></header>
 Можно писать так же отдельно в css файле: <link rel="stylesheet" href="Index.css0">
---------------------------------------------------------
padding: 0px 20px 0px 20px - можно написать сразу для 4х сторон. Отсчёт идёт по часовой стрелке.
padding - внутренние отступы (внутри рамки)
margine - внешние отступы (за рамкой)
margin: auto; - выравнивание по центру 
bottom - подвал/низ
top - верх
---------------------------------------------------------
* {} - селектор задает значение всему на странице
#id {} - стилизация через ID: #id {}
.card p {} -для обращения к безликому(повторяющемуся в др местах) дочернему тегу через родительский указываем путь: .card p {}
@import url() - Импорт шрифта
div p - выбор всех элементов p внутри элемента div
---------------------------------------------------------
filter: blur(2px)
filter: grayscale (0%) - сепия
filter: opacity (100%) - непрозрачность
filter: saturate (100%) - насыщенность 
filter: contrast (100%) - контрастность
background: linear-gradient ( 45deg, blue, lightGreen) - градиент
cursor:pointer; - изменение курсора при наведении
---------------------------------------------------------
background-image: url("img/whistle.svg"); - выставление бэкграунд фото
background-repeat: no-repeat; - не размазывать фон (иконки) по всему блоку
background-position: center top; - местоположение бэкграунд изображения (может выступать иконкой, а не фоном сайта)
background-position: right 35% bottom 45%;
background-size: - размер изображения
---------------------------------------------------------
list-style: none или url('/media/examples/rocket.svg'); - что будет показываться в пунктах(точках) списка
---------------------------------------------------------
.cards a:hover {} - интерактивность при наведении на элемент, меняет цвет/размер шрифта итд 
transition: all .2s; - анимация увеличения для селектора (например для ссылки при наведении)
.table:nth-child(odd/even/1/2/3..) - выделение столбцов таблицы
---------------------------------------------------------
Flex
---------------------------------------------------------
Используется для родительского элемента:
<div class="container"><div></div></div>

display: flex; - создаёт флекс контейнер 
flex-direction: row/column; - элементы в строку/ в колонке

.container { justify-content: center; } - установка элемента по центру
justify-content: space-around; - равномерное распределение элементов по контейнеру (space-around/space-between/center/start/end)
---------------------------------------------------------
JavaScript 
JS - регистрозависимый язык
---------------------------------------------------------
Функция isNaN() возвращает true, если значение не число, равно NaN (Not-a-Number), и false, если нет.
---------------------------------------------------------
== 	равно
=== 	равное значение и равный тип
!= 	не равный
---------------------------------------------------------
unshift - Добавление новых элементов в начало массива
var fruits = ["Банан", "Апельсин", "Яблоко", "Манго"];
fruits.unshift("Lemon","Pineapple");
---------------------------------------------------------
/=/=/ Math.max([x[, y[, …]]])- Возвращает наибольшее число из своих аргументов.
-------------------
    Math.max(1, 3, 2); // Expected output: 3
    Math.max(0, -14); // Expected output: 0

---------
// Установка ограничений для счетчика (чтобы не уходил в минус)
---------
    Math.max(0, initialState[0].value - 1);
    // вернет либо 0, либо значение initialState[0].value - 1, если оно больше нуля.
---------
// Функция счетчика с +/- в одном 
---------
    onClick={() => onCounterChange(id, 1)}
    onClick={() => onCounterChange(id, -1)}

    const handleCounterChange = (id, delta) => {
        setCounters((prevState) =>
            prevState.map((el) =>
                el.id === id
                ? { ...el, value: Math.max(0, el.value + delta) }
                : { ...el }
            )
        );
    };

---------------------------------------------------------
/=/=/ Math.abs() - используется для получения абсолютного значения числа. Абсолютное значение числа - это значение числа без его знака.
-------------------
    console.log(Math.abs(-5)); /=/ Output: 5
    console.log(Math.abs(10)); /=/ Output: 10
    console.log(Math.abs(0)); /=/ Output: 0

    let numStr = "-1000";
    let num = parseInt(numStr);
    let positiveNum = Math.abs(num);

    console.log(positiveNum); /=/ 1000
---------------------------------------------------------
/=/=/=/ Циклы
---------------------------------------------------------
// Будь внимателен в Циклах и Массивах
* со знаками <= >= < > 
* с Мутациями массива
-------------------
Если не сходится счет цикла с индексами массива, то возможно дело в знаках или в slice(start, end) – создаёт новый массив, копируя в него элементы с позиции start до end (не включая end). 
Дело может быть так же в методах массивов: С мутацией или без 

// Вот пример когда создание переменной с хранением в ней длинны массива может помочь избежать неправильного подсчета итераций и индексов при мутации массива с использованием на примере shift(). 

const peopleWaiting = [
   "Кристина",
   "Олег",
   "Кирилл",
   "Мария",
   "Светлана",
   "Артем",
   "Глеб"
];

let numberGotParcel = peopleWaiting.length;

for (let i = 0; i < numberGotParcel; i++) {
   console.log('numberGotParcel', numberGotParcel); // 7
   console.log('peopleWaiting.length', peopleWaiting.length); // 7 => 1

   const visitorLeaveName = peopleWaiting.shift();
   console.log(`${visitorLeaveName} получил(а) посылку. В очереди осталось ${peopleWaiting.length} человек`);
};

-------------------
for (начало; условие; шаг) {
  // ... тело цикла ...
}
for (let i = 0; i < 3; i++) { 
   // выведет 0, затем 1, затем 2
  alert(i);
}
---------------------------------------------------------
Чтобы вывести объединить текстовую строку и переменную является знак «+». Чтобы сообщить о том, что здесь закончился текст и начинается переменная Javascript, нужно открыть и закрыть кавычки.
alert( "Привет " + name + "!");
---------------------------------------------------------
<script defer src="js/vendor/jquery.js"></script>
async - выполнение скриптов по мере возможности, "рандомно"
defer - выполнение в строгой последовательности их размещения
---------------------------------------------------------
Math.floor() - округление вниз. Округляет аргумент до ближайшего меньшего целого.
---------------------------------------------------------
querySelector - "найди и принеси элемент" селектор запросов (en/ru)
document.querySelector('селектор');
document.querySelector('.page'); - js ищет на странице элемент с классом "page"
---------------------------------------------------------
Для добавления js в html, <script></script> добавляется перед </body>
Для подключения js к html необходимо ввести в конце <body> <script src="index.js"></script> </body>
---------------------------------------------------------
Тестирование с помощью консоли (вывод в консоль):
console.log(document.querySelector('.page'));
console.log - обращение к консоли
(document. ___ ) - "документ" поиск по данному файлу 
---------------------------------------------------------
/=/=/ classList.remove() - удаление класса 
-------------------
элемент.classList.remove('класс');
document.querySelector('.page').classList.remove('light-theme');

Сначала ищем селектор, во втором моменте "." не ставится, тк js знает что это класс

// OR

найденный_класс.remove();

    document.querySelector('.cookie-consent').remove();
---------
    const cookieConsentButton = document.querySelector('.cookie-consent__button');

    cookieConsentButton.addEventListener('click', function() {
        document.querySelector('.cookie-consent').remove();
    });
---------------------------------------------------------
/=/=/ classList.add - добавление класса 
элемент.classList.add('класс');
---------------------------------------------------------
Переменная — это способ сохранить данные, дав им понятное название (ярлык с файлами).
Константа - почти тоже самое что и переменная, только значение которой нельзя менять
---------------------------------------------------------
let - с помощью него можно создать (объявить) переменную. 
let: - "пусть/допустим" за которым следует имя для вашей переменной. 
Чтобы задать несколько значений let 
let numbers = [10, 4, 100, -5, 54, 2]; - массив

У переменных после их наименования с помощью "let" должно быть присвоено значение.
" = " - с помощью знака равенства присваиваем значение переменной
let variableName = 'Я значение переменной!';

let header = document.querySelector('header'); - при вводе переменной "header", JS выполняет функцию поиска по документу селектора header
---------------------------------------------------------
Условия / условные выравнивания (Conditionals) - it/else/else if 
---------------------------------------------------------
События (Events) - это действия, которые происходят в браузере, например, нажатие кнопки или загрузка страницы или воспроизведение видео, в ответ на которые мы можем запускать блоки кода.
Конструкции прослушивающие события - прослушиватели событий
Блоки кода выполняемы в ответ на срабатывание события - обработчики событий
---------------------------------------------------------
Циклы (Loops)

for - для / of - из

const fruits = ['apples', 'bananas', 'cherries'];
for (const fruit of fruits) {
  console.log(fruit);
}
Данный цикл будет поочередно выводить значения массива константы "fruits"
Строка for (const fruit of fruits) говорит:
1.Получи первый элемент из fruits.
2.Установи переменную fruit для этого элемента, затем запусти код между скобками {}.
3.Получи следующий элемент из fruits и повторяй, пока не дойдешь до конца.
---------------------------------------------------------
Массив — это набор элементов
Строка const fruit = ['apples', 'bananas', 'cherries']; создает массив.
---------------------------------------------------------
focus() - 
guessField.focus(); помещает курсор в текстовое поле при загрузки страницы 
---------------------------------------------------------
alert() - выводит модальное окно на странице
const years = prompt('Сколько вам лет?', 100);
alert('Вам ' + years + ' лет!')

prompt() - выводит окно с строкой заполнения и его возможным заполнением('Наименование окна','Запись в строке заполнения') 
Сохранить в переменную: const userName = prompt('Как вас зовут?');

confirm() - диалоговое окно с сообщением и кнопками выбора "cancel" - false, "ok" - true.
---------------------------------------------------------
Чтобы вывести в консоль в одну строку несолько параметров:
console.log(`${myInfoText[0]} ${myInfoText[441]}`)
---------------------------------------------------------
Определяем переменную let: 
let name = 'Petr the pig';
Переопределяем и выводим для проверки в консоль:
name = 'Nastya'
console.log("Имя было изменено", name);
Или можно переопределить на другую переменную:
ageOfPerson2 = ageOfPerson1;

Определяем переменную const: 
const programmingLanguage = 'JavaScript';
Константа не переопределяется и выходит ошибка:
programmingLanguage = 'Java'
console.log(Java);
---------------------------------------------------------
В JS 8 типов данных:
- String (строка)
- Number - число
- Boolean - (логический) оперирует только trye/false
- Null - пустое значение или значение неизвестно 
- Undefined - переменная была объявлена, но значение ей не присвоено.
let x;
console.log(x);
(оставь этот вывод значения системе, используй null)
- Object - сложный тип данных, объединяющий несколько параметров
const car = {
   name: "Toyota Corolla",
   year: 2017,
   isNew: false,
   owner: null
 }
//  Обратиться к свойству Объекта:
 console.log(car.name);
- Symbol - нужен для создания уникальных ключей объекта (невозможно преобразовать в number)
const id = Symbol('id');
console.log(id);
- BigInt - большое число (больше, чем (2⁵³-1), т.е. 9007199254740991).
Для создания переменной этого типа нужно поставить букву n в конце числа: 
let bigNumber = 123456789n;
Число гугол может быть записано как 1e9 (1 * 10^9).

---------------------------------------------------------
/=/=/ Разделения разрядов в JavaScript
-------------------
Можно использовать и запятую (",") и точку (".") в числах для разделения разрядов. Оба формата будут распознаны как числа, и typeof для них будет возвращать "number".

    let number1 = 10,000;
    console.log(number1); /=/ Выведет 10000
    console.log(typeof number1); /=/ Выведет "number"

    let number2 = 10.000;
    console.log(number2); /=/ Выведет 10.0
    console.log(typeof number2); /=/ Выведет "number"

!!! Внимание!
! Во втором примере точка используется как десятичный разделитель, поэтому число будет интерпретировано как 10.0
-------------------
/=/=/ Форматирование чисел с разделением на каждый разряд
---------
Для форматирования чисел с разделением на каждый разряд в JavaScript вы можете использовать метод toLocaleString(). Этот метод позволяет настроить форматирование числа с разделением на основе локали.

    const arr = [-100, -2000, 50000, 900000, 100000000];
    const formattedArr = arr.map(number => number.toLocaleString());

    console.log(formattedArr); // =>
    ["-100", "-2 000", "50 000", "900 000", "100 000 000"]

-------------------
/=/ Обратное форматирование 
---------
    const num1 = "-2 000".replace(/[^\d-]/g, ""); 
    console.log(num1); /=/ -2000

    const num2 = "-2,000".replace(/,/g, "")
    console.log(num2) /=/ -2000

    /=/ [^\d-] заменяет все символы, кроме цифр и минуса
---------------------------------------------------------
/=/=/=/ parseInt() и parseFloat() - преобразовывать строки, содержащие числа, обратно в числовой формат.
-------------------
/=/=/ parseInt() - для преобразования строки в целое число. Он принимает два аргумента: строку, которую нужно преобразовать, и опциональный аргумент, указывающий систему счисления. 

    parseInt("42") /=/ 42.

---------
/=/=/ parseFloat() - для преобразования строки в число с плавающей точкой. Он также принимает один аргумент: строку, которую нужно преобразовать.

    parseFloat("3.14") /=/ 3.14.

-------------------
/=/ BigInt особенности
---------
Почему выдает 6145390195186705000 а не 6145390195186705004?

    const num = [6, 1, 4, 5, 3, 9, 0, 1, 9, 5, 1, 8, 6, 7, 0, 5, 5, 4, 3].join("");

    console.log(Number(num) + 1);

В данном случае, строка num содержит очень большое число, которое превышает максимально возможное число для представления в JavaScript (которое равно 9007199254740991). При попытке выполнить операцию сложения, JavaScript не может точно представить полученное число и использует приблизительное представление в виде экспоненциальной записи.

Поэтому результатом является число 6145390195186705000, которое является приближенным значением полученного числа. Если вы хотите получить точный результат, вам следует использовать библиотеку для работы с большими числами, такую как BigInt. Например:


    const num = [6, 1, 4, 5, 3, 9, 0, 1, 9, 5, 1, 8, 6, 7, 0, 5, 5, 4, 3].join("");
    const bigNum = BigInt(num) + 1n;
    console.log(bigNum.toString()); // "6145390195186705004"
    
В этом примере мы использовали функцию BigInt(), чтобы создать большое число, которое может быть точно представлено в JavaScript, и добавили к нему единицу. Затем мы использовали метод toString() для преобразования большого числа в строку.
---------------------------------------------------------
/=/ Как определить тип данных? (например что это строка)
    typeof('') или typeof ''
    console.log(typeof 'Maxim')
---------
//=/ Проверка на тип значения = 'число'
   const value = 2   
   if (typeof value === 'number') {
      //it's a number
   }
-------------------
/=/=/ Array.isArray(arr) - проверка на массив 
---------
    const BoxWithBoxes = [
        [3, [3, [3, [3]]]],
        [1, 2, 3],
        [1, 5, 4, [1, 3]],
        [7, 3],
        [9, [0, 1]],
    ];

    console.log(Array.isArray(BoxWithBoxes)); // true
---------------------------------------------------------
// Явное преобразование к строке:
String(_переменная_)
const age = 22;
console.log('string age:', age, typeof String(age)); 

// Явное преобразование к числу:
Number(_переменная_)
'Hello' - выведет NaN (not a number)
'1 2' - выведет NaN (not a number)
let question2 = Number(prompt('Сколько будет 2 * 2?'))

// Явное преобразование к Boolean:
Большинство переменных выводится "true"
null, Undefined, NaN, 0, '' - выводится false ('' - пустая строчка)
'0' - строка, выдаст true
---------------------------------------------------------
// Конкатенация - операция соединения строк (например строк, строк строки, поиск нужных символов и фраз)
const name = 'Denis';
const specialization = 'Novice-developer';

// Конкатенация 3 способа:

const allInfo1 = name + ' ' + specialization;
console.log(allInfo1);

const allInfo2 = `${name} ${specialization}`
console.log(allInfo2);

let allInfo3 = name + ' ';
allInfo3 += specialization;
console.log(allInfo3);

"Hello".concat(" T", "p", "r", "o", "g", "e", "r"); // "Hello Tproger"
---------------------------------------------------------
// Узнать длину строки (length)
const programmingLanguage = 'JavaScript';
console.log(programmingLanguage.length); // 10

// Получение индекса (буквы) строки
   Отсчет идет с 0
console.log(programmingLanguage[4]); // S
console.log(programmingLanguage[44]); // undefined
Или с помощью команды .charAt(0)
   С помощью этого НЕЛЬЗЯ поменять символ 
programmingLanguage[4] = 's'; (не сработает)
   Получаем последний символ
alert( str[str.length - 1] ); // o
---------------------------------------------------------
// toUpperCase, toLowerCase - изменяет на ЗАГЛАВНЫЕ и строчные 
   const animal = 'Lion';
   console.log('upper', animal.toUpperCase());
   console.log('lower', animal.toLowerCase());
   console.log(animal); - не изменяет само значение, а создает новое с заглавными или строчными

Слово с заглавной буквы:
   const publication = "freeCodeCamp";
   const FreeCodeCamp = publication[0].toUpperCase() + publication.substring(1);

   console.log('freeCodeCamp toUpperCase:', FreeCodeCamp);

Несколько слов с заглавной буквы:
   const mySentence = "freeCodeCamp is an awesome resource";
   const words = mySentence.split(" ");
   words.map((word) => { 
      return word[0].toUpperCase() + word.substring(1); 
   }).join(" ");
---------------------------------------------------------
// slice, substring - Если нужно получить символы между определенными индексами
    const programmingLanguage1 = 'JavaScript';

    console.log('slice', programmingLanguage1.slice(1, 5)); // avaS
    console.log('slice', programmingLanguage1.substring(1, 5)); // avaS

---------
// Удалить 1-й и last символ
---------
    const arr = [
        { _id: "673eeb7f6f471100", name: "Странный", color: "warning" },
        { _id: "673eeb7f6f471103", name: "Робкий", color: "dark" }
    ];

    const stringArr = JSON.stringify(arr);

    stringArr.slice(1, -1); 
    // {"_id":"673eeb7f6f471100","name":"Странный","color":"warning"},
       {"_id":"673eeb7f6f471103","name":"Робкий","color":"dark"}
       // Удалил внешние скобки массива

---------------------------------------------------------
// replace, replaceAll - Замена (одного и всех)символов символов в строке.

    const programmingLanguage2 = 'JavaScript';
    console.log('replace', programmingLanguage2.replace('a', 'A')); 
    console.log('replaceAll', programmingLanguage2.replaceAll('a', 'A')); 

---------
// Задача на шифр Цезаря через 
---------   
    function rot13(text) {
        return text.replace(/[a-zA-Z]/g, (char) => {
            const offset = char.charCodeAt() >= 97 ? 97 : 65;
            return String.fromCharCode(((char.charCodeAt() - offset + 13) % 26) + offset);
        });
    }
---------
Syntax:
    
    .replace(элемент_для_замены, на_что_заменяем)

    "Ruby is cool!".replace(/[a-zA-Z]/g, (char) => {
        const offset = char.charCodeAt() >= 97 ? 97 : 65;
        return String.fromCharCode(((char.charCodeAt() - offset + 13) % 26) + offset);
    });

---------
// .replace() with regular expression
---------
Filter out non-letter characters from a string:

    let str = "Hello, world!";
    let lettersOnly = str.replace(/[^a-zA-Z]/g, "");
    console.log(lettersOnly); // Output: "Helloworld"

// The regular expression /[^a-zA-Z]/g matches all characters that are not in the range of uppercase or lowercase letters from A to Z. The ^ character inside the square brackets means "not", so [^a-zA-Z] means "match any character that is not an uppercase or lowercase letter from A to Z".
---------
// Заменить все кроме цифр 

    let words = [ 'is2', 'Thi1s', 'T4est', '3a' ]
    
    const numbsOnly = words.map(el => el.replace(/[^\d+]/g, "")) 
      // [ '2', '1', '4', '3' ]

---------------------------------------------------------
// trim() - удаление лишних пробелов
const nameOfUser = prompt('Ты кто?')
console.log('nameOfUser', nameOfUser.trim());
---------------------------------------------------------
console.log(- 5); // Унарный минус
console.log(10 - 5); // Бинарный минус

// Инкремент и Декремент
let cupsOfCoffeee = 2;

cupsOfCoffee = + 5;
cupsOfCoffee += 1;
cupsOfCoffee = * 6; 
cupsOfCoffee = / 2; 
cupsOfCoffee *= 6;
cupsOfCoffee /= 2;
   
// Постфикc и префикс
let cupsCoffee = 0;

console.log('cupsCoffee++:', cupsCoffee++); // Возвращает исходное значение
   
console.log('++cupsCoffee:', ++cupsCoffee);
---------------------------------------------------------
/=/=/=/ Математические операторы
   +, -, *, /, %, **

// Взятие остатка от деления %
a % b – это остаток от целочисленного деления a на b

   alert( 5 % 2 ); // 1, остаток от деления 5 на 2
   alert( 8 % 3 ); // 2, остаток от деления 8 на 3

// Возведение в степень **
В выражении a ** b оператор возведения в степень умножает a на само себя b раз.

alert( 2 ** 3 ); // 8  (2 * 2 * 2, 3 раза)
alert( 4 ** (1/2) ); // 2 (степень 1/2 эквивалентна взятию квадратного корня)
alert( 8 ** (1/3) ); // 2 (степень 1/3 эквивалентна взятию кубического корня)
---------------------------------------------------------
/=/=/=/ Сравнение строк

// Операторы сравнения: 
> < >= <= == ===
Примечание: никогда в разработке веб-приложений не используй нестрогое сравнение ==. Оно является инициатором большого количества багов, так как производит преобразование типов. Используй исключительно строгое сравнение ===. Оно не преобразует типы и уменьшает шанс возникновения ошибок. 

console.log("'Ass' == 'ass'",'Ass' == 'ass'); // false
console.log('"A".charCodeAt()', 'A'.charCodeAt()); // 65
console.log('"a".charCodeAt()', 'a'.charCodeAt()); // 97

// String.fromCharCode() - Получится символ в обратную сторону из числа
console.log(String.fromCharCode(97)) // 'a'
console.log(String.fromCharCode(65)) // 'A

// == vs ===
// == сравнивает значения
console.log("'1' == 1", '1' == 1);
console.log("'200' > '21'", '200' > '21');
console.log("true == 1", true == 1);

// === сравнивает типы (рекомендовано)
console.log("1 === 1", 1 === 1)
console.log("true === 1", true === 1)

---------------------------------------------------------
/=/=/=/ JSON.stringify() - Приведение Объекта к строке
-------------------
Для сравнения объектов, а не ссылок, нам просто нужно привести их к строке

    const obj1 = { a: 1, b: 2 };
    const obj2 = { a: 1, b: 2 };

    console.log(obj1 === obj2); // false
    console.log(JSON.stringify(obj1) === JSON.stringify(obj2)); // true

При сравнении объектов или массивов в JavaScript с помощью оператора == или === будет производиться сравнение ссылок на объекты. Даже если два объекта имеют одинаковое содержание, они будут разными объектами и оператор == или === вернет false. 
Поэтому в данном случае используется метод JSON.stringify, чтобы преобразовать объекты в строки и сравнить уже строки, а не ссылки на объекты.

-------------------
/=/=/ JSON.parse(JSON.stringify(obj)) - Превращает обратно в JSON
    Производит глубокое копирование Объекта 
---------
    const obj = {a: 1, b: {c: 2}};
    const copy = JSON.parse(JSON.stringify(obj));

---------
// OR - Lodash

Использование специализированных методов сравнения - например, метод isEqual() из библиотеки Lodash. Этот метод рекурсивно сравнивает два объекта на равенство по свойствам и значениям.

---------------------------------------------------------
/=/=/ ASCII code - method to find out the index of a letter in the alphabet
---------
//charCodeAt()
//fromCharCode()
//charCodeAt()

    let letter = 'A';
    let ascii = letter.charCodeAt(0);
    console.log(ascii); // Output: 65

    let ascii = 65;
    let letter = String.fromCharCode(ascii);
    console.log(letter); // Output: "A"
---------
    let letter = 'B';
    let ascii = letter.charCodeAt(0);
    let index = ascii - 65 + 1;
    console.log(index); // Output: 2

    ASCII value of 'B' = 66
    ASCII value of 'A' = 65
    66 - 65 + 1 = 2 // index "B" in the alphabet
// OR 
    66 - 64 = 2 // index "B" in the alphabet

-------------------
/=/=/ RGB to HEX code
---------
    function decimalToHex(decimalValue) {
    // преобразуем в шестнадцатеричное значение
        var hexValue = decimalValue.toString(16); 
    // добавляем ведущий ноль, если необходимо
        return hexValue.length == 1 ? "0" + hexValue : hexValue; 
    }

---------------------------------------------------------
/=/=/=/ Math() 
---------------------------------------------------------
console.log('Math объекты');
console.log('Число Pi', Math.PI); // 3.141592653589793

-------------------
/=/ Math.round() – простое округление
---------
    console.log('Простое округление:');
    console.log('Math.round(40.4)', Math.round(40.4)); // 40
    console.log('Math.round(40.5)', Math.round(40.5)); // 41
    console.log('Math.round(40.6)', Math.round(40.6)); // 41

-------------------
/=/ Math.floor() – округление вниз
---------
    console.log('Округление вниз:');
    console.log('Math.floor(40.5)', Math.floor(40.5)); // 40
    console.log('Math.floor(40.9)', Math.floor(40.99)); // 40

-------------------
/=/ Math.ceil() – округление вверх
---------
    console.log('Округление вверх:');
    console.log('Math.ceil(40.1)', Math.ceil(40.1)); // 41

-------------------
/=/=/ Math.max(...arr) - Вывести максимальное число из Массива
---------

    Math.max(...[ 316, 105, 412, 97, 438, 229, 227, 432 ]) // 438

-------------------
/=/=/ Math.random(). Создание рандомного числа с помощью 
---------

   function getRandomInt (min, max) {
      return Math.floor(Math.random() * (max - min + 1) + min)
   };
   console.log('getRandomInt', getRandomInt (3, 6));

-------------------
/=/=/ Math.pow() - возведение в степень
---------
    Math.pow(7, 2); // 49
    Math.pow(4, 0.5); // 2
    Math.pow(7, -2); // 0.02040816326530612 // (1/49)
    Math.pow(-7, 0.5); // NaN

---------------------------------------------------------
// .toFixed(x) - обрезает/сокращает значение
let result = Number((amount / rate).toFixed(2)); // .toFixed(2) - обрезает значение до 2х символов. 
---------------------------------------------------------
/=/=/=/ Условное ветвление

!!!   const offset = 's'.charCodeAt() >= 97 ? 97 : 65;

Если ASCII код 's' == (115) > 97, то offset = 97, если нет, то offset = 65
    
---------
/=/=/ {if} {else}
---------
    if (условие) {
      // Выполнится, если условие будет истинным
    } else {
      // Выполнится, если условие будет ложным
    }

    let isFrontendDeveloper = true;

    if (isFrontendDeveloper) {
       console.log('isFrontendDeveloper = true','You are a Front-End developer. Welcome to the team!');
    } else {
       console.log('isFrontendDeveloper = false', 'You are not a Front-End developer');
    }

    const condition = 5 > 10; // вернет false
    if (condition) {
      console.log('Выражение истинно!');
    } else {
      console.log('Выражение ложно!');
    }
    Вывод: Выражение ложно!

    let developerJobType = 'Front-End';

    if (developerJobType === 'Front-End') {
       console.log('2000$');
    } else if (developerJobType === 'Back-End') {
       console.log('1500$');
    } else if (developerJobType === 'Full-Stack') {
       console.log('3500$');
    } else {
       console.log('Зарплата не определена');
    }
---------------------------------------------------------
/=/=/=/ switch case / break / default 
-------------------
В `case` можно передавать Функцию

    case "isRequired": {
        return Boolean(value.trim());
    }
---------
    switch (ruleName) {
        case "isRequired": {
            return Boolean(value.trim());
        }
        case "isEmail":
            return isEmail(value);
        default:
            return true;
    }
    
-------------------
    let arg = prompt("Введите число?");
    switch (arg) {
    case '0':
    case '1':
        alert( 'Один или ноль' );
        break;

    case '2':
        alert( 'Два' );
        break;

    case 3:
        alert( 'Никогда не выполнится!' );
        break;
    default:
        alert( 'Неизвестное значение' );
    }
-------------------
   let developerJobType = 'Front-End';

   switch (developerJobType) {
      case 'Front-End':
         console.log('2000$');
         break;
      case 'Back-End':
         console.log('1500$');
         break;
      case 'Full-Stack':
         console.log('3500$');
         break;
      default:
         console.log('Зарплата не определена');
---------------------------------------------------------
/=/=/=/ ? : - замена else if

let favoriteDrink = '???'

let message = favoriteDrink === 'Coffeee' // условие 
   ? 'Your favorite drink is Coffeee' 
   // после '?' выполняет если условие 'true'
   : 'You most likely have a healthy CNS'; 
   // после ':' выполняет если условие 'false'

let question2 = prompt ('Сколько будет 2 * 2?') 
    question2 = Number(question2)

   question2 === 2 * 2
   ? alert('Ответ Верный') + correctAnswers++
   : alert('Ответ Неверный') + incorrectAnswers++;
-------------------
// Несколько операторов ? :

   let age = prompt('Возраст?', 18);

   let message = (age < 3) ? 'Здравствуй, малыш!' :
   (age < 18) ? 'Привет!' :
   (age < 100) ? 'Здравствуйте!' :
   'Какой необычный возраст!';

   console.log('message:', message);
-------
    inputValue === ""  
    ? console.log('Название задачи не должно быть пустым')

    : tasks[i-1].text === inputValue 
    ? console.log('Задача с таким названием уже существует')

    : callTaskTemplate(el.id, el.text) 
---------------------------------------------------------
// && (И) - Возвращает true если все аргументы истинны, а иначе – false:
   alert( true && true );   // true
   alert( false && true );  // false
   alert( true && false );  // false
   alert( false && false ); // false
// || (ИЛИ) - Если какой-либо из аргументов true, он вернёт true, в противоположной ситуации возвращается false.
   alert( true || true );   // true
   alert( false || true );  // true
   alert( true || false );  // true
   alert( false || false ); // false
// ! (НЕ)
// ?? (Оператор объединения с null) - Пропускает только значения "null" и "undefined" 

/=/=/=/ && (И) - Ищет и выводит значение с "false". Значения  "true" пропускаются.
Пропускает алгоритм далее если оба значения true:
if (existingUserLogin === userLogin && existingUserPassword === userPassword) {
  alert(`Добро пожаловать, ${userLogin}!`);
} else {
  alert("Логин и (или) Пароль введены неверно!");
}

console.log('//&& (И)//');

let userAge = 20;

if (userAge > 6 && userAge <= 18) {
   console.log('Пользователь ходит в школу');
} else {
   console.log('Пользователь НЕ ходит в школу');
}


let programingLanguage = 'JavaScript'
let experienceInYear = 1;

if (programingLanguage === 'JavaScript' && experienceInYear >= 1) {
   console.log('Добро пожаловать в нашу команду');
} else {
   console.log('Нужно бооольше опыта');
}

/=/=/=/ || (ИЛИ) - Ищет и выводит значение с "true". Значения  "false" пропускаются.

let currentHour = 10;

if (currentHour < 8 || currentHour > 20) {
   console.log('Наш офис Закрыт');
} else {
   console.log('Наш офис Открыт');
}


let userNickname = null;
let defaultNicname = 'User';

let nickname = userNickname || defaultNicname || 'noname';
console.log('nickname', nickname);

/=/=/=/ ! (НЕ)
let = answer = prompt ('How old are you?')
answer = Number(answer);

if (!answer) {
   alert('Enter your total number of years')
} else {
   alert(`You are ${answer} years old`)
}

Предположим, у нас есть сайт и мы хотим сделать какие-то действия, если пользователь не авторизован. Также у нас есть переменная isAuth:
let isAuth = false; //if (existingUserPassword === userPassword) {
   alert (`Добро пожаловать, ${userPassword}`)
} Пользователь не авторизован

if (!isAuth) {
  // Пользователь не авторизован, условие выполнится
}
Условие сработает, так как !isAuth === true и в if будет передано true. 

/=/=/=/ ?? (Оператор объединения с null)

// ?? - undefined, null 
console.log(false ?? 'Hello worldblat!');

// || - false, 0, "", NaN, undefined, null
console.log(false || 'Hello worldblat!');

---------------------------------------------------------
/=/=/=/ Циклы 
---------------------------------------------------------
// Переменные в циклах не видны за их пределами. 
// Чтобы переменные были видны ни только в цикле о и за ним, необходимо создать эту переменную заранее.
---------
/=/=/ .repeat(i) - вместо for, для loop повторений 

    function accumulate(ltr) {
    ltr = ltr.split('')
    return ltr.map((el, i) => el.toUpperCase() + el.toLowerCase().repeat(i)).join('-');
    }

    console.log(accumulate("abcd"));
-------------------
/=/=/=/ for () {}
-------------------
// for (начальное значение; условие (до тех пор пока); шаг) {
   ... тело цикла ...
};

   for(let i = 0; i<5; i++){
      
      console.log(i);
   }
   console.log("Конец работы"); 
   // 0
   // 1
   // 2
   // 3
   // 4
   // Конец работы
---------------------------------------------------------
/=/=/=/ Перебор Массивов
---------------------------------------------------------
/=/=/ for
-------------------
   for (let i = 0; i < developerNames.length; i++) {
      console.log('i', i);
      console.log('item', developerNames[i]);
   }
-------------------
// Посчитать сумму значений массива
-------------------
   let sum = null;
   for (let i = 0; i < arr.length; i++) {
      sum += arr[i];
   }
---------
    arr.forEach(el => {
        console.log(sum += el);
    });
-------------------
/=/=/ for of
-------------------
   for (const item of object) {
      // item - переменная отвечающая за элемент массива
      // object - название перебираемого массива/объекта
   };
-------
   for (const name of developerNames) {
      console.log('name', name);
   };
-------
   let iterable = [10, 20, 30];

   for (let value of iterable) {
      value += 1;
      console.log(value);
   };
   // 11
   // 21
   // 31
-------------------
/=/=/ forEach
-------------------
! Разница между forEach() и for()
- forEach() не прерывает цикл даже если есть if() и return и проходится до конца, выводя все значения и лишь потом идет к if() и return
- for() же прерывает цикл при необходимости.
- for (const el of arr) {} - тоже работает как и for ()
---------
! Метод forEach не возвращает никакое значение, он используется только для перебора массива и выполнения какого-либо кода для каждого элемента массива!

Не сработает:
    const check = fnArguments.forEach((el, i) => 
        isNaN(el)
    )
    console.log(check);

forEach - не нуждается в [i] при переборе, он сам сдвигает очередь элементов без упоминания счетчика циклов (i)

   let updatedStudent = [
      ...students,
   ];

   updatedStudent.forEach((el, i) => {
      el.job = "веб-разработчик";
   });

-------------------
   array.forEach(() => {}); 
   forEach это метод массива => необходимо обращаться к массиву.

   array.forEach((элемент, индекс, массив) => {
   // тело функции
   })

1. Метод forEach() принимает в себя функцию-callback. Callback - это функция, которая передается в другую функцию.
2. В свою очередь, функция принимает в себя три параметра:
   - Элемент. Данный параметр принимает в себя, непосредственно, значение каждого элемента массива по порядку.
   - Индекс. Данный параметр является опциональным (необязательным) и принимает в себя индекс текущего элемента массива.
   - Массив. Данный параметр также является опциональным и каждый раз принимает в себя текущий массив.
3. Тело функции. В данном месте мы прописываем всю необходимую логику. Она будет выполняться для каждого элемента массива.   

   developerNames = [
      'Maxim',
      'Jora',
      'Kiristina',
      'Alberto',
      'Djovanni'
   ];

   developerNames.forEach((name, index, array) => {
      console.log('name', name);
      console.log('index', index);
      console.log('array', array);
   });
---------------------------------------------------------
// Проверка четных / нечетных чисел с помощью оператора получения остатка от деления %.
   for (let i = 0; i <= 10; i++) {
      if (i % 2 == 0) {
         console.log(i);
      }
   }   
--------------------------------------------------------- 
// Найти делители числа и их количество

   let n = 12, divisor = [];
      for (let i = 1; i <= n; i++) {
         if (n % i == 0) {
            divisor.push(i);
         }
      }
console.log(`Делители числа ${n}:  ${divisor}`);
console.log(`Кол-во делителей числа:  ${divisor.length}`);
-------------------
function getDivisors (number) {
   let counter = 0;
      for (let i = number; i > 0; i--) {
         if (number % i === 0) {
            counter++;
         }
      };
      return counter;
}; // Найти кол-во делителей
---------------------------------------------------------
// Сохранить результат каждой итерации цикла for

Создать массив, и пушить результат при каждой итерации в него:
   var array = [];
   for (i = 1; i <= 3; i++) {
      var x = 0;
      x += (i); 
      array.push(x);
   }
// OR
   var array = [];
   for (i = 1; i <= 3; i++) {
      array.push(i);
   }
// OR
   var x = 0;
   for (i = 1; i <= 3; i++) {
      x += i;
   }
   var array = [],
// OR
   x = 0;
   for (i=0; i<=3; i++){
   x += (i); 
   array.push(x);
   }
   console.log(x);
-------------------
   for (let x = 0; x <= 10; x += 1) {
      console.log('x = ', x);
   };

   for (let value = 10; value >= 0; value -= 1) {
      console.log('value = ', value);
   };
-------------------
   for (let i = 0; i < 3; i += 1) {
      let newStudent = prompt("Введите имя нового студента!"); 
      if (newStudent) {
      newStudent = newStudent.trim();
      alert(`Добро пожаловать, ${newStudent}!`);
      }
   } // Будет повторять вывод тела функции (Вопрос об имени, Приветствие + Имя)  3 итерации, до тех пор пока (i < 3)

   let sequence = [1, 1, 2, 3, 5, 8, 13];
   for (let i = 0; i < sequence.length; i++) {
   console.log(sequence[i]);
   } 
   // 1, 1, 2, 3, 5, 8, 13
   // Цикл выводит следующее значение в консоль по порядку, тк указано sequence[i]. sequence с индексом [i] на начальном этапе подразумевает что i = 0 (тк отсчет указан с 0), а даной цифре отсчета соответствует индекс массива [0], в данном случае индекс массива sequence[0] = 1. А тк i++, цикл движется дальше на +1 ход вперед к следующему индексу массива.

// function calculateFlights (distance, isBusinessClass, milesTarget) {
      // body //
   };
   
   let targets = [Saskatoon = 3000, Asuncion = 7000,Tokio = 15000];
   let flightsVariant1 = calculateFlights(3118, true, targets[i]);
   let flightsVariant2 = calculateFlights(3617, false, targets[i]);

   for (let i = 0; i < targets.length; i++) {
      flightsVariant1();
      flightsVariant2(); 

   // Так не сработает! "ReferenceError: i is not defined". 
   // flightsVariant1/2 - как не знал до этого так и не знает что за значение "i"."i" становится известно лишь после объявления цикла.

   let targets = [Saskatoon = 3000, Asuncion = 7000,Tokio = 15000];
   for (let i = 0; i < targets.length; i++) {
      let flightsVariant1 = calculateFlights(3118, true, targets[i]);
      let flightsVariant2 = calculateFlights(3617, false, targets[i]);

   // Так сработает!
---------------------------------------------------------
/=/=/=/ Замена for (без возможности использовать индекс i)

const userNames = ['petya', 'vasya', 'evgeny'];

// name на каждой итерации свой собственный (локальный), поэтому используется const
for (const name of userNames) {
  console.log(name);
}
   // => "petya"
   // => "vasya"
   // => "evgeny"

---------------------------------------------------------
/=/=/=/ while - сначала смотрит условие, потом делает
---------------------------------------------------------
Код из тела цикла выполняется, пока условие condition истинно.

   let i = 0;
   while (i < 10) {
      console.log('i = ', i);
      i += 1;
   }

---------
    let romanNumerals = [];

    const lookup = {
    M:  1000,
    CM: 900,
    D:  500,
    CD: 400,
    C:  100,
    XC: 90,
    L:  50,
    XL: 40,
    X:  10,
    IX: 9,
    V:  5,
    IV: 4,
    I:  1
    };

    function convertToRoman(num) {
    let roman = "";
    for (let el in lookup) {
        while (num >= lookup[el]) {
        roman += el;
        num -= lookup[el];
        }
    }
    return roman;
    }

    for (let i = 5; i <= 100; i++) {
    romanNumerals.push(convertToRoman(i));
    }
    console.log(romanNumerals);

---------------------------------------------------------
/=/=/=/ do while - сначала делает, потом смотрит условие

   let i = 0;
   do {
      i += 1
      console.log('i = ', i);
   } while (i <= 5) // Выдаст 6, начав с 1 (тк сначала делает, а потом проверяет. Важна последовательность)

   let i2 = 0;
   do {
      console.log('i2 = ', i2);
      i2 += 1
   } while (i2 <= 5) // Выдаст 5, начав с 0 

---------------------------------------------------------
/=/=/=/ break 

   let z = 0;
   while (z < 10) {
   console.log(z);
   if (z === 3) break;
   z++;
   }
Остановится на 3х. Выведет: 0 1 2 3

---------------------------------------------------------
/=/=/=/ continue 

   for (let f = 0; f <= 5; f++) {
      if (f === 2) continue;
      console.log(f);
   }
Пропустит 2. Выведет: 0 1 3 4

---------------------------------------------------------
/=/=/=/ Массивы
---------------------------------------------------------
let target = [
   {nameTown:'Saskatoon', km: 3000}, 
   {nameTown:'Asuncion', km: 7000}, 
   {nameTown:'Tokio', km: 15000}
   ];

   for (let i = 0; i < target.length; i++) {
      const el = target[i];
      console.log(`Town name: ${el.nameTown} km: ${el.km}`);
   }
//Or
   target.forEach(el => console.log(el.nameTown)); // Saskatoon Asuncion Tokio
   target.forEach(el => console.log(el.km)); // 3000 7000 15000
-------------------
// Обычный вызов
   const el = target[0];
   console.log(`Town name: ${el.nameTown} km: ${el.km}`)
-------------------
let fruits = ["Яблоко", "Апельсин", "Слива"];
   alert( fruits[0] ); // Яблоко
   alert( fruits[1] ); // Апельсин
   alert( fruits[2] ); // Слива
-------------------
let numbers = [0, 0, 0, 0, 1];
let sum = 0;

for (let i = 0; i < numbers.length; i += 1) {

   numbers[i] = numbers[i] + 2; 
   // При каждом проходе цикла прибавляет к "i" +1, что пошагово продвигает цикл по элементам [ ] массива "numbers".
   Будет получаться:
   numbers = [2, 0, 0, 0, 1]; - 1й проход цикла
   numbers = [2, 2, 0, 0, 1]; - 2й проход цикла
   numbers = [2, 2, 2, 0, 1]; - 3й проход цикла
   numbers = [2, 2, 2, 2, 1]; - 4й проход цикла
   numbers = [2, 2, 2, 2, 3]; - 5й проход цикла

   sum = sum + numbers[i];
   // Складывает к переменной "sum" актуальное значение массива (в зависимости на какой позиции сейчас находится цикл)
   sum = 0 + 2 = 2
   sum = 2 + 2 = 4
   sum = 4 + 2 = 6
   sum = 6 + 2 = 8
   sum = 8 + 2 = 11
}
console.log(sum); // 11
-------------------
// Math.sqrt(x) - Извлечь корень из числа 

    console.log(Math.sqrt(25)); // 5
---------
    var isSquare = function (n) {
    return n >= 0 && Math.sqrt(n) % 1 === 0;
    }
    console.log(
    isSquare(-1),
    isSquare(0),
    isSquare(1),
    isSquare(25),
    isSquare(26)
    );
---------
// Выявить min / max значение из массива:
! Важно !
! Массивы должны обязательно передаваться со Spreed оператором.

   let arr = [22, 4, 7];
   console.log(Math.min(...arr));
   
-------------------
// Разные типы значений
   let arr = [ 'Яблоко', { name: 'Джон' }, true, function() { alert('привет'); } ];

   получить элемент с индексом 1 (объект) и затем показать его свойство
   alert( arr[1].name ); // Джон

   получить элемент с индексом 3 (функция) и выполнить её
   arr[3](); // привет

// let cities = [
   {Valencia: 3118}, 
   {Lisbon: 3617}, 
   {Saskatoon: 3000}, 
   {Asuncion: 7000}
   ];

(cities[0].Valencia); // 3118
(cities[0]); // { Valencia: 3118 }
---------------------------------------------------------
/=/=/=/ Массивы (edit/delete/add)
---------------------------------------------------------
// Мутация массива 
JavaScript предоставляет несколько способов для добавления, удаления и замены элементов в массиве. Но некоторые из них используют мутацию, то есть видоизменяют изначальный массив, а некоторые — нет, они просто создают новый массив.
-------------------
I. Добавление: С мутацией
-------------------
Мутирующими методами для добавления элементов в массив:
  * array.push()
  * array.unshift()

    const array1 = [1, 2, 3];

    console.log(array1.unshift(4, 5)); 
     // Expected output: 5
    console.log(array1); 
     // Expected output: Array [4, 5, 1, 2, 3]

-------------------
III. Удаление: С мутацией
-------------------
Методы для удаления элементов с мутацией: 
  * array.pop()
  * array.shift()
  * array.splice()
-------------------
II. Добавление: Без мутации
-------------------
Есть два способа, чтобы добавить новые элементы в массив без мутации изначального массива:
  * array.concat().
  * (...)
-------------------
1) array.concat().
    const arr1 = ['a', 'b', 'c', 'd', 'e'];

    const arr2 = arr1.concat('f'); // ['a', 'b', 'c', 'd', 'e', 'f']
    console.log(arr1); // ['a', 'b', 'c', 'd', 'e']

    const arr2 = ['f'].concat(arr1); // ['f', 'a', 'b', 'c', 'd', 'e']
    console.log(arr2);
-------------------
2) (...)
   Второй способ для добавления элементов без мутации — это использование оператора расширения. Оператор расширения записывается в виде трех точек (...) предшествующих массиву.

const arr2 = [...arr1, 'f']; // ['a', 'b', 'c', 'd', 'e', 'f']
const arr3 = ['z', ...arr1]; // ['z', 'a', 'b', 'c', 'd', 'e']
-------------------
IV. Удаление: Без мутации
-------------------
  * array.filter()
  * array.slice()
Метод array.filter() создает новый массив из первоначального массива, но новый содержит только те элементы, которые соответствуют заданному критерию.

   const arr1 = ['a', 'b', 'c', 'd', 'e'];
   const arr2 = arr1.filter(a => a !== 'e'); // ['a', 'b', 'd', 'f']  
// OR
   const arr2 = arr1.filter(a => {  
   return a !== 'e';
   }); // ['a', 'b', 'd', 'f']

В этом примере, критерием для отсеивания является неравенство 'e', поэтому новый массив (arr2) почти такой же, как и оригинальный, но содержащий только те элементы, которые не равны 'e'.

Некоторые особенности стрелочных функций:
Для однострочных стрелочных функций ключевое слово return подразумевается по умолчанию, так что вам не нужно писать его.
Однако для многострочных стрелочных функций нужно явно указывать возвращаемое значение.
Другой способ удалить элементы из массива без мутации — это использование array.slice(). (Не путать с array.splice())

array.slice() принимает два аргумента.
   Первый аргумент указывает откуда должна начинаться копия.
   Второй аргумент задает последний индекс не включительно.

const arr1 = ['a', 'b', 'c', 'd', 'e'];

const arr2 = arr1.slice(1, 5) // ['b', 'c', 'd', 'e']
const arr3 = arr1.slice(2) // ['c', 'd', 'e']

На строке с кодом const arr2 = arr1.slice(1, 5), arr2 создается путем копирования arr1 начиная с индекса 1 и заканчивая предыдущим индексом для 5 (то есть 4).

На следующей строке const arr3 = arr1.slice(2) показан полезный трюк. Если второй параметр метода array.slice() не задан, то метод берет копию с начального индекса до конца массива.
---------------------------------------------------------
/=/=/=/ Добавление элементов
---------------------------------------------------------
   const salariesOfDev = [400, 500, 600, 2000, 3500];
   const newSeniorDevSalary = 5000;

/=/=/ .push() - добавляет в конец 
   salariesOfDev.push(newSeniorDevSalary); 
   console.log('salariesOfDev', salariesOfDev);

/=/=/ .unshift() - добавляет в начало 
   salariesOfDev.unshift(101, 202, 303) 
   console.log('salariesOfDev', salariesOfDev);
-------------------
/=/=/=/ Удаление элементов
-------------------
/=/=/ .shift() - удаляет первый элемент массива и возвращает его значение в переменную (если имеется)
   const firstRemovedElement = salariesOfDev.shift(); 
   console.log('firstRemovedElement', firstRemovedElement);

/=/=/ .pop() - удаляет последний элемент массива и возвращает его значение в переменную (если имеется)
   const lastRemovedElement = salariesOfDev.pop(); 
   console.log('lastRemovedElement', lastRemovedElement);
-------------------
// Изменение элементов
   salariesOfDev[4] = 6000;
-------------------
// Получение элементов
-------------------
   array[3]
// OR
   array.at(3)

   array[array.length - 1] - чтобы получить последний элемент массива
-------------------
/=/=/ arr.slice 
-------------------
   let arr = ["t", "e", "s", "t"];
   alert( arr.slice(1, 3) ); // e,s (копирует с 1 до 3)

Он возвращает новый массив, в который копирует элементы, начиная с индекса start и до end (не включая END).
Оба индекса start и end могут быть отрицательными. В таком случае отсчёт будет осуществляться с конца массива
-------------------
/=/=/=/ Получить последний элемент массива
-------------------
  * array[array.length - 1] // Выполняется дольше всех
  * array.slice(-1) // Возвращает typeof: String
  * array.pop() // Вырезает элемент из массива

--------------------------------------------------------
// array.forEach()

Метод используется для перебора массива.

   arr.forEach(function callback(item, index, array)){
      ... делать что-то с item
      }); 

Он для каждого элемента массива вызывает функцию callback.
Этой функции он передаёт три параметра callback(item, i, array):
    item – очередной элемент массива.
    i – его номер.
    array – массив, который перебирается.

Например, этот код выведет на экран каждый элемент массива:
   ["Bilbo", "Gandalf", "Nazgul"].forEach(alert);
 // Вызов alert для каждого элемента

А этот вдобавок расскажет и о своей позиции в массиве:
   ["Bilbo", "Gandalf", "Nazgul"].forEach((item, index, array) => {
   alert(`${item} имеет позицию ${index} в ${array}`);
   });

//  arr = [
      {name:'Saskatoon', value: 3000}, 
      {name:'Asuncion', value: 7000}, 
      {name:'Tokio', value: 15000}
   ];
   
   arr.forEach(el => console.log(el.name));
   arr.forEach(el => console.log(el.value));
---------------------------------------------------------
/=/=/=/ Работа с методами массивов: map(), filter(), find(), findIndex(), some(), every()
---------------------------------------------------------
/=/=/ map - модифицирует каждый элемент массива и возвращает данные в новый массив
   ! Не забывай писать return! или если функция в одну строчку, то после "=>" подразумевается return.
   ! return в конце тел методов - нужен
   ! Так же помни, что return в конце цикла тормозит итерации цикла на 1-ом круге! (необходимо выносить его за цикл)
   ! В цикле методы перезаписываются. Возвращай их результат с помощью return

// Более быстрая запись поиска элемента и применение метода:
document.querySelectorAll(".task-item").forEach((taskItem) => {
    taskItem.style.color = taskItemTextColor;
  });
-------
	let result = arr.map(function(item, index, array) {
        // возвращается новое значение вместо элемента
	});
-------
Преобразуем каждый элемент в его длину:

	let lengths = ["Bilbo", "Gandalf", "Nazgul"].map(item => item.length);

    console.log(lengths); // 5,7,6
-------
    const  salariesOfDevelopers = [ 400, 500, 600, 2000, 350];
    const updatedSalaries = salariesOfDevelopers.map((salary,index, array) => {
        return salary ** 2
    });
    console.log('updatedSalaries', updatedSalaries);
---------
   let searchName = 'barry';
   let index = inputArr.map(el => el.name).indexOf(searchName);
---------
// map(Number)

    const number = 10;
    const digits = number.toString().split('').map(Number);
    console.log(digits); // [1, 0]

Используем метод map() с функцией обратного вызова Number для преобразования каждого символа в числовое значение [1, 0].
-------------------
/=/=/ filter - фильтрует каждый элемент массива и возвращает ЭЛЕМЕНТЫ в новый массив. (добавляет в массив если условия == true)

   const filteredSalaries = salariesOfDevelopers.filter((salary,index, array) => {
      return salary > 600 // [ 2000 ]
      // return index % 2 == 0 // [ 400, 600, 350 ]
   });
   console.log('filteredSalaries', filteredSalaries);
-------
    return newArr = arr.filter(el => {
      return el > 0
    })
-------------------
/=/=/ find - находит первый найденный элемент, выводит в новый массив

   const searchedSalary = salariesOfDevelopers.find(salary => {
      return salary > 500
   });
   console.log('searchedSalary', searchedSalary);

-------
	let users = [
	{id: 1, name: "Вася"},
	{id: 2, name: "Петя"},
	{id: 3, name: "Маша"}
	];

	let user = users.find(item => item.id == 1);
	alert(user.name); // Вася

-------------------
/=/=/ findIndex - Выводит Индекс нужного элемента в массиве.
Возвращает первый найденный индекс элемента, выводит в новый массив

   const searchedIndex = salariesOfDevelopers.findIndex(salary => {
      return salary > 500
   });
   console.log('searchedIndex', searchedIndex);
   
-------
findIndex() Найти нужный элемент объекта в массиве. 

   let patients = [
   { id: 1, name: "Максим" },
   { id: 2, name: "Николай" },
   { id: 3, name: "Ангелина" },
   { id: 4, name: "Виталий" }
];

   const indexOfPatients = patients.findIndex((el, i) => {
      return el.id ==  3;
   })
   console.log('indexOfPatients', indexOfPatients);
-------------------
/=/=/ some(), every() - Возвращают true/false
-------------------
some == true если хотя бы 1 элемент массива удовлетворяет условию
every == true если все элементы массива удовлетворяет условию

    const isBiggerThan10 = (element) => element > 10;

    console.log([2, 5, 8, 1, 4].some(isBiggerThan10));
    // expected output: false

    console.log([12, 5, 8, 1, 4].some(isBiggerThan10));
    // expected output: true
---------
   const elementExists = salariesOfDevelopers.some(salary => {
      return salary > 1000
   });
   console.log('elementExists', elementExists);

   const allElementExists = salariesOfDevelopers.every(salary => {
      return salary > 1000
   });
   console.log('allElementExists', allElementExists);
-------------------
/=/=/ new Set(arr) - позволяет хранить уникальные значения
-------------------
new Set(arr) - создает новый Объект Set, который позволяет хранить уникальные значения любого типа (примитивы или объекты). Набор можно повторять, а значения можно добавлять, удалять и проверять на принадлежность.

    // Creating a new set
    let mySet = new Set();

    // Adding values to the set
    mySet.add(1);
    mySet.add("Hello");
    mySet.add({name: "John"});

    // Checking the size of the set
    console.log(mySet.size); // 3

    // Checking if a value is in the set
    console.log(mySet.has("Hello")); // true

    // Removing a value from the set
    mySet.delete("Hello");
    console.log(mySet.has("Hello")); // false

    // Looping through the set
    for (let value of mySet) {
    console.log(value);
    }   
        // Output:
        // 1
        // Object {name: "John"}

---------
// Удалить все дубликаты в массиве (Оставить только уникальные значения)
    let arr = [1, 2, 3, 4, 4, 3, 2, 1];
    arr = [...new Set(arr)];

    console.log(arr); // [1, 2, 3, 4]

Объект Set используется для хранения уникальных значений любого типа. Используя оператор распространения (...) для преобразования набора в массив, мы можем быстро получить массив только с уникальными элементами.

-------------------
/=/=/ .flatMap () - Это идентично map() с последующим flat()
---------
flatMap() метод возвращает новый массив, сформированный путем применения заданной функции обратного вызова к каждому элементу массива, а затем выравнивает результат на один уровень. 

    const x = ['2', '3', '6'];
    const y = ['3', '5', '6', '9', '6', '8', '9'];

    const result = x.flatMap(elemX => y.map(elemY => elemX + elemY));

    console.log(result);
    // Output: [ '23', '25', '26', '29', '26', '28', '29', '33', '35', '36', '39', '36', '38', '39', '63', '65', '66', '69', '66', '68', '69' ]
---------
    const x = ["2", "3", "6"];
    const y = ["3", "5", "6", "9", "6", "8", "9"];

    const res = x.map((elemX) => y.map((elemY) => elemX + elemY));

    console.log(res.flat());
    // Output: [ '23', '25', '26', '29', '26', '28', '29', '33', '35', '36', '39', '36', '38', '39', '63', '65', '66', '69', '66', '68', '69' ]

-------------------
/=/=/ .flat() - Выравнять многоуровневый массив 
---------

    const arr1 = [0, 1, 2, [3, 4]];
    console.log(arr1.flat()); // [0, 1, 2, 3, 4]

    const arr2 = [0, 1, 2, [[[3, 4]]]];
    console.log(arr2.flat(2)); // [0, 1, 2, [3, 4]]

-------------------
/=/=/ if (n in obj) {} - Проверка на вхождение ключа в Объект
---------
Оператор `in` используется для проверки наличия свойства в объекте. Он возвращает true, если свойство с указанным именем существует в объекте, и false в противном случае

Использование оператора in:
    const obj = {}
    const a = 'a'

    if (a in obj) {
      console.log('Ключ со значением "a" есть в объекте')
    } else {
      console.log('Ключ со значением "a" отсутствует в объекте')
    }
---------
Использование метода hasOwnProperty():
    const obj = {}
    const a = 'a'

    if (obj.hasOwnProperty(a)) {
      console.log('Ключ со значением "a" есть в объекте')
    } else {
      console.log('Ключ со значением "a" отсутствует в объекте')
    }
---------
Использование метода Object.keys():
    const obj = {}
    const a = 'a'

    if (Object.keys(obj).includes(a)) {
      console.log('Ключ со значением "a" есть в объекте')
    } else {
      console.log('Ключ со значением "a" отсутствует в объекте')
    }

-------------------
/=/=/ includes()/indexOf()/find()/filter() - Проверка на вхождение элемента в массив/строку.
---------
Метод includes(): он возвращает true, если значение найдено в массиве, и false в противном случае.

    const arr = ['a', 'b', 'c']
    if (arr.includes('b')) {
      console.log('Значение "b" найдено в массиве')
    } else {
      console.log('Значение "b" не найдено в массиве')
    }
---------
Метод indexOf(): он возвращает индекс первого элемента, который соответствует заданному значению, или -1, если такой элемент не найден.

    const arr = ['a', 'b', 'c']
    if (arr.indexOf('b') !== -1) {
      console.log('Значение "b" найдено в массиве')
    } else {
      console.log('Значение "b" не найдено в массиве')
    }
---------
Метод find(): он возвращает значение первого элемента в массиве, который удовлетворяет условию переданной функции. Если такой элемент не найден, то метод возвращает undefined. 

    const arr = [1, 2, 3]
    const result = arr.find(element => element > 1)
    if (result) {
      console.log(`Первый элемент больше 1: ${result}`)
    } else {
      console.log('Такой элемент не найден')
    }

-------------------
/=/=/ .reduce() Сложение чисел массива, которые возвращаются в новую переменную

	array.reduce((аккумулятор, элемент, индекс, массив) => {
		// тело функции
	}, начальное значение)

// Начальное значение играет важную роль, поэкспериментируй!

-------------------
/=/=/ Методы .reduce()
---------
// Удалить все рядом стоящие дубликаты:
---------
    var uniqueInOrder = function(iterable) {
    try {
        iterable = iterable.split('');
    } catch { }

    return iterable.reduce((sum, n) => {
            if (sum[sum.length - 1] !== n) {
            sum.push(n);
        }
            return sum;
        }, []);
    };
    // sum[sum.length-1] - last элемент массива sum
    // , [] - sum = []
---------
// OR
---------
    function uniqueInOrder(iterable) {
        var result = []
        var last

        for (var i = 0; i < iterable.length; i++) {
            if (iterable[i] !== last) {
                result.push(last = iterable[i])
            }
        ---------
        // OR
        ---------
            if (iterable[i] !== result[result.length-1]) {
               result.push(iterable[i])
            }
        }
        return result
    }
    console.log(uniqueInOrder('AAAABBBCCDAABBB')) 
    // ['A', 'B', 'C', 'D', 'A', 'B']

---------
// Удалить все дубликаты:
    function duplicateCount(text) {
        text = text.toLowerCase().split('');
        let arr = [];

        for (let i = 0; i < text.length; i++) {
            if (!arr.includes(text[i])) {
                arr.push(text[i]);
            }
        }
        return arr
    }
    console.log(duplicateCount("abbcdea"))
    
---------
// Может складывать и перебирать не только числа

    function solution(roman){
    var conversion = {M: 1000, CM: 900, D: 500, CD: 400, C: 100, XC: 90, L: 50, XL: 40, X: 10, IX: 9, V: 5, IV: 4, I: 1};
    
    return [ 'X', 'X', 'I' ].reduce((sum, roman) => sum + conversion[roman], 0);
    }
    console.log(solution('XXI')) //  21

---------

Метод reduce() принимает в себя два параметра:

   1. Функцию-callback, которая, в свою очередь, принимает в себя четыре параметра:
      * Аккумулятор. Он равен “начальному значению” при первом вызове функции, либо первому элементу массива, если “начальное значение” не задано. При последующих вызовах он равен результату предыдущего вызова функции.
      * Элемент - текущий элемент массива.
      * Индекс - индекс текущего элемента массива. Необязательный параметр.
      * Массив - текущий массив. Также является необязательным параметром.
   2. Начальное значение - значение, которое будет задано аккумулятору перед первым вызовом функции. Является необязательным параметром. Если он не задан, тогда аккумулятору присвоится значение первого элемента массива.
   3. Тело функции. В нем мы прописываем всю необходимую логику.
-------------------
/=/=/ .reduce() при работе с аргументами функции, с использованием ...rest

   function sum(...other) {
   console.log(other.reduce((acc, value) => acc + value)); 
}
   sum(1, 2, 3);  // 6
   sum(2, 2); // 4
   sum(10, 15, 249, 653, 846); // 1773
-------
   const euros = [29.76, 41.85, 46.5, 55.8, 43.6];

   const sum = euros.reduce((total, amount) =>  total + amount); 
   console.log('sum', sum); // 217.51 (Debugger to help)

* В этом примере reduce() принимает два параметра, total и число с которым сейчас идёт работа.
* Метод проходится по каждому числу в массиве, как бы это было с циклом for.
* Когда цикл только начинается, total имеет значение первого числа с начала массива (29.76), а числом в обработке становится следующее по этому же массиву число (41.85).
* Конкретно в этом примере, нам надо прибавить настоящее число к total.
* Такое вычисление повторяется для каждого числа в массиве и каждый раз настоящее число меняется на следующее число в массиве справа.
* Когда уже нет чисел в массиве, метод отдаёт значение total.
-------------------
/=/=/ sort() - Сортировка значений массива. Изменяет массив!
-------
Внимание! Поэтому для избежания мутирования исходного массива нужно использовать slice() или [...spread]:

    products.slice().sort((itemA, itemB) => {
        return itemA.price - itemB.price;
    })
    [...products].sort((itemA, itemB) => {
        return itemA.price - itemB.price;
    })

-------
Внимание! При передачи просто sort(), без callback, то будет преобразование элементов в 'string'

   salariesOfDevelopers = [ 400, 500, 600, 2000, 350];

   salariesOfDevelopers.sort((a, b) => {
      return a - b // Сортировка по возрастанию
      return b - a // Сортировка по убыванию
   });
   console.log('salariesOfDevelopers', salariesOfDevelopers);

-------
   let arr = [76, 25, 58, 91, 27]

   console.log('arr.sort', arr.sort());

Метод sort() работает по следующему принципу:

   * sort() должен вернуть значение меньше нуля, равное нулю или больше нуля.
   * Если вернется значение меньше нуля, сортировка поставит a по меньшему индексу, чем b, то есть, a будет идти первым.
   * Если вернется значение больше нуля, сортировка поставит b по меньшему индексу, чем a, то есть, b будет идти первым.
   * Если вернётся значение равное нулю, сортировка оставит a и b неизменными по отношению друг к другу.

   const array = ['b', 'd', 'c', 'a', 'e', 'f', 'g'];
   array.sort((a, b) => {
   if (a < b) {
      return 1;
   }
   if (a > b) {
      return -1;
   }
   return 0;
   });
   console.log(array); // ['g', 'f', 'e', 'd', 'c', 'b', 'a']

-------------------
/=/=/ toSorted() - Сортирует, не мутирует
--------- 
    const values = [1, 10, 21, 2];
    const sortedValues = values.toSorted((a, b) => a - b);

    console.log(sortedValues); // [1, 2, 10, 21]
    console.log(values); // [1, 10, 21, 2]
-------------------
/=/=/ .splice() - умеет добавлять, удалять и заменять элементы.
-------------------
Возвращает вырезанные элементы. Мутирует текущий массив. Может принимать новые значения для замены вырезанных.

Cинтаксис:
	arr.splice(startIndex[, deleteCount, elem1, ..., elemN])

Он начинает с позиции startIndex, удаляет deleteCount элементов и вставляет elem1, ..., elemN на их место. Возвращает массив из удалённых элементов.

	const cars = ['BMW', 'Mercedes', 'Lada'];
	const removedElements = cars.splice(0, 2, 'Audi', 'Bugatti')

	console.log('cars', cars); // 'Audi', 'Bugatti', 'Lada' 
	console.log('removedElements', removedElements); // 'BMW', 'Mercedes'
-------
Удалим 3 элемента и заменим их двумя другими:
	let arr = ["Я", "изучаю", "JavaScript", "прямо", "сейчас"];

	// удалить 3 первых элемента и заменить их другими
	arr.splice(0, 3, "Давай", "танцевать");

	alert( arr ) // теперь ["Давай", "танцевать", "прямо", "сейчас"]
-------
Метод splice также может вставлять элементы без удаления, для этого достаточно установить deleteCount в 0:
	let arr = ["Я", "изучаю", "JavaScript"];

	// с позиции 2
	// удалить 0 элементов
	// вставить "сложный", "язык"
	arr.splice(2, 0, "сложный", "язык");

	alert( arr ); // "Я", "изучаю", "сложный", "язык", "JavaScript"
-------
Отрицательные индексы разрешены

В этом и в других методах массива допускается использование отрицательного индекса. Он позволяет начать отсчёт элементов с конца, как тут:
	let arr = [1, 2, 5];

	// начиная с индекса -1 (перед последним элементом)
	// удалить 0 элементов,
	// затем вставить числа 3 и 4
	arr.splice(-1, 0, 3, 4);

	alert( arr ); // 1,2,3,4,5
-------------------
// slice - возвращает вырезанные элементы. Не мутирует текущий массив. 
! Для обрезки до конца используй один параметр .slice(i)
Если писать .slice(i, iterable.length - 1) может быть ошибка

const agesOfDevelopers = [25, 18, 45, 30];

const slicedAgesOfDevelopers = agesOfDevelopers.slice(0, 2);
console.log('slicedAgesOfDevelopers', slicedAgesOfDevelopers);
console.log('agesOfDevelopers', agesOfDevelopers);

-------------------
/=/=/ indexOf lastIndexOf - Для Строк и Массивов
---------
// indexOf - возвращает индекс искомого элемента в переменную
// lastIndexOf - возвращает индекс элемента с конца
   (или используй для объектов "findIndex")
   
---------
// Проверка на вхождение
---------
    'Синий кит'.indexOf('Синий') !== -1; // true
    'Синий кит'.indexOf('Голубой') !== -1; // false
---------
Синтаксис:
	arr.indexOf(searchElement, fromIndex = 0)

   const favoriteFood = ['Мясо', 'Торт', 'Кефирчик'];

   const indexOfFood = favoriteFood.indexOf('Мясо')
   console.log('Element:', favoriteFood[indexOfFood], 'Index:', indexOfFood);
---------
   const myText = 'Здесь должна была быть шутка, но я ее не придумал';

   console.log('indexOf', myText.indexOf('о')); // 7
   console.log('indexOf', myText.indexOf('шутка')); // 23
   console.log('indexOf', myText.indexOf('мыш кыш')); // -1

   console.log('includes', myText.includes('не придумал')); // true

-------------------
/=/=/ .matchAll() - поиска всех совпадений в строке

    const str = [false, 1, 0, 1, 2, 0, 1, 3, "a"].toString();
    const regex = /0/g;

    const matches = [...str.matchAll(regex)];
    
    console.log(matches); // [
        [ '0', index: 8, input: 'false,1,0,1,2,0,1,3,a', groups: undefined ],
        [ '0', index: 14, input: 'false,1,0,1,2,0,1,3,a', groups: undefined ]
    ]

    console.log(matches[0].index); // 8
    console.log(matches[1].index); // 14

-------------------
/=/=/ .match() - используется для поиска в строке совпадения с предоставленным выражением и возвращает совпадения в виде массива. Или возвращает null, если совпадений не найдено.
-------------------
Для поиска совпадения можно использовать indexOf() или .includes()

    ^: Соответствует началу строки.
    $: Соответствует концу строки.

Рекомендуется использовать символы ^ и $ при поиске точного соответствия шаблона и не использовать их, когда вы ищете конкретный шаблон в большей строке.

    let pattern = /(I|II|III|IV|V|VI|VII|VIII|IX|X)/;
    let string = "This is Roman numeral X";
    console.log(!!string.match(pattern)); // true

    Без Boolean: 
    // [
            'X',
            'X',
            index: 22,
            input: 'This is Roman numeral X',
            groups: undefined
        ]
---------
Однако, если вы хотите убедиться, что вся строка совпадает, то рекомендуется включить символы ^ и $.
    let pattern = /^(I|II|III|IV|V|VI|VII|VIII|IX|X)$/;
    let romanNum = 'X';

---------
    /^(X|(IX|IV|V?I{0,3}))$/ - проверяет наличие пустой строки, которая начинается и заканчивается либо X, либо (IX|IV|V?I{0, 3}). Поэтому на '' видит совпадение. 
---------
Исправить можно с помощью Boolean(str.trim():
    const str = ''
    if (Boolean(str.trim()) && /^(X|(IX|IV|V?I{0,3}))$/.test(str)) {
        console.log('str:', str); // не пропустит пустую строку
    }

/CM|CD|XC|XL|IX|IV|\w/g 
    - \w - ищет совпадения в любом символе слова
    - Флаг "g" в конце указывает глобальный поиск, что означает, что будут возвращены все совпадения во входной строке, а не только первый
---------
// Как понять регулярное выражение (пример с римскими цифрами)
--------- 
    const rome = /^M{0,4}(CM|CD|D?C{0,3})(XC|XL|L?X{0,3})(IX|IV|V?I{0,3})$/;

    (M{0,4}) - означает что в строке могут находится от 0 до 4 М
    (IX|IV|V?I{0,3}) - в строке могут находится IX,IV, от 0 до 3 I, а так же 0 или 1 V перед 0-3 I

-------------------
/=/=/ Важно! В Regular Expression не ставятся "" для строк
---------
    let arr = ["NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST"];
    const [n, s, e, w] = ["NORTH", "SOUTH", "EAST", "WEST"];

    let str = arr.join(",");
    const pattern = /NORTH\s*,\s*SOUTH|SOUTH\s*,\s*NORTH/g;
    str.replace(pattern, "");

-------------------
// Если нужно передать переменные:
---------
    let arr = ["NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST"];
    const [n, s, e, w] = ["NORTH", "SOUTH", "EAST", "WEST"];

    let str = arr.join(",");
    const pattern = new RegExp(`${n}\\s*,\\s*${s}|${s}\\s*,\\s*${n}`, 'g');
    str = str.replace(pattern, "");
---------

    function handleSearch(search) {
        const regex = new RegExp(search, "gi"); // /рататуй/gi

        return users.filter((user) => user.name.match(regex));
    }

    handleSearch('рататуй')  //   [
      {
        _id: '63eeb7471824',
        name: 'Рататуй',
        profession: { _id: '63eeb7471829', name: 'Повар' },
        qualities: Array(2) [
          { _id: '63eeb7471102', name: 'Красавчик', color: 'info' }, { _id: '67eeb7f711012', name: 'Юморист', color: 'success' },
          
        ],
        completedMeetings: 17,
        rate: 4.5,
        bookmark: false
      }
    ]
-------------------
/=/=/ .match(/../g) - Разбить строку на равные куски по два символа 
---------
    "abcdefg".match(/../g) // [ 'ab', 'cd', 'ef' ]

    .match(/.{3}/g)) // [ 'abc', 'def' ]

    "abcdefg".match(/..../g) // [ 'abcd' ]
---------
    function solution(str) {
!!      return (str.length % 2 ? str + '_' : str).match(/../g)
    }

    solution("abcdef"); // ["ab", "cd", "ef"];
-------------------
Регулярное выражения для фильтрации чисел от 1 до 10:
/^([1-9]|10)$/; - () скобочки важны! Иначе будет пропускать 11 как 1 и тд
-------------------
/^-?\d+\.?\d*$/
    ^: Соответствует началу строки.
    -?: Соответствует необязательному - символу, указывающему отрицательное число.
    \d+: соответствует одной или нескольким цифрам.
    \.?: Соответствует необязательному символу . с указанием десятичной запятой.
    \d*: совпадает с нулем или более цифрами после необязательной десятичной запятой.
    $: Соответствует концу строки.
    
    g: Глобальный поиск, будут найдены все совпадения во входной строке, а не только первый
    /^[IVXLCDM]+$/ - [IVXLCDM] обозначают допустимые символы римских цифр
    +: одно или более вхождений предшествующего символа 


---------
    let numberRegex = /^-?\d+\.?\d*$/;
    let rangeRegex = /^([1-9]|10)$/;

    console.log(numberRegex.test("-1234") & rangeRegex.test("-1234")); // false
    console.log(numberRegex.test("12.34") & rangeRegex.test("12.34")); // false

Следующие строки будут соответствовать шаблону:
    -1234
    -12.34
    1234
    12.34
    .34
Следующие строки не будут соответствовать шаблону:
    -
    12.3.4
    12a34
    12 34
---------
    /^[\/\*\-\+]$/ - Фильтр по операторам / * - +

    Их нужно писать через \ обратный слеш
-------------------
/=/=/=/ new RegExp - создание регулярного выражения
-------------------
	const elements = ["#", "!"];
	const regex = new RegExp(`[${elements.join('')}]`);

	console.log(regex); // /[#!]/
-------------------

Функция сравнения массивов:
    function getCount(str) {
        return (str.match(/[aeiou]/ig)||[]).length;
    }
    getCount("abracadabra")
    
Функция getCount использует метод match для поиска всех вхождений символов «a», «e», «i», «o» или «u» в строке независимо от регистра. Метод match возвращает массив совпадающих символов или null, если совпадений не найдено. Флаг /i делает процесс сопоставления нечувствительным к регистру, а флаг g заставляет его сопоставлять все вхождения, а не останавливаться на первом совпадении. ||[] используется в качестве запасного варианта для возврата пустого массива, если возвращается значение null, чтобы можно было использовать свойство .length. Свойство .length возвращает количество элементов в массиве, то есть количество гласных в строке. Функция возвращает это количество гласных в качестве окончательного вывода.
-------------------
/=/ .includes() - элемент есть/нет (true/false)
Метод проверяет, содержит ли строка/массив заданный элемент
!!! Сам перебирает массив!

Синтаксис:
    перебираемый_массив.includes(искомый_элемент)

    const technologies = ['JS', 'HTML', 'CSS'];

    const isTechnologiesExists = technologies.includes('CSS')
    console.log('isTechnologiesExists', isTechnologiesExists);

-------------------
/=/=/ startsWith()/endsWith()  - проверяет, начинается/кончается ли строка с указанной подстроки
---------
const str = "Hello, world!";

console.log(str.startsWith("Hello")); // true
console.log(str.startsWith("hello")); // false

console.log(str.endsWith("world!")); // true
console.log(str.endsWith("World!")); // false

-------------------
/=/=/ (/^[\/\*\-\+]$/).test() - замена .includes() 
-------------------
Синтаксис:
    регулярное_выражение.test(валидируемый_элемент)

    function calculator(string) {
        const res = string.split(' ').filter((el) => /[-+*/]/.test(el))
        console.log(res);
    }
    calculator('1 + 1')
    
Метод includes() принимает строку в качестве аргумента, но в этом случае вы передаете регулярное выражение.

Чтобы устранить эту проблему, можно использовать метод test() регулярного выражения вместо метода includes()). Метод test() возвращает логическое значение, указывающее, соответствует ли регулярное выражение строке.
---------
Метод test() используется для проверки строки на наличие совпадений с регулярным выражением. Метод возвращает true/false

    let str = "Hello World!";
    let result = /World/.test(str); // true
    
-------------------
/=/=/ eval(string) - преобразовывает и считает строку уравнения в Number 
-------------------
    function calculator(string) {
        const res = eval(string);
        console.log(res);
    }
    calculator('1 + 1') // 2

-------
// OR Boolean()
-------
С помощью ! (НЕ) трансформируем в Boolean(), если нужно найти что-то с отрицанием (например добавить элемент если он отсутствует)
Или просто использовать Boolean() без отрицания 

    let technologies2 = {
        langs: ['JS', 'HTML', 'CSS'],
        libs: ['React', 'Vue']
    };
    let searchWord = 'name'

    if (!technologies2[searchWord]) {
        technologies2 = {
            ...{name: 'Maxim'},
            technologies2,
        }
    }
    console.log('searchWord:', technologies2);
-------
// Аналогия записи без spreed
-------
    if (!this.words[word]) {
        this.words[word] = {
            word, 
            description,
        };
    }
-------
// object.hasOwnProperty(prop)
-------
    o = new Object();
    o.prop = 'существует';

    function changeO() {
    o.newProp = o.prop;
    delete o.prop;
    }
    o.hasOwnProperty('prop');   // вернёт true
    changeO();
    o.hasOwnProperty('prop');   // вернёт false
-------
    add (word, description) {
        if (!this.words.hasOwnProperty(word)) {
            this.words[word] = {
                word, 
                description,
            }
        }
    }
Можно проверять, есть ли такое свойство в объекте, через метод hasOwnProperty или, если необходимо, так же проверять и в прототипе через метод in.
-------
// [key] in arr (Для Объектов)
-------
    let user = {
        name: 'Maxim',
        age: 21,
    }
    console.log('name' in user ); // true

-------------------
// split - разделяет массив(и слова). Принимает в себя разделитель.

   const listOfOrders = 'Майка, шорты, кроссовки, рюкзак';

   const listOfOrdersArray = listOfOrders.split(', ')
   console.log('listOfOrdersArray', listOfOrdersArray);

---------
    function calculator(string) {
        const res = string.split(' ')

        console.log(res); // [ '1', '+', '1' ]
    }
    calculator('1 + 1')
---------
/=/=/ split(/[-_]/) - Разделить слова где есть определенные символы 
---------
// split(/\s+/g) - удаляет все виды пробелов 

    function toCamelCase(str){
        let words = str.split(/[-_]/);
        let camelCased = words[0];
        for (let i = 1; i < words.length; i++) {
            camelCased += ((words[i][0].toUpperCase() + words[i].substring(1)))
        }
        return camelCased;
    }

    console.log(toCamelCase("the-stealth-warrior")); // "theStealthWarrior"
    console.log(toCamelCase("The_Stealth_Warrior")); // "TheStealthWarrior"

---------
    function getCount(str) {
        const vowels = ['a', 'e', 'i', 'o', 'u' ]

        return str.split('')
        // [
        'a', 'b', 'r', 'a',
        'c', 'a', 'd', 'a',
        'b', 'r', 'a'
       ]
    }
    console.log(getCount("abracadabra"));

-------------------
// join - превратить массив обратно в строчку. Принимает в себя разделитель.

   const ordersString = listOfOrdersArray.join('; ')
   console.log('ordersString', ordersString);
-------------------
// reverse - полностью переворачивает массив

let numbers = [1, 10, 5, 15]
numbers.reverse();
console.log('technologies', numbers);
---------------------------------------------------------
/=/=/ Объединение массивов 
---------------------------------------------------------
// concat() 
-------------------
	[1, 2, 3].concat([4, 5, 6]) // [1, 2, 3, 4, 5, 6]
---------
	let currentDevelopers = ['Maxim', 'Oleg'];
	let newDevelopers = ['Anton', 'Gleb']

	let allDevelopers = currentDevelopers.concat(newDevelopers);
	console.log('allDevelopers', allDevelopers);
---------
// Выравнять массив:

	let arr = [["#"], ["!"]];
	let newArr = [].concat(...arr);
	
	console.log(newArr); // Output: ["#", "!"]
-------------------
// Spreed-оператор "..." 
-------------------
    allDevelopers = [
    ...newDevelopers,
    ...currentDevelopers
    ];
    console.log('allDevelopers', allDevelopers);

-------------------
/=/=/ Когда делаем перебор Объекта через 
for in и добавляем его новый Объект: el нужно писать в [].
// [el]: arr[el]

/=/=/ Не забывай упоминать ..obj, при добавлении в его самого 
//  newObj = {
        ...newObj,
        [el]: arr[el]
    }

    for (const el in arr) {
            if (arr[el] !== undefined) {
                newObj = {
                    ...newObj
                    [el]: arr[el]
                }
            }
        }
-------------------
// Array.length - число элементов этого массива
-------------------
   let items = ['shoes', 'shirts', 'socks', 'sweaters'];
   console.log(items.length); // 4
---------------------------------------------------------
/=/=/ Найти индекс элемента в массиве объектов по элементу из другого массива
---------------------------------------------------------
   let orders = [4, 1, 2, 3]
   let patients = [
      { id: 1, name: "Максим" },
      { id: 2, name: "Николай" },
      { id: 3, name: "Ангелина" },
      { id: 4, name: "Виталий" }
   ];
-------------------
// for Метод

let patientsInOrder = [];

function giveTalonsInOrder (patients, orders) {
   for (let i = 0; i < orders.length; i++) {
      let queue = orders[i];
   
      for (let j = 0; j < patients.length; j++) {
         let patientId = patients[j]['id'];
   
         if (queue === patientId) {
            patientsInOrder.push(patients[j])
         }
      }
   }
   return patientsInOrder
}
let queueOfPatientsResult = giveTalonsInOrder(patients, orders);
console.log('giveTalonsInOrder', queueOfPatientsResult);

-------------------
// findIndex() Метод

function giveTalonsInOrder (patients, orders) {
   let rightQueue = [];

   for (let i = 0; i < patients.length; i++) {
      let searchElement = orders[i];
      let patientsIndex = patients.findIndex(el => el.id === searchElement)
      rightQueue.push(patients[patientsIndex]);
      }
      return rightQueue
}
queueResult = giveTalonsInOrder(patients, orders)
console.log('Patients in order:', queueResult);

-------------------
// map() Метод

function giveTalonsInOrder (patients, orders, ) {
   let patientsQueue = [], rightQueue = [];

   for (let i = 0; i < patients.length; i++) {
      let searchElement = orders[i];
      patientsQueue = patients.map(el => el.id).indexOf(searchElement); // INFO*
      rightQueue.push(patients[patientsQueue]);
   };
   return rightQueue
}
let queueResult = giveTalonsInOrder(patients, orders)
console.log('Patients in order:', queueResult);

// INFO* Ищем индексы элементов массива orders в другом массиве.
// Тк мы знаем что по очереди должен идти пациент № 4, затем № 1, № 2, № 3
// И знаем что индексы этих позиций очередности разбросаны в другом массиве на индексах [3, 0, 1, 2]
// Следовательно в такой последовательности и необходимо вызывать массив пациентов, для соблюдения правильной очереди 

---------
// Object.keys(items).map(item) - map() метод для Объектов

const GroupList = ({ profs }) => {
  return (
    <ul className="list-group">
      {Object.keys(profs).map((prof) => (
        <li key={profs[prof]._id} className="list-group-item">
          {profs[prof].name}
        </li>
      ))}
    </ul>
  );
};
---------------------------------------------------------
/=/=/=/ Объекты
---------------------------------------------------------
   const developer = {
      // key: value,
      'My name': 'Maxim',
      job: 'Front-End Dev',
      experience: 24,
      jobAllInfo: {
         type: 'Front-End',
         framework: 'ReactJS'
      }
   }

// Вывести значение объекта
console.log('name:', developer.'My name'); // ошибка 
console.log('jobAllInfo:', developer.jobAllInfo);
-------------------
// Вывести значение объекта (для некоторых случаев)
console.log('name:', developer['My name']);
-------------------
// Вывести значение Объекта из Массива
console.log(arr[i].key);
-------------------
// Передача переменных с ключом из объекта
const key = 'job'
console.log('job:', developer[key]);
-------
   let fruit = prompt('Корзина фруктов:', 'mango');
   let fruitBasket = {
      [fruit]: 6
   };
   console.log('fruitBasket', fruitBasket);
   const car = {
   name: "Toyota Corolla"
   };
-------
   const key = "color";
   car[key] = "red";

   console.log(car); // { name: 'Toyota Corolla', color: 'red' }
-------------------
// Цепочки обращения к объектам
console.log('type', developer.jobAllInfo.type);
console.log('type', developer['jobAllInfo']['type']);
---------------------------------------------------------
/=/=/ Объект - ссылочный тип данных
---------------------------------------------------------
// Примитивы (хранение данных) 
   У каждой переменной — своё отдельное значение

   let x = 10;
   let xCopy = x; // Копируется значение
   xCopy = 20;
   
   console.log(x); // 10 (значение оригинальной x не изменилось)
   console.log(xCopy); // 20
-------------------
// Не примитив - Объект (ссылочный тип)
   В переменных типах object хранится не сам объект, а ссылка на него.

   const object = { x: 10 };
   const objectCopy = object; // Копируется ссылка на объект
   objCopy.x = 20;

   console.log(object.x); // 20
   console.log(objCopy.x); // 20

То есть, по сути, в двух переменных хранится один и тот же объект, точнее ссылка на него.

   const entity = {};
   const entityCopy = entity;

   console.log(entity === entityCopy); // true (Тк entityCopy хранит ссылку на объект entity. А их ссылки будут равны)

   console.log({} === {}); // false (здесь разные ссылки)
   console.log([] === []); // false (здесь разные ссылки)

   console.log('hello' === 'hello'); // true (тк у примитивов нет ссылок)
---------------------------------------------------------
/=/=/ Передача примитива и объекта в функцию
---------------------------------------------------------
   const x = 10;
   const updateX = arg => arg = 20;
   updateX(x);

   console.log(x); // 10 (оригинал переменой не изменен)
-------------------
   const obj = { x: 10 };
   const updateObjX = arg => arg.x = 20;
   updateObjX(obj);

   console.log(obj.x); // 20 (обновилось исходное значение)
---------------------------------------------------------
/=/=/ Объекты add/delete/edit
---------------------------------------------------------
   const student = {
      id: 1,
      programmingLanguage: 'JavaScript',
      hasExperienceInReact: false,
   };

// Добавление значения в объект:
-------------------
   student.experience = 6;
   console.log('student', student);
-------
   const student = {
    	fullName: "Максим",
      experienceInMonths: 12,
      stack: ["HTML", "CSS", "JavaScript", "React"]
   };

   {
   	...student,
   	job: jobName
  }
-------------------
// delete - удаление из Объекта
   delete student.hasExperienceInReact;
   console.log('student', student);
   // Оставляет empty slot
-------------------
// Изменение
	student.experience = 12;
   console.log('student', student);

   const car = {
   name: "Toyota Corolla"
   };
-------------------
// Создание свойств
   car.engine = 1.6;
   car["maxSpeed"] = 185;
-------------------
// Обновление свойства
   car.name = "My Car";
   
   console.log(car); 
   { name: 'My Car', engine: 1.6, maxSpeed: 185 }
---------------------------------------------------------
/=/=/ Итерация объектов/ Перебор Объектов
---------------------------------------------------------
const goodInfo = {
    id: 1,
    price: 80,
    currency: '$',
    name: 'shoes',
}
-------------------
/=/=/=/ for in - проходится по ключам и свойствам объекта 
-------------------
// arr[i] in obj - Найти элементы массива в Объекте
    const arr = ['one', 'two', 'three'];
    const obj = {one: 1, two: 2, three: 3};

    console.log(arr[0] in obj) // true

---------
    for (const key in goodInfo) {
        console.log('key:', key);
        console.log('value:', goodInfo[key]);
    };
-------
    showAllWords () {
        for (const el in this.words) {
            console.log(el, '-', this.words[el].description);
        }
    } // В более сложных случаях когда объект имеет свои объекты с элементами

-------------------
/=/=/ Object.keys() - Создает массив из ключей. Выводит значения в отдельный массив
---------
    const keys = Object.keys(goodInfo);
    console.log('keys', keys);

-------------------
/=/=/ Object.values() - Создает массив из значений. Выводит значения в отдельный массив
---------
    const values = Object.values(goodInfo);
    console.log('values', values);
    
-------------------
/=/ Object.entries() - Возвращает многомерный массив, элементами которого являются другие массивы из ключей и значений. Выводит все в отдельный массив
/=/ _.toPairs() - лодаш

   const entries = Object.entries(goodInfo);
   console.log('entries', entries); 
    Выведет:
    // entries [
      [ 'id', 1 ],
      [ 'price', 80 ],
      [ 'currency', '$' ],
      [ 'name', 'shoes' ]
    ];
-------------------
   const car = {
      name: "Toyota Corolla",
      year: 2017,
      isNew: false
   };

   Object
      .entries(car) // Вернет массив [ ["name", "Toyota Corolla"], ... ]
      .forEach(arr => console.log(`${arr[0]}: ${arr[1]}`));

    Выведет:
   // name: Toyota Corolla
   // year: 2017
   // isNew: false

Метод Object.entries() возвращает многомерный массив, то есть массив, элементами которого являются другие массивы. В каждом из этих подмассивов arr в первом элементе arr[0] хранится название свойства, а во втором arr[1] — его значение.
-------------------
Однако есть более элегантный способ работы с массивами в параметрах. Рассмотрим тот же код, но с использованием деструктуризации:

Object
   .entries(car)
   .forEach(([key, value]) => console.log(`${key}: ${value}`));

Здесь мы "разобрали" массив на отдельные значения. Делается это с помощью квадратных скобок с указанием переменных, куда нужно поместить значения из массива. Таким образом, список аргументов стрелочной функции ([key, value]) означает, что первое значение из записи будет помещено в переменную key, а второе значение в переменную value.

---------------------------------------------------------
/=/=/=/ Деструктуризация - позволяет извлекать данные из массивов или объектов.
---------------------------------------------------------
function calcValues (a, b) {
   return [
      a + b,
      undefined,
      a * b,
      a / b,
   ];
};
   const result = calcValues(42, 10);

   const sum = result[0];
   const sub = result[1];
   console.log('result:', result);
   console.log('sum, sub:', sum, sub);
-------------------
// С помощью деструктуризации
   const result = calcValues(42, 10);

   const [sum, sub] = result;
   console.log('result:', result);
   console.log('sum, sub:', sum, sub);

// OR Запись короче: 
   [sum, sub] = calcValues(42, 10)
-------------------
// Игнорирование значений
-------------------
   const [sum, , mult, ...other] = calcValues(42, 10);
   console.log(sum, mult, other);
-------------------
// Значения по умолчанию
-------------------
   const [sum, sub = 'Вычитания нет', mult, ...other] = calcValues(42, 10);
   console.log(sum, mult, other, sub);
-------------------
   var a, b, rest;
   [a, b] = [1, 2];
   console.log(a); // 1
   console.log(b); // 2

   [a, b, ...rest] = [1, 2, 3, 4, 5];
   console.log(a); // 1
   console.log(b); // 2
   console.log(rest); // [3, 4, 5]

   ({a, b} = {a:1, b:2});
   console.log(a); // 1
   console.log(b); // 2

   ({a, b, ...rest} = {a:1, b:2, c:3, d:4});
   console.log(a); // 1
   console.log(b); // 2
   console.log(rest); // { c:3, d:4 }
-------
   var foo = ["1", "2", "3"];

   // без деструктурирования
   var one   = foo[0];
   var two   = foo[1];
   var three = foo[2];

   // с деструктурированием
   var [one, two, three] = foo;

-------------------
// Обмен значений переменных
-------------------
   var a = 1;
   var b = 3;

   [a, b] = [b, a];
-------------------
// Игнорирование некоторых значений
-------------------
	function f() {
		return [1, 2, 3];
	}

	var [a, , b] = f();
	console.log("A is " + a + " B is " + b);
   
После выполнения кода, a будет 1, b будет 3. Значение 2 игнорируется. Таким же образом вы можете игнорировать любые (или все) значения.
-------------------
// Деструктуризация с Объектами
-------------------
   const person = {
      name: 'Max',
      age: 20,
      address: {
         country: 'Russia',
         city: 'Moscow',
      },
   };

   const name = person.name;
   const age = person.age;
// OR
   const {
      name: firstName = 'Без имени', 
      age, 
      car = 'Машины нет',
      address: {country, city: homeTown}
   } = person;
   console.log(firstName, age, car, country, homeTown);
// key: variable - Смена значения переменной (если например занята)
   const {name, ...info} = person
   console.log(name, info);
-------------------
// Применение на практике 
-------------------
   function logPerson0 (per) {
      console.log(per.name, per.age);
   }
   logPerson0(person)
-------
   function logPerson1 ({name: firstName1, age}) {
      console.log(firstName1, age);
   }
   logPerson1(person)
---------------------------------------------------------
/=/=/=/ Symbol() - Создает уникальные ключи объекта. Позволяет использовать повторяющиеся ключи в объекте.
---------------------------------------------------------
// Пример ошибки однотипных ключей 
-------------------
let user = {
   name: 'Maxim',
   name: 'Igor',
   name: 'Michael',
}; // Сохраниться только последнее значение

console.log('user:', user); // { name: 'Michael' };

-------------------
// Решение с помощью Symbol() 
-------------------
const id = Symbol('name')

user = { 
   [id]: 'symbol value',
   name: 'Maxim',
   [Symbol('name')]: 'Igor',
   [Symbol('name')]: 'Michael',
};
console.log('user:', user);
console.log('user[id]:', user[id]);

-------------------
// in - Проверяет существует ли искомый ключ внутри объекта
-------------------
const searchInObject = 'name' in user
console.log('searchInObject', searchInObject); // true

console.log(id in user); // true
-------------------
В качестве имени ключа можно использовать переменные.
В объекте они означаются в "[]" 
   const key = "color";

   const car = {
   name: "Nissan Note",
   [key]: "silver"
   };

-------------------
// Создание скрытых свойств объекта с помощью Symbol()
-------------------
Использование символьных ключей гарантирует, что получить доступ к свойству мы можем, только имея ссылку на данный символ. Это может быть полезно, когда объекту нужно добавить свойство, которое другие части программы могут случайно изменить. При использовании symbol в ключе случайно зацепить свойство не получится. Также такие свойства не видны при переборе обычными способами (такими как цикл for...in или метод Object.entries()).

Для получения всех символьных ключей объекта можно использовать специальный метод Object.getOwnPropertySymbols().

   const car = {
   [Symbol("name")]: "Toyota Corolla",
   [Symbol("name")]: "Nissan Note"
   };

   const symbols = Object.getOwnPropertySymbols(car);
   for (const symbol of symbols) {
   console.log(`${symbol.description} - ${car[symbol]}`);
   }
   // Цикл выведет:
   // name - Toyota Corolla
   // name - Nissan Note

---------------------------------------------------------
/=/=/=/ Объединение нескольких Объектов в один
---------------------------------------------------------
   const developerInfo = {
      age: 25,
      experience: 3,
      name: 'Maxim'
   };

   const developerExtraInfo = {
      name: 'Igor',
      height: 180,
      isJunior: false,
   };

При слиянии, методы пропустят совпадающие ключи name и выведут только последний.
-------------------
// С помощью spreed оператора "..." (рекомендуется)
-------------------
   const developer = {
      ...developerInfo,
      ...developerExtraInfo,
      name: 'Nastya',
   };

   console.log('developer', developer); 
-------
Чтобы объединить объекты в массиве:
-------
При объединении объект-ы должны быть в "{}"

   const developer = [
      {...developerInfo},
      {...developerExtraInfo},
      {name: 'Nastya',}
   ];
-------------------
/=/=/ Object.assign() - копирование и объединение Объектов
---------
   Object.assign(Объект-хранилище, перемещаемые объекты)

---------
    const obj1 = { a: 1, b: 2 };
    const obj2 = { b: 3, c: 4 };
    const obj3 = { c: 5, d: 6 };

    const result = Object.assign({}, obj1, obj2, obj3);
    console.log(result);
    /=/ Output: { a: 1, b: 3, c: 5, d: 6 }

Здесь мы передаем пустой объект {} в качестве первого аргумента, а затем передаем три объекта obj1, obj2 и obj3 в качестве аргументов для объединения. Результатом является новый объект, содержащий свойства всех трех объектов. Обратите внимание, что свойство b берется из obj2, так как оно переопределяет значение b из obj1.
---------
   Object.assign(developerInfo, developerExtraInfo);

   console.log('developerInfo', developerInfo); 
    // developerInfo { a: 1, b: 2, c: 3 }
    
---------
   const developer2 = Object.assign({}, developerExtraInfo);

   console.log('developer2', developer2); 
    // developer2 { a: 1, b: 2, c: 3 }
-------------------
/=/=/ Копирование данных Объекта через for in
-------------------
!Главная суть: Каждый Объект должен копироваться отдельно. Каждый вложенный копируется отдельно. Если данные не копируются, значит ты где-то пропустил объект или не так скопировал или не весь! 

    let user = {
    name: "John",
    age: 30
    };

    let clone = {}; // новый пустой объект

    // давайте скопируем все свойства user в него
    for (let key in user) {
    clone[key] = user[key];
    }

    // теперь clone это полностью независимый объект с тем же содержимым
    clone.name = "Pete"; // изменим в нём данные

    alert( user.name ); // все ещё John в первоначальном объекте
-------
let pageDesign = [
    tasksItem = {
        create: {a: 'tasksItem', b: 'div'},
        paste: {a: '.tasks-list', b: 'appendChild'},
        valueAtr: {
            class:"task-item",
            dataName: 'taskId', dataValue: '1',
        }, ...
    ]
// Копирование каждого Объекта:
    archiveCopies.push([   
            {
                create: {
                    ...el.create
                },
                paste: {
                    ...el.paste
                },
                valueAtr: {
                    ...el.valueAtr
                }
            }
        ])
-------------------
/=/=/ Копирование Объекта с вложенными Объектами
-------------------
!Главная суть: Каждый Объект должен копироваться отдельно. Каждый вложенный копируется отдельно. Если данные не копируются, значит ты где-то пропустил объект или не так скопировал или не весь! 

Все вышестоящие способы не работают в исходном виде, они не копируют данные вложенных объектов, а копируют только ссылки!
Для копирования данных необходимо прописывать структуру вручную:

    let user2 = {
        man: {
            name: "John",
            age: 30,
            job: {
                status: 'middle',
            }
        }
    };

    let clone2 = {
        man: {
            ...user2.man,
            job : {
                ...user2.man.job,
            }
        }  
    }

        clone2.man.name = "Pete";
        clone2.man.age = 24;
        clone2.man.job.status = "sin";

        console.log('user2', user2 ); 
        console.log('clone2', clone2);
-------------------
let user2 = [
        man = {
            name: "John",
            age: 30,
            job: {
                status: 'middle',
            }
        }
    ];

    function indexEl(arr, el) {
        return arr.indexOf(el)
    }
    
    let clone2 = [
        man = {
            ...user2[indexEl(user2, man)],
            job : {
                ...user2[indexEl(user2, man)].job,
            }
        }    
    ]

        clone2[0].name = "Pete";
        clone2[0].age = 24;
        clone2[0].job.status = "sin"; 

        console.log('user2', user2 ); 
        console.log('clone2', clone2);

-------------------
/=/=/ Работа с Объектами. Вызов референса функции через Ключ Объекта
-------------------
! Используя ключ объекта, можно не только вывести значение ключа. 
  НО И вызвать функцию с помощью передачи ВЫЗОВА КЛЮЧУ!

    const usersData = [
        { id: 1, name: 'John' },
        { id: 2, name: 'Jane' },
        { id: 3, name: 'Bob' }
    ];

    function fetchAll() {
        return usersData;
    }

    const API = {
        users: {
            fetch: fetchAll
        }
    };

    console.log(API.users.fetch()); 
    // [
        { id: 1, name: 'John' },
        { id: 2, name: 'Jane' },
        { id: 3, name: 'Bob' }
    ]

---------------------------------------------------------
/=/=/=/ ?. Оператор опциональной последовательности 
---------------------------------------------------------
// ("?." вместо "&&" в if)

    const developer = {
    name: 'Maxim',
    job: 'Front-End Dev',
    experience: 24,
    jobAllInfo: {
        type: 'Front-End',
        framework: {
            nameFw: 'ReactJS'
        },
    }
    }
-------------------
// if (developer.jobAllInfo.framework.nameFw)
-------------------
   if (developer && developer.jobAllInfo && developer.jobAllInfo.framework && developer.jobAllInfo.framework.nameFw) {
      console.log('The developer already knows the framework');
   } else {
      console.log("The developer doesn't knows the framework");
   }
-------------------
// ?. Оператор опциональной последовательности 
-------------------
   if (developer?.jobAllInfo?.framework?.nameFw) {
      console.log('The developer already knows the framework');
   } else {
      console.log("The developer doesn't knows the framework");
   }
---------------------------------------------------------
/=/=/=/ Функции 
---------------------------------------------------------
     С помощью них предотвращают дублирование кода. 
     Функция вызывается добавлением () после нее

// Анонимная функция вызывается:
   (function (){
   console.log("work");
   })();
// OR
   (function (str){
   console.log(str);
   }("work"));
-------------------
В функцию мы можем передавать параметры (любые типы данных). Одним из параметров может быть другая функция (например callback, alert, console.log) 

// Function Declaration - объявление функции
   (Можем вызывать функцию до ее определения)
   
   function name(param) {}

   function sum0 (a = 1, b = 3) {
      console.log(a + b);
   }
   sum0(); // 4
// OR
   function sum1 (a, b) {
      console.log(a + b);
   }
   sum1(1, 3); // 4
// OR
   function sum2 (a, b = 3) {
      console.log(a + b);
   }
   sum2(1); // 4
---------------------------------------------------------
/=/=/=/ Callback — это функция, в основной функции, которая должна быть выполнена после того, как другая (вторая) функция завершила выполнение (отсюда и название: callback — функция обратного вызова).

При передачи коллбэка в функцию, скобки у передаваемой функции ставить не нужно.

Также функцию callback можно передать в виде анонимной функции – прописать прямо в круглых скобках вызываемой функции:

    // Принимаем коллбэк ourCallback()
    function firstFunc(ourCallback) {
    setTimeout(() => {
        console.log('Hello');
        ourCallback(); // Вызываем коллбэк в нужный момент
    }, 500);
    };

    firstFunc(() => {
    console.log('World');
    });

    // Вывод:
    // Hello
    // World

---------
   function f2(callback) {
   let i = 0;
   i+=1;
   callback(i);
   }

   function handler(val) {
   console.log(val+1);
   }

   f2(handler);
---------
   function sum03(a, b, callback) {
   const result = a + b;
   callback(result);
   }

   function displacer(res) {
      console.log('Результат:', res);
   }

   sum03(3, 10, displacer);

/* Что тут происходит?
Создаем функцию sum03 с параметрами 'a', 'b', 'callback' 
(параметрами могут быть любые данные, даже функции, как и callback в данном случае.)
'callback' - это лишь произвольное название функции (хотя тут больше похоже на переменную со значением, чем на функцию. Но так как callback принимает значение от функции - это функция), в которую мы далее будем передавать полноценную функцию со значениями displacer. 

Создаем переменную result которая выполняет сложение двух неизвестных переменных 'a' и 'b' (пока их значение undefined)

Назначаем что функция callback будет иметь и выводить параметр result который хранит результат сложения.

Далее создаем функцию с наименованием displacer.
(которая в дальнейшем будет назначена передавать свое значение в callback. По сути можно сказать что callback = displacer)

Функция displacer имеет параметр res.
Далее тело функции displacer будет выводить в консоли строку 'Результат:' и переменную res (которую перенимает значения из result)

Далее самое важное. Мы передаем (назначаем) наши параметры функции sum 
Теперь (a, b, callback) = (3, 10, displacer)
a = 3
b = 10
callback = функция displacer

Грубо говоря, общая картина такова, что сумма значений 
(a + b) = result
result = callback 
callback = displacer
А так как displacer передает значения в callback, а callback хранит в себе значение переменной result, то есть сумму (a + b), то для функции displacer нам необходимо сохранить это значение в переменную res.

3 + 10 = 13. Помещается в функцию (параметр) callback и храниться в переменной result в качестве параметра.
А наш параметр callback является функцией displacer которая так же хранит в себе аналогичную переменную res в качестве параметра.

Получается displacer это отражение callback, которая хранит в себе все ее значения с небольшими дополнениями. Которая могла бы вызываться по необходимости (в конце), то есть отдельно от выполнения главного тела функции sum, где участвует callback.
*/

// Или это же, но через анонимную функцию (без названия)

   function sum04(a, b, anon_function) {
      const result = a + b;
      anon_function(result);
   }

   sum04(5, 10, function(res01) {
      console.log('Результат:', res01);
   });

// callback с уже существующими функциями 

   function sum05(a, b, alert) {
      const result = a + b;
      alert('Результат: ' + result);
   }

   sum05(5, 11, alert)
   
---------------------------------------------------------
/=/=/=/ Return - позволяет вернуть результат(значение) из функции 
*return - останавливает выполнение функции

// let increaseByTwo = function (number) {
      let sum = 2 + number;
      return sum;
   };

   increaseByTwo(1); // Функция вернёт 3
   increaseByTwo(2); // Функция вернёт 4

Чтобы функция вернула значение, мы используем оператор return. После оператора указываем, что именно надо вернуть. В нашем случае значение переменной sum. Когда программа доходит до строки с return, функция отдаёт результат своей работы и выполнение кода из тела функции останавливается, иными словами происходит выход из функции.

Несколько вещей, которые нужно знать:

   -Код, написанный на новой строке после return, не выполняется.
   -Функция не может вернуть сразу много значений, она возвращает только один результат.
   -Если внутри функции нет return или после return не указано, какое значение нужно вернуть, функция вернёт undefined, иными словами, ничего.

---------------------------------------------------------
Обрати внимание на разницу между параметрами и аргументами. На практике зачастую эти слова взаимозаменяемы, но стоит понимать отличия:

    * Аргумент — это значение параметра, которое передается при вызове функции. 
    (100, 5)
    
    * Параметр — это название переменной, которое указывается в объявлении функции. Они используются для многоразовости функции, для подставления в нее разных аргументов на место ярлыков(параметров). 
    (price, count)
    
    function showTotalPrice(price, count) {
        console.log(price * count);
    };

   Данная функция имеет два параметра — цена (price) и количество (count). По сути это переменные, которым присваиваются значения при вызове функции.

   showTotalPrice(100, 5); // Выведет в консоль: 500
   // Аргументы (100, 5)

---------------------------------------------------------
// document.querySelector('.селектор') - найти элемент
   console.log(document.querySelector('.селектор')) - удостовериться, что найден нужный элемент

// document.classList.remove() - удалить класс
   document.querySelector('.page').classList.remove('light-theme') - удалить класс в найденном селекторе

// document.classList.add() - добавить класс
   document.querySelector('.page').classList.add('dark-theme');  - добавить класс в найденном селекторе 

Но это некорректная запись. Для нормализации читабельности, скорости и удобства кода назначим переменной значение поиска, чтобы не искать ее каждый раз.

   let page = document.querySelector('.page');
   page.classList.remove('light-theme');
   page.classList.add('dark-theme');
-------------------
/=/=/ .onclick
-------------------
   let themeButton = document.querySelector('.theme-button');

   themeButton.onclick = function() {
   console.log('Кнопка нажата!');
   page.classList.remove('light-theme');
   page.classList.add('dark-theme');
   };

'onclick' свойство (по клику) - это событие для браузера 

Данная конструкция создает переменную которая будет хранить в себе найденный класс с кнопкой для смены темы сайта.
При нажатии на кнопку будет запущенна функция удаления светлой темы и добавления темной.

// .classList.toggle - чередование переключения классов.
Удаляет(remove) если есть, добавляет(add) если нет.

   селектор.classList.toggle('класс');
   page.classList.toggle('light-theme');

Итого код для переключения темы:
   let themeButton = document.querySelector('.theme-button');

   themeButton.onclick = function() {
   console.log('Кнопка нажата!');
   page.classList.toggle('light-theme');
   page.classList.toggle('dark-theme');
   };

---------------------------------------------------------
// .textContent - выводит текст класса или селектора, без HTML тегов

   let message = document.querySelector('.subscription-message');
   console.log(message.textContent);

С помощью .textContent можно переназначить текст
message.textContent = 'Измененный текст'
---------------------------------------------------------
'onsubmit' свойство - триггер на событие отправки формы (не кнопки!)

   let message = document.querySelector('.subscription-message');
   let form = document.querySelector('.subscription');

   form.onsubmit = function(evt) {
   // Инструкция ниже отменяет отправку данных
   evt.preventDefault();
   message.textContent = 'Форма отправлена!';
   };

---------------------------------------------------------
Отличия Function Declaration и Function Expression в том 
что FD мы можем вызывать до определения функции, а FE нет
---------------------------------------------------------
/=/=/=/ Рефакторинг 

Разработчики рефакторят свой код для того, чтобы он был понятен коллегам и самому автору через какое-то время, легко поддерживался, не содержал в себе повторов, огромных сложных конструкций и так далее. Здесь, как в школе: сначала пишем в черновик, пробуем, зачёркиваем, пробуем снова, пока не придём к решению, а потом аккуратно выводим в чистовик.

При этом рефакторингом занимаются все, даже самые крутые рок-звёзды из мира разработки.
---------------------------------------------------------
 Хороший код всегда состоит из множества частей, каждая из которых занимается только своей задачей.
---------------------------------------------------------
/=/=/=/ Arrow Function Expression
// Символ "=>" заменяет термин "function"

   let sum = (a, b) => {
      let calculate = a + b;
      return calculate;
   };
   let result = sum(3.14, 3.14);
   console.log('Result:', result);

// Создаем имя функции "sum", вводим в () параметры, с помощью => обозначаем что это стрелочная функция которая переходит к телу {}. После "=>" без указания "{}", дальнейший текст будет воспринят как для команды "return".

   const sayHello = () => {
      alert("Hello");
   };

   const sayHello = (name) => {
      alert(`Hello, ${name}`);
   };  

const sayHello = name => alert(`Hello, ${name}`);
const calc = (a, b) => a + b;

sayHello("Vasya"); // Выведет сообщение "Hello, Vasya"
console.log(calc(1, 2)) // Выведет в консоль: 3

   let sum = function (a, b) {
      return a + b
   } 

   let result = sum(3.14, 3.14);
   console.log('Result:', result);
//Or
   let sum = (a, b) => {
      let calculate = a + b;
      return calculate;
   }

   let result = sum(3.14, 3.14);
   console.log('Result:', result);
//Or
   let sum = (a, b) => a + b; 

   let result = sum(3.14, 3.14);
   console.log('Result:', result);
   // Только если функция состоит из 1 строчки

---------------------------------------------------------
/=/=/=/ Использование Arrow Function как callback

   function multiply (a, b, callback) {
      const result = a * b;
      callback(result);
   }

   multiply(5, 2, (multiplyResult) => {
      console.log('multiplyResult:', multiplyResult);
   });

---------------------------------------------------------
/=/=/=/ Замыкание - функция внутри функции

// Замыкания — это функции, ссылающиеся на независимые (свободные) переменные. Другими словами, функция, определённая в замыкании, «запоминает» окружение, в котором она была создана.
// Свободные переменные — это переменные, которые не объявлены локально и не передаются в качестве параметра.

   let numberGenerator = function() {
// Локальная переменная, которая доступна только в замыкании
      var num = 1;
      function checkNumber() {
         console.log(num);
      }
      num++;
      return checkNumber;
      }

   var number = numberGenerator();
   number(); // 2

В примере функция numberGenerator создаёт локальную «свободную» переменную num (число) и checkNumber (функция, которая выводит число в консоль). 
Функция checkNumber не содержит собственной локальной переменной, но благодаря замыканию она имеет доступ к переменным внутри внешней функции, numberGenerator. 
Поэтому объявленная в numberGenerator переменная num будет успешно выведена в консоль, даже после того, как numberGenerator вернёт результат выполнения.

Если посмотреть Debugger, то clg функции checkNumber будет выполняться последним. Почему? Тк идет передача этой функции в главную, с помощью return. А при вызове главной функции number(), следовательно и вызывается clg функции checkNumber.

-------------Разбор примера-------------
const createCounter = (initialValue = 0) => {
   return (valueToAdd) => {
      return initialValue + valueToAdd
   };
};

const addFive = createCounter(5);
const result = addFive(7);
console.log(result);

// Смотрим процесс через Debugger. До момента с назначением аргумента (5) функции createCounter все понятно. Далее это значение с параметром, упаковывается в переменную addFive. 
После, уже нынешняя переменная addFive(тобишь createCounter(5)) двигается далее и встречает return(1*), который возвращает в наш addFive вложенную анонимную функцию(со всеми ее значениями). 
То есть, теперь наш addFive != createCounter(5)
А имеет значение addFive = (valueToAdd) => {
      return initialValue + valueToAdd
   };
Это Debugger обработал первый(1*) return.
После процесс Debugger видит новый аргумент addFive(7)и переключается на него, одновременно упаковывая эти значения в переменную result.
И теперь самый важный момент. 
Параметр addFive стал (7). Но тут важно не ошибиться, addFive != исходному createCounter(5)
addFive имеет значение стрелочной функции с параметром (valueToAdd).
Поэтому при объявлении addFive(7), меняется параметр (valueToAdd). А дальше уже все понятно. Этот параметр используется в return для возврата initialValue + valueToAdd. 
Которые в итоге возвращаются в их анонимную стрелочную функцию которая = переменой addFive, которая уже ныне = переменой result, которая в последствии и выводится в консоль.

   createCounter = (initialValue = 0) => {
      let counter = initialValue;

      return (valueToAdd) => {
         counter += valueToAdd;
         return counter;
      };
   };

   const addTwo = createCounter(2);
   result = addTwo(10); // 12
   result = addTwo(5);
   result = addTwo(3);
   console.log(result);

-------------------
/=/=/ Отличие Замыкания, Колбэка и Рекурсии 
-------------------
Замыкание - это функция, которая может использовать переменные из внешней области видимости. Например1:
    function outer() {
        const x = 5; // локальная переменная
        return function inner() {
            console.log(x); // замыкание имеет доступ к x
        };
    }

    const f = outer(); // f - это функция inner
    f(); // выводит 5
---------
    Колбэк - это функция, которая передается в качестве аргумента другой функции и вызывается ею.

    function add(a, b, callback) {
        const result = a + b; // вычисляем результат
        callback(result); // вызываем колбэк с результатом
    }

    function print(x) {
        console.log(x); // выводим x
    }

    add(2, 3, print); // передаем print в качестве колбэка для add
    // выводит 5
---------
    Рекурсия - это функция, которая вызывает сама себя с новыми аргументами. 

    function factorial(n) {
        if (n === 0) {
                return 1; // базовый случай
        } else {
            return n * factorial(n - 1); // рекурсивный вызов с меньшим аргументом
        }
    }

    console.log(factorial(5)); // выводит 120
---------------------------------------------------------
/=/=/=/ Область видимости переменных
---------------------------------------------------------
/=/=/ Глобальная область видимости
Позволяет переменной быть видимой из любой точки кода. Переменная считается глобальной, когда она объявлена вне функций и блоков:
const x = 10; // Глобальная переменная

   function show() {
   console.log(x); // Выведет 10
   }

/=/=/ Локальная область видимости (3 вида):
// Блочная -
Область видимости ограничена блоком кода (т.е. фигурными скобками { и }):

   if (true) {
   const x = 10;
   }
   console.log(x); // Ошибка ReferenceError: x is not defined
   / Переменная x будет доступна только внутри блока if

   // Исключение — var. Они не имеют блочной области видимости и доступны даже вне блока.

// Область видимости функции -
Ограничена функцией, в которой объявлена переменная (Аналогично блочному)

   function test() {
   const x = 10;
   }
   console.log(x); // Ошибка ReferenceError: x is not defined

// Модульная — область видимости ограничена модулем.

---------------------------------------------------------
/=/=/ Алгоритм поиска переменных
---------------------------------------------------------
   const x = 10;

    function show() {
        const y = 20;

        if (true) {
            const z = 30;
            console.log(x + y + z);
        }
    }
    show(); // Выведет в консоль 60   

В данном примере функция show() выводит в консоль сумму трёх переменных. При обращении к переменной x, движок JavaScript действует по такому алгоритму:

    Пытается найти переменную с именем x внутри блока if. Не найдя её, переходит к родительскому блоку наверх.
    Пытается найти переменную x в функции show(). Не найдя её, переходит к глобальному контексту.
    Находит глобальную переменную x и использует её значение.
    
   / Поиск происходит изнутри наружу. От локальных (точка отправления) к более глобальным

// При этом, если во внутреннем блоке уже найдена переменная с нужным именем, поиск останавливается:
   const x = 10;
   
    if (true) {
        const x = 20;
        console.log(x); // Выведет 20
    }
    console.log(x); // Выведет 10

---------------------------------------------------------
/=/=/ Формула чисел Фибоначчи / Формула расчета подъема по лестнице
---------------------------------------------------------
Фибоначчи - это последовательность чисел, в которой каждое число является суммой двух предыдущих чисел.

    Формула чисел Фибоначчи: 
        Fn = Fn–2 + Fn–1
        f(n) = f(n-1) + f(n-2)

 

---------------------------------------------------------
/=/=/=/ Выбор имени функции
---------------------------------------------------------
Функции, начинающиеся с…
    "get…" – возвращают значение,
    "calc…" – что-то вычисляют,
    "create…" – что-то создают,
    "check…" – что-то проверяют и возвращают логическое значение, и т.д.

showMessage(..)     // показывает сообщение
getAge(..)          // возвращает возраст (получая его каким-то образом)
calcSum(..)         // вычисляет сумму и возвращает результат
createForm(..)      // создаёт форму (и обычно возвращает её)
checkPermission(..) // проверяет доступ, возвращает логическое значение
---------------------------------------------------------
// Number.isInteger(value) определяет, является ли переданное значение целым числом.
---------------------------------------------------------
   function fits(x, y) {
   if (Number.isInteger(y / x)) {
      return 'Fits!';
   }
   return 'Does NOT fit!';
   }

   console.log(fits(5, 10));
   // expected output: "Fits!"

   console.log(fits(5, 11));
   // expected output: "Does NOT fit!"
---------------------------------------------------------
/=/=/=/ Дата и Время
---------------------------------------------------------
/=/ Создаем Объект
   const date = new Date(); 
   console.log('date', date);

   const newDate = new Date(2000, 0, 31, 00, 00, 0, 0); 
/ newDate(year, month, date, hours, minutes, seconds, ms) 
/ Месяца: 0 (январь) до 11 (декабрь)

   console.log('newDate', newDate); 
/ Mon Jan 31 2000 00:00:00 GMT+0000 (Coordinated Universal Time)

---------------------------------------------------------
/=/=/ .toLocaleString() для преобразования даты в человеко-читаемый формат
-------------------
   const humanDate = new Date().toLocaleString();
   console.log(humanDate);  /=/ '22.06.2023, 20:23:57'
---------
   const date = new Date(date);
   const humanDate = date.toLocaleString();

-------------------
/=/=/ Разделение дат запятой
---------
    const arr = [100, 2000, 50000, 900000, 100000000];
    const formattedArr = arr.map(number => number.toLocaleString());

    console.log(formattedArr); // =>
    ["100", "2,000", "50,000", "900,000", "100,000,000"]

-------------------
/=/ Создание даты из строки
---------
Также new Date() может принимать в себя строку с датой:

   const date = new Date('December 17, 2006 03:24:00');
   console.log(date); // Thu Dec 17 2006 03:24:00 GMT...

Это будет работать, если в конструктор был передан единственный аргумент с типом данных string.
-------------------
// Date.parse() 
-------------------
   Анализирует строку на наличие даты и переводит её в миллисекунды
   console.log(Date.parse('December 17, 2006 03:24:00')); 
-------------------
// Конвертировать миллисекунды в объект Date()
-------------------
   const dateInMs = 1498555006770
   const date = new Date(dateInMs)

   console.log(date.toString())
   / Tue Jun 27 2017 12:16:46 GMT+0300 (RTZ 2 (зима))

---------
/=/=/ ().toString(2) - Преобразование числа в двоичное с помощью функции 

    console.log((1234).toString(2)); // 10011010010
-------------------
// variable.get_() Вывести значение даты
-------------------
console.log('year', newDate.getFullYear());
console.log('month', newDate.getMonth());
console.log('date', newDate.getDate());
const hours = (newDate.getHours())
const minutes = (newDate.getMinutes())
console.log('seconds', newDate.getSeconds());

-------------------
// variable.getDay() Вывести день недели
-------------------
/ 0 (Вс) - 6 (Сб)
   console.log('day', newDate.getDay());
   if (newDate.getDay() === 1) {
      console.log('Сегодня Пн') 
   }

-------------------
// variable.set_() Установить/передать дату
-------------------
   newDate.setFullYear(1996, 0, 31) // Можно установить ПолнуюДату
   console.log('newDate.FullYear', newDate);

-------------------
// Расчет разности между датами
-------------------
// getTime()

   const date1 = new Date(2005, 4, 20);
   const date2 = new Date(2006, 4, 10);

   console.log('date1', date1.getTime()); 
   console.log('date2', date2.getTime()); 
   / кол-во мс с Jan 1, 1970 

   const difference = date2.getTime() - date1.getTime();
   console.log('difference', difference / 1000 / 60 / 60 / 24); 
   / разница в днях (1000 * 3600 * 24)
-------------------
// Высчитывание скорости выполнения кода (Таймстамп)
-------------------
   const startTime = Date.now()
   for (let i = 0; i < 1000000; i++) {
      // do something
   }
   const endTime = Date.now()
   console.log('endTime - startTime:', endTime - startTime, 'ms');

---------
    var start = performance.now();

    // Your code here

    var end = performance.now();
    var time = end - start;
-------------------
// timestamp - Date.now(). Количество мс с 1 января 1970 г.
-------------------
Чтобы добавить определенное число миллисекунд, можно использовать следующую запись:
    new Date(Date.now() + 5000)
В итоге мы получим дату, которая на 5000 миллисекунд больше текущей.
---------------------------------------------------------
/=/=/=/ Комбинаторное объединение с использованием Методов и Функций
---------------------------------------------------------
const getDateFormat0 = (date, separator = ".") => {

  const dateItem = date.getDate();
  const monthIndex = date.getMonth();
  const year = date.getFullYear();

  return [dateItem, monthIndex + 1, year]
    .map(addZero)
    .join(separator);
};

const addZero = (el) =>
  String(el).length === 1 ? `0${el}` : String(el);

console.log(getDateFormat(new Date()));
---------------------------------------------------------
/=/=/=/ Проверка класса: "instanceof"
---------------------------------------------------------
Оператор instanceof позволяет проверить, принадлежит ли объект указанному классу, с учётом наследования.

  if (!(date instanceof Date)) {
    return "Первый параметр должен быть экземпляром класса Date!";
  }
---------------------------------------------------------
// this - ключевое слово указывающее на текущий контекст выполнения кода (чаще всего this - Объект)
---------------------------------------------------------
Простыми словами, this — это объект, который используется для функции, которая сейчас выполняется.
-------------------
// Пример работы this и Функции в Объекте
-------------------
    let student = {
        name: 'Lamar',
        stack: [
            'HTML',
        ],
        level: 1,
        improveLevel() {
            this.level += 1
            if (this.level === 2) {
                this.stack.push('CSS')
            } else if (this.level === 3) {
                this.stack.push('JavaScript')
            } else if (this.level === 4) {
                this.stack.push('React')
            } else if (this.level === 5) {
                this.stack.push('NodeJS')
                console.log('Студент выучил все технологии!');
            };
            return this
        },
    };

    let stud = student
    .improveLevel()
    .improveLevel()
    .improveLevel()
    .improveLevel()
    .improveLevel();
    console.log('stud', stud);

Примечание: цепочка из подряд идущих функций improveLevel() работает так, потому что improveLevel() возвращает объект student, а у объекта student есть метод improveLevel().
------------------
/=/=/ Глобальный this, globalThis
-------------------
При обращении из глобального контекста к this он будет указывать на глобальный объект. Для браузеров — это объект window
Для всех браузеров - window. Для NodeJS - global
    console.log('this', this);
К глобальному объекту можно также обратиться из любого контекста с помощью глобального свойства globalThis:
    console.log(globalThis);
-------------------
/=/=/ this в объекте
-------------------
Как сказано выше, this — это объект, который "владеет" кодом, который сейчас выполняется. Поэтому, при обращении к this из метода объекта, это ключевое слово будет указывать на этот объект:
-------
// Способы создания функций внутри объекта и обращение к ним
-------
* В функциях внутри объектов НЕ стоит ссылаться напрямую к имени объекта, это делает код не универсальным.
* Нужно использовать this.key, вместо user.key 
    const user = {
        name: 'Maxim',
        dateOfBirth: 2001,
        getName() {
        //  return user.name // (дубово, тк привязано к объекту user)
            return this.name // (можно исп. для других пользователей)
        },
        calculateAge() {
            const currentYear = new Date().getFullYear();
            return currentYear - this.dateOfBirth;
        },
        getAllInfo: function() {
            const age = this.calculateAge();
            console.log(`Имя: ${this.name}, Возраст: ${age}`);
        }
    }
    console.log('user.getName:', user.getName());
    console.log('calculateAge:',  user.calculateAge());
    user.getAllInfo();

-------------------
/=/=/ Обращение к Объекту или Массиву (точечная нотация и скобки)
---------

    const person = { name: 'John', age: 30, address: { city: 'New York' } };

    // Используя точечную нотацию
    console.log(person.address.city); // 'New York'

    // Используя квадратные скобки
    console.log(person['address']['city']); // 'New York'

    // Используя комбинацию точечной нотации и квадратных скобок
    console.log(person.address['city']); // 'New York'

Точечная нотация - это простой и удобный способ обращения к свойствам объекта, когда название свойства не содержит пробелы или специальные символы. 
Например, к свойству city объекта person.address можно обратиться так: person.address.city.

Квадратные скобки - позволяют обращаться к свойствам объекта, название которых содержит пробелы, специальные символы, начинается с цифры или сохранено в переменной. 
Например, к свойству first name объекта person можно обратиться так: 
person['first name']. 
Также квадратные скобки могут быть полезны, когда нужно обратиться к свойству объекта, название которого хранится в переменной: 

    const person = {
        name: "John",
        age: 30
    };

    const propertyName = "name";
    console.log(person[propertyName]); // "John"

---------
Комбинация точечной нотации и квадратных скобок - позволяет комбинировать оба способа обращения к свойствам объекта. 
Например, к свойству city объекта person.address можно обратиться так: person.address['city']. 
Этот способ может быть полезен, если в названии свойства есть символы, которые не могут быть использованы в точечной нотации, но при этом можно использовать точечную нотацию для обращения к более простым свойствам объекта, чтобы код был более читабельным.

-------------------
/=/=/ bind, call, apply - Методы для привязки к функции какого-то контекста (Применимо только к Функциям.)
-------------------
    const user2 = {
        name: 'Igor'
    }
    const newValueForThis = user.getName.call(user2) 
    console.log('newValueForThis', newValueForThis);

this из объекта user, будет заменен на user2, следовательно и name будет использовано из объекта user2
-------------------
// Различия bind, call, apply
-------------------
    const mainHero = {
        fullName: 'SpiderMan',
        health: 65,
        strength: 5,
    };
    const badHero = {
        fullName: 'SpiderMan',
        health: 55,
        strength: 10,
    }

    function printHeroInfo(extraInfo = '') {
        console.log(`Имя: ${this.fullName}, Здоровье: ${this.health}, Сила: ${this.strength}, ${extraInfo}`);
    }
-------
// Метод call()
-------
    printHeroInfo.call(badHero, 'Роль: Злодей'); 
С помощью call(variable) указываем this какой объект нас интересует
    Пример: this из объекта user, будет заменен на user2, следовательно и name будет использовано из объекта user2
-------
// Метод apply()
-------
    printHeroInfo.apply(badHero, ['Роль: Злодей']); 
Отличия: Метод call() принимает параметры в виде списка через запятую, а apply() — в виде массива:
func.apply(context, [arg1, arg2, ...])
-------
// Метод bind()
-------
    const bindedPrintHeroInfo = 
       printHeroInfo.bind(mainHero, 'Роль: Главный Герой') 
    bindedPrintHeroInfo(); 
Задает контекст this, но не вызывает функцию. При этом он возвращает новую функцию, с заданным this.
---------------------------------------------------------
/=/=/=/ Потеря контекста "this"
---------------------------------------------------------
    const user = {
        name: 'Maxim',
        programmingLang: 'JavaScript',
        getName() {
            return this.name;
        },
        getProgrammingLang() {
            return this.programmingLang;
        },
    }
    console.log('getName:', user.getName()); 
    // getName: Maxim
-------------------
/=/=/ Потеря контекста при сохранении объекта.функции в переменную
-------------------
    const newGetName = user.getName
    console.log('newGetName:', newGetName()); 
    // newGetName: undefined. 
Тк мы вызываем функцию newGetName() без контекста(без элемента перед точкой). Поэтому контекст ссылается не на user, а на глобальный объект windows.
-------
// Решение ситуации:
-------
    const newGetName = user.getName
    console.log('newGetName:', newGetName.call(user)); 
    // Через call указали контекст - объект user
-------
    // Если сделать так, то тоже сработает 
    (но потеряет возможность вызывать нужный объект):
    const newGetName = user.getName() // Вызываем f() тут
    console.log('newGetName:', newGetName); // () уже не надо 

Так же назначение, без ее использования, считается за вызов, это может сбить счетчик:

for (let i = 0; i < 5; i++) {
    let callFn = student0.improveLevel;
    let callForOther = callFn.call(student1); 
    // callFn.call(student1) не применятся далее, воспринимается как лишний вызов функции
    console.log(i, callFn.call(student1));
}
for (let i = 0; i < 5; i++) {
    let callFn = student0.improveLevel;
    let callForOther = callFn.call(student1);
    console.log(i, callForOther); 
    // Вызывается, результат вызовов верен
}
-------------------
/=/=/ Пример работы вызова Функции Объекта в другом Объекте
-------------------
    const user = {
        name: 'Maxim',
        programmingLang: 'JavaScript',
        getName() {
            return this.name;
        },
        getProgrammingLang() {
            return this.programmingLang;
        },
    }
    const user2 = {
        name: 'Maxim',
        programmingLang: 'JavaScript',
        getName() {
            return this.name;
        },
        // getProgrammingLang() {
        //     return this.programmingLang;
        // },
    }

    let callFn = user.getProgrammingLang // Чья f() Объекта
    console.log(callFn.call(user2)); // Выводим ее для user2
    // JavaScript

-------------------
/=/=/ Пример использования Функций Объектов
-------------------
const footballer = {
    fullName: 'Cristiano Ronaldo',
    attack() {
        console.log(`${this.fullName} сейчас с мячом и начинает атаку!`);
    },
    scoreGoal (sound) {
        console.log(`${this.fullName} забил гол! Вот это да!`);
        this.celebrate(sound);
    },
    celebrate (sound) {
        console.log(sound);
    },
    goToSubstitution: function (newPlayer) {
        console.log(`${this.fullName} уходит на замену. На поле выходит ${newPlayer}`);  
    }
};

    const attack = footballer.attack;
    const score = footballer.scoreGoal;
    const substitute = footballer.goToSubstitution;

    attack.bind(footballer)();
    score.call(footballer, "Сиииии");
    substitute.apply(footballer, ["Paulo Dibala"]);
-------------------
/=/=/ Потеря контекста при стрелочных функциях 
-------------------
    getProgrammingLang: () => {
        return this.programmingLang;
    } 
    // У стрелочной функции нет this
-------
Возможно только через "variable: function() {}" или "variable() {}"
    getProgrammingLang: function () {
        return this.programmingLang;
    }
    getProgrammingLang() {
        return this.programmingLang;
    }
---------------------------------------------------------
/=/=/=/ ООП - объектно-ориентированное программирование 
---------------------------------------------------------
/=/=/ function и class
-------------------
// Создаем объект с помощью function
-------
    function Animal (name) {
        this.name = name;

        this.getName = function() {
            return this.name;
        }
    }

    console.log('result', Animal('кот')); 
    // Пытаемся вызвать функцию для создания объекта: result undefined
    const cat = new Animal('кот');
    console.log('cat', cat);

----------------------------
// Создаем объект с помощью class (рекомендуется)
----------------------------
// Класс – это шаблон кода для создания объектов.
    * В классе устанавливаются:
    начальные значения (свойства) и поведение (методы).
// constructor() - это спец-я функция которая вызывается в первый же момент, и инициализирует начальные значения.
// Поля - это каждая сущность внутри constructor() 
   (this.name = name, name - поле)
// Методы - Функции в class (getName() - метод)

    class Animal {
        constructor(name) {
            this.name = name;
        }

        getName() {
            return this.name;
        }
    }

    const dog = new Animal('@');
    console.log('dog', dog);
    console.log('dog.name', dog.name);
    console.log('dog.getName', dog.getName());
-------------------
* Представим, что наземные млекопитающие – это класс. 
* У каждого из них есть четыре конечности, два глаза, каждому из них нужно питаться – это свойства с конкретными значениями, они общие для всех объектов. 
* Также животные могут быть домашними или дикими, травоядными или хищниками, ходить на четырех лапах или на двух – это свойства со значениями, которые задаются конкретному объекту. 
* А такие действия, как поспать, поесть, побежать – это методы.

-------------------
/=/=/ Создание класса с помощью функции-конструктора
-------------------
Один из способов создать класс - функция или, вернее, функция-конструктор. Это обычные функции, но с двумя соглашениями:
    Имя функции-конструктора должно быть с заглавной буквы.
    Функция-конструктор должна вызываться с помощью оператора new.
Создание и вызов функции-конструктора выглядит следующим образом:
-------
// Класс через функцию-конструктор
-------
    function Class(значениеСвойства) {
    this.названиеСвойства = значениеСвойства;
    this.названиеМетода = function() { /* ... */ };
    };

    const obj = new Class(переданноеЗначение);
-------
    function Pet(type, name) {
    this.type = type;
    this.name = name;
    this.favoriteAction = 'спать';
    this.say = function() {
        console.log(`${this.type} по имени ${this.name} любит ${this.favoriteAction}.`);
    };
    };

    const cat = new Pet('Кот', 'Барсик');

    console.log(cat);
    // Pet {type: 'Кот', name: 'Барсик', favoriteAction: 'спать', say: ƒ}

    cat.say();
    // Кот по имени Барсик любит спать.

-------------------
/=/=/ Создание класса с помощью ключевого слова class
-------------------
    class Class {};
    console.log('type of Class:', typeof Class); // type of Class: function
class – это всего лишь разновидность функции.

В случае с class действуют те же правила, что и с функцией-конструктором:
    Имя должно быть с заглавной буквы.
    Вызов происходит с помощью оператора new.
-------
// Создание класса
-------
    class Class {
    constructor(значениеСвойства) {
        this.названиеСвойства = значениеСвойства;
    }
    названиеМетода1() {} // не ставим ","!
    названиеМетода2() {}
    }

    const obj = new Class(переданноеЗначение);
-------
    class Pet {
    constructor(type, name) {
        this.type = type;
        this.name = name;
        this.favoriteAction = 'спать';
    }
    say() {
        console.log(`${this.type} по имени ${this.name} любит ${this.favoriteAction}.`);
    }
    };

    const cat = new Pet('Кот', 'Барсик');

    console.log(cat);
    // Pet {type: 'Кот', name: 'Барсик', favoriteAction: 'спать'}

    cat.say();
    // Кот по имени Барсик любит спать.
-------------------
// Особенности class
-------------------
class нельзя вызвать без оператора new. 
Если попытаться это сделать, то мы получим ошибку:
    class Class {};
    Class();
    // Uncaught TypeError: Class constructor Class cannot be invoked without 'new'
-------
Вывод класса в консоль начинается с 'class...', что открывает возможности для его отслеживания:
    class Class {};
    console.log(Class); // class Class {}
---------------------------------------------------------
/=/=/=/ Принципы ООП. 
Наследование, Инкапсуляция, Полиморфизм, Абстракция
---------------------------------------------------------
/=/=/ Наследование - создание дочерних классов на основе базовых
-------------------
class Plane {
    constructor(type, numOfPassengers) {
        this.type = type;
        this.numOfPassengers = numOfPassengers;
    }

    startFlight() {
        console.log('Полетели!');
    }
}
-------------------
/=/=/ extends - назначает дочерние элементы
-------------------
Делаем MilitaryPlane дочерним к обычному Plane(чтобы например пассажирский самолет не имел в себе доступных параметров которы доступны военному)

    class MilitaryPlane extends Plane {
        constructor(type) {
            super(type, 0); 
            // Вызов род-го конструктора и его параметров
        }

        setNumberOfGuns(NumberOfGuns) {
            this.NumberOfGuns = NumberOfGuns;
        }

        shoot() {
            console.log('Стреляем');
        }
    }
У дочерних есть доступ к родительским Методам и Полям. А у род-х к доч-м - нет.

    const plane = new Plane('Пассажирский', 100);
    console.log('plane', plane);
    plane.startFlight();

    const militaryPlane = new MilitaryPlane('Военный')
    militaryPlane.startFlight() // Вызывает первый найденный Метод. Если нет у себя (у дочернего), то вызывает у род-го
    militaryPlane.setNumberOfGuns('4');
    militaryPlane.shoot();
    console.log('militaryPlane', militaryPlane);
-------------------
/=/=/ instanceof - проверяет принадлежит ли объект определенному классу 
    console.log(militaryPlane instanceof Plane); // true
---------------------------------------------------------
/=/=/ Инкапсуляция - скрытие данных от доступа вне класса или при наследовании 
-------------------
    class SimpleClass {
    constructor() {
        this.value = 'Hello World!';
    }

    sayHi() {
        console.log(this.value);
    }
    };
-------
// Публичные данные:
-------
    const obj = new SimpleClass();

    // Читаем
    console.log(obj.value); // Hello World!
    obj.sayHi(); // Hello World!

    // Обновляем
    obj.value = 'Hello!';
    obj.sayHi(); // Hello!

-------
// Приватные данные:
-------
Приватные данные (Поля и Методы) мы можем вызвать только через помещение их в публичные методы и обращение через них. 
Публичный метод может вызывать цепочку из вложенных в друг друга приватных элементов.

Также перед тем как создать приватное свойство, в начале тела класса его нужно проинициализировать с помощью "#" перед конструктором

class SimpleClass {
    // Приватное свойство
    #privateValue

    constructor() {
        this.value = 'Hello World!';
        // Запись в приватное свойство
        this.#privateValue = 'JavaScript';
    }

    sayHi() {
        console.log(this.value);
        // Вызов приватного метода
        this.#privateMethod();
    }

    // Приватный метод
    #privateMethod() {
        // Чтение приватного свойства
        console.log(`I love ${this.#privateValue}`)
    }
    };

    const obj = new SimpleClass();

    console.log(obj.#privateValue);
    // Uncaught SyntaxError: Private field '#privateValue' must be declared in an enclosing class

    obj.#privateMethod();
    // Uncaught SyntaxError: Private field '#privateMethod' must be declared in an enclosing class

    obj.sayHi();
    // Hello World!
    // I love JavaScript

-------
class SimpleClass {
    #privateValue

    constructor() {
        this.#privateValue = 'JavaScript';
    }

    get value() {
        // сработает, при чтении obj.value
        return this.#privateValue;
    }

    set value(newValue) {
        // сработает, при записи obj.value = ...
        this.#privateValue = newValue;
    }
    };

    const obj = new SimpleClass();
    console.log(obj.value); // JavaScript

    obj.value = 'TypeScript';
    console.log(obj.value); // TypeScript
    
---------------------------------------------------------
/=/=/ get & set - вызов и изменение приватных элементов 
(за пределами класса)
---------------------------------------------------------
// Геттер get
-------------------
    console.log(developer.devSalary) 
    // Вызываем без ()!
-------------------
// Сеттер set
-------------------
    developer.setSalary = 5000 
    // Передаем новое значение в приватное поле

---------------------------------------------------------
/=/=/ Полиморфизм - одно действие, несколько реализаций 
-------------------
Полиморфизм означает «множество форм». 
Это способность вызвать один и тот же метод у разных объектов, и при этом они могут выполнять разные действия. То есть одинаковым будет только имя метода, его реализация будет зависеть от класса.

    class Animal {
        constructor(name) {
            this.name = name;
        }
        makeSound () {}
    }

    class Dog extends Animal {
        constructor(name) {
            super(name)
        }
        makeSound () {
            console.log('гаф');
        }
    }

    class Horse extends Animal {
        constructor(name) {
            super(name)
        }
        makeSound () {
            console.log('игого');
        }
    }
---------------------------------------------------------
/=/=/ Абстракция - использование только тех характеристик объекта которые с наибольшей точностью представляют его в определенной системе
-------------------
Говоря на примере, Абстракция это создание главного объекта с каркасом из обобщенных параметров, с целью его дальнейшего использования для уточнения в дочерних классах с помощью переопределения.

    class Footballer {
        constructor(name, club) {
            this.name = name;
            this.club = club;
        }

        shoot() {}
        celebrateGoal() {}
        pass() {}
    }

    class Forward extends Footballer {
        constructor(name, club) {
            super(name, club)
        }

        shoot() {
            console.log('Очень сильный удар');
        }

        celebrateGoal() {
            console.log('Даа! Я забил гол!');
        }

        pass() {
            console.log('Средний пас');
        }
    }

-------------------
/=/=/ static Статические поля и методы 
-------------------
Статические методы/свойства нужны тогда, когда наше свойство или метод не принадлежит конкретному объекту, а относится именно к классу.

Например, есть класс Person:
    class Person {
    constructor (name, age) {
        this.name = name;
        this.age = age;
    }
    }
    const person1 = new Person('Алекс', 25);
    const person2 = new Person('Игорь', 30);

Ключевое слово "static" применяется когда наше Поле или Метод не принадлежит конкретному объекту.
Либо когда внутри Метода не используется this.
Так же static можно использовать как приватный.

    class Car {
        static isCar(car) {
            return car instanceof Car
        } // проверяем соответствует ли переменная car классу Car
        
        static #initialParams = {
            name: 'Audi',
            maxSpeed: 150,
        } // Будет использовано если параметры не переданы

        constructor(name, maxSpeed) {
            this.name = name || Car.#initialParams.name;
            this.maxSpeed = maxSpeed || Car.#initialParams.maxSpeed;
        }

        drive () {
            console.log(`Машина ${this.name} сейчас в пути`);
        }
    }

    const car = new Car('BMW', 200);
    console.log('car:', car);

    const checkIsCar = Car.isCar(car) 
    // Обращаемся к статическому полю через название класса без new!
    console.log('checkIsCar:', checkIsCar);

    Car.#initialParams 
    // Private field '#initialParams' must be declared in an enclosing class

---------------------------------------------------------
/=/=/=/ DOM (Document Object Model) - дерево объектов веб-страницы
---------------------------------------------------------
DOM – это представление HTML-документа в виде дерева тегов.
Основой HTML-документа являются теги. 
Каждый HTML-тег - объект и является узлом. Текст, который находится внутри тега, также является объектом-узлом.

DOM-узлы – это обычные объекты JavaScript. Мы можем их изменять.
Например, создадим новое свойство для document.body:
    document.body.myData = {
        name: 'Caesar',
        title: 'Imperator'
    };
    alert(document.body.myData.title); // Imperator

Мы можем добавить и метод:
    document.body.sayTagName = function() {
        alert(this.tagName);
    };
    document.body.sayTagName(); // BODY (значением "this" в этом методе будет document.body)

Также можно изменять встроенные прототипы, такие как Element.prototype и добавлять новые методы ко всем элементам:
    Element.prototype.sayHi = function() {
        alert(`Hello, I'm ${this.tagName}`);
    };
    document.documentElement.sayHi(); // Hello, I'm HTML
    document.body.sayHi(); // Hello, I'm BODY

-------------------
/=/=/ Методы для поиска элементов:
-------------------
/=/=/ .getElementBy_() (устарел)
    const tasksBlock = document.getElementById('tasks');
    const allNavButtons = 
        document.getElementsByClassName('main-navigation');
    const allButtons = document.getElementsByTagName('button');

    console.log('tasksBlock:', tasksBlock);
    console.log('allNavButtons:', allNavButtons);
    console.log('allButtons:', allButtons);
-------------------
/=/=/ .querySelector() - выводит Первый элемент
-------------------
// поиск id через "#"
    const tasksBlock2 = document.querySelector('#tasks'); 
    console.log('tasksBlock2:', tasksBlock2);

// поиск классов через "."
    const classMainNav = document.querySelector('.main-navigation')
    console.log('classMainNav:', classMainNav);

// поиск тэга
    const firstButton = document.querySelector('button');
    console.log('firstButton:', firstButton);

// поиск атрибута через "[]"
    const thirdNavButton = document.querySelector('[data-button-id="3"]')
    console.log('thirdNavButton:', thirdNavButton);

// комбинированный поиск по селектору:
    const elements = document.querySelector("#main p.text");
    
В этом примере осуществляется поиск всех элементов <p> с классом .text, вложенных внутрь элемента с id = #main. Пробел указывает на поиск по потомкам.
-------------------
/=/=/ .querySelectorAll() - находит и выводит Все элементы
-------------------
    const allNavigationButtons = document.querySelectorAll('.main-navigation__button-item')
    console.log('allNavigationButtons:', allNavigationButtons);

Можем перебирать эти элементы:
    allNavigationButtons.forEach((el, i) => {
        console.log('i, el:', i, el);
    })
---------------------------------------------------------
/=/=/=/ Получить Переименовать Аттрибут
---------------------------------------------------------
// Получить имя класса:
    const taskWrapper = document.querySelector('.tasks__wrapper');
    console.log(taskWrapper.className);

// Назначить имя класса:
    taskWrapper.className = 'tasks__wrapper_1';
    console.log(taskWrapper.className);

// Получить имя тэга:
    const elemTagName = element.tagName

// Назначить id:
    const tasksBlock1 = document.querySelector('#tasks');
    tasksBlock1.id = 'new_tasks' 
    // Переименовали (верстка сломалась)

// Назначить href:
    const newNavButton = document.createElement('a');
    newNavButton.href = '#tasks_expired'

// Назначить data-*:
    newNavButton.dataset.buttonId = '4'

// Назначить text:
    newNavButton.textContent = 'Просроченные задачи'
    newNavButton.innerText = 'Просроченные задачи'

// Назначить аттрибут for:
    newNavButton.htmlFor = "task-1"

// Найти el по аттрибуту:
    document.querySelectorAll('[attributeName="attributeValue"]');

// Поиск по классу 
    <div class="_1Fm4m _1h2dM app-wrapper-web font-fix">

    document.querySelector("._1Fm4m._1h2dM.app-wrapper-web.font-fix");

-------------------
/=/=/ .innerText 
    .textContent - вывести/изменить текстовое содержимое элемента. 
-------------------
    const submitButton = document.querySelector('.create-task-block__button');
    console.log(submitButton.innerText);
    console.log(submitButton.textContent);

// Переименовать значение элемента (не читает переданные теги):
    submitButton.textContent = '<b>Создать новую задачу</b>'
    // <b>Создать новую задачу</b>

// Изменить верстку (для вставки prettier кода используй ``)
    const submitButton = 
        document.querySelector('.create-task-block__button');
    submitButton.innerHTML = `<b>Создать новую задачу</b>`
    // Создать новую задачу //(bold)
-------------------
/=/=/ .innerHTML - содержит в себе код HTML-разметки элемента: 
-------------------
Свойство innerHTML позволяет получить HTML-содержимое элемента в виде строки. Мы также можем изменять его. 
Пример ниже показывает содержимое document.body, а затем полностью заменяет его:
    <body>
    <p>Параграф</p>
    <div>DIV</div>
    <script>
        alert( document.body.innerHTML ); // читаем текущее содержимое
        document.body.innerHTML = 'Новый BODY!'; // заменяем содержимое
    </script>
    </body>

Скрипты не выполнятся
Если innerHTML вставляет в документ тег <script> – он становится частью HTML, но не запускается.

Будьте внимательны: «innerHTML+=» осуществляет перезапись
Мы можем добавить HTML к элементу, используя elem.innerHTML+="ещё html".
Вот так:
    chatDiv.innerHTML += 
        "<div>Привет<img src='smile.gif'/> !</div>";
    chatDiv.innerHTML += "Как дела?";
На практике этим следует пользоваться с большой осторожностью, так как фактически происходит не добавление, а перезапись.

-------------------
/=/=/ .children - Вывести дочерние элементы класса
-------------------
    const createTaskForm = 
        document.querySelector('.create-task-block');
    console.log('createTaskForm.children', createTaskForm.children);
-------------------
// appendChild() - adding an element to a div
-------------------
To add an element to a div, you create an element and append it to the div using the appendChild() method:

    let div = document.createElement('div');
    div.id = 'content';
    div.className = 'note';

// create a new heading and add it to the div
    let h2 = document.createElement('h2');
    h2.textContent = 'Add h2 element to the div';
    div.appendChild(h2);

// add div to the document
    document.body.appendChild(div);

-------------------
/=/=/ data-атрибуты - это атрибуты, которые можно применять для удобного хранения в стандартных HTML-элементах различной полезной информации. (похоже на class id и тд)
-------------------
В нашем примере такие атрибуты (data-id) есть у элемента p:
    <p class="text" data-id="1">Первый абзац</p>
    const firstNavButton =
        document.querySelector('.main-navigation__button-item');

Стилизация элементов с использованием атрибутов data-*
В CSS можно выбирать HTML-элементы, основываясь на атрибутах и их значениях.

Выбрать элемент с таким именем атрибута, имеющим такое значение
    [data-size="large"] {
      padding: 2rem;
      font-size: 125%;
    }

Выбор можно ограничить элементом, классом, или чем-то другим
    button[data-type="download"] { }
    .card[data-pad="extra"] { }

Это может показаться интересным. Для стилизации в HTML/CSS используются, в основном, классы. И хотя классы — это замечательный инструмент (они отличаются средним уровнем специфичности, с ними можно работать с помощью удобных JavaScript-методов через свойство элементов classList), элемент может либо иметь, либо не иметь некоего класса (то есть, класс в элементе либо «включен», либо «выключен»). При использовании атрибутов data-* в распоряжении разработчика оказываются и возможности классов («включено/выключено»), и возможность выбора элементов, основываясь на значении атрибута, которое он имеет на том же уровне специфичности.

Выбор элементов, у которых имеется указанный атрибут
    [data-size] { }

Выбор элемента, атрибут которого имеет заданное значение
    [data-state="open"],
    [aria-expanded="true"] { }

Селектор "начинается с", использование которого приведёт к выбору элементов, атрибут которых содержит "3", а так же - что угодно другое, начинающееся с 3 - вроде "3.14"
    [data-version^="3"] { }

Селектор "содержит" указывает на то, что заданная строка должна содержаться где-то в значении свойства
    [data-company*="google"] { }

-------------------
/=/=/ dataset - получить коллекцию data-атрибутов
-------------------
    console.log(firstNavButton.dataset); 
    // DOMStringMap { buttonId → "1" }
На основе прошлого вывода:
    console.log(firstNavButton.dataset.buttonId); // 1

// Изменение data-атрибутов:
    firstNavButton.dataset.buttonId = '10';
    console.log(firstNavButton.dataset.buttonId); // 10
-------------------
/=/=/ .style - создание и изменение стилей
-------------------
В css: font-weight 
В js: fontWeight 
    firstNavButton.style.fontWeight = 'bold';
    firstNavButton.style.boxShadow = 'inset 0 0 0 3px #fff';

    firstNavButton.style = ''; // сброс всех стилей

К примеру, к CSS-свойству background-color мы обращаемся из кода через .style.backgroundColor = "green";

-------
// Функция переключения стилей с передачей аргументов через Объект
-------
	function toggleThemes({bodyBackground, taskTextColor, buttonBorder}) {
		document.body.style.background = bodyBackground 
		// Важно! При таком методе важно писать не ".style = background:", а ".style.background = "
		const taskItem = document.querySelectorAll('.task-item');
		taskItem.forEach(el => {
			el.style.color = taskTextColor
		});
		const findButtons = document.querySelectorAll('button');
		findButtons.forEach(el => {
			el.style.border = buttonBorder
		});
	}

	toggleThemes({
      bodyBackground: "#24292E",
      taskItemTextColor: "#ffffff",
      buttonBorder: "1px solid #ffffff"
   });
   toggleThemes({
      bodyBackground: "initial",
      taskItemTextColor: "initial",
      buttonBorder: "none"
   });

-------------------
/=/=/ style.cssText - задание нескольких стилей
-------------------
Для задания нескольких стилей в одной строке используется специальное свойство style.cssText:
    div.style.cssText=`color: red !important;
      background-color: yellow;
      width: 100px;
      text-align: center;
    `;
То же самое можно сделать установкой атрибута: div.setAttribute('style', 'color: red...')
Это свойство редко используется, потому что такое присваивание удаляет все существующие стили: оно не добавляет, а заменяет их.
-------------------
/=/=/ style.display - сброс стилей
-------------------
elem.style.display = "none" - Скрыть элемент
elem.style.display = "" - Вернуть элемент

если мы запустим этот код, <body> "мигнёт":
    document.body.style.display = "none"; // скрыть
    setTimeout(() => document.body.style.display = "", 1000); 
    // возврат к нормальному состоянию
---------------------------------------------------------
/=/=/=/ Создание HTML-элементов и добавление их в DOM
---------------------------------------------------------
/=/=/ .createElement() - создание нового элемента
-------------------
    const newNavButton = document.createElement('a');

    newNavButton.className = 'main-navigation__button-item'
    newNavButton.href = '#tasks_expired'
    newNavButton.dataset.buttonId = '4'
    newNavButton.textContent = 'Просроченные задачи'
    console.log(newNavButton);

Имя пользовательского элемента должно содержать дефис -, например, my-element и super-button – валидные имена, а myelement – нет.

Это чтобы гарантировать отсутствие конфликтов имён между встроенными и пользовательскими элементами HTML.
-------------------
/=/=/ node.remove() - удаляет элемент из DOM-дерева.
-------------------
    <div id="main">
    <p class="text" data-id="1">Первый абзац</p>
    <p class="text" data-id="2">Второй абзац</p>
    </div>
Удалим первый абзац:
    const p = document.querySelector("p");
    p.remove();

-------------------
/=/=/ Добавление созданных элементов в DOM 
-------------------
    .before() - добавляет перед блоком
    .prepend() - добавляет в начало
    .append() - добавляет в конец
    .after() - добавляет после блока
    
    const mainNavigation = 
        document.querySelector('.main-navigation');
    mainNavigation.append(newNavButton)
-------------------
/=/=/ .after() - поменять местами теги (узлы)
-------------------
	<div id="first">Первый</div>
	<div id="second">Второй</div>
	<script>
	/=/ нет необходимости вызывать метод remove
	second.after(first); 
    /=/ берёт #second и после него вставляет #first
	</script>

-------------------
/=/=/ .cloneNode() - клонирование узлов
-------------------
Как вставить ещё одно подобное сообщение?
   Мы могли бы создать функцию и поместить код туда. Альтернатива – клонировать существующий div и изменить текст внутри него (при необходимости).
Иногда, когда у нас есть большой элемент, это может быть быстрее и проще.
   Вызов elem.cloneNode(true) создаёт «глубокий» клон элемента – со всеми атрибутами и дочерними элементами. Если мы вызовем elem.cloneNode(false), тогда клон будет без дочерних элементов.
Пример копирования сообщения:
	<style>
	.alert {
	padding: 15px;
	border: 1px solid #d6e9c6;
	border-radius: 4px;
	color: #3c763d;
	background-color: #dff0d8;
	}
	</style>

	<div class="alert" id="div">
	<strong>Всем привет!</strong> Вы прочитали важное сообщение.
	</div>

	<script>
	let div2 = div.cloneNode(true); // клонировать сообщение
	div2.querySelector('strong').innerHTML = 'Всем пока!'; // изменить клонированный элемент

	div.after(div2); // показать клонированный элемент после существующего div
	</script>
-------------------
/=/=/ .classList - управление классами
-------------------
У classList есть несколько методов:
    _.classList.add() — добавляет класс к элементу
    _.classList.remove() — удаляет класс
    _.classList.toggle() — добавляет если нет / удаляет если есть
    _.classList.replace() — заменяет один класс другим

    const p = document.querySelector("p");
    p.classList.add("red");
-------------------
/=/=/ .replaceWith() - заменить элемент на другой
-------------------
Заменим первый абзац на новый с помощью этого метода:
    const firstParagraph = document.querySelector("p");
    firstParagraph.replaceWith(newParagraph);
---------
    myElement = document.querySelector("div._3ndVb");
    
    const myButton = document.createElement("button");
    myElement.replaceWith(myButton);
-------------------
/=/=/ closest - ищет ближайший родительский элемент 
    (например div или body)
-------------------
    elem.closest('селектор')   
Метод closest поднимается вверх от элемента и проверяет каждого из родителей. Если он соответствует селектору, поиск прекращается. Метод возвращает либо предка, либо null, если такой элемент не найден.

    const taskItemText = document.querySelector('.task-item__text'); 
    console.log(taskItemText); // элемент <span> 

    const taskItem = taskItemText.closest('.task-item')
    console.log(taskItem); элемент <span> принадлежит <div>

-------------------
/=/=/ matches - проверяет, удовлетворяет ли elem селектору, и возвращает true или false.
-------------------
Этот метод удобен, когда мы перебираем элементы (например, в массиве или в чём-то подобном) и пытаемся выбрать те из них, которые нас интересуют.
Например:
    <a href="http://example.com/file.zip">...</a>
    <a href="http://ya.ru">...</a>

    <script>
    // может быть любая коллекция вместо document.body.children
    for (let elem of document.body.children) {
        if (elem.matches('a[href$="zip"]')) {
        alert("Ссылка на архив: " + elem.href );
        }
    }
    </script>
    
-------------------
/=/=/ ._Attribute() - управление атрибутами
-------------------
    document.hasAttribute() - существует ли атрибут 
    document.getAttribute() - выводит значение атрибута
    document.removeAttribute() - удалить атрибут
    document.setAttribute('nameAttribute', 'value') - добавить атрибут (второй параметр обязателен, если null то '')

Имеет ли элемент указанный атрибут. Возвращает булево значение:
    const p = document.querySelector("p");
    console.log(p.hasAttribute("class")); // true

Устанавливает значение атрибута: 
    const p = document.querySelector("p");
    p.setAttribute("id", "firstParagraph")
    console.log(p.getAttribute("id")); // firstParagraph
-------------------
/=/=/ .insertAdjacentElement() - добавить элемент в нужную позицию в зависимости от указанных параметров.
-------------------
    elem.insertAdjacentElement(where, newElem);

Параметр where может принимать следующие значения:
    "beforebegin" – вставить newElem непосредственно перед elem,
    "afterbegin" – вставить newElem в начало elem,
    "beforeend" – вставить newElem в конец elem,
    "afterend" – вставить newElem непосредственно после elem.

newElem
    Элемент, добавляемый в DOM-дерево.

Наглядное отображение параметра position:
    <!-- beforebegin -->
    <p>
    <!-- afterbegin -->
    lorem-text
    <!-- beforeend -->
    </p>
    <!-- afterend -->

    mainNavigation.insertAdjacentElement('afterbegin', newNavButton)
Примечание: значения beforebegin и afterend работают только если targetElement находится в DOM-дереве и имеет родительский элемент.
-------------------
/=/=/ .insertAdjacentHTML() - вставляет указанный HTML, без перезаписи
-------------------
    targetElement.insertAdjacentHTML(position, text);

Вставляет указанный HTML в DOM дерево в указанную позицию. Данная функция не переписывает имеющиеся элементы, что предотвращает дополнительную сериализацию и поэтому работает быстрее, чем манипуляции с innerHTML.

    const textToAdd = event.target.elements.text.value;
    const div = document.getElementById("main");
    div.insertAdjacentHTML("beforeend", `<p>${textToAdd}</p>`);
---------------------------------------------------------
/=/=/ Добавление элементов с помощью функций
---------------------------------------------------------
  const createInputWithLabel = (label, inputType, inputName, placeholder) => {
    const labelContainer = document.createElement("label");
    labelContainer.innerText = label;
  
    const inputElement = document.createElement("input");
    inputElement.type = inputType;
    inputElement.name = inputName;
    inputElement.placeholder = placeholder;
  
    labelContainer.append(inputElement);
  
    return labelContainer;
  };
  
  const formContainer = document.createElement("form");
  formContainer.className = "create-user-form";

  const userNameLabel = createInputWithLabel(
    "Имя",
    "text",
    "userName",
    "Введите ваше имя"
  );    // это аргументы функции

  const passwordLabel = createInputWithLabel(
    "Пароль",
    "password",
    "password",
    "Придумайте Пароль"
  );    // это аргументы функции

  const confirmButton = document.createElement("button");
  confirmButton.type = "submit";
  confirmButton.innerText = "Подтвердить";
  
  formContainer.append(userNameLabel, passwordLabel, confirmButton);
  document.body.prepend(formContainer);
---------------------------------------------------------
/=/=/ Пропуск аргументов при вызове функции
---------------------------------------------------------
    function foo(options) {
        let arr = [
            a = options.a,
            b = options.b,
            c = options.c,
            d = options.d,
            e = options.e,
            f = options.f
        ]
        return newArr = arr.filter(el => {
            return el !== undefined
        })
    }
    const callFoo3 = foo({f: 6, c: 4});
    console.log(callFoo3);

// Грубо говоря тут говориться что: options f = 6, а options с = 4
// Сначала мы ищем по переменной параметра, а потом находим более точно по букве.
// И найденное значение запоминаем в новую переменную
-------
    function foo(options) {
        let arr = {
            a: options.a,
            b: options.b,
            c: options.c,
            d: options.d,
            e: options.e,
            f: options.f,
        }
        let newArr = []
        for (const el in arr) {
            if (arr[el] !== undefined) {
                newArr.push(arr[el])
            }
        }
        return newArr
    }
    const callFoo = foo({f: 15, c: 6});
    console.log(callFoo);
-------
    function foo(options) {
    let arr = {
        a: options.a,
        b: options.b,
        c: options.c,
        d: options.d,
        e: options.e,
        f: options.f,
    }
    let newObj = {}
    for (const el in arr) {
        if (arr[el] !== undefined) {
            newObj = {
                ...newObj,
                [el]: arr[el]
            }
        }
    }
    return newObj
    }
    const callFoo = foo({a: 15, c: 6});
    console.log(callFoo);
-------
    function fn (className, classId,type, valueText) {
        return [
            className, 
            classId, 
            type,
            valueText,
        ];
    }

    [className, id, , value] = fn('name', 1, undefined, 'TEXT!')

    let arr2 = [className, id, value]
    console.log(arr2);
// OR
    let [className, id, , value] = fn('name', 1, undefined, 'TEXT!')
    console.log([className, id, value]);
---------------------------------------------------------
/=/=/=/ Функция для раздачи id, классов и тд тегам
---------------------------------------------------------
    const tasksList = document.querySelector('.tasks-list');

    function giveValueTags (tag) {
        return obj = {
            valueClass: tag.i_class,
            valueType: tag.i_type,
            valueId: tag.i_id,
            valueDataId: tag.i_dataset,
            valueText: tag.i_value,
        }

    //  let newObj = {}
    //  for (const el in obj) {
    //      if (obj[el] !== undefined) {
    //          newObj = {
    //              ...newObj,
    //              [el]: obj[el]
    //          }
    //      }
    //  }
    //  return newObj // Этот фильтр не поможет, тк при запуске второй функции отсутствующие элементы все равно упоминаются и пытаются быть назначенными (что равно undefined)
    }

    const tagsTaskList = giveValueTags
    ({ 
        i_class: 'tasks-list!',
        i_value: 'TEXT!', 
        i_id: 15, 
    })

    function giveNameTag(elem) {
        // Добавил if, так фильтр не пропустит undefined элементы
        if (!!atrTaskList.valueClass) 
        elem.className = atrTaskList.valueClass;
        if (!!atrTaskList.valueType) 
        elem.type = atrTaskList.valueType;
        if (!!atrTaskList.id) 
        elem.id = atrTaskList.id
        if (!!atrTaskList.valueDataId) 
        elem.dataset = atrTaskList.valueDataId;
        if (!!atrTaskList.valueText) 
        elem.innerText = atrTaskList.valueText; 
    }
    giveNameTag(tasksList)
-------
/=/=/ Refactoring
-------
// Так же добавил исправление с добавлением имени и значения data-*
(пишем имя в формате camelCase, data-* сама ставит "-" между словами)
function giveValueAttribute (atr, elem) {
    if (!!atr.class)   elem.className = atr.class
    if (!!atr.type)    elem.type = atr.type
    if (!!atr.id)      elem.id = atr.id
    if (!!atr.value)   elem.innerText = atr.value
    if (!!atr.dataName) elem.dataset[atr.dataName] = atr.dataValue
}
giveValueAttribute({
    class:"task-item!",
    dataName: 'taskId', dataValue: '1',
},tasksItem)

-------------------
// Функция для создания, перемещения, назначения атрибута элементу
-------------------
// Заметка от куратора: старайся именовать функции, которые добавляют ноды в DOM ключевым словом render

    const tasksList = document.querySelector('.tasks-list');

    function find(selector) {
        return document.querySelector(selector);
    } // Добавил поиск по querySelector для вставки в pasteElem()

    let pasteElem, giveValueAttribute;

    function createElem (elemName, command, tag) {
        if (!!elemName) 
            elemName = document[command](tag)
        
        
        pasteElem = function (toWhom, command, whichElemPaste = elemName) {
            toWhom[command](whichElemPaste)
        }

        giveValueAttribute = function (atr, elem = elemName) {
            if (!!atr.class)    elem.className = atr.class
            if (!!atr.type)     elem.type = atr.type
            if (!!atr.id)       elem.id = atr.id
            if (!!atr.value)    elem.innerText = atr.value
            if (!!atr.dataName) elem.dataset[atr.dataName] = atr.dataValue
        } // Так же можно устанавливать аттрибуты через: 
            elem.setAttribute("id", atr.id)
    }

// Родительская функция всегда должна инициализироваться для вызова дочерних.
    createElem() 
    createElem('tasksItem', 'createElement', 'div') 

// Использовать для добавление созданный createElem() - 3й аргумент оставить пустым:  
    pasteElem(find('.tasks-list'), 'appendChild', );
 

// Если нужно вызвать добавление для отдельной переменной:  
    pasteElem(document.body, 'prepend', tasksList) 

giveValueAttribute({
    // class:"task-item",
    id: 1,
    dataName: 'taskId', dataValue: '1',
}, tasksList) 
// Изменять аттрибуты созданного createElem() - 2й аргумент оставить пустым (убрать из аргументов tasksList)
-------------------
// "Variant_2 Function" для создания/перемещения/назначения с использованием Цикла и Массива данных
-------------------
function find(selector) {
    return document.querySelector(selector);
}
let pasteElem, giveValueAttribute;

function createElem (createdElem, tag) {
    if (!!createdElem) 
        createdElem = document.createElement(tag)
    
    pasteElem = function (toWhom, command, whichElemPaste = createdElem) {
        toWhom[command](whichElemPaste)
    }

    giveValueAttribute = function (atr, elem = createdElem) {
        if (!!atr.class)    elem.className = atr.class
        if (!!atr.type)     elem.type = atr.type
        if (!!atr.id)       elem.id = atr.id
        if (!!atr.value)    elem.innerText = atr.value
        if (!!atr.dataName) elem.dataset[atr.dataName] = atr.dataValue
        if (!!atr.for)      elem.setAttribute("for", atr.for) 
    }
}

let arr = [
    tasksItem = {
        create: {a: 'tasksItem', b: 'div'},
        paste: {a: '.tasks-list', b: 'appendChild'},
        valueAtr: {
            class:"task-item",
            dataName: 'taskId', dataValue: '1',
        }
    },
    mainContainer = {
        create: {a: 'mainContainer', b: 'div'},
        paste: {a: '.tasks-list', b: 'appendChild'},
        valueAtr: {
            class:"task-item",
            dataName: 'taskId', dataValue: '1',
        }
    }
]


for (const el of arr) {
    createElem (el.create.a, el.create.b)
    pasteElem(find(el.paste.a), el.paste.b, );
    giveValueAttribute({
        class: el.valueAtr.class,
        dataName: el.valueAtr.dataName, 
        dataValue: el.valueAtr.dataValue,
    }, );
}

---------------------------------------------------------
/=/=/=/ Обработчики событий. 'click'
---------------------------------------------------------
/=/=/ event.target - Найти элемент, по которому сделан клик
-------------------
    const {target} = event - рекомендованная запись
    const target = event.target // Тоже самое
-------------------
/=/=/ .addEventListener() - Метод добавления обработчика событий
-------------------
    elem.addEventListener('click', (event) => {})
-------
// Добавить обработчик для одного элемента:
    const p = document.querySelector("p");
    p.addEventListener("click", (event) => {
        event.target.textContent += " клик";
    });

-------
// Добавить обработчик для нескольких элементов, необходимо пропустить их через Цикл:

    const paragraphs = document.querySelectorAll("p");
    paragraphs.forEach(p => {
        p.addEventListener("click", event => {
            event.target.textContent += " клик";
        });
    }) 
    // const {target} = event // это event.target

Однако такой многоуровневый код достаточно сложно читать, поэтому вынесем обработчик в отдельную функцию addText():

    const paragraphs = document.querySelectorAll("p");
    paragraphs.forEach(p => {
        p.addEventListener("click", addText);
    });

    function addText(event) {
        event.target.textContent += " клик";
    }
-------------------
/=/ DOMContentLoaded - гарантирует, что вся структура DOM была загружена, прежде чем запускать ваш код
---------

    document.addEventListener("DOMContentLoaded", () => {
        console.log("Страница загружена1!");
    });
  ==/OR/==
    document.addEventListener("load", () => {
        console.log("Страница загружена2!");
    });
    
  ==/OR/==
    const checkElement = setInterval(() => {
        const myElement = document.querySelector('div[data-tab="2"]'); /=/ поиск по тегу и аттрибуту

        if (myElement) {
            clearInterval(checkElement);
            console.log("loaded!");
        }
    }, 100);

  ==/OR/==
    (async function () {
        "use strict";

        let myElement = null;
        while (!myElement) {
            myElement = document.querySelector("div._3ndVb");
            await new Promise(resolve => setTimeout(resolve, 100));
        }
        console.log(myElement);
    })();

Этот код будет проверять наличие элемента каждые 100 миллисекунд с помощью цикла while. Как только элемент будет найден и document.querySelector("div._3ndVb") вернет не null, цикл будет прерван, и вы сможете выполнить нужные действия с элементом. Обратите внимание, что вам нужно использовать await с setTimeout(), чтобы не блокировать выполнение скрипта.
-------------------
// Создать переключение темы для элемента при нажатии
---------
    const allNavButton = 
        document.querySelectorAll('.main-navigation__button-item');

    allNavButton.forEach(button => {
        button.addEventListener('click', event => {
            allNavButton.forEach(button => {
                button.classList.remove
                    ('main-navigation__button-item_selected')
            });

            const {target} = event
            target.classList.add('main-navigation__button-item_selected')
        })
    });

-------------------
/=/=/ Событие 'submit'
-------------------
Элемент HTML form (<form>) — элемент позволяющий пользователю отправлять информацию на веб-сервер.

    !DOCTYPE html>
    <html>
        <head>
            <title>Пример документа</title>
        </head>
        <body>
            <form id="form">
                <input name="text" type="text" />
                <input type="submit" value="Добавить" />
            </form>
            <div id="main">
                <p class="text" data-id="1">Первый абзац</p>
                <p class="text" data-id="2">Второй абзац</p>
            </div>
            <script src="form.js"></script>
        </body>
    </html>

Найдем элемент <form> и добавим к нему обработчик события submit
    const form = document.getElementById("form");

    form.addEventListener("submit", (event) => {
    // Код обработчика
    });
В коде обработчика нам нужно реализовать следующий алгоритм:
    *Получить введённый пользователем текст из текстового поля.
    *Найти блок <div>, в который будет делаться вставка данных.
    *Вставить новый абзац (элемент <p>) в основной блок.

-------------------
/=/=/=/ event.preventDefault() - Отмена поведения по умолчанию 
-------------------
Отмена поведения по умолчанию 
(При 'submit' отмена перезагрузки страницы)

-------------------
/=/=/=/ elementForm.elements - Обращение к input у form
-------------------
    <form id="form">
        <input name="username" type="text" />
        <input type="submit" value="Добавить" />
    </form>
    <div id="main">
        <p class="text" data-id="1">Первый абзац</p>
        <p class="text" data-id="2">Второй абзац</p>
    </div>

Находим тег 'form', и для обращения например к его 'input' обращаемся 
к найденному тегу(target, если настроен).elements.имяInput.value

    const form = document.querySelector('#form')

    form.addEventListener('submit', event => {
        event.preventDefault()

        const {target} = event
        
        const enteredText = target.elements.username.value
        const div = document.getElementById('main')
        div.insertAdjacentHTML('afterbegin', `<p>${enteredText}</p>`)

    })
// OR
    const formInputs = document.getElementById("form");
    const inputByIndex = elements.formInputs[0];
    const inputByName = elements.formInputs["username"];

---------------------------------------------------------
/=/=/=/ Планирование: setTimeout и setInterval
---------------------------------------------------------
// setTimeout() позволяет вызвать функцию один раз через определённый интервал времени.
// setInterval() позволяет вызывать функцию регулярно, повторяя вызов через определённый интервал времени
// clearInterval() отменить какой-либо таймер 

Синтаксис:
    let timerId = setTimeout(func|code, [delay], [arg1], [arg2], ...);

Параметры:
    func|code
        Функция или строка кода для выполнения. Обычно это функция. По историческим причинам можно передать и строку кода, но это не рекомендуется.
    delay
        Задержка перед запуском в миллисекундах (1000 мс = 1 с). Значение по умолчанию – 0.
    arg1, arg2…
        Аргументы, передаваемые в функцию

Например, данный код вызывает sayHi() спустя одну секунду:

    function sayHi() {
    alert('Привет');
    }
    setTimeout(sayHi, 1000);

---------
// Выводит каждый элемент через 1 сек
    let arr = [1, 2, 3, 4, 5]

    arr.forEach((el, i) => {
        setTimeout(() => {
            console.log(el)
        }, i * 1000)
    })
---------
С аргументами:

    function sayHi(phrase, who) {
    alert( phrase + ', ' + who );
    }

    setTimeout(sayHi, 1000, "Привет", "Джон"); // Привет, Джон
-------
Следующий пример выводит сообщение каждые 2 секунды. Через 5 секунд вывод прекращается:

    // повторить с интервалом 2 секунды
    let timerId = setInterval(() => alert('tick'), 2000);

    // остановить вывод через 5 секунд
    setTimeout(() => { clearInterval(timerId); alert('stop'); }, 5000);

---------
// Каждую секунду выводить сообщение

    const words = [
    "JS",
    "borderlands",
    "message",
    "keyboard",
    "bob",
    "coding",
    "computer",
    "programming",
    "developer",
    "javascript",
    ];

    let i = 0;
    const intervalId = setInterval(() => {
        console.log(words[i]);

        i++;
        if (i === 3) clearInterval(intervalId);
    }, 1000);
---------
// Самодельный таймер

    function setTimer(t, callback) {
        const startTime = Date.now();
        while ("go!") {
            const endTime = Date.now();
            if (endTime - startTime === t) {
            callback();
            break;
            }
        }
    }

    function myFunction() {
        console.log("Время таймера истекло!");
    }

    for (let i = 0; i < 3; i++) {
        setTimer(1000, myFunction);
    }

-------------------
/=/=/=/ .hidden = true/false
-------------------
Мигающий элемент:
    <div id="elem">Мигающий элемент</div>

    <script>
        setInterval(() => {elem.hidden = !elem.hidden}, 1000);
    </script> // Появляется на 1 сек и пропадает на 1 сек
-------
    document.getElementById("okButton")
            .addEventListener("click", function() {
      document.getElementById("welcome").hidden = true;
      document.getElementById("awesome").hidden = false;
    }, false);

---------------------------------------------------------
/=/=/ События "keydown" и "keyup"
---------------------------------------------------------
// Нажатие и отжатие кнопки

    document.addEventListener('keydown', (event) => {
        const {key} = event
        console.log(key);

        const taskItemToDelete = document.querySelector(`[data-task-id='${key}'`);
        if (taskItemToDelete) {
            const deleteConfirm = confirm('Удалить элемент?')
            if (deleteConfirm) {
                taskItemToDelete.remove()
            }
        }
    })
-------
    document.addEventListener("keyup", (event) => {
        const key = event.key;
        const p = document.querySelector(`[data-id='${key}']`);
        if (p) {
            p.style.fontWeight = "bold";
        }
    });
---------------------------------------------------------
/=/=/ События "mouseover", "mouseout", "mousemove"
---------------------------------------------------------
// mouseover - курсор поверх элемента 
// mouseout - курсор ушел с элемента

    const paragraphs = document.querySelectorAll("p");

    paragraphs.forEach(p => {
    p.addEventListener("mouseover", (event) => {
        event.target.style.fontWeight = "bold";
    });
    });

    paragraphs.forEach(p => {
    p.addEventListener("mouseout", (event) => {
        event.target.style.fontWeight = "normal";
    });
    });

-------
    const createToolTip = (text) => {
        const tooltip = document.createElement('span');
        tooltip.textContent = text
        tooltip.className = 'tooltip'
        return tooltip
    }

    document.addEventListener('mouseover', (event) => {
        const {target} = event
        // console.log(target);
        const isOverDeleteButton = target.className.includes('task-item__delete-button')
        if (isOverDeleteButton) {
            console.log('yes');
            const taskItemHTML = target.closest('.task-item');
            const taskId = taskItemHTML?.dataset.taskId;
            if (taskId) {
                const tooltipHTML = createToolTip(`Удалить задачу №${taskId} ?`)
                target.append(tooltipHTML)
            }
        }
    });
-------
    document.addEventListener('mouseout', (event) => {
        const {target} = event
        const isOutDeleteButton = target.className.includes('task-item__delete-button')
        if (isOutDeleteButton) {
            console.log('del');
            const tooltip = document.querySelector('.tooltip');
            tooltip.remove()
        }
    });
-------
    document.addEventListener('mousemove', function (e) {
        console.log(e);
    });
---------------------------------------------------------
/=/=/ События "contextmenu", "change", "input"
---------------------------------------------------------
/=/=/ contextmenu
-------------------
Событие contextmenu срабатывает при открытии контекстного меню, то есть когда пользователь кликает правой кнопкой мыши по любой части страницы.
Это событие может пригодиться тогда, когда мы хотим сделать собственное контекстное меню вместо стандартного. Для этого нужно в обработчике отменить действие по умолчанию с помощью метода event.preventDefault():

    document.addEventListener("contextmenu", (event) => {
    event.preventDefault();
    // Дальнейший код
    });

-------------------
/=/=/ "change", "input"
-------------------
// change - срабатывает после внесенных изменений и клика вне в поля.
// input - срабатывает сразу во время введения в поле.

Будем делать кнопку "Добавить" неактивной, если пользователь ничего не ввёл:
    const button = document.querySelector("input[type='submit']");
    button.disabled = true; // По умолчанию поле пустое и кнопка неактивна

    const input = document.querySelector("input[type='text']");
    input.addEventListener("input", (event) => {
    button.disabled = !event.target.value;
    });

-------
    const checkTaskNameOnValidation = (value) => {
        if (!value || value.includes('@')) {
            return false
        }
        return true
    }

    const createTaskBlock = document.querySelector('.create-task-block')
    const createTaskBlockInput = createTaskBlock.querySelector('.create-task-block__input');

    createTaskBlockInput.addEventListener('input', (event) => {
        const {target} = event
        const {value} = target
        const isValid = checkTaskNameOnValidation(value)
        const messageError = document.querySelector('.error-message-block');

        if (!isValid) {
            const newMessageBlock = document.createElement('span')
            newMessageBlock.className = 'error-message-block';
            newMessageBlock.textContent = 'Error. The task field cannot be empty or contain a dog symbol'
            createTaskBlock.append(newMessageBlock)
        } else if (isValid && messageError) {
            messageError.remove()
        } // Если поле notValid - создает errorBlock.
        // Если введено valid - удаляет errorBlock
    });

---------------------------------------------------------
/=/=/ Всплытие и погружение. Прекращение всплытия
---------------------------------------------------------
    const allElem = document.querySelectorAll('*');

    allElem.forEach(el =>{
        el.addEventListener('click', event => {
            if (event.currentTarget.tagName === 'FORM') {
                event.stopPropagation() // Прекращение всплытия 
            }

            console.log(el.tagName);
        }, ) // Всплытие

        // el.addEventListener('click', event => {
        //     console.log(el.tagName);
        // }, true) // Если true, отслеживаем стадию погружения
    })
---------------------------------------------------------
/=/=/ Обработчики событий. Делегирование событий
---------------------------------------------------------
Делегирование события заключается в том, что вместо добавления однотипных обработчиков события для каждого элемента, мы добавляем один обработчик для родительского элемента.
  Тк добавление множества однотипный обработчиков усугубляет производительность 

    const mainNav = document.querySelector('.main-navigation');

    mainNav.addEventListener('click', function (event) {
        const {target} = event
        const button = target.closest('.main-navigation__button-item')
        if (button) {
            button.style.color = 'red'
            setTimeout(() => {
                button.style.color = 'white'
            }, 1000)
        }
    });
Делегирование событий возможно благодаря технологии распространения событий, которую мы рассмотрели ранее.
-------
    table.onclick = function(event) {
    let td = event.target.closest('td'); // (1)

    if (!td) return; // (2)

    if (!table.contains(td)) return; // (3)

    highlight(td); // (4)
    };

(1) Метод elem.closest(selector) возвращает ближайшего предка, соответствующего селектору. В данном случае нам нужен <td>, находящийся выше по дереву от исходного элемента.
(2) Если event.target не содержится внутри элемента <td>, то вызов вернёт null, и ничего не произойдёт.
(3) Если таблицы вложенные, event.target может содержать элемент <td>, находящийся вне текущей таблицы. В таких случаях мы должны проверить, действительно ли это <td> нашей таблицы.
(4) И если это так, то подсвечиваем его.

(1-2) Пояснение elem.closest(selector). Когда мы кликаем на элемент к которому назначен поиск по родству, мы проверяем принадлежит ли он данной группе элементов, так же он может возвращать сам себя. Так мы устанавливаем что это нужный нам элемент

---------------------------------------------------------
/=/=/=/ Async/await - асинхронные функции
---------------------------------------------------------
// async - делает функцию асинхронной.
---------
И async function() всегда возвращает промис. Значения других типов оборачиваются в завершившийся успешно промис автоматически.

	async function f() {
	    return 1;
	}

	f().then(alert); // 1

Можно и явно вернуть промис, результат будет одинаковым:

	async function f() {
	    return Promise.resolve(1);
	}

	f().then(alert); // 1

---------
// await - ожидание готовности результата promise
---------
Синтаксис:
	let value = await promise;

Ключевое слово await заставит интерпретатор JavaScript ждать до тех пор, пока промис справа от await не выполнится. После чего оно вернёт его результат, и выполнение кода продолжится.

Ключевое слово – await работает только внутри async–функций

В этом примере промис успешно выполнится через 1 секунду:

	async function f() {
		let promise = new Promise((resolve, reject) => {
			setTimeout(() => resolve("готово!"), 1000)
		});

		let result = await promise; // будет ждать, пока промис не выполнится 
		alert(result); // "готово!"
	}
	f();

---------
// await нельзя использовать в обычных функциях
---------
	function f() {
	let promise = Promise.resolve(1);
	let result = await promise; // SyntaxError
	}

Ошибки не будет, если мы укажем ключевое слово async перед объявлением функции. Как было сказано раньше, await можно использовать только внутри async–функций.
---------
// await нельзя использовать на верхнем уровне вложенности 
	(вне тела функции)
---------
Можно обернуть этот код в анонимную async–функцию, тогда всё заработает:
	(async () => {
		let response = await fetch('/article/promise-chaining/user.json');
		let user = await response.json();
		...
	})();
---------------------------------------------------------
/=/=/=/ Асинхронность (Promise + Fetch)
---------------------------------------------------------
/=/=/ Объект Promise - уведомляет запрашивающие части о результате выполненного кода. 
    Сервер <---Гонец с результатами---> Запрашивающий код
-------------------
Promise (по англ. promise - обещать) – это специальный объект в JavaScript, который связывает «создающий» и «потребляющий» коды вместе. В терминах нашей аналогии – это «подписка на уведомления от автора». «Создающий» код может выполняться сколько потребуется, чтобы получить результат, а промис делает результат доступным для кода, который подписан на него, когда результат готов.

Синтаксис Promise:
	let promise = new Promise(function(resolve, reject) {
	// функция-исполнитель (executor) - // "певец"
	});
	
Функция, переданная в конструкцию new Promise, называется исполнитель (executor). Когда Promise создаётся, она запускается автоматически. Она должна содержать «создающий» код, который когда-нибудь создаст результат. В терминах нашей аналогии: исполнитель – это «певец».

Когда код получает результат, сейчас или позже – не важно, он должен вызвать один из этих колбэков:
   resolve(value) — если работа завершилась успешно, value – результат.
   reject(error) — если произошла ошибка, error – объект ошибки.

Итак, исполнитель запускается автоматически, он должен выполнить работу, а затем вызвать resolve или reject.

У объекта promise, возвращаемого конструктором new Promise, есть внутренние свойства:

   state («состояние»): 
	0) Вначале "pending" («ожидание»)
		1) Затем, в случае успеха вызывается: "resolve". И статус меняется на "fulfilled" («выполнено успешно»).
		2) В случае неудачи вызывается "reject". И статус меняется на "rejected" («выполнено с ошибкой»)
	
Три статуса Promise:
	pending - ожидание
	fulfilled - удачное выполнение promise
	rejected - выполнение promise с ошибкой

	result («результат»):
	0) Вначале "undefined":
		1) Далее изменяется на value при вызове resolve(value) 
		2) Или изменяется на error при вызове reject(error) 

-------------------
// Вызвано может быть что-то одно: 
	 либо результат(resolve)
	 либо ошибка(reject)
-------------------
Исполнитель должен вызвать что-то одно: resolve или reject. Состояние промиса может быть изменено только один раз.
Все последующие вызовы resolve и reject будут проигнорированы:

	let promise = new Promise(function(resolve, reject) {
		resolve("done");
		reject(new Error("…")); // игнорируется
		setTimeout(() => resolve("…")); // игнорируется
	});
Идея в том, что задача, выполняемая исполнителем, может иметь только один итог: результат или ошибку.

Также заметим, что функция resolve/reject ожидает только один аргумент (или ни одного). Все дополнительные аргументы будут проигнорированы.
---------
// Вызывайте "reject" с объектом new Error("…")
---------
В случае, если что-то пошло не так, мы должны вызвать reject. Это можно сделать с аргументом любого типа (как и resolve), но рекомендуется использовать объект Error

-------------------
/=/=/ Потребители: then, catch
-------------------
Объект Promise служит связующим звеном между исполнителем («создающим» кодом или «певцом») и функциями-потребителями («фанатами»), которые получат либо результат, либо ошибку. Функции-потребители могут быть зарегистрированы (подписаны) с помощью методов .then и .catch
---------
// .then( fResult(){}, fError(){} ) - наиболее важный метод
---------
Синтаксис:
	promise.then(
		function(result) { /* обработает успешное выполнение */ },
		function(error) { /* обработает ошибку */ }
	);

1) Первый аргумент метода .then – функция, которая выполняется, когда промис переходит в состояние «выполнен успешно», и получает результат.
2) Второй аргумент .then – функция, которая выполняется, когда промис переходит в состояние «выполнен с ошибкой», и получает ошибку.

Если мы хотели бы только обработать ошибку, то можно использовать null в качестве первого аргумента: 
	.then(null, errorHandlingFunction => {new Error('Error message')})

---------
	const variable = true

	let promise = new Promise(function(resolve, reject) {
		if (variable) {
			setTimeout(() => resolve("done!"), 1000);
		} else {
			setTimeout(() => reject(new Error("Whoops!")), 1000);
		}
	});

	promise.then(
		result => alert(result), // выведет "done!" через одну секунду
		error => alert(error) // не будет запущена
	);  // resolve запустит первую функцию, переданную в .then
 
---------
// .catch(fError) – это сокращённый вариант .then(null, f)
---------
Если мы хотели бы только обработать ошибку, то можно использовать null в качестве первого аргумента: .then(null, errorHandlingFunction). 
Или можно воспользоваться методом .catch(errorHandlingFunction), который сделает то же самое:

	let promise = new Promise((resolve, reject) => {
	setTimeout(() => reject(new Error("Ошибка!")), 1000);
	});

	// .catch(f) это то же самое, что promise.then(null, f)
	promise.catch(alert); // выведет "Error: Ошибка!" спустя одну секунду

---------
// .finally() – выполнится в любом случае, когда промис завершится: успешно или с ошибкой.
---------
Идея finally состоит в том, чтобы настроить обработчик для выполнения очистки/доведения после завершения предыдущих операций.
 Например, остановка индикаторов загрузки, закрытие больше не нужных соединений и т.д.

	new Promise((resolve, reject) => {
		/* сделать что-то, что займёт время, и после вызвать resolve или может reject */
	})
		.finally(() => остановить индикатор загрузки)
		  // выполнится, когда промис завершится, независимо от того, успешно или нет

		.then(result => показать результат, err => показать ошибку)
		  // таким образом, индикатор загрузки всегда останавливается, прежде чем мы продолжим

Есть важные различия:
 1) Обработчик, вызываемый из finally, не имеет аргументов.
 2) Обработчик finally «пропускает» результат или ошибку дальше, к последующим обработчикам.
 
Например, здесь результат проходит через finally к then:

	new Promise((resolve, reject) => {
		setTimeout(() => resolve("value"), 2000);
	})
		.finally(() => alert("Промис завершён")) // срабатывает первым
		.then(result => alert(result)); // <-- .then показывает "value"

 3) Если обработчик finally возвращает что-то, это игнорируется.
	Когда finally выдает ошибку, выполнение переходит к ближайшему обработчику ошибок.

---------
Чтобы получить данные которые мы передавали в resolve, reject, необходимо обработать наш promise с помощью: then / catch / finally

	const promise = new Promise ((resolve, reject) => {
		if (developer.isJSDev) {
			setTimeout(() => {
				resolve(`${developer.name} - JS developer`);
			}, 3000)
		} else {
			reject(`${developer.name} - Not a JS developer`);
		}
	})
	console.log(promise);

	promise
		.then((successMessage) =>{ 
			// Обрабатывает успешное выполнение promise
			console.log(successMessage);
		})
		.catch((error) => { 
			// Принимает в себя ошибку от и позволяет двигаться коду дальше 
			console.log(error);
		})
		.finally(() => { 
			// Вызовется, когда promise будет выполнен (вне зависимости успешно или с ошибкой)
			console.log(`finally message`);
		})
-------
	promise
		.then((result) => {
			console.log(result); // Всё хорошо, можно ехать!
		})
		.catch((error) => {
			console.log(error);  // Нужно заправиться
		});
Более которая форма записи 
	promise
		.then(console.log)   // Всё хорошо, можно ехать!
		.catch(console.log); // Нужно заправиться
---------------------------------------------------------
/=/=/=/ fetch() - функция для получение данных с сервера по URL
---------------------------------------------------------
Метод fetch() позволяет получать данные по сети асинхронно (то есть он возвращает объект Promise).

Cинтаксис:
	let promise = fetch(url, [options])
		`url` – URL для отправки запроса.
		`options` – дополнительные параметры: метод, заголовки и так далее.

Без `options` это простой GET-запрос, скачивающий содержимое по адресу `url`.

	const createTodoElement = (text) => {
		const todoElem = document.createElement('li');
		const todoElemAnchor = document.createElement('a');
		todoElemAnchor.href = '#'
		todoElemAnchor.textContent = text;
		todoElem.append(todoElemAnchor)

		return todoElem
	}
	const toggleLoader = () => {
		const loaderHTML = document.querySelector('#loader');
		const isHidden = loaderHTML.hasAttribute('hidden')
		if (isHidden) {
			loaderHTML.removeAttribute('hidden')
		} else {
			loaderHTML.setAttribute('hidden', '')
		}
	}

	const dataContainer = document.querySelector('#data-container');

	const getAllTodoes = () => {
		toggleLoader();
		fetch('https://jsonplaceholder.typicode.com/todos', {
		method: 'GET', // GET, POST, DELETE..
	})
		.then((responseValue) => {
			if (!responseValue.ok) { 
				// ok - произошел ли запрос успешно 
				throw new Error('Ошибка запроса'); 
				// throw - выбрасывает ошибку и переводит в блок .catch()
			}
			return responseValue.json(); 
			// декодирование запроса
		})
		.then((todoes) => { 
			// передаем дальше декодированный запрос
			todoes.forEach((el, i, arr) => {
				const todoHTML = createTodoElement(el.title);
				dataContainer.append(todoHTML);
			});
		})
		.catch((error) => {
			console.log('error:', error);
		})
		.finally(() => {
			toggleLoader();
		})
	};
	getAllTodoes()

-------------------
/=/=/ Замена `then` на `await try/catch`
---------
->> then

	fetch("https://api.github.com/users")
		.then((response) => {
			if (!response.ok) {
				throw new Error("Ошибка запроса");
			}
		return response.json();
		})
		.then((data) => {
			outputTable(data);
		})
		.catch((error) => {
			console.log(error);
		})
		.finally(() => {
			const loader = document.getElementById("loader");
			loader.style.display = "none";
		});

	function outputTable(users) {
		const table = document.createElement("table");
		for (const user of users) {
			const row = table.insertRow();

			const column1 = row.insertCell();
			column1.innerHTML = `<img class="avatar" src="${user.avatar_url}" />`;

			const column2 = row.insertCell();
			column2.innerHTML = `<a href="${user.html_url}">${user.login}</a>`;
		}
		document.body.append(table);
	}
---------
->> try/catch

    const url = `https://api.github.com/users`;

    async function fetchData() {
        try {
            const response = await fetch(url);
            const jsonData = await response.json();

            outputTable(jsonData);
        } catch (err) {
            console.error(err);
        } finally {
            const loader = document.getElementById("loader");
            loader.style.display = "none";
        }
    }
    fetchData()

---------------------------------------------------------
/=/=/=/ "try..catch" - обработка ошибок 
---------------------------------------------------------
Конструкция try..catch, позволяет «ловить» ошибки и вместо падения делать что-то более осмысленное. 

Синтаксис «try…catch»:

Конструкция try..catch состоит из двух основных блоков: try, и затем catch:
	try {
		// код...
	} catch (err) {
		// обработка ошибки
	}

1) Сначала выполняется код внутри блока try {...}.
2) Если в нём нет ошибок, то блок catch(err) игнорируется: выполнение доходит до конца try и потом далее, полностью пропуская catch.
3) Если же в нём возникает ошибка, то выполнение try прерывается, и поток управления переходит в начало catch(err). Переменная err (можно использовать любое имя) содержит объект ошибки с подробной информацией о произошедшем.

Пример с ошибками: выведет (1) и (3):
	try {
		alert('Начало блока try');  // (1) <--
		undefinedVariable; // ошибка, переменная не определена!
		alert('Конец блока try (никогда не выполнится)');  // (2)
	} catch(err) {
		alert(`Возникла ошибка!`); // (3) <--
	}

---------
/=/=/ try..catch работает синхронно
---------
Исключение, которое произойдёт в коде, запланированном «на будущее», например в setTimeout, try..catch не поймает:

	try {
		setTimeout(function() {
			noSuchVariable; // скрипт упадёт тут
		}, 1000);
	} catch (e) {
		alert( "не сработает" );
	}

Это потому, что функция выполняется позже, когда движок уже покинул конструкцию try..catch.

Чтобы поймать исключение внутри запланированной функции, try..catch должен находиться внутри самой этой функции:

	setTimeout(function() {
		try {
			noSuchVariable; // try..catch обрабатывает ошибку!
		} catch {
			alert( "ошибка поймана!" );
		}
	}, 1000);

---------
// throw - выбрасывает ошибку и переводит в блок .catch()

-------------------
/=/=/ try..catch с useEffect()
---------
  const [user, setUser] = useState();

  useEffect(() => {
    const fetchData = async () => {
      try {
        const resp = await axios.get(`/api/users/${userId}`);
        setUser(resp.data.user);
      } catch (error) {
        console.error(error);
      }
    };

    fetchData();
  }, [userId]);

---------------------------------------------------------
/=/=/=/ Promise.all() - метод для обработки нескольких Promise
---------------------------------------------------------
Метод Promise.all() позволяет дождаться выполнения нескольких промисов и получить результат в виде массива. 
Возвращает rejected - если есть хотя бы одна ошибка   

Каждый Promise - это Объект
Promise.all() возвращает новый промис, который завершается с массивом результатов из всех входных промисов. Если вы пытаетесь использовать метод `map` на этом объекте, то вы получите ошибку, так как `map` может использоваться только с массивами. 
То есть Promise.all() не может работать с `map` до тех пор, пока не выполнится полностью. А чтобы он выполнился необходим `await`

Чтобы исправить эту ошибку, вы должны дождаться завершения промиса (получив результат или ошибку) с помощью `await` или `.then()` и затем использовать метод `map` на результирующем массиве.

Так же `await` позволяет дождаться получения массива данных, а не его промиса.
Например здесь:
    const albums = await response.json() 
Если же писать без `await`, то данные тоже придут, но в виде необработанного промиса, а нам нужен готовый массив.

Синтаксис метода:
    const arrPromises = Promise.all([ promise1, promise2, /* и т.д. */ ]);

    Promise.all()[
    	new Promise(),
    	new Promise(),
    	new Promise()
    ]

Promise.all() возвращает:
    fulfilled - если все выполнены успешно 
    rejected - если есть хотя бы одна ошибка  

---------
    const TASKS_URL = 'https://jsonplaceholder.typicode.com/todos'
    const tasksIds = [1, 41, 20, 100, 50, 1]
    const dataContainer = document.querySelector('#data-container');

    const createTodoElement = (text) => {
        const todoElem = document.createElement('li');
        const todoElemAnchor = document.createElement('a');
        todoElemAnchor.href = '#';
        todoElemAnchor.textContent = text;
        todoElem.append(todoElemAnchor);

        return todoElem
    }

/=/ requests - Запросы
/=/ responses - Ответы

    const getTasksById = (ids) => {       
        /=/ requests - Массив Promise-ов, которые содержат необработанные запросы по выбранным id задач.
        const requests = ids.map((id) => fetch(`${TASKS_URL}/${id}`))

        /=/ Обрабатываем массив с из 6-ти Promise с помощью Promise.all().
        Promise.all(requests)
            /=/ Обрабатываем Promise.all
            .then((responses) => {
                /=/ Декодируем КАЖДЫЙ Promise и помещаем в новый массив.
                /=/ Тк можно считать что Promise.all - массив для промисов. А массив нужно перебрать, для применения к каждому el.
                dataResults = responses.map((response) => response.json()) 
                
                /=/ dataResults - массив декодированных Promise-ов, для работы с ним возвращаем массив в Promise.all().
                 /=/ Если не передать результат через "return", то следующий "then" не получит данных для обработки 
                return Promise.all(dataResults)	
            })
            .then((tasks) => {
                tasks.forEach(el => {
                    tasksHTML = createTodoElement(el.title)
                    dataContainer.append(tasksHTML)
                });
            })
            .catch((error) => {
                console.log(error);
            })
    }
    getTasksById(tasksIds)
---------------------------------------------------------
/=/=/=/ Promise.race() - возвращает результат самого быстрого промиса
---------------------------------------------------------
Promise.race() - как и Promise.all() принимает в себя массив промисов. Возвращает результат Promise-а (независимо resolve || reject) который выполнился первым 

Синтаксис метода:
    const promise = Promise.race([
        new Promise(),
        new Promise(),
        new Promise(),
    ])

    const promise1 = new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve('promise1')
        }, 500)
    })
    const promise2 = new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve('promise2')
        }, 2000)
    })
    const promise3 = new Promise((resolve, reject) => {
        setTimeout(() => {
            reject('promise3')
        }, 100)
    })

    Promise.race([promise1, promise2, promise3])
        .then((result) => {
            console.log('result', result);
        })
        .catch((error) => {
            console.log('error', error);
        })

---------------------------------------------------------
/=/=/=/ Асинхронность (async/await) рекомендуется вместо .then()
---------------------------------------------------------
/=/=/ Ключевое слово async
-------------------
Ключевое слово "async" позволяет удобным способом создавать асинхронные функции. Async перед функцией гарантирует, что эта функция вернёт промис

Два аналогичных примера:

    const sum = async () => {
    return 2 + 2;
    }

    function sum() {
        return new Promise((resolve, reject) => {
            resolve(2 + 2);
        });
    }

Поскольку асинхронная функция всегда возвращает промис, для обработки результата используется конструкция then:

    sum().then(result => {
        console.log(result); // Выведет 4
    })

-------------------
/=/=/ Ключевое слово await
-------------------
Ключевое слово await используется, чтобы дождаться выполнения асинхронной операции справа от await и вернуть его результат:

    const result = await promise;

Например, в следующем примере с помощью await мы ждем результат промиса и выводим его в консоль:

    async function test() {
        const promise = new Promise(resolve => {
            setTimeout(() => resolve("Успех"), 1000);
        });
        const result = await promise;
        console.log(result);
    }
    test(); // "Успех"
Аналогичный результат можно получить и с помощью Promise.then(), однако await позволяет получить результат промиса более компактным и наглядным способом.

-------------------
/=/=/ Обработка ошибок
-------------------
Обработать ошибки внутри async функций можно двумя способами:
    * С помощью блоков try/catch внутри самой функции.
    * С помощью метода Promise.catch() на верхнем уровне при обработке результата функции.

    async function getData() {
        try {
            const result = await promise;
            return result;
        } 
        catch(error) {
            console.error("Ошибка! " + error);
        }
    }
---------
    async function getData() {
        const result = await promise;
        return result;
    }

    getData()
        .then(result => {
            // Обработка результата
        })
        .catch(error => {
            console.error("Ошибка! " + error);
    });

---------
    <!DOCTYPE html>
    <html>
        <head>
            <title>Пример async/await</title>
        </head>
        <body>
            <span id="loader">Загрузка...</span>
            <h1 id="header"></h1>
            <img id="image">
            <script src="index.js"></script>
        </script>
        </body>
    </html>

    function getRandomArrayElement(array) {
        const randomIndex = Math.floor(Math.random() * array.length);
        return array[randomIndex];
    }

    async function getCat() {
        // Получаем список тегов
        const tagsResponse = await fetch("https://cataas.com/api/tags");
        const tags = await tagsResponse.json();

        // Выбираем случайный тег
        const randomTag = getRandomArrayElement(tags);

        // Получаем котиков по тегу
        const catsResponse = await fetch(
            `https://cataas.com/api/cats?tags=${randomTag}`
        );
        const cats = await catsResponse.json();

        // Выбираем случайного котика
        const randomCat = getRandomArrayElement(cats);

        // Формируем результат
        return {
            tag: randomTag,
            url: `https://cataas.com/cat/${randomCat.id}`
        };
    }

    getCat()
        .then((result) => {
            // Выводим заголовок
            const header = document.getElementById("header");
            header.textContent = result.tag;

            // Выводим картинку
            const image = document.getElementById("image");
            image.src = result.url;
        })
        .catch(console.error)
        .finally(() => {
            // Скрываем статус загрузки
            const loader = document.getElementById("loader");
            loader.style.display = "none";
        });
Вообще, совмещение двух подходов — это нормально и зачастую они используются вместе.

---------
    const getTodosWithUserData = async () => {
        try {
            const response = await fetch(USERS_URL) 
             /=/ Функция не пойдет дальше пока код не выполниться 
            if (!response.ok) {
                throw new Error('Ошибка запроса пользователя')
            }
            const users = await response.json()
            const firstUserId = users[0]?.id; 
             /=/ Это синхронный вызов, await не нужен
            const todosResponse = await fetch(`${TODOS_URL}?userId=${firstUserId}`)
            if (!todosResponse.ok) {
                throw new Error('Ошибка запроса задач')
            }
            const todos = await todosResponse.json()
            console.log('todos:', todos);
        } catch (error) {
            console.log(error);
        } finally {
            console.log("finally");
        }
    };

    getTodosWithUserData()
---------------------------------------------------------
/=/=/=/ Вызвать функцию с помощью Объекта 
---------------------------------------------------------
    const calculateTotalMortgage = 
    (percent, contribution, amount, countMonth) => {
        console.log(percent+contribution+amount+countMonth);
    }

    const calculatorArguments = [    
        [10, 0, 50000, 12],
        [10, 1000, 50000, 12],
        [10, 0, 20000, 24],
        [10, 1000, 20000, 24],
        [10, 20000, 20000, 24],
        [10, 0, 10000, 36],
        [15, 0, 10000, 36]
    ]

    calculatorArguments.forEach(el => {
        let obj = {};
        el.forEach((val, i) => {
            obj[`arg${i}`] = val;
        });
        calculateTotalMortgage(obj.arg0, obj.arg1, obj.arg2, obj.arg3);
    });
---------------------------------------------------------
/=/=/=/ isNaN() - Аналог typeof, но с попыткой преобразования значения. Выводит так же true/false
---------------------------------------------------------
!!! Не используй в сравнении x === NaN. Нифига не получиться. 
Используй для этого isNaN()

    console.log(NaN === NaN); // false
    console.log(isNaN(NaN)); // true

Метод isNaN пытается преобразовать в число переданный параметр. Если параметр не может быть преобразован, возвращает true, иначе возвращает false.
Эта функция полезна, так как значение NaN не может быть проверено операторами эквивалентности.

То есть, если значение not a number, то выдает true, иначе false.
Пример

isNaN(NaN);       // true
isNaN(undefined); // true
isNaN({});        // true

isNaN(true);      // false
isNaN(null);      // false
isNaN(37);        // false

// strings
isNaN("37");      // false: "37" преобразуется в число 37 которое не NaN
isNaN("37.37");   // false: "37.37" преобразуется в число 37.37 которое не NaN
isNaN("");        // false: пустая строка преобразуется в 0 которое не NaN
isNaN(" ");       // false: строка с пробелом преобразуется в 0 которое не NaN
isNaN("37,5");    // true

// Даты
isNaN(new Date());                // false
isNaN(new Date().toString());     // true

// Пример почему использование isNaN не всегда уместно
isNaN("blabla")   // true: "blabla" преобразовано в число.
    
---------------------------------------------------------
/=/=/=/ Как сократить количество параметров функции?
---------------------------------------------------------
Можно использовать объект в качестве аргумента. 
Вместо передачи нескольких переменных в функцию можно передать один объект, содержащий все необходимые параметры.

    const calculateTotalMortgage = (params) => {
        const percent = params.percent;
        const contribution = params.contribution;
        const amount = params.amount;
        const countMonth = params.countMonth;
        // далее идет основной код функции
    }
---------
    const calculateTotalMortgage = (params) => {
        const percent = params.arg0
        const contribution = params.arg1
        const amount = params.arg2
        const countMonth = params.arg3

        console.log( percent+contribution+amount+countMonth );
    }

    const mortgageValues = [    
        [10, 0, 50000, 12],
        [10, 1000, 50000, 12],
        [10, 0, 20000, 24],
        [10, 1000, 20000, 24],
        [10, 20000, 20000, 24],
        [10, 0, 10000, 36],
        [15, 0, 10000, 36]
    ]

    mortgageValues.forEach(el => {
        let obj = {};
        el.forEach((val, i) => {
            obj[`arg${i}`] = val;
        });
        calculateTotalMortgage(obj);
    });
---------------------------------------------------------
/=/=/=/ Callback-hell - Ад коллбеков
---------------------------------------------------------
Используя коллбэки по-крупному, мы рискуем получить так называемый “ад коллбэков”.

Наглядно это выглядит так:
    setTimeout(() => {
    setTimeout(() => {
        setTimeout(() => {
        setTimeout(() => {
            console.log('Hello World!')
        }, 1000)
        }, 1000)
    }, 1000)
    }, 1000)

Таким образом, наш код растет вправо. Решить такую проблему можно с помощью Promise.

    const FIRST_TODO_URL = 
    'https://jsonplaceholder.typicode.com/todos/1';

    const getTodo = (callback) => {
        fetch(FIRST_TODO_URL)
            .then((response) => response.json())
            .then((todo) => {
                // console.log(todo)
                callback(todo)
            })
            .catch((error) => {
                console.log(error)
            })
    }
    getTodo((todoItem) => {
        console.log(todo)
    })

---------------------------------------------------------
/=/=/=/ Event Loop - цикл событий: 
     Callback Stack, Microtask Queue, Callback Queue
---------------------------------------------------------
1) Callback Stack - первый пришел — последний ушел (стакан)
2) Microtask Queue - первый пришел — первый ушел (очередь)
3) Callback Queue - первый пришел — первый ушел (очередь)

Event Loop как прошелся по всему Callback Stack и достиг последней строчки идет смотреть Callback Queue.
Если он обнаруживает там элемент, то он закидывает его в Callback Stack

---------
/=/=/ Web API - сущности которы предоставляет нам Браузер.
---------
setInterval, setInterval - на самом деле нет в JS, это Web API браузера

---------
/=/=/ Microtask Queue (микрозадачи) - это код в then, catch, finally
---------
Существуют мАкрозадачи и мИкрозадачи.

Более приоритетная очередь чем Callback Queue - это Microtask Queue (очередь микрозадач)

Приоритет:
1) мАкрозадачи - Основной вектор движения выполнения кода от первой строчки к последней.
   // После того как движок достиг последней сточки, выполнив все main-задачи, идет смотреть:
2) мИкрозадачи - все что есть в очереди мИкрозадач
   // Если в микрозадачах что-то есть, то добавляет в Callback Stack и выполняет. Если нет или закончились, то проверяет:
3) Callback Queue - все что есть в очереди Callback Queue
   // Если там есть задачи, то так же удаляет ее из очереди, добавляет в Callback Stack, вызывает и удаляет как отработанную 

   // Как только появляется новая мАкрозадача, цикл повторяется 
---------
    console.log('start macrotask');
    console.log('performing macrotask...');

    setTimeout(() => { // Callback queue
        console.log('timeouted');
    }, 0);

    const promise = new Promise((resolve) => {
        // Этот текст выведется при вызове then
        resolve('result from promise');
    });

    promise.then((result) => { // Microtask queue
        console.log(result);
    })

    console.log('end macrotask');

    // Вывод:
    // start macrotask
    // performing macrotask...
    // end macrotask
    // result from promise
    // timeouted

    * В данном примере движок JavaScript сначала начинает главную макрозадачу – обычное синхронное выполнение скрипта.
    * Дойдя до setTimeout(), он отправит её на обработку в Web API. Затем, когда обработка завершится, переданный callback будет отправлен в Callback queue.
    * Дойдя до промиса, он его обработает, выполнит, а затем callback из then() поместит в Microtask queue.
    * Затем закончит выполнение первой макрозадачи.
    * Затем движок проверит очередь микрозадач и выполнит их по очереди, если таковые имеются. В данном случае вызовет callback из then().
    * После микрозадачи он перейдет к выполнению оставшейся макрозадачи из очереди задач. В данном случае вызовет callback из setTimeout().

---------
    setTimeout(() => {
        console.log("№4 setTimeout"); // Вызывается в callback очереди
    }, 0);

    const promise = new Promise((resolve) => {
        console.log("№1 Promise"); // Вызывается в main очереди
        resolve();
    });

    promise.then(() => {
        console.log("№3 Promise resolve"); // Вызывается в micro очереди
    });

    console.log("№2 End"); // Вызывается в main очереди

    // №1 Promise
    // №2 End
    // №3 Promise resolve
    // №4 setTimeout

---------
function runCode() {
    console.log("№1 before promise");

    return new Promise((resolve) => { // Обещает вернуть ответ когда код выполнится
        setTimeout(() => { // setTimeout переходит в буфер ожидания Callback Queue, после setTimeout(console.log("Zero"))
        // Далее код идет выполнять main-задачи, в частности console.log("One"). Как только main-задачи закончились, движок проверяет какие задачи готовы к выполнению (чьи таймеры закончились). 
        // Первым в очереди Callback Queue стоял clg("Zero") и тк время ожидания таймеров у нас одинаково, то он сохраняет свою очередь и идет первым к исполнению. Оболочка таймера раскрывается и clg("Zero") попадает в Стакан Вызовов, где и реализуется, отображая в консоли "Zero"
        // Далее в очереди стоял данный промисовский setTimeout(). Тк его таймер так же равен первому, но пришел он в очередь вторым, то и выполняется он вторым, после "Zero", то есть сейчас. 
        // Оболочка таймера так же раскрывается и первым движок видит console.log("№ Zero Promise"), после чего помещает его в Стакан Вызовов, где тот и исполняется, выводя сообщение "Zero Promise".
            console.log("№4 Zero Promise"); 
            resolve(); // После, в раскрытом таймере видит resolve(). Видит что это Microtask и переводит его в очередь Microtask Queue. Тк микротасков нет, эта задача становится там первой и от туда сразу же перемещается в Стакан Вызовов, где и исполняется с помощью обработчика .then(), выводя в консоль сообщение "Zero Promise Invoked"
        }, 0);
    });
}

    setTimeout(() => {
        console.log("№3 Zero");
    }, 0);

    runCode()
        .then(() => console.log("№5 Zero Promise Invoked"));

    console.log("№2 One");
    // Zero

---------------------------------------------------------
/=/=/=/ Webpack, Rollup
---------------------------------------------------------
"./" - корневая папка файла, то где файл лежит
"../" - выйти из текущей паки на уровень выше

Особенности Rollup:
---------
// Tree shaking:
Rollup имеет интересную возможность, которая называется Tree Shaking. При сборке весь неиспользуемый код исключается, чтобы сократить размер выходного файла.

Например если мы убрали вызов функции, он уберет всю неактивную функцию.

-------------------
0.0.0) Install & add LTS репозиторий Node.js в систему.
   $ curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -

Установить конкретную версию (тут указана 10)
   $ curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -

-------------------
/=/=/ n - это утилита для управления установленными версиями Node.js.
---------
Она позволяет легко установить, удалить и переключаться между разными версиями Node.js, а также позволяет управлять глобальными пакетами Node.js.

    $ sudo npm install -g n

Установите необходимую версию Node.js с помощью утилиты n:
    $ sudo n 10

Показать все доступные LTS версии Node.js
    $ n --lts

---------------------------------------------------------
/=/=/ Установка проекта через Npm 
-------------------
0.1) Установить/обновить ласт версию
    $ sudo npm install -g npm

1.0) Инициализировать package.json
    $ npm init -y

1.1) Чтобы установить все пакеты которые уже прописаны package.json 
    $ npm i

1.2) Инициализируем проект перед началом работы:
    $ npm init -y

Создастся package.json. 
Это файл конфигурации проекта, который применяется npm для управления настройками проекта и пакетами приложения. 

2) Установка сборщика Rollup:
    $ sudo npm install --global rollup

3) Создадим файл конфигурации Rollup rollup.config.js:
    export default {
        input: './index.js',
        output: {
            file: './build/bundle.js',
            format: 'cjs'
        }
    };

4) Сборка/Пересборка проекта
    $ rollup -c --bundleConfigAsCjs

1.2) Или вместо пункта 2) 3) выполнить:
    $ rollup ./index.js --file ./build/bundle.js --format cjs

---------
Установка дополнительных пакетов для сборки Rollup:

1) Babel - конвертирует новый синтаксис JavaScript в старый. 
@rollup/plugin-babel 
    $ npm install -D @rollup/plugin-babel @babel/preset-env

После установки откроем файл package.json и убедимся, что в него добавилась секция devDependencies со списком установленных пакетов:
    {
        "name": "code",
        "version": "1.0.0",
        "description": "",
        "main": "index.js",
        "scripts": {},
        "keywords": [],
        "author": "",
        "license": "ISC",
        "devDependencies": {
            "@rollup/plugin-babel": "^5.3.1",
            "@babel/preset-env": "^7.18.10"
        }
    }

Чтобы Rollup использовал Babel при сборке, нужно также внести изменения в конфиг rollup.config.js:

    import { babel } from '@rollup/plugin-babel';

    export default {
        input: './index.js',
        output: {
            file: './build/bundle.js',
            format: 'cjs'
        },
        plugins: [
            babel({
            babelHelpers: "bundled",
            presets: ["@babel/env"]
            }),
        ]
    };
Для проверки работы плагина добавим в наш index.js файл какой-нибудь код, которого не было в более ранних версиях языка. Например, используем стрелочную функцию в методе map():
    const array = [1, 2, 3].map(n => n + 1);
    console.log(array);
    
---------
2) Плагин для работы со стилями:
rollup-plugin-styles
    $ npm install -D rollup-plugin-styles

Затем добавим информацию о плагине в конфиг Rollup rollup.config.js. 

    import styles from "rollup-plugin-styles";
    styles()

После добавления плагина мы можем импортировать CSS-файлы в коде. 
То есть вместо добавления ссылки в HTML-документе, как мы делали ранее, в начале скрипта index.js добавим инструкцию import и название CSS-файла:

!!!   import "../index.css";

    function hello() {
        console.log("Hello world!");
    }
    hello();

---------
3) Плагин для работы с картинками:
@rollup/plugin-image
    $ npm install @rollup/plugin-image --save-dev

Далее обновим конфиг rollup.config.js, добавим в него:

    import image from "@rollup/plugin-image"; 
    image() 

Для тестирования возьмём любую картинку и положим её в папку assets нашего проекта. Далее в index.js напишем код добавления картинки на страницу. Он включает инструкцию import с путём до нашей картинки, а также добавление элемента img на страницу:

    import "./index.css";
    import MY_IMAGE from './assets/image.png';

    // Остальной код

    const img = document.createElement("img");
    img.src = MY_IMAGE;
    document.body.append(img);

Если после сборки открыть выходной файл build/bundle.js, то можно обратить внимание, что наша картинка представлена в коде в виде base64-строки. Такой подход хорошо работает для маленьких картинок, но для больших лучше использовать обычный подход с указанием ссылки на картинку (без импорта).

---------
4) Локальный сервер
rollup-plugin-serve
    $ npm install -D rollup-plugin-serve 

Обновим конфиг rollup.config.js, добавив в него:

    import serve from 'rollup-plugin-serve' 
    serve({
          open: true, 
            // Авт-ки открывает стр в браузере при запуске проекта
          contentBase: './', 
            // Директория откуда будут браться файлы 
          port: 8000,
        }),

        Функция serve() принимает объект с параметрами, которые описаны в документации. Пока оставим все параметры по умолчанию, изменим только параметр open на true, чтобы при сборке наша страницу сразу открывалась в браузере.

Запустим сборку проекта с помощью команды rollup -c и убедимся, что наша страница открывается в браузере по адресу http://localhost:10001/ (если мы не указали другой порт в настройках плагина).

---------
5) Автоматическое применение изменений
rollup-plugin-livereload
    $ npm install -D rollup-plugin-livereload

Обновим конфиг rollup.config.js, добавив в него:

    import livereload from 'rollup-plugin-livereload' 
    livereload() 

Для отслеживания изменений в исходном коде запустим сборку с дополнительным флагом -w (watch). При необходимости перед этим отключим локальный сервер с помощью сочетания клавиш Ctrl+C, чтобы иметь возможность ввести команду в терминале:
    $ rollup -c -w --bundleConfigAsCjs
    
    // npm run dev
    // npm run prod

---------------------------------------------------------
/=/=/=/ Yarn и Vite 
---------------------------------------------------------
Yarn - это менеджер пакетов, а Vite - это быстрый сборщик проектов.

    $ sudo npm install --global yarn - установка глобально на ОС
    $ sudo npm install -g 

    $ yarn outdated - выведет список устаревших пакетов и их текущие версии
    $ yarn upgrade имя_пакета - обновит все пакеты/пакет
    
-------------------
/=/ Установить большинство необходимых зависимостей:
---------
    $ yarn add bootstrap react-bootstrap @popperjs/core lodash eslint react-select yup query-string nanoid prop-types react-router-dom@5.3.0 -D miragejs @faker-js/faker

    $ yarn add tailwindcss postcss autoprefixer cssnano
    $ yarn remove tailwindcss postcss autoprefixer cssnano

    $ eslint --init 
---------
/=/=/ Шаг 1 — Создание проекта Vite
---------
Запуск нового проекта с Vite
    $ yarn create vite
---------
Установка зависимостей проекта:
    $ yarn
---------
/=/=/ Шаг 2 — Запуск сервера разработки
---------
    $ yarn run dev
// OR
    $ vite dev

-------------------
/=/=/ Bootstrap в React + Vite:
-------------------
// Установка Bootstrap и Popper: 

    $ yarn add bootstrap // обычный бутстрап
    $ yarn add react-bootstrap // библиотека основанная на бутстрап
    $ yarn add @popperjs/core

    $ yarn add bootswatch
// OR
    $ npm i --save bootstrap @popperjs/core 

Popper - это библиотека, используемая Bootstrap для позиционирования всплывающих окон, выпадающих списков и других элементов интерфейса на веб-странице.

yarn add react-bootstrap устанавливает не только CSS-стили и JavaScript-компоненты Bootstrap, но и React-компоненты, которые интегрированы с React-кодом и могут быть использованы в вашем проекте. React-компоненты react-bootstrap представляют собой обёртки над компонентами Bootstrap, которые позволяют использовать их в React приложениях.
-------------------
/=/=/ react-bootstrap 
---------
    import React from "react";
    import { Container, Row, Col, Button } from "react-bootstrap";

    const Page404 = () => {
      return (
        <Container className="mt-5">
          <Row>
            <Col>
              <h1 className="text-center">404 - Page not found</h1>
              <p className="text-center">
                Oops! The page you are looking for does not exist.
              </p>
              <div className="text-center">
                <Button href="/" variant="primary">
                  Return to homepage
                </Button>
              </div>
            </Col>
          </Row>
        </Container>
      );
    };

    export default Page404;

---------
// Установка доп зависимостей (Sass), позволяет настроить стили компонентов Bootstrap: 
->> Global
    $ npm install -g sass
---------
->> Project
    $ yarn add sass
    $ npm i --save-dev sass

---------
Импортируйте CSS Bootstrap в свой основной файл JavaScript:

    import 'bootstrap/dist/css/bootstrap.min.css' 

Файл import 'bootstrap/dist/css/bootstrap.min.css' следует поместить в файл, который будет подключаться к вашей HTML-странице.

-------------------
/=/=/ Скрипты для Popper и Bootstrap стилей
-------------------
Для работы кнопки с выпадающим меню, необходимо подключить два скрипта: jQuery и Popper.js. Вы можете скачать их с официальных сайтов или использовать CDN-ссылки.

    <!-- Подключение jQuery -->
    <script src="https://code.jquery.com/jquery-3.7.0.slim.min.js"></script>

    <!-- Подключение Popper.js -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/2.11.8/umd/popper.min.js"></script>

    <!-- Подключение скриптов Bootstrap -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.min.js"></script>


Поместите эти три скрипта перед закрывающим тегом </body> в вашем HTML-файле, и кнопка с выпадающим меню должна работать корректно.

-------------------
/=/=/ Добавление yarn как пакетный менеджер по умолчанию
-------------------
Чтобы внести настройку "npm.packageManager": "yarn" только для текущего проекта, нужно создать файл .npmrc в корне проекта и добавить в него следующую строку:

// .npmrc
    package-manager=yarn

Это установит менеджер пакетов Yarn для текущего проекта вместо NPM. Эта настройка не затронет другие проекты на вашей машине.

-------------------
/=/=/ Axios
-------------------
    $ yarn add axios
// OR
    $ npm install axios
    
---------------------------------------------------------
/=/=/=/ Array.from() - создаёт новый массив из итерируемого объекта. 
    Имеет в себе функцию map
---------------------------------------------------------
Синтаксис:
    Array.from(object, mapFn, thisArg)

object
    Массивоподобный или итерируемый объект, преобразуемый в массив.
mapFn 
    Отображающая функция, вызываемая для каждого элемента массива.
thisArg 
    Значение, используемое в качестве this при выполнении функции mapFn

---------
    Array.from({length: 5}, (_, i) => i + 1) // [ 1, 2, 3, 4, 5 ]
    Array.from({length: 5}, (_, i) => i ) // [ 0, 1, 2, 3, 4 ]

// i+n n - точка отсчета 
// Изменить шаг `i` можно через `map`

    const numbers = 
        Array.from({length: 10 - 1}, (_, i) => i + 1 * 2).map(x => x * 2);
---------
    const users = Array.from({ length: 10 }, (_, i) => ({
        name: `User ${i + 1}`,
        phone: `555-1234-${i}`,
        email: `user${i + 1}@example.com`
    }));

==/OR/==
    Array.from(Array(10))

Метод Array.from создает новый массив из переданного объекта. В случае, когда вы передаете ему объект Array, он создает новый массив, полностью скопировав элементы этого массива. Если вы передаете ему число (например, Array.from(Array(10))), он создает массив из 10 пустых элементов.

В случае с Array(10) метод Array создает новый массив из 10 пустых элементов. Однако, когда вы используете метод map для преобразования каждого элемента массива, он не будет выполняться, потому что каждый элемент массива является пустым.

==/OR/==
Создать цикл с шагом 2: Использовать цикл for и увеличивать счетчик на 2 в каждой итерации.

    for (let i = 0; i < 10; i += 2) {
        console.log(i);
    }

---------
  const calcNaturalNumbersBelowNum = (untilNum, ...multiples) => {
    return Array.from({length: untilNum - 1}, (_, i) => i + 1)
      .filter(num => multiples.some(multiple => num % multiple === 0));
  }
  // some() исп-ся как условие для фильтрации метода filter(), если true, то возвращает значение

Метод Array.from() создает новый экземпляр массива с неглубоким копированием из объекта. Первым аргументом метода Array.from() является итеративный объект, такой как массив, строка, набор или объект, подобный массиву (например, arguments или NodeList).
В этом конкретном примере код использует метод Array.from() для создания нового массива с длиной, равной значению переменной untilNum минус 1. Второй аргумент метода Array.from() - это функция сопоставления, которая используется для заполнения нового массива значениями. В этом случае функция сопоставления использует переменную i, которая передается функции в качестве второго аргумента, и добавляет к ней 1, поэтому новый массив будет заполнен последовательными числами, начинающимися с 1.
Символ подчеркивания "_" используется в качестве заполнителя для первого аргумента функции сопоставления, который в данном случае не нужен. Обычной практикой является использование подчеркивания в таких сценариях, чтобы указать, что аргумент не используется.

Метод Array.prototype.some() проверяет, проходит ли хотя бы один элемент в массиве проверку, реализованную предоставленной функцией. В этом случае предоставленная функция проверяет, делится ли текущий элемент (i + 1) на какое-либо из переданных кратных. Если это так, он вернет true для этого элемента, а some() вернет true для всего массива, указывая, что по крайней мере один элемент делится на переданные множители. Это позволяет нам отфильтровывать элементы, которые не делятся на переданные кратные, и оставлять только те, которые делятся хотя бы на одно из них.

---------------------------------------------------------
/=/=/=/ Webpack
---------------------------------------------------------
1) Инициализируем проект
    $ npm init -y

2) Установить Webpack
    $ npm install webpack webpack-cli --save-dev

3) Создаем webpack.config.js

    const path = require('path');

    module.exports = {
        mode: 'development', 
        entry: path.resolve(__dirname, 'src', 'index.js'),
        output: {
            filename: 'main.js',
            path: path.resolve(__dirname, 'dist'),
            clean: true,
        },
    };
// ./src/index.js (можно исп-ть и обычный способ пути)
// __dirname - корневая папка
// mode: 'development' - означает в разработке
// clean: true - папка сборки проекта будет очищаться при пересборке

---------
4) Устанавливаем HtmlWebpackPlugin
    $ npm install --save-dev html-webpack-plugin

Добавляем в начало webpack.config.js

    const HtmlWebpackPlugin = require('html-webpack-plugin')

И в module.exports = {}
    plugins: [
        new HtmlWebpackPlugin({
        template: path.resolve(__dirname, 'index.html'),
        })
    ]

---------
5) Устанавливаем babel-loader
    $ npm install -D babel-loader @babel/core @babel/preset-env webpack

Добавляем 
    module: {
        rules: [
        {
            test: /\.m?js$/,
            exclude: /node_modules/,
            use: {
            loader: 'babel-loader',
            options: {
                presets: [
                ['@babel/preset-env', { targets: "defaults" }]
                ],
                plugins: ['@babel/plugin-proposal-class-properties']
            }
            }
        }
        ]
    },

---------
6) Устанавливаем css-loader 
Guides --> Asset Management --> Loading CSS
    $ npm install --save-dev style-loader css-loader

Добавляем в rules
    {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader'],
    },

Импортируем style.css в index.css

---------
7) Устанавливаем css-loader 
Guides --> Asset Management --> Loading Images

Добавляем в rules
    {
        test: /\.(png|svg|jpg|jpeg|gif)$/i,
        type: 'asset/resource',
    },

Импортируем картинку в index.js
    import Image from './Image.png';

И там же добавляем ее в img.src
    imgName.src = KEKS;

---------
8) Сбилдить проект
    $ npm run start

package.json --> scripts

    "scripts": {
        "start": "webpack"
    },

---------
9) Установка webpack-dev-server 
    $ npm install --save-dev webpack webpack-dev-server

Guides --> Development --> Using webpack-dev-server

Добавляем в webpack.config.js перед plugins
    devServer: {
        static: './dist', // Путь к паке с готовым проектом
        port: 8080,
        open: true,
    },

---------
10) Запустить сервер 
package.json --> scripts

    "start": "webpack serve",

---------------------------------------------------------
/=/=/=/ Object.fromEntries(Object.entries(obj).reverse()) -
перевернуть Объект
-------------------

    let obj = {a: 1, b: 2, c: 3};
    let reversedObj = Object.fromEntries(Object.entries(obj).reverse());

    console.log(reversedObj); // Output: {c: 3, b: 2, a: 1}

/=/=/ Object.entries() - преобразовать Объект в Массив пар ключ-значение
---------
/=/=/ Object.fromEntries() - преобразовать Массив в Объект

    Для преобразования Массив должен иметь вид: 
    [ ["apples", 3], ["flour", 300], ["milk", 100], ["oil", 100] ];

-------------------
/=/=/ JSON.parse(JSON.stringify(obj)) - Глубокое копирование Объекта
---------
    const obj = {a: 1, b: {c: 2}};
    const copy = JSON.parse(JSON.stringify(obj));

---------------------------------------------------------
/=/=/ Метод чтобы перебрать Массив и Объект
-------------------
    const arrayLikeObject = {
        0: "a",
        1: "b",
        2: "c",
        length: 3
    };

    const trueArray = Array.prototype.slice.call(arrayLikeObject, 0);
    console.log(trueArray); // ["a", "b", "c"]

---------
// Или использовать цикл for
---------
// Или использовать цикл for in

    const myObj = {
    doctor: { _id: "67rdca3eeb7f6fgeed471818", name: "Доктор" },
    waiter: { _id: "67rdca3eeb7f6fgeed471820", name: "Официант" },
    physics: { _id: "67rdca3eeb7f6fgeed471814", name: "Физик" },
    engineer: { _id: "67rdca3eeb7f6fgeed471822", name: "Инженер" },
    actor: { _id: "67rdca3eeb7f6fgeed471824", name: "Актер" },
    cook: { _id: "67rdca3eeb7f6fgeed471829", name: "Повар" }
    };

    const myArr = [
    { _id: "67rdca3eeb7f6fgeed471818", name: "Доктор" },
    { _id: "67rdca3eeb7f6fgeed471820", name: "Официант" },
    { _id: "67rdca3eeb7f6fgeed471814", name: "Физик" },
    { _id: "67rdca3eeb7f6fgeed471822", name: "Инженер" },
    { _id: "67rdca3eeb7f6fgeed471824", name: "Актер" },
    { _id: "67rdca3eeb7f6fgeed471829", name: "Повар" }
    ];

    for (const el in myObj) {
        console.log(myObj[el]);
    }

---------------------------------------------------------
/=/=/=/ Использование import, export, export default
---------------------------------------------------------
/=/=/ Экспортировать: 
---------
    export class App {
      run() {
        document.body.textContent = 'Jello!'
      }
    }
// OR 
    class App {
      run() {
        document.body.textContent = 'Jello!'
      }
    }
    export {
        App,
    }
// OR 
    export const PI = 3.14;
    function sayHello() {}
    class Car {}

    export { PI, sayHello, Car };
---------
/=/=/ Импортировать:
---------
    import { PI, sayHello, Car } from "./module.js";

    console.log(PI);

    sayHello();

    const car = new Car("BWM X5", 2020);
    car.showInfo();
---------
    import './file.js';

Будет выполнен код из файла file.js, однако нельзя будет использовать элементы из этого файла.
---------
Импортировать в другой файл элемент файла: 
    import { App, Element2 } from './src/modules/app.js'

Переименовать передаваемый элемент с помощью 'as'
    import { App as AppComponent, Element2 } from './src/modules/app.js'
---------
К HTML-файлам ES-модули подключаются с помощью тегов <script>, как и обычные скрипты, добавляется только атрибут type="module":
    <script type="module" src="index.js"></script>
-------------------
/=/=/ export default - может быть только один в файле
-------------------

    export default function sum(a, b) {
        return a + b;
    }
// OR
    function sum(a, b) {
        return a + b;
    }

    export default sum;

Экспортировать таким способом можно только один элемент модуля. То есть модуль может содержать только одну инструкцию export default.
Для экспортированных таким способом элементов импорт делается без фигурных скобок:

    import Any_Name from "./module.js";
    const result = Any_Name(2, 3);

Экспорт по умолчанию можно также смешивать с обычным именованным экспортом:
    export const PI = 3.14;
    export default function sum(a, b) {
        return a + b;
    }
Импорт:
    import sum, { PI } from "./module.js";

-------------------
/=/=/ import * as - импортировать все экспорт-е сущности из файла
-------------------
Синтаксис:
    import * as MyModule from "./module.js";

    console.log(MyModule.PI);

    MyModule.sayHello();

    const car = new MyModule.Car("BWM X5", 2020);
    car.showInfo();

---------------------------------------------------------
/=/=/=/ LocalStorage
---------------------------------------------------------
LocalStorage - работает только со String

To use localStorage to remember that a button was pressed, you can use the following code:

    const button = document.querySelector('button');

    button.addEventListener('click', function() {
        localStorage.setItem('buttonClicked', 'true');
    });

    if (localStorage.getItem('buttonClicked') === 'true') {
        // button was pressed, do something
    }
---------
    const myNumber = 42;
    
    Записать el
    >- localStorage.setItem("users", JSON.stringify(users));

    Получить el
    >- localStorage.getItem('number') 
    >- JSON.parse(localStorage.getItem("users"))
    
    Удалить el
    >- localStorage.removeItem('number') 

    Очистить полностью storage
    >- localStorage.clear() 

---------
/=/=/ Работа с Объектами
---------
    const obj = {
        name: 'Max',
        age: 20,
    }
---------
// JSON.stringify(obj) - завернуть Объект в тип string
    person:"{"name":"Max","age":20}"
---------
// JSON.parse(raw) - преобразовать в нормальный Объект
    Object { name: "Max", age: 20 }
---------

    localStorage.setItem('person', obj); 
     // person:"[object Object]"

    localStorage.setItem('person', JSON.stringify(obj)) 
     // person:"{"name":"Max","age":20}"

    const raw = localStorage.getItem('person') // string
    console.log(raw.name); // undefined

    const person = JSON.parse(raw);
    console.log(person); 
     // Object { name: "Max", age: 20 }

    person.name = 'Vladilen'
    console.log(person); 
     // Object { name: "Vladilen", age: 20 }
-------------------
// Отличие localStorage от cookie
-------------------
localStorage больше по объему ~ 5MB
localStorage не уходит на сервер, в отличие от cookie
---------------------------------------------------------
/=/=/=/ Инициализация проекта через Git
---------------------------------------------------------
    $ git clone https://github.com/... - скачать репозиторий (находясь в папке)
    $ ls -a - выводит список файлов в папке + скрытые
    $ git config user.name 'your name'
-------------------
// Git fix

    git config pull.rebase false  # merge
    git config pull.rebase true   # rebase
    git config pull.ff only       # fast-forward only
------------------- 
!/=/=/ Отправка изменений
    $ git status - отображение статуса изменения файлов
   *$ git add . / $ git add [name1 name2 ...] - разрешает файлы для обработки их commit (промежуточная область - stage) 
   *$ git commit -m 'comment' - запись
    $ git log / $ git log --oneline - Отображение истории записи коммитов
   *$ git push [rep_link = origin] [branch_name] - Отправить на сервер
    // rep_link - можно узнать с помощью $ git remote -v или ввести origin
    // branch_name - $ git branch или ввести master (к какой ветке)
    $ git push origin master

/=/=/ Отмена изменений
    $ git reset name1 - удаление файла из буферной зоны для коммита
    $ git diff - история изменений файлов
    $ git reset --hard - откатывает все сделанные изменения во всех файлах (до прошлого коммита)

/=/=/ Файл .gitignore - хранит данные папок для игнорирования при добавлении в облако
---------
/=/=/ Ветки в Git
    $ git branch new_branch_name - создать ветку
    $ git checkout new_branch_name - переключение между ветками
      $ git push origin new_branch_name - опубликовать новую ветку и сохраненные в нее данные

    $ git branch -d branch_name - удалить ветку

// Перенос Ветки на Ветку
    На сайте вкладка pull requests --> Merge 
      В этой же вкладке можно добавить проверяющего "Reviewers"

// Перенос Изменений с облака
    $ git pull origin master - накатывает изменения из облака в локал 

// Слияние веток 
    $ git checkout master - переключение туда куда будем переносить
    $ git merge branch_name - переносит с указанной ветки на текущую
      $ git push origin branch_name - отправить изменения ветки 

---------------------------------------------------------
/=/=/=/ GitFlow
    1) Создать репозиторий и клонировать его на комп
        $ git clone url_git
    2) Создать ветку разработки develop от главной ветки (master , main)
        $ git branch develop
        $ git checkout develop
        $ git push origin develop
    3) От develop отходят ветки дробления задач 
    develop:
      - feature/main-page     (разрабатывается гл. страница)
      - feature/company-page     (разрабатывается стр. о компании)
      - feature/modals        (разрабатывается модальные окна)
      - feature/global-styles (разрабатываются глобальные стили)
    - Как только одна из веток была завершена, она объединятся (мержится) с главной develop
    4) Создание ветки release/0.1.0 от develop (когда близится дата релиза)
        $ git checkout develop -b release/0.1.0 
          (флаг -b говорит о переключении на созданную ветку)
        $ git push origin release/0.1.0 
    - В релизе допускается только исправление багов. Новые фичи запрещены.
    5) Когда ветка release/0.1.0 закончена (у нас есть что показать заказчику), то она мержится в develop и main, затем удалятся.
        $ git checkout main
        $ git merge release/0.1.0
        $ git push origin main

        $ git checkout develop
        $ git merge release/0.1.0
        $ git branch -d release/0.1.0
        $ git push origin develop
    6) Если в ветке main обнаружена ошибка, то создается hotfix-ветка 
        $ git checkout main
        $ git checkout -b hotfix/about-page-title-error
        // исправляем ошибку
        $ git commit -n 'add title on the about-page'
        $ git push origin hotfix/about-page-title-error
    7) Когда работа над hotfix-веткой завершается, то ее нужно мержить в develop и main
        $ git checkout main
        $ git merge hotfix/about-page-title-error
        $ git push origin main

        $ git checkout develop
        $ git merge hotfix/about-page-title-error
        $ git push origin develop

        $ git branch -d hotfix/about-page-title-error
        // git branch -d удалил локально, так же нужно удалить гитхабе 
---------------------------------------------------------
/=/=/=/ Доступ к репозиторию по SSH (для приватных репозиториев)
    1) Получаем SSH ссылку репозитория на сайте github
    2) Генерируем SSH-ключ для доступа по ссылке
        $ ssh-keygen -o
    - Указываем путь и название файла (называем как проект вместо id_rsa)
    - Вводим пароль для генерации 
    - Получаем наш ssh-key 
        $ cat указанный_путь_к_файлу
    - Переходим на github --> settings --> SSH and GPG keys --> New SSH Key
    - Вводим название ключа и вставляем наш ключ 
    3) Копируем наш репозиторий с помощью SSH и ключа 
        $ ssh-add указанный_путь_к_файлу (но без .pub в конце!)
          - Вводим пароль который установили при создании ключа
        $ git clone ssh_link
---------------------------------------------------------
/=/=/=/ React
---------------------------------------------------------
// React
    $ npm install
// OR
    $ npx create-react-app my-app - Собрать React
    $ npm start - Запустить проект
---------
    Error: sh: 1: react-scripts: not found
Fix: 
    $ npm install react-scripts
    $ npm i --package-lock-only
    $ npm audit fix --force
// OR
    delete node_modules 
    &&
    $ npm audit fix --force
-------------------
/=/=/ Bootstrap - библиотека, которая с помощью названия классов позволяет добавлять стили к нашим компонентам 

    $ npm install bootstrap

!!! import "bootstrap/dist/css/bootstrap.css"; // В index.js

---------
Для подключения 'Bootstrap Icons' необходимо в файле index.html добавить в секцию <head> следующее: 
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.5.0/font/bootstrap-icons.css">

---------------------------------------------------------
/=/=/ Теги rb Bootstrap
-------------------
 >- 'btn-sm' - сделать кнопку меньше 
    'btn-lg' - сделать кнопку больше
    'btn btn-outline-success' - обводка кнопки
-------------------
 >- 'align-items-center' || 'd-flex' - что-то из этого сделает по центру 
-------------------
 >- 'padding & margin'
--------- 
    m - для классов , которые устанавливают margin
    p - для классов , которые устанавливают padding

Где sides - одна из:

    t - margin-top или padding-top
    b - margin-bottom или padding-bottom
    s - (начало) margin-left или padding-left 
    e - (конец) margin-right или padding-right 
    x - оба *-left и *-right
    y - оба *-top и *-bottom
    пустой - для классов, которые задают margin или padding на всех 4 сторонах элемента

    mx-auto - класс для горизонтального центрирования содержимого на уровне блоков фиксированной ширины

    <div class="mx-auto p-2" style={{ width: "200px" }}>
        Centered element
    </div>
-------------------
 >- 'container' - контейнер с фиксированной шириной, который центрирует и горизонтально заполняет содержимое сайта
---------
    <div className="container fs-6">
        <div className="row">
            <div className="col-4">
                // малый элемент слева
            </div>
            <div className="col-8">
                // больший элемент справа
            </div>
        </div>
    </div>
-------------------
 >- 'row' - образует строку. Стоки используются для группировки колонок и обеспечения правильного выравнивания и отступов между ними.
------------------- 
    'col-4' и 'col-8' - Сетка Bootstrap состоит из 12 колонок.
    Поэтому класс col-4 означает, что колонка занимает 4 из 12 колонок (1/3 ширины родительского элемента), а класс col-8 означает, что колонка занимает 8 из 12 колонок (2/3 ширины родительского элемента)
-------------------
 >- 'fs-6' - размера шрифта font-size 
    'style={{ fontSize: "15px" }}'
-------------------
 >- 'd-flex justify-content-end' - Выравнивает элементы контейнера по правой стороне 
---------
    <div className="container d-flex justify-content-end">
        <button className="btn btn-warning mt-2">Reset</button>
    </div>
-------------------
 >- 'd-flex gap-2' - расстояние между элементами
-------------------
 >- 'd-grid gap-2 d-md-flex justify-content-md-end' - Выравнивает элементы контейнера по правой стороне 
---------
    * d-grid - задает элементу свойство display: grid, которое позволяет создавать сетки элементов; растянет элемент по контейнеру если он там один
    * gap-2 - задает расстояние между элементами;
    * d-md-flex - задает элементу свойство display: flex на устройствах с шириной экрана от md и выше, т.е. на средних и больших экранах;
    * justify-content-md-end - выравнивает элементы в сетке по горизонтали, при этом элементы сдвигаются вправо на устройствах с шириной экрана от md и выше.

    * align-items-center - выравнивает элемент по центру по вертикали
    * justify-content-center - выравнивает элемент по центру по горизонтали

    <div class="d-grid gap-2 d-md-flex justify-content-md-end">
        <button class="btn btn-primary me-md-2" type="button">Button</button>
        <button class="btn btn-primary" type="button">Button</button>
    </div> // Выравняет кнопки по правой стороне 
-------------------
 >- 'flex-shrink-0' - элемент не должен сжиматься внутри контейнера flex. Это означает, что элемент будет иметь фиксированную ширину и не будет сжиматься, если контейнер flex станет слишком маленьким.
-------------------
 >- 'text-muted' - сделать текст более серым
-------------------
 >- 'text-success' - окрасить текст
-------------------
 >- 'fw-bold' - жирный шрифт
    'fw-normal'
    'fw-light'
---------
    style={{ fontWeight: "bold" }} - Выделенный текст

    <h3 className="text-success" style={{ fontWeight: "bold" }}>
        Специальное предложение
    </h3>
-------------------
 >- 'd-inline-block' - создаст блок, который будет занимать только необходимое пространство для размещения содержимого
-------------------
 >- 'style={{ width: "max-content" }}' - сделать ширину ul пропорциональной максимальной длине элемента в списке
-------------------
 >- 'style={{ width: "max-content" }}' - сделать ширину ul пропорциональной максимальной длине элемента в списке
-------------------
 >- 'nav' - создание панели навигации:
---------
    <ul className="nav flex-row">
      <li className="nav-item">
        <Link to={"/"} className="nav-link text-primary">
          Main
        </Link>
      </li>
-------------------
 >- '<footer className="fixed-bottom">' - создание подвала
---------
    <footer className="fixed-bottom">
        <Container>
          <Row>
            <Col md={9}>
              <p>Copyright © 2021</p>
            </Col>
            <Col md={3}>
              <p>Designed by John Doe</p>
            </Col>
          </Row>
        </Container>
      </footer>
-------------------
 >- '<form/>' - создание формы
---------
    <form onSubmit={handleSubmit}>
        <p>
            <label>
                Email <input type="text" name="email" />
            </label>
        </p>
    <form/>

    div className="form-group">
        <label htmlFor="description">Описание:</label>{" "}
        <input
            id="description"
            name="desc"
            value={data}
            className="form-control"
          />
    </div>

    <Form onSubmit={handleSubmit}> 
        <Form.Group>
            <Form.Label htmlFor="email">Email:</Form.Label>
            <Form.Control id="email" className="my-1" type="text" name="email" />
        </Form.Group>
    </Form>
-------------------
 >- 'disabled={hasErrors}' - отключить кнопку
    <button
        disabled={hasErrors}
        className={"btn btn-primary"}
        type="submit"
    >
        Вход
    </button>
---------
    className={"btn btn-primary " + (hasErrors ? "disabled" : "")} - более мороченско через бутстрап
-------------------
 >- 'style={{ width: "250px" }}' - установит ширину 250px
-------------------
 >- 'w-100' для установки ширины элемента в 100% от ширины родительского элемента
---------
    style={{ width: "100%" }}
    w-25, w-50, w-75, w-100, w-auto 
    h-25, h-50, h-75, h-100, h-auto
-------------------
 >- 'mx-auto' - задает элементу автоматический отступ слева и справа, выравнивая его по центру горизонтально.
 >- 'mx-auto d-block' - если mx-auto не работает
-------------------
 >- 'd-block' - элемент занимает всю ширину родительского элемента 
-------------------
 >- 'invalid-feedback' - Визуальный отклик на валидацию поля. Им должен быть обернут родительский <div> и <div> для вывода

    <div className="mb-4">
        <label htmlFor="id">Email</label>
        <input
            id="id"
            className=""form-control " + (error ? "is-invalid" : "is-valid")
        />
        <div className="invalid-feedback">{error}</div>
    </div>
---------
const TextField = ({ label, type, name, value, onChange, error }) => {

    const getInputClasses = () => {
        return "form-control " + (error ? "is-invalid" : "is-valid");
    };

    return (
        <div className="mb-4">
        <label htmlFor={name}>{label}</label>
        <input
            className={getInputClasses()}
            type={type}
            id={name}
            name={name}
            value={value}
            onChange={onChange}
        />
        <div className="invalid-feedback">{error}</div>
        </div>
    );
};
-------------------
    '<form>' - Создание формы (логина)
-------------------
    <div className="container mt-5">
        <div className="row">
            <div className="col-md-6 offset-md-3 shadow p-4">
                <form className="mx-3" onSubmit={handleSubmit}>
                    // ...
                <button
                    disabled={hasErrors}
                    className={"btn btn-primary w-100 mx-auto"}
                    type="submit"
                    >
                        Вход
                </button>
            </form>
            </div>
        </div>    
    </div>  
---------
return (
    <div className="container mt-5">
      <div className="row">
        <div className="col-md-6 offset-md-3 shadow p-4">
          <form className="mx-3" onSubmit={handleSubmit}>
            <h3 className="mb-4">Login</h3>
              <TextField
                label={"Email:"}
                type="text"
                name="email"
                value={email}
                onChange={handleInputChange}
                error={errors.email}
              />
              <TextField
                label={"Пароль:"}
                type="password"
                name="password"
                value={password}
                onChange={handleInputChange}
                error={errors.password}
              />
            <button
              disabled={hasErrors}
              className={"btn btn-primary w-100 mx-auto"}
              type="submit"
            >
              Вход
            </button>
          </form>
        </div>
      </div>
    </div>
  );
};
-------------------
 >- 'col-md-6 offset-md-3' - центрирует. Занимает по середине 6 колонок, отступ слева и справа - 3 колонки
---------
    '<div className="row">
        <div className="col-md-6 offset-md-3 shadow">
            // ...
        </div>
    </div>
-------------------
 >- 'shadow' - придает тени div-у
-------------------
 >- 'has-validation' - исправляет баг квадратной кнопки в div-е с проверкой валидности формы и кнопкой скрыть/показать пароль
-------------------
 >- 'input-group' - связывает поле <input/> и <button/> для создания поля с кнопкой
-------------------
    <div className="input-group has-validation">
        <input
          className={getInputClasses()}
          type={showPass ? "text" : type}
          id={name}
          name={name}
          value={value}
          onChange={onChange}
        />
        {type === "password" && (
          <button
            type="button"
            className="btn btn-outline-primary"
            onClick={toggleShowPass}
          >
            {showPass ? eyeSlash : eyeFill}
          </button>
        )}
        <div className="invalid-feedback">{error}</div>
    </div>
-------------------
 >- 'col-md-6' - создать столбец, который занимает половину ширины родительского элемента.
-------------------
 >- <Spinner animation="border" className="mb-2" /> - Спиннер загрузки
---------
    <Spinner
        animation="border"
        className="mb-3 mt-3 mx-auto d-block"
        style={{ height: "3rem", width: "3rem" }}
    />
-------------------
 >- 'card' - создать карточку
---------
    <div className="card">
        <div className="card-body">
            <h3 className="card-title">{name}</h3>
            <div className="card-text">
               Tel.: {phone}, email: {email}
            </div>
        </div>
    </div>
-------------------
 >- Красивый шрифт для проекта 
---------
    body {
        margin: 0;
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto",
            "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans",
            "Helvetica Neue", sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
    }

    code {
        font-family: source-code-pro, Menlo, Monaco, Consolas, "Courier New",
            monospace;
    }
-------------------
 >- Зафиксировать Header вверху, поверх элементов независимо от скрола 
---------
    <header className="fixed-top bg-light">
        <NavBar />
    </header>
-------------------
 >- Зафиксировать Footer внизу экрана пользователя
---------
    <div className="d-flex flex-column min-vh-100">
        <div className="flex-grow-1">
            <MainPage />
        </div>
        <Footer />
    </div>
-------------------
 >- 'min-vh-100' - устанавливает минимальную высоту элемента на высоту окна просмотра (viewport height).
-------------------
 >- 'flex-grow-1' - определяет, как много свободного пространства внутри контейнера должен занять элемент
---------
flex-grow-1 занимает все доступное свободное пространство внутри контейнера, которое не было занято другими элементами с фиксированной шириной.

    <div class="d-flex">
        <div class="flex-grow-1">I will take up all the available space!</div>
        <div>But I will only take up the space I need.</div>
    </div>

Здесь первый div с классом flex-grow-1 займет все свободное пространство внутри контейнера, а второй div займет только необходимое для своего содержимого пространство.

-------------------
 >- 'box-shadow' - тени вокруг элемента 
---------
Тени для Switcher бутстрап:

    .form-check-input {
        box-shadow: 0 0 0 0.2rem rgba(0, 123, 255, 0.25);
    }
-------------------
 >- 'd-flex justify-content-center align-items-center' - центрирование по x и y
---------
    <Container>
      <Row>
        <Col md="4">
          <div
            className="d-flex justify-content-center align-items-center"
            style={{ border: "solid", height: "100px" }}
          >
            <h5>Element</h5>
          </div>
        </Col>
        <Col md="4">
          //...
        </Col>
        <Col md="4">
          //...
        </Col>
      </Row>
    </Container>
-------------------
 >- 'border border-dark border-3' - создать рамку 
-------------------
 >- 'overflow-auto' - добавляет скроллбар, когда количество элементов в списке превышает максимальную высоту, установленную в стиле maxHeight
---------
  const AccountCard = () => {
    const cardList = _.times(10);

    return (
        <ListGroup 
            className="list-group-flush overflow-auto" style={{ maxHeight: "150px" }}
        >
        {cardList.map((el) => (
            <ListGroupItem 
                key={el} 
                className="d-flex justify-content-between align-items-center"
            >
            <span className="me-2">Sum</span>
            <span className="me-2">Category</span>
            <Button variant="danger">Delete</Button>
            </ListGroupItem>
        ))}
        </ListGroup>
    );
  };

  export default AccountCard;
-------------------
 >- Настроить внешний вид скроллбара с помощью CSS
---------
->> Глобально в проекте 

/* Устанавливаем ширину скроллбаров */
    ::-webkit-scrollbar {
    width: 2px;
    }
/* Устанавливаем цвет ползунка скроллбара */
    ::-webkit-scrollbar-thumb {
    background-color: grey;
    }
/* Цвет полосы прокрутки */
    ::-webkit-scrollbar-track {
    background-color: white; 
    }
-------------------

.list-group::-webkit-scrollbar {
  width: 8px; /* Ширина скроллбара */
}
.list-group::-webkit-scrollbar-track {
  background-color: #f5f5f5; /* Цвет фона скроллбара */
}
.list-group::-webkit-scrollbar-thumb {
  background-color: #888; /* Цвет полосы прокрутки */
  border-radius: 4px; /* Закругление углов полосы прокрутки */
}
.list-group::-webkit-scrollbar-thumb:hover {
  background-color: #555; /* Цвет полосы прокрутки при наведении */
}

/=/ Вертикальный скроллбар
body::-webkit-scrollbar {
  width: 6px;
}
body::-webkit-scrollbar-track {
  background-color: #f5f5f5;
}
body::-webkit-scrollbar-thumb {
  background-color: #888;
  /* border-radius: 4px; */
}
body::-webkit-scrollbar-thumb:hover {
  background-color: #555;
}

/=/ Горизонтальный скроллбар
body::-webkit-scrollbar {
  height: 6px;
}
body::-webkit-scrollbar-track {
  background-color: #f5f5f5;
}
body::-webkit-scrollbar-thumb {
  background-color: #888;
  /* border-radius: 4px; */
}
body::-webkit-scrollbar-thumb:hover {
  background-color: #555;
}

-------------------
 >- 'text-overflow: ellipsis' - обрезать текст и добавить троеточие, если он не помещается в контейнере
---------
Добавляет троеточие для текста, который не помещается в контейнере:

.container {
    white-space: nowrap; 
     /=/ предотвращает перенос строк
    overflow: hidden; 
     /=/ скрывает все, что выходит за границы элемента
    text-overflow: ellipsis;
     /=/ добавляет троеточие для текста, который не помещается в контейнере
}
-------------------
 >- 'user-select-none' - запретить выделение текста для элемента
-------------------
 >- 'style={{ cursor: "pointer" }}' - устанавливает курсор при наведении на элемент
-------------------
 >- 'sticky-top bg-white' - зафиксировать вверху и сделать фон белым
-------------------
 >- 'text-underline-offset' - отступ подчеркивания
---------
    .navbar .nav-link.active {
        font-weight: 500;
        text-decoration: underline;
        text-underline-offset: 5px;
    }
-------------------
 >- 'style={{ height: "45vh" }}' - высоты видимой области страницы. 
 Устанавливает высоту элемента в зависимости от размера экрана пользователя.
-------------------
 >- (tw)'select-none' - запретить выделение текста 
-------------------
 >- (tw)
    'mr-[-3px]' - [negative-value] отрицательное значение
    'pr-[3px]' - положительное в px
    'bg-[#EBEAE6]' - backgroundColor: "#EBEAE6",
-------------------
 >- 'mb-3 mb-md-0' - динамически изменять отступ на разных экранах
    'p-md-0' - padding 0 для md
---------
    По умолчанию md-3, для экранов md и выше md-0
-------------------
 >- (tw) 'flex gap-3' - создает промежутки между элементами
-------------------
 >- (tw) 'w-fit' - установка ширины в соответствии с его содержимым.
-------------------
 >- (tw) grid
---------
    <div className="grid grid-cols-12 gap-1">
        <div className="col-span-2 gap-1">
            <div className="bg-blue-300 p-4">element</div>
            <div className="bg-green-300 p-4">element</div>
        </div>
        <div className="col-span-10 gap-1 grid grid-cols-2">
            <div className="bg-red-300 p-4">element</div>
        <div className="bg-yellow-300 p-4">element</div>
        </div>
    </div>
==/OR/==
    <div className="grid grid-cols-12 gap-1">
        <div className="col-span-2 gap-1">
            <div className="bg-blue-300 p-4">element</div>
            <div className="bg-green-300 p-4">element</div>
        </div>
        <div className="col-span-10 gap-1 flex">
            <div className="bg-red-300 p-4 flex-1">element</div>
            <div className="bg-yellow-300 p-4 flex-1">element</div>
        </div>
    </div>

В этом коде мы используем классы col-span-2 и col-span-10 для определения ширины колонок. Мы также добавляем класс flex для контейнера, чтобы элементы красный и желтый выстроились в одной строке. Класс flex-1 применяется к каждому элементу красного и желтого, чтобы они занимали равные части доступного пространства внутри контейнера.
-------------------
 >- (tw) - 'focus:outline-none active:outline-none'
---------
Удаление эффекта нажатия для Button
Эти классы удаляют обводку при фокусировке и при активации кнопки
-------------------
 >- md={{ span: 4, offset: 4 }}
---------
    * span: 4 указывает, что столбец будет занимать 4 из 12 доступных колонок в системе сетки. Это означает, что столбец будет занимать третью часть ширины контейнера.
    * offset: 4 указывает, что столбец будет смещен на 4 из 12 доступных колонок. Это означает, что в начале, перед столбцом будет 4 невидимых колонки, создавая таким образом отступ.
-------------------
 >- line-height - пространство между строками текста
---------

-------------------
 >- 
---------

-------------------
 >- 
---------

-------------------
 >- 
---------

-------------------
 >- 
---------

-------------------
 >- 
---------

-------------------
 >- 
---------

-------------------
 >- 
---------

-------------------
 >- 
---------

-------------------
 >- 
---------

-------------------
 >- 
---------
rb
-------------------
/=/=/ Добавление ветвления класса:
---------
    className={"page-item " + (pageNum === currentPage ? "active" : "")}

-------------------
/=/=/ Передать два элемента не используя "+"
---------  
Необходимо использовать React.Fragment

    <>
        {columns[column].name}
        {selectedSort.order === "asc" ? caretUp : caretDown}
    </>
---------
    const getArrowToHeader = (column) => {
        if (columns[column].path === selectedSort.path) {
            return (
                <div style={{ display: "flex", alignItems: "center" }}>
                    {columns[column].name}
                    {selectedSort.order === "asc" ? caretUp : caretDown}
                </div>
            );
        }
        return columns[column].name;
    };
-------------------
/=/=/ Lodash
---------
    $ yarn add lodash
// OR
    $ npm i lodash@4.17.15

 !  import _ from "lodash";

-------------------
-<< _.range() - создать массив из чисел 
---------
    _.range(4);    // => [0, 1, 2, 3]
    _.range(1, 5); // => [1, 2, 3, 4]
-------------------
-<< _.orderBy() - позволяет указывать порядок сортировки итераций для сортировки. 
---------
Если значение orders не указано, все значения сортируются в порядке возрастания. В противном случае укажите порядок сортировки "desc" по убыванию или "asc" по возрастанию

    _.orderBy(users, ['name', 'age'], ['asc', 'desc']);
---------
Например, можно отсортировать массив объектов по возрастанию значения поля age:

    const users = [
        { name: 'John', age: 25 },
        { name: 'Bob', age: 20 },
        { name: 'Mary', age: 30 }
    ];

    const sortedUsers = _.orderBy(users, ['age']);

    console.log(sortedUsers);
    // Output: [{ name: 'Bob', age: 20 }, { name: 'John', age: 25 }, { name: 'Mary', age: 30 }]
---------
Также можно указывать порядок сортировки (по возрастанию или убыванию) для каждого критерия:

    const sortedUsers = _.orderBy(users, ['name', 'age'], ['asc', 'desc']);
---------
Эта функция также позволяет сортировать не только по значениям полей объектов, но и по результатам выполнения функций, которые принимают объекты в качестве аргументов:

    const sortedUsers = _.orderBy(users, [(user) => user.name.toLowerCase(), 'age'], ['asc', 'desc']);

-------------------
-<< _.get(obj, путь_обращения_к_нему) - получить значение свойства объекта по переданному пути
---------
Например когда у нас передается строка с вложенным путем:

    item[columns[column].iter] === item["profession.name"] 
    // не выдаст

    _.get(item, columns[column].iter) === _.get(item, "profession.name") 
    // выдаст, без разницы в каком формате 


-------------------
-<< _.take(array, [сколько_el_взять_из_начала]) - Создает срез массива с n элементами, взятыми с самого начала.
--------- 
    _.take([1, 2, 3], 2) // => [1, 2]
    _.take([1, 2, 3], 5) // => [1, 2, 3]
    _.take([1, 2, 3], 0) // => []
-------------------
-<< _.times(3) - создать массив длиной в 3
---------
    const arr = _.times(3, (i) => `element ${i + 1}`);

Каждый элемент будет содержать значение, равное его индексу плюс 1

-------------------
-<< _.forEach(obj||arr, fn)
---------
    _.forEach([1, 2], function(value) {
        console.log(value);
    });

    _.forEach({ a: 1, b: 2 }, (value, key) => {
        console.log(key);
    });
-------------------
-<< _().value() - замена JSON.stringify()
---------
    _({ id: ALL, name: ALL }).value()
    JSON.stringify({ id: item.id, name: item.name })
---------
    id={'"all-ids"'} - готовый формат stringify
       "\"all-ids\""

    Или любые кавычки двух разных типов 
    `"${"all-ids"}-${type}"`
-------------------
-<< _.merge({}, {}) - замена Object.assign()
---------
    var object = {
        'a': [{ 'b': 2 }, { 'd': 4 }]
    };
    var other = {
        'a': [{ 'c': 3 }, { 'e': 5 }]
    };
    
    _.merge(object, other);
/=/ => { 'a': [{ 'b': 2, 'c': 3 }, { 'd': 4, 'e': 5 }] }
-------------------
-<<  _.chain() - создает цепочку методов. В конце обязательно .value()
---------
const transactions = [
    {
      id: 'transaction-id-1',
      amount: 5000,
      type: 'income',
      account: 'account-id-1',
      category: 'category-id-1',
      date: '2022-03-01T10:00:00Z'
    },
    // ...
]
    const expenses = _.chain(transactions)
        .filter({ type: "expense" })
        .map(({ id, date }) => ({ id, date }))
        .value();

    console.log(humanDate);
---------
    const dateString = humanDate[0];
    const [day, month, year] = dateString.split(".");
    const date = new Date(`${month}-${day}-${year}`);

    console.log(date);
    /=/ Формат даты должен быть:
    "месяц/день/год" или "день-месяц-год"
-------------------
-<< .uniqBy() - замена new Set()
---------
    _.chain(transactions)
        .filter({ type })
        .map(({ id, date }) => ({ id, date }))
        .uniqBy("date")
        .value();
    }
-------------------
-<<  _.isArray() - замена Array.isArray()
-------------------
-<< _.isEqual() - сравнить Objects
---------
    var object = { 'a': 1 };
    var other = { 'a': 1 };
    
    _.isEqual(object, other); /=/ => true
    object === other; /=/ => false
-------------------
-<< _.keys/values/toPairs() - Object.keys/values/entries
---------
_.keys()
    const obj = {a: 1, b: 2, c: 3};
    const keys = _.keys(obj); 
    /=/ ["a", "b", "c"]
---------
_.values()
    const obj = {a: 1, b: 2, c: 3};
    const values = _.values(obj); 
    /=/ [1, 2, 3]
---------
_.toPairs()
    const obj = {a: 1, b: 2, c: 3};
    const entries = _.toPairs(obj);
    /=/ [["a", 1], ["b", 2], ["c", 3]]
-------------------
-<< toLocaleString() / new Date() - преобразовать дату (не lodash)
---------
    const humanDate = new Date(date).toLocaleString().split(",");

    console.log(humanDate);
---------
    const dateString = humanDate[0];
    const [day, month, year] = dateString.split(".");
    const date = new Date(`${month}-${day}-${year}`);

    console.log(date);
    /=/ Формат даты должен быть:
    "месяц/день/год" или "день-месяц-год"
-------------------
-<< _.sumBy - может использоваться для сложения чисел в массиве объектов, где каждый объект имеет свойство с числовым значением. Если вам нужно сложить числа в строках, вам нужно будет привести строки к числам перед использованием
---------
    const strings = ['1', '2', '3'];

    const sum = _.sumBy(strings, Number);
    console.log(sum); /=/ Output: 6

В этом примере мы преобразовываем каждую строку в число с помощью функции `Number` и затем используем `_.sumBy` для сложения чисел.
---------
    const objects = [
        { value: 1 },
        { value: 2 },
        { value: 3 }
    ];

    const sum = _.sumBy(objects, 'value');
    console.log(sum); /=/ Output: 6

    const sum = _.sumBy(objects, (o) => { return o.value });
    console.log(sum); /=/ Output: 6

-------------------
-<< _.chunk - разбивает массив на подмассивы заданного размера.
---------
    _.chunk(['a', 'b', 'c', 'd'], 2);
    // => [['a', 'b'], ['c', 'd']]
    
    _.chunk(['a', 'b', 'c', 'd'], 3);
    // => [['a', 'b', 'c'], ['d']]
-------------------
-<< _.remove - удаляет все элементы массива, которые соответствуют заданному условию. Мутирует исходный массив.
---------
    const transactions = [
        { id: 1, amount: 100 },
        { id: 2, amount: 200 },
        { id: 3, amount: 300 },
    ];

    const transactionIdToRemove = 2;

    _.remove(transactions, { id: transactionIdToRemove });
-------------------
-<< {compose, pipe}  
---------
    half(square(double(x))) - Композиция функций
---------
const App = () => {
    const x = 2;
    const double = (num) => num * 2;
    const square = (num) => num * num;
    const half = (num) => num / 2;

    // const mathCalculate = half(square(double(x)))
    // const mathCalculate = compose(half, square, double);
    const mathCalculate = pipe(double, square, half);

    return <h1>{mathCalculate(x)}</h1>;
};

-------------------
-<< _.bind
---------
    const newFunc = func.bind(thisArg, ...partials);

    * func - это исходная функция, которую вы хотите привязать к определенному контексту.
    * thisArg - это значение, которое вы хотите использовать в качестве контекста (значения this) для новой функции.
    * partials (необязательный) - это предварительно заданные аргументы, которые будут переданы в исходную функцию при вызове новой функции. Эти аргументы будут располагаться перед аргументами, переданными при вызове новой функции.

    function greet(greeting, name) {
        console.log(`${greeting}, ${name}!`);
    }

    const greetHi = greet.bind(null, "Hi");
    greetHi("Bob"); /=/ Выведет: Hi, Bob!


В этом примере greetHi имеет фиксированный аргумент greeting, который передается автоматически при вызове. В этом случае thisArg установлен в null, что означает, что значение this в исходной функции будет определено контекстом, в котором будет вызвана новая функция.
-------------------
-<< _.defer()  
---------
    _.defer(function(stamp) {
        console.log(_.now() - stamp);
    }, _.now());
    /=/ Logs the number of milliseconds it took for the deferred invocation.

Внутри функции `defer` передается два аргумента:
    * Первый аргумент - это функция, которую вы хотите выполнить.
    * Второй аргумент - это аргумент, который будет передан в эту функцию при её вызове.
-------------------
-<< _.pick() - создает объект, состоящий из выбранных свойств.
---------
const data = {
  Date: '2023-08-23T11:30:00+03:00',
  PreviousDate: '2023-08-22T11:30:00+03:00',
  PreviousURL: '//www.cbr-xml-daily.ru/archive/2023/08/22/daily_json.js',
  Timestamp: '2023-08-22T20:00:00+03:00',
  Valute: {
    AUD: {
      ID: 'R01010',
      NumCode: '036',
      CharCode: 'AUD',
      Nominal: 1,
      Name: 'Австралийский доллар',
      Value: 60.3958,
      Previous: 60.2511
    },
    AZN: {
      ID: 'R01020A',
      NumCode: '944',
      CharCode: 'AZN',
      Nominal: 1,
      Name: 'Азербайджанский манат',
      Value: 55.3638,
      Previous: 55.3779
    }
  }
};

const filteredObj = _.pick(data.Valute, ['AUD', 'AZN']);
-------------------
-<< Отсортировать объект по возрастанию / убыванию
---------
    const obj = {
        a: 5,
        b: 2,
        c: 8
    };

    const sortedObj = Object.fromEntries(
        Object.entries(obj).sort(([,a], [,b]) => b - a)
    );
---------
     const sortedObj = fromPairs(
        toPairs(obj).sort(([, a], [, b]) => b - a)
    );
---------
    chain(sortedObj)  
        .toPairs()
        .sortBy(([, a]) => -a) /=/ Сортируем по убыванию
        .fromPairs()
        .value();

-------------------
-<< _.sortBy() - Сортировка Массива Объектов по ключу
---------
    const array = [
        { name: 'Зарплата', value: 75000, color: '#10b981' },
        { name: 'Аренда', value: 26800, color: '#06b6d4' }
    ];

    array.sort((a, b) => a.value - b.value);
---------
    sortBy(array,(a) => -a.value);

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

ld
---------------------------------------------------------
/=/=/=/ JSON 
-------------------
Читает файлы `users.json` и `accounts.json` и выводит всех пользователей и их счета:

[
  {
    "id": "user-id-1",
    "name": "John",
    "email": "john@example.com"
  },
  {
    "id": "user-id-2",
    "name": "Alex",
    "email": "alex@example.com"
  }
]

[
  {
    "id": "account-id-1",
    "name": "Сбербанк",
    "public": false,
    "private": true,
    "userId": "user-id-1",
    "categoryIds": ["category-id-1"],
    "balance": 90000,
    "transactionIds": ["transaction-id-1", "transaction-id-2"]
  },
  {
    "id": "account-id-2",
    "name": "Альфа-банк",
    "public": false,
    "private": true,
    "userId": "user-id-1",
    "categoryIds": ["category-id-2"],
    "balance": 80000,
    "transactionIds": ["transaction-id-3", "transaction-id-4"]
  },
  {
    "id": "account-id-3",
    "name": "Тинькофф",
    "public": true,
    "private": false,
    "userId": "user-id-2",
    "categoryIds": ["category-id-3"],
    "balance": 100,
    "transactionIds": ["transaction-id-6"]
  }
]
---------
    const fs = require('fs');
    /=/ fs - модуль Node.js для работы с файловой системой. Он предоставляет множество методов для чтения, записи и манипулирования файлами и папками на компьютере.

    /=/ Чтение файла users.json
    const usersData = fs.readFileSync('users.json');
    const users = JSON.parse(usersData);

    /=/ Чтение файла accounts.json
    const accountsData = fs.readFileSync('accounts.json');
    const accounts = JSON.parse(accountsData);

    /=/ Вывод пользователей и их счетов
    users.forEach(user => {
        console.log(`User: ${user.name}`);
        const userAccounts = accounts.filter(account => account.userId === user.id);
        userAccounts.forEach(account => {
            console.log(`  Account: ${account.name}, balance: ${account.balance}`);
        });
    });
-------------------
/=/=/ Генерация массива из числа
---------
    const numberOfPages = 4
    console.log([...Array(numberOfPages).keys()]); //  [0, 1, 2, 3]

Данный код создает массив ключей чисел от 0 до (numberOfPages - 1) и выводит его в консоль.

---------
Используя метод Array.from():
---------
// Syntax: 
    Array.from({ length: n }, (_, i) => i)

    const numberOfPages = 4;
    const arr = Array.from({ length: numberOfPages }, (_, i) => i); 
    // [0, 1, 2, 3]

    const arr = Array.from({ length: 4 }, (_, i) => i + 65); 
    //[ 65, 66, 67, 68 ]


Array.from() - это статический метод, который позволяет создавать новый массив из массивоподобных или итерируемых объектов.

---------
Используя метод Array().fill().map
---------
    const arr = Array(5).fill().map((_, index) => index);
    console.log(arr); // [0, 1, 2, 3, 4]

---------
/=/=/ .Array(value) - создает массив с указанным кол-вом элементов
---------
    Array(5).fill(0) // [ 0, 0, 0, 0, 0 ]
    
---------
/=/=/ .fill() - используется для заполнения всех элементов массива одним значением. 
---------
// Syntax:
    arr.fill(чем_заполнить, indexStart, indexEnd(не включительно))

    const arr = [1, 2, 3, 4, 5];
    arr.fill(0); // [0, 0, 0, 0, 0]

Метод .fill() изменяет существующий массив, а не возвращает новый. 

---------
index.js – входной в приложение JavaScript-файл, все начинается отсюда.

Здесь происходит монтирование корневого компонента в DOM-дерево, глобальное подключение сторонних библиотек и т.д.

    import React from "react";
    import ReactDOM from "react-dom/client";
    import App from "./App";
// Подключение Bootstrap из папки node_modules
    import "bootstrap/dist/css/bootstrap.css";

    const root = ReactDOM.createRoot(document.getElementById("root"));
    root.render(<App />);

Перед подключением библиотек их необходимо установить.
Установка Bootstrap фиксированной версии 5.1.0:
    $ npm i bootstrap@5.1.0

-------------------
React-компонент можно создать как обычную JavaScript-функцию:
    const Post = () => {
        return <div>Post</div>;
    };
Компонент может принимать в себя данные - props и выводить их
    const Post = (props) => {
        return <div>Post: {props.title}</div>; // JSX синтаксис
    };
Такой синтаксис в JavaScript, похожий на HTML, называется JSX
---------
Вот так выглядит компонент Post после конвертации в обычный JavaScript:
    
    const Post = props => {
        return React.createElement("div", null, "Post: ", props.title);
    };

-------------------
// JSX - JS XML синтаксис для описания интерфейсов для React
-------------------
С помощью Babel преобразует JSX выражение в обычный JavaScript.

JSX выражение - интерпретация React.createElement('div')
JSX выражение в JS файле: <h1>Hello</h1> //(JSX)

    const Component = () => {
        return //(JSX)
    }
    reactDom.render(<Component />, document.getElementById('root'))

Все React-компоненты начинаются с заглавной буквы.
(если компонент называется с маленькой буквы, то React принимает его за DOM-тег)

React компоненты являются основными строительными блоками при разработке приложений на React. Компоненты представляют собой небольшие, независимые части пользовательского интерфейса, которые могут быть повторно использованы в различных местах приложения.
---------
Эти React-элементы можно также записывать и в обычную переменную:
    const title = 'Junior Frontend Developer';
    const course = <h1>Course: {title}!</h1>;
Без JSX:
    const title = 'Junior Frontend Developer';
    const course = React.createElement("h1", null, "Course: ", title, "!");

-------------------
// React DOM - библиотека отвечает за рендеринг, отрисовку React-элементов в браузере
-------------------
React разработан таким образом, что он не зависит от браузера

Благодаря этому, на React мы можем разрабатывать не только браузерные интерфейсы, но и, к примеру, интерфейсы для мобильных приложений. Там уже вместо React DOM будет использоваться React Native. 

Таким образом React отвечает за работу с компонентами, React-элементами и тд, а за визуализацию в различных окружениях отвечают другие библиотеки (такие как React DOM).

---------
// Монтирование компонента в DOM-дерево:
---------
    import React from "react";
    import ReactDOM from "react-dom/client";

    const Post = (props) => {
        return <div>Post: {props.title}</div>;
    };

    const root = ReactDOM.createRoot(document.getElementById("root"));
    root.render(<Post title={'Hello World'} />);

В элемент по селектору #root произойдет вставка <div>Post: Hello World</div>.

-------------------
/=/=/ Указание дочерних компонентов React
-------------------
Не сработает: 
Babel не поймет тк JSX выражение это React.createElement('div')
    
    const Counter = () => {
        return <h1>Counter</h1><button>+</button>;
    };

Если мы попытаемся вернуть из компонента несколько элементов, то мы получим ошибку: Выражения JSX должны иметь один родительский элемент.
---------
Сработает: (использование оберточной оболочки)
    const Counter = () => {
        return (
            <div>
                <h1>Counter</h1>
                <button>+</button>
            </div>
        );
    };
---------
Сработает: (Без использование оберточной оболочки)
    const Counter = () => {
        return (
            <React.Fragment>
                <h1>Counter</h1>
                <button>+</button>
            </React.Fragment>
        );
    };
---------
// OR 
---------
Сработает: (современный аналог)

    const Counter = () => {
        return (
            <>
                <h1>Counter</h1>
                <button>+</button>
            </>
        );
    };

Лучше чем <React.Fragment> (современный аналог):

-------------------
/=/=/ Вложения переменных, выражений, ветвлений, вызовов f() в React
-------------------
Переменные передаются в таких случаях как в JS через фигурные скобки {}, но только тут без наклонных кавычек ``

    const Counter = () => {
        const count = 2;
        return (
            <>
                <h1>{count + 2}</h1>
                <button>+</button>
            </>
        );
    };
---------
    export const Page = () => {
        const logoUrl = "";
        const siteName = "example.com";

        const getHeadline = () => {
            return logoUrl 
              ? (
                <img src={logoUrl} alt="logo"/>
            ) : (
                <div>{siteName}</div>
            );
        };

        return (
            <>
                <header>{getHeadline()}</header>
                <footer>подвал</footer>
            </>
        );
    };
---------
! // Good example:

    import React from "react";

    const Counter = () => {
        const count = 0;

        const formatCount = () => {
            return count === 0
                ? 'empty'
                : count;
        };

        const getBadgeClasses = () => {
            let classes = "badge m-2 ";
            classes += count === 0
                ? "bg-warning"
                : "bg-primary";
            return classes;
        };

        return (
            <>
                <span className={getBadgeClasses()}>
                    {formatCount()}
                </span>
                <button className="btn btn-primary btn-sm m-2">+</button>
            </>
        );
    };

    export default Counter;

---------
// className = '' - добавление класса HTML в JSX
---------
className используется для добавления класса в HTML с помощью JSX (используется вместо обычного class, тк оно уже зарезервировано)

    <span className="badge bg-primary">{formatCount()}</span>

---------
// Добавить тернарное ветвление в класс:
---------
    className={
        "page-item " + (page === currentPage ? "active" : "")
    }
!!! Внимание! помести в скобки (тернарный выбор класса)

-------------------
// Ветвление с использованием ||
---------
    columns[column].component || _.get(item, columns[column].iter)

Если columns[column].component не существует, то отображаем _.get(item, columns[column].iter)
---------
    {data.map((item) => (
        <tr key={item._id}>
          {Object.keys(columns).map((column) => (
            <td key={column}>
              {columns[column].component || _.get(item, columns[column].iter)}
            </td>
          ))}
        </tr>
    ))}

---------
! Но лучше используй просто тернарное выражение! 
  Оно надежней. Или if/else в функции 
---------
-------------------
// Ветвление с использованием &&
---------
role в JSX может использоваться только в {...{role:}}
Подобно style={{ height: "100%" }}

    {...{ role: columns[column].iter && "button" }}

Если свойство iter существует в columns[column] (где column - это название столбца), и оно является истинным значением, то свойство role будет установлено на значение "button". В противном случае свойство role не будет добавлено в th.

    <thead>
      <tr>
        {Object.keys(columns).map((column) => (
          <th
            key={column}
            onClick={
              columns[column].iter
                ? () => handleSort(columns[column].iter)
                : undefined
            }
            scope="col"
            {...{ role: columns[column].iter && "button" }}
          >
            {columns[column].name}
          </th>
        ))}
      </tr>
    </thead>
-------------------
// key={id} 
---------
- Key={id} нужен при работе с Массивами и отображении их el. 
  Ключи сообщают React, какому элементу массива соответствует каждый компонент. 
  Поэтому элементам внутри map() всегда нужны ключи!

Добавляем `key` только если нода Родительская
    <ParentTag key={id}>
        <childTag>text<childTag/>
    <ParentTag/> 

-------------------
/=/=/ Обработка событий в React
-------------------
Референс функции это ссылка на функцию (без вызова)
---------
Элементы React пишутся с Заглавной буквы (Func-s, Var-s ets) 
---------
// `handle` - Обработчики событий должны начинаться с `handle`
---------
// `set` -  setФункция в useState() должна начинаться с `set`
---------

    <span className={getBadgeClasses()}>{formatCount()}</span>
    <button
        className="btn btn-primary btn-sm m-2"
        onClick={handleIncrement}
    >
        +
    </button>

Для обработки функции при передаче в EventListener, необходимо передавать референс функции, а не ее вызов

-------------------
/=/=/ useState() - хук для обновления данных (перерисовке DOM-el)
-------------------
// useState() - состоит из двух элементов. Возвращает кортеж (массив), в котором содержится значение состояния и функция для его изменения.

   I el - Хранит текущее состояние; (read)
   II el - Функция которая устанавливает данные массива состояния; (set)
           (Имя данной функции должно всегда начинаться с `set`)

 const [count, setCount] = useState(0);
     variable | function           (n) - variable_value / any_item 
                                                        (obj/arr/func etc)
---------
Для сообщения React о том что наше состояние изменилось, необходимо использовать функцию setCount()

    const Counter = () => {
        const [count, setCount] = useState(0);

        const handleIncrement = () => {
            setCount(count + 1);
        };
        ...
    };

useState() хранит значение нашей переменной "count" вне нашего компонента, в своем хранилище, поэтому переменная не перезаписывается в начальное значение при новом запуске.

---------
У useState() имеется система оптимизации дублирования событий.
useState() - асинхронная функция.

Например, если в коде, где-то дублируются одинаковые события, то он схлопнет их воедино.
    const handleIncrement = () => {
        setCount(count + 1);
        setCount(count + 1); // Итого будет count === 1
    };
---------
// Если мы вызываем setCount() 2 раза осознанно и его не надо схлопывать для оптимизации, то необходимо добавить callback. И передать в него текущее состояние переменной (чтобы операции шли именно с актуальным значением) 

Тк запрос на выполнение двух наших функций может быть асинхронным. 
  В связи с этим, не факт что первая переменная при вызове первого дубликата функции, обновиться к тому моменту как мы попробуем произвести с ним вторую операцию.

Поэтому передаем callback c параметром `prevState`.
    prevState - это текущее значение переменной, которое храниться в нашем состоянии.

    const handleIncrement = () => {
        setCount((prevState) => prevState + 1);
        setCount((prevState) => prevState + 1); // Итого будет count === 2
    };

---------
При наличии слушателя на элементе:
    1) Нам необходимо создать функцию handler которая будет возвращать результат того что должно произойти после клика.
      1.1) В handler-функции необходимо использовать callback(prevState), чтобы быть уверенным что используется именно текущее значение изменяющейся переменной.
    2) Для того чтобы значения обновлялись при event-е, нужно использовать Хук useState() для обновления данных.
    В который будет передаваться:
    [имя_переменной, setФункция] = сам_useState(начальное_значение)
    3) В handle-функцию необходимо передавать вместо обычной переменной
    setФункцию(new_value_after_event)

-------------------
/=/=/ Вывести данные массива в HTML через JSX
-------------------
// Для рендеринга el Массивов используется метод .map()

    <div>
        {array.map((arrayItem) => (
            <span>{arrayItem}</span>
        ))}
    </div>;
---------
Внутри JSX мы перебираем элементы массива и возвращаем нужные нам React-элементы.

В нашем примере выведем список пунктов меню:

! // Good example:

    const Navbar = () => {
        const [open, setOpen] = useState(false);
        const [menuItems, setMenuItems] = useState(["Главная", "Блог", "Контакты"]);

        const handleMenuClick = () => {
            setOpen((prevState) => !prevState);
        };

        return (
            <>
            <button
                className="btn btn-sm btm-primary"
                onClick={handleMenuClick}
            >
                Меню
            </button>
            {open && (
                <ul className="list-group">
                    {menuItems.map((item) => (
                        <li 
                            className="list-group-item" 
                            key={item}>
                            {item}
                        </li>
                    ))}
                </ul>
            )}
            </>
        );
    };

---------
Проблема в том, что в коде нет return-стейтмента. Код должен был выглядеть следующим образом:

    <tbody>
        {users.map((user) => {
            return (
                <tr key={user._id}>
                    <td>{user.name}</td>
                    <td>{user.qualities}</td>
                    <td>{user.profession}</td>
                    <td>{user.completedMeetings}</td>
                    <td>{user.rate}</td>
                </tr>;
            )
        })}
    </tbody>

Return - стейтмент является необходимым, чтобы React знал, что он должен возвращать.

-------------------
/=/=/ Найти и удалить el при клике по нему
-------------------
const Counter = () => {

    const [tags, setTags] = useState(["tag1", "tag2", "tag3"]);

    const handleTagChange = (id) => {
        setTags(prevState => prevState.filter(tag => tag !== id))
    };                         [tags].filter

    return (
        <>
            <ul>
                {tags.map((tag) => (
                <li
                    key={tag}
                    className="btn btn-primary btm-sm m-2"
                    onClick={() => handleTagChange(tag)}
                >
                    {tag}
                </li>
                ))}
            </ul>
        </>
---------
// Ветвление map()
---------
    function handleAddBookmark(id) {
        setUsers(prevState =>
            prevState.map(user => {
                if (user.id === id) {
                    return { ...user, bookmark: !user.bookmark };
                }
                    return user;
                })
        );
    }
    // bookmark: !user.bookmark - меняем прошлое значение Объекта на противоположное

---------
!// При работе с фильтрацией Массива Объектов, не забывай писать не просто `el`, а `el.key`

    const [counters, setCounters] = useState([
        { id: 0, value: 0, name: "Ненужная вещь" },
        { id: 1, value: 1, name: "Ложка" },
        { id: 2, value: 1, name: "Вилка" },
        { id: 3, value: 1, name: "Тарелка" },
        { id: 4, value: 1, name: "Набор минималиста" },
    ]);

    const handleDelete = (id) => {
        const newCounters = counters.filter((el) => el.id !== id);
    };
Тогда все отфильтруется

---------
/=/=/ Spread React Attribute - передача всех полей из объекта в атрибуты.
---------
В React есть специальный синтаксис и с помощью Spread-оператора мы можем передать сразу все поля из объекта в атрибуты.

    <NavLink
        key={item.id}
        {...item}
        onActiveChange={handleItemClick}
    />
---------
Вместо
    <>
      {counters.map((el) => (
        <Counter
          key={el.id}
          id={el.id}
          value={el.value}
          name={el.name}
          onDelete={handleDelete}
        />
      ))}
    </>
Пишем:
    <>
      {counters.map((el) => (
        <Counter
          key={el.id}
          onDelete={handleDelete}
          {...el} 
          // Включает в себя все элементы из Массива Объектов `counters`
          />
      ))}
    </>

---------
Особенность такого метода
---------
Тк props - объект, если мы устанавливаем значение какого-то поля объекта и потом пытаемся сделать это ещё раз, то поле просто перезаписывается.

    const obj = {
        example: 1
    }
    obj.example = 2
    console.log(obj.example) // 2
---------
    const example = {
        id: 1,
        testField: 'testField from object'
    }
    return (
        <ExampleComponent testField="testField from props" {...example}/>
    )

Аттрибут `testField` перезапишется на значение объекта `example`
    // testField='testField from object'
Необходимо помнить о такой особенности и выставлять нужный порядок передачи атрибутов, или убирать из объекта ненужные поля.

---------
// Передача нескольких аргументов свойству props
---------
    <UsersList
        onAddBookmark={() => {
            handleAddBookmark();
            setActive(!active);
        }}
    >
-------------------
/=/=/ onClick={} обработчик событий
-------------------
// Как вызывается функция при клике, когда мы передаем в onClick лишь референс?
---------
Когда мы передаем ссылку на функцию в качестве обработчика событий, например onClick={handleClick}, React автоматически вызовет функцию при возникновении соответствующего события (в данном случае, когда пользователь нажимает на элемент).

Передавая Референс в onClick, мы говорим React-ту вызвать() данный референс когда произойдет событие.
---------
Вызвать выполнение функции при клике:
    onClick={handleTagChange}

Передать аргумент в функцию handle или вернуть результат работы функции при клике:
    onClick={() => handleTagChange()}
    onClick={() => handleTagChange(tag)}
---------
Since with the construction onClick={handleTagChange(tag)}, `handleTagChange()` is called when the component is rendered, not when the button is clicked.

By using an arrow function () => handleTagChange(tag), you are creating a new function that takes no arguments and returns the result of calling handleTagChange with the tag argument. This allows you to delay the execution of handleTagChange until the onClick function is triggered.

Поэтому когда нет необходимости передавать аргументы функции, мы передаем  Референс функции в onClick. Тк при рендере Референс без вызова сам не сработает. 

---------
/=/=/ useState() - Передача обновленных значений элементов
---------
Значение useState(value) задается при первоначальном создании компонента и в дальнейшем больше не обращается к value, а берет значение из своего хранилища useState.

Пример:
  const [value, setValue] = useState(props.value);

 // useState будет равно первому значению props.value
 // Если props.value изменится, useState не обновится, а будет использовать записанное значение в value
---------
Как исправить?
---------
Необходимо убрать данную автономность, заменив useState на перезапись объекта:
  const { value } = props;
// OR
  const value = value.props;
---------
Но тогда пропадет возможность обновлений через setValue() в useState
---------
Если в useState(props.value) в качестве `init_value` мы передавали значение props, то переменную из useState можно напрямую заменить именно этим пропсом - props.value.

---------
Необходимо использовать методы setState() или useState() для передачи обновлений элементов в React, вместо прямого изменения DOM дерева. 

Тк React в свою очередь использует виртуальный DOM. 
Когда какой-то элемент изменяется, React обновляет виртуальный DOM, сравнивает изменения с предыдущим виртуальным DOM и обновляет фактический DOM только там, где это необходимо. 

Такой подход обеспечивает более высокую производительность и более эффективный механизм обновления, поскольку React обновит только те части DOM, которые действительно изменились, а не повторно отобразит все дерево компонентов. 

А прямое изменение элемента не приведет к повторному рендерингу, и React не будет знать об изменениях. Что приведет к снижению эффективности и к колхозному отношению к производительным технологиям.
---------

    const [tags, setTags] = useState(["tag1", "tag2", "tag3"]);

    const handleTagChange = (id) => {
        setTags(prevState => prevState.filter(tag => tag !== id))
    };

Для обновления элементов и их передачи, в нашем примере, необходимо использовать функцию setTags() - конструкцию метода UseState() 
и метод .filter() для передачи всех элементов которые подходят под описание элемента нажатия и исключая тот, который не удовлетворяет условиям. 
В итоге, новый список элементов передаем в функцию setTags() - конструкцию метода UseState(), в последствии чего нажатый элемент удаляется. 
---------
Так же необходимо использовать prevState (а не переменную которую передаем в конструкцию useState), когда имеем дело с изменением состояния переменной, в связи взаимодействия пользователя с UI!

    setTags(prevState => prevState.filter(tag => tag !== id))

It's important to use prevState because React state updates are asynchronous. If multiple updates are made to the state in quick succession, it's possible that some updates will be lost, as the state will be overwritten by the time the update function runs.

By using `prevState`, you ensure that your state updates correctly, regardless of when the update function runs.

So, in general, it's a good practice to always use `prevState` when updating state based on the previous state, to ensure that your state updates correctly and as expected.

---------------------------------------------------------
/=/=/ Когда нужен prevState. Особенности ...prev
-------------------
!!! Внимание !
При передаче ...prev в setState() необходимо передавать его первым

    setDropdown((prev) => ({
      ...prev,
      name: eventKeys.name,
      id: eventKeys.id
    }))
-------------------

prevState нужен тогда, когда вы обновляете состояние на основе предыдущего значения состояния. 
Если идет полная перезапись значения, то prevState не нужен.

Это особенно важно, когда функция обновления состояния вызывается асинхронно, потому что вы не можете гарантировать, что используемое вами значение состояния будет актуальным на момент вызова функции.

Вот несколько примеров, когда нужен prevState:
---------
// Увеличение числового значения на 1:
---------

    setCount((prevState) => prevState + 1);

Здесь мы обновляем состояние count, увеличивая его на 1. Мы используем prevState, чтобы гарантировать, что мы обновляем состояние на основе предыдущего значения.
---------
// Обновление массива, добавление нового элемента в конец:
---------

    setItems((prevState) => [...prevState, newItem]);

Здесь мы обновляем состояние items, добавляя новый элемент в конец массива. Мы используем prevState, чтобы гарантировать, что мы обновляем состояние на основе предыдущего значения.
---------
// Обновление объекта, замена значения свойства:
---------￼

    setUser((prevState) => ({ ...prevState, name: newName }));

Здесь мы обновляем состояние user, заменяя значение свойства name на новое значение. Мы используем prevState, чтобы гарантировать, что мы не перезаписываем остальные свойства объекта и обновляем состояние на основе предыдущего значения.
---------
Однако, если вы обновляете состояние на основе фиксированного значения, например, если вы переключаете флаг isActive между true и false, то prevState не нужен:

    setIsActive(!isActive);

Здесь мы обновляем состояние isActive, переключая его между true и false. В этом случае мы не используем prevState, потому что мы не обновляем состояние на основе предыдущего значения.

---------------------------------------------------------
/=/=/ Условное ветвление Рендеринга
-------------------
// Ветвление в React допустимо двумя способами:

    - Тернарных выражений 
    {condition ? <Element1 /> : <Element2 />} 

    - Логических операций
    {condition && <Element1 />}

---------
import React, { useState } from "react";

const Navbar = () => {
  const [open, setOpen] = useState(false);
  const [menuItems, setMenuItems] = useState(["Главная", "Блог", "Контакты"]);

  const handleMenuClick = () => {
    setOpen((prevState) => !prevState);
  };

  const handleItemClick = (id) => {
    console.log(id);
  };

  // Создание пунктов меню
  const renderMenu = () => {
    return (
      // Если переменная open равна true то мы выводим пункты меню, иначе мы не выводим ничего.
      open && (
        <ul className="list-group">
          {menuItems.map((item) => (
            <li
              className="list-group-item"
              key={item}
              onClick={() => handleItemClick(item)}
            >
              {item}
            </li>
          ))}
        </ul>
      )
    );
  };

  return (
    <div>
      <button
        className="btn btn-sm btm-primary"
        onClick={handleMenuClick}
      >
        меню
      </button>
      {renderMenu()}
    </div>
  );
};

Будем выводить стрелочку вверх или вниз внутри кнопки ”меню” в зависимости от переменной open:

import React, { useState } from "react";

const Navbar = () => {
  const [open, setOpen] = useState(false);
  const [menuItems, setMenuItems] = useState(["Главная", "Блог", "Контакты"]);

  const handleMenuClick = () => { /* ... */ };
  const handleItemClick = (id) => { /* ... */ };
  const renderMenu = () => { /* ... */ };

  // Стрелочка вверх
  const arrowTop = (
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="16"
      height="16"
      fill="currentColor"
      className="bi bi-arrow-up"
      viewBox="0 0 16 16"
    >
      <path
        fillRule="evenodd"
        d="M8 15a.5.5 0 0 0 .5-.5V2.707l3.146 3.147a.5.5 0 0 0 .708-.708l-4-4a.5.5 0 0 0-.708 0l-4 4a.5.5 0 1 0 .708.708L7.5 2.707V14.5a.5.5 0 0 0 .5.5z"
     />
    </svg>
  );

  // Стрелочка вниз
  const arrowDown = (
    <svg
      xmlns="http://www.w3.org/2000/svg"
      width="16"
      height="16"
      fill="currentColor"
      className="bi bi-arrow-down"
      viewBox="0 0 16 16"
    >
      <path
        fillRule="evenodd"
        d="M8 1a.5.5 0 0 1 .5.5v11.793l3.146-3.147a.5.5 0 0 1 .708.708l-4 4a.5.5 0 0 1-.708 0l-4-4a.5.5 0 0 1 .708-.708L7.5 13.293V1.5A.5.5 0 0 1 8 1z"
      />
    </svg>
  );

  // Функция для отображения стрелочек
  const renderArrow = () => {
    return open ? arrowDown : arrowTop;
  };

  return (
    <div>
      <button
        className="btn btn-sm btm-primary"
        onClick={handleMenuClick}
      >
        {/*вызываем renderArrow() внутри кнопки*/}
        меню {renderArrow()}
      </button>
      {renderMenu()}
    </div>
  );
};
---------------------------------------------------------
/=/=/=/ Композиции компонентов
---------------------------------------------------------
Композиция компонентов – способ использования компонентов как частей внутри друг друга. 
В React-приложениях компоненты используются внутри друг друга. Подобно конструктору lego мы составляем наше приложение из компонентов словно из деталей и можем менять их последовательность как нам нужно. 

-------------------
/=/=/ props - (properties - свойства)
-------------------
Props - это способ передачи данных из родительского компонента в дочерний компонент. 

По сути, это неизменяемые значения, которые передаются от родительского элемента к дочернему, и затем дочерний элемент может использовать эти props для визуализации своего пользовательского интерфейса или выполнения какого-либо другого действия. 

    // Parent Component
    function ParentComponent() {
        return (
            <ChildComponent name="Alice" age={30} />
        );
    }

    // Child Component
    function ChildComponent(props) {
        return (
            <div>
                <p>Name: {props.name}</p>
                <p>Age: {props.age}</p>
            </div>
        );
    }

-------------------
/=/=/ Деструктуризация аргументов
---------
    const years = episodes.map((episode) => episode.airDate.slice(-4));
    const years = episodes.map(({ airDate }) => airDate.slice(-4));
-------------------
/=/=/ Деструктуризация. Передать вложенную структуру пропса:
---------

    const handleChange = ({ target: { value } }) => {
        console.log(value);
    };
---------
    const Product = ({ id, image, title, price, rating: { rate } }) => {
        clg(rate) 
    }
    
-------------------
/=/=/ Избежание дублирования названий при передачи свойств компоненту
---------
    <TableHeader onSort={onSort} selectedSort={selectedSort} />

    <TableHeader {...{ onSort, selectedSort }} />

-------------------
/=/=/ Избежание дублирования названий + переименование пропса
---------

    <TableBody {...{ columns, data: usersCurntPage }} />

-------------------
/=/=/ Передача пропсов 
---------
    const Component = ({ prop1, prop2, ...rest }) => {...}

    const Component = (props) => {
        const { prop1, props2, ...rest} = props
    }

---------
    const props = { 
        id: 1, 
        text: "hello", 
        active: true, 
        onClick: Function 
    }
    const { id, text, ...rest } = props 
    // rest = { active: true, onClick: Function }

Таким образом, можно извлечь некоторые данные из изначальных props, а rest передать дальше потомку

---------
Было:
    const Breadcrumbs = (props) => {
        const isMainPage = props.page.id === "main";
        const mainPageClass = "breadcrumb-item" + (isMainPage ? " active" : "");

        return (
            <nav>
            <ol className="breadcrumb">
                <li className={mainPageClass} onClick={props.onGoMain}>
                Главная
                </li>
                {!isMainPage && (
                <li className="breadcrumb-item active">{props.page.text}</li>
                )}
            </ol>
            </nav>
        );
    };
---------
Оптимизация деструктуризацией: 

    const Breadcrumbs = ({ page, onGoMain }) => {
        const isMainPage = page.id === "main";
        const mainPageClass = "breadcrumb-item" + (isMainPage ? " active" : "");

        return (
            <nav>
            <ol className="breadcrumb">
                <li className={mainPageClass} onClick={onGoMain}>
                    Главная
                </li>
                {!isMainPage && (
                    <li className="breadcrumb-item active">{page.text}</li>
                )}
            </ol>
            </nav>
        );
    };
---------
// Props доступен только для чтения
---------
Props включает в себя данные, которые мы передаем компоненту, а State является локальным или частным для этого компонента. Другие компоненты не могут получить доступ к состоянию. Существуют компоненты, у которых нет состояния, и они занимаются лишь отображением чего-либо.

Props мы не можем изменить внутри компонента т.к. он доступен только для чтения. React запрещает нам изменять первоначальные props. При попытке это сделать, React выведет нам ошибку.

    const handleClick = () => {
        props.active = !active 
        /* 
        *  console output: 
        *  "Uncaught TypeError: Cannot assign to read only 
        *  property 'value' of object '#<Object>'"
        */
        
        setValue((prevState) => prevState + 1);
    };

---------
// Как props понимает что передавать?
---------
Когда в родительском элементе мы взаимодействуем с дочерним и передаем там ему различные аргументы,: 
    <ChildComponent name="Alice" age={30} />

Метод props позволяет запомнить эти аргументы и перенести их в дочернюю функцию, находящуюся вне родительской.

    function ChildComponent(props) {
        return (
            <div>
                <p>Name: {props.name}</p> // Alice
                <p>Age: {props.age}</p> // 30
            </div>
        );

-------------------
/=/=/ .defaultProps = {} - Установить значения по умолчанию:
---------

    GroupList.defaultProps = {
        valueProperty: "id",
        contentProperty: "text"
    };

---------
Child Component with default props

    function ChildComponent({ name, age, city }) {
        return (
            <div>
            <p>Name: {name}</p>
            <p>Age: {age}</p>
            <p>City: {city}</p>
            </div>
        );
    }

    ChildComponent.defaultProps = {
        city: 'Unknown'
    };

Если родитель не передаст дочернему элементу реквизит города, по умолчанию он будет иметь значение "Неизвестно".

-------------------
/=/=/ props.children - позволяет родительским компонентам принимать и отображать дочерние элементы. 
(Раскрывать родительский элемент и выводить вложенные)
---------
Отличие `props.children` от обычного `props` в том, что он передается не как атрибут, а передается между открывающими и закрывающими скобками тега.
Обычно children используют, когда содержимое никак не связано с компонентом. Например, в диалоговых окнах.

    // Grandparent Component
    function GrandparentComponent() {
        return (
            <ParentComponent>
                <ChildComponent name="Bob" age={25} />
            </ParentComponent>
        );
    }

    // Parent Component
    function ParentComponent(props) {
        return (
            <div>
                {props.children} 
                 // <ChildComponent name="Bob" age={25} />
            </div>
        );
    }

    // Child Component
    function ChildComponent({ name, age }) {
        return (
            <div>
                <p>Name: {name}</p>
                <p>Age: {age}</p>
            </div>
        );
    }

---------------------------------------------------------
/=/=/ Деструктуризация Пропсов 
---------------------------------------------------------
    const Qualities = (props) => {
        const {
            user: { name, profession, qualities, completedMeetings, rate, ...rest },
        } = props;

        return (
            <>
                <td>{name}</td>
                <td>
                    {qualities.map((el) => (
                    <span className={`badge bg-${el.color}`} key={el._id}>
                        {el.name}
                    </span>
                    ))}
                </td>
                <td>{profession.name}</td>
                <td>{completedMeetings}</td>
                <td>{rate}/5</td>
            </>
        );
    };

---------
/=/=/ Деструктуризация Пропсов c переименованием пропса
---------
const UsersList = ({ users: allUsers, ...rest }) => {
    const pageSize = allUsers.length;
    ...
}

При использовании объекта деструктуризации { users: allUsers, ...rest } мы извлекаем свойство users из объекта props и сохраняем его в переменной allUsers.
Таким образом, мы можем обращаться к переданному свойству users внутри компонента как к allUsers
---------
/=/=/ Деструктуризация Пропсов c помощью (...) Rest
---------
// episodes.js
    export const episodes = [
        {
            id: 1,
            name: "Pilot",
            airDate: "December 2, 2013",
            episode: "S01E01",
            created: "2017-11-10T12:56:33.798Z",
        },
        ...
    ]

Передаем при мапировании лишь {...episode}! 
Тем самым предоставляя доступ пропсам ко всем значениям массива episodes.
// EpisodesList.jsx
    const EpisodesList = () => {
        return (
            <>
            <div className="container">
                <div className="row">
                {episodes.map((episode) => (
                    <Episode key={episode.id} {...episode} />
                ))}
                </div>
            </div>
            </>
        );
    };

// Episode.jsx
    const Episode = ({ name, episode, airDate }) => {
        return (
            <div className="col-4 mb-2">
            <div className="card" style={{ height: "100%" }}>
                <div className="card-body">
                <h5 className="card-title">
                    {name} {episode}
                </h5>
                <h6 className="card-subtitle mb-2 text-muted">{airDate}</h6>
                </div>
            </div>
            </div>
        );
    };
---------------------------------------------------------
/=/=/ Пагинация - постраничная навигация (pagination)
---------------------------------------------------------
Для того чтобы отображать только часть записей, нам нужно при переключении между страницами получать новый массив из массива эпизодов. 
---------
Нахождение индексов элементов для вырезки:

    const users = Array(14).fill("").map((_, i) => "user" + (i + 1));

    const itemsPerPage = 4;

    function usersOnPage(users, itemsPerPage, pageNum) {
        const firstIndex = itemsPerPage * (pageNum - 1);
        return [...users].splice(firstIndex, itemsPerPage);
    }

    usersOnPage(users, itemsPerPage, 1); ['user1', 'user2', 'user3', 'user4']
    usersOnPage(users, itemsPerPage, 4); [ 'user13', 'user14' ]

---------
    const paginate = (items, pageNumber, pageSize) => {
        const startIndex = (pageNumber - 1) * pageSize;
        return [...items].splice(startIndex, pageSize);
    };

    // [...items] - Создаем копию, чтобы не мутировать оригинал
    // Высчитываем startIndex 
    // Передаем в splice() index элемента с которого начинаем 
    // Передаем в splice() кол-во элементов для вырезки

---------
/=/=/ React Paginate - библиотека для реализации пагинации пользователей
---------
    $ yarn add react-paginate
// OR
    $ npm install react-paginate --save

---------
    import ReactPaginate from 'react-paginate';

    function MyComponent() {
        const handlePageChange = (selectedPage) => {
            // Обработка изменения страницы
        };

        return (
            <ReactPaginate
            pageCount={10}
            onPageChange={handlePageChange}
            containerClassName={'pagination'}
            activeClassName={'active'}
            />
        );
    }

Передаем количество страниц в свойство pageCount, функцию обратного вызова для обработки изменения страницы в свойство onPageChange, классы CSS для контейнера и активной страницы в свойства containerClassName и activeClassName.


---------------------------------------------------------
/=/=/=/ PropTypes 
---------------------------------------------------------

    $ yarn add prop-types
// OR
    $ npm i prop-types

PropTypes позволяет определить ожидаемые типы данных для свойств (props) компонентов и предупреждать об ошибке, если они не соответствуют ожидаемому типу данных.

MyComponent.propTypes = {
    
Можно объявить проп на соответствие определённому JS-типу.
    optionalArray: PropTypes.array,
    optionalBool: PropTypes.bool,
    optionalFunc: PropTypes.func,
    optionalNumber: PropTypes.number,
    optionalObject: PropTypes.object,
    optionalString: PropTypes.string,
    optionalSymbol: PropTypes.symbol,

Все, что может быть отрендерено:
числа, строки, элементы или массивы
(или фрагменты) содержащие эти типы
    optionalNode: PropTypes.node,

React-элемент
    optionalElement: PropTypes.element,

Тип React-элемент (например, MyComponent).
    optionalElementType: PropTypes.elementType,
    
Можно указать, что проп должен быть экземпляром класса
Для этого используется JS-оператор instanceof.
    optionalMessage: PropTypes.instanceOf(Message),

Вы можете задать ограничение конкретными значениями
при помощи перечисления
    optionalEnum: PropTypes.oneOf(['News', 'Photos']),

Объект, одного из нескольких типов
    optionalUnion: PropTypes.oneOfType([
        PropTypes.string,
        PropTypes.number,
        PropTypes.instanceOf(Message)
    ]),

Массив объектов конкретного типа
    optionalArrayOf: PropTypes.arrayOf(PropTypes.number),

Объект со свойствами конкретного типа
    optionalObjectOf: PropTypes.objectOf(PropTypes.number),

Объект с определённой структурой
    optionalObjectWithShape: PropTypes.shape({
        color: PropTypes.string,
        fontSize: PropTypes.number
    }),
    
При наличии необъявленных свойств в объекте будут вызваны предупреждения
    optionalObjectWithStrictShape: PropTypes.exact({
        name: PropTypes.string,
        quantity: PropTypes.number
    }),     

Можно добавить`isRequired` к любому приведённому выше типу, чтобы показывать предупреждение, если проп не передан
    requiredFunc: PropTypes.func.isRequired,

Обязательное значение любого типа
    requiredAny: PropTypes.any.isRequired,
};

-------------------
/=/=/ Указать проверку на Date()
---------
Component.propTypes = {
  pickedDate: PropTypes.instanceOf(Date) // Ожидаем объект типа Date
};

---------------------------------------------------------
/=/=/ Передать в функцию аргументы от propTypes
-------------------
DropdownComponent.propTypes = {
  /=/ Если isAdditionEnabled === true, то onElemAdding required
  onElemAdding: (props, propName, componentName) =>
    checkOnPropRequired(
      props,
      propName,
      props.isAdditionEnabled,
      componentName
    )
};
---------
->> Функция принимающая аргументы

const checkOnElemAdding = (
  props,
  propName,
  isExistedPropName,
  componentName
) => {
  if (isExistedPropName && !props[propName]) {
    return new Error(
      `The prop ${propName} is required when isAdditionEnabled is set to true in ${componentName}.`
    );
  }
};

export default checkOnElemAdding;


-------------------
// isRequired
---------
isRequired следует использовать тогда, когда свойство является обязательным для работы компонента или когда его отсутствие может привести к ошибкам или некорректному поведению компонента.

-------------------
/=/=/ Значения пропсов по умолчанию 
---------
    class Greeting extends React.Component {
        static defaultProps = {
            name: 'Незнакомец'
        }

        render() {
            return (
            <div>Привет, {this.props.name}</div>
            )
        }
    }

---------
Обозначаем какие типы данных должны передаваться в качестве свойств:

    <Pagination
        itemsCount={count} 
          // Должно быть числом. Должно обязательно передаваться.
        pageSize={pageSize}
        onPageChange={handlePageChange}
        currentPage={currentPage}
    />
    
    Pagination.propTypes = {
        itemsCount: PropTypes.number.isRequired,
        pageSize: PropTypes.number.isRequired,
        onPageChange: PropTypes.func.isRequired,
        currentPage: PropTypes.number.isRequired,
    };
    // isRequired - свойство является обязательным для передачи компоненту

-------------------
// .shape({ }) - Обозначение проверки вложенных объектов.
---------
// .arrayOf( ) - Массив определенного типа 

    qualities: PropTypes.arrayOf(
        PropTypes.shape({
            name: PropTypes.string.isRequired
        })
    )
---------
Проверка на массив, где каждый элемент является числом:

    PropTypes.arrayOf(PropTypes.number)
---------
    const Qualities = ({ user: { name, qualities } }) => {
        ...
    }

    Qualities.propTypes = {
        user: PropTypes.shape({
            name: PropTypes.string.isRequired,
            qualities: PropTypes.arrayOf(
                PropTypes.shape({
                    _id: PropTypes.string.isRequired,
                    name: PropTypes.string.isRequired,
                    color: PropTypes.string.isRequired
                })
            ).isRequired
        }).isRequired
    };

---------
/=/=/ <Pagination Ctr+Space/> - отображение доступных свойств и методов этого компонента

---------------------------------------------------------
/=/=/ ESLint
---------------------------------------------------------
Глобальная установка ESLint (чтобы не устанавливать для каждого проекта)
    $ yarn global add eslint
// Or
    $ sudo npm i -g eslint

-------------------
Установка и настройка файла конфигурации:

!  $ eslint --init

   /* eslint-disable */
-------------------
/=/=/ Установка необходимых пакетов для ESLint
---------
    $ yarn add @vitejs/plugin-react

  ? $ yarn add eslint eslint-plugin-react eslint-config-react-app --dev
      // устанавливает ESLint и связанные с ним пакеты, необходимые для проверки кода React
      
  ? $ yarn add -D vite-plugin-eslint 
      // автоматически запускает ESLint при запуске dev-сервера

---------
// vite.config.js:
---------
    import { defineConfig } from "vite";
    import react from "@vitejs/plugin-react";
    // import eslintPlugin from "vite-plugin-eslint";

    export default defineConfig({
        plugins: [react()]
    });
---------
// .eslintrc.cjs
    "rules": {
        "block-spacing": "off",
        "brace-style": "off"
    }
---------
// .eslintrc.cjs:
module.exports = {
    env: {
        browser: true,
        es2022: true
    },
    extends: [
        "plugin:react/recommended",
        "standard"
    ],
    parserOptions: {
        ecmaFeatures: {
        jsx: true
        },
        ecmaVersion: "latest",
        sourceType: "module"
    },
    plugins: [
        "react"
    ],
    rules: {
        "multiline-ternary": "off",
        // indent: ["error", 2],  
        indent: "off",
         // Отступ количество пробелов 
        semi: [2, "always"], 
         // Точка с запятой в конце строки
         "space-before-function-paren": [
            "error",
            { anonymous: "always", named: "never" }
        ],
         // Ошибка при наличии пробела при обозначении функции, уберём её
        quotes: ["error", "double", { allowTemplateLiterals: true }],
         // Использование двойных кавычек
    }
};
-------------------
/=/ Обновленная конфигурация `eslint`
---------
|> .eslint.cjs

    module.exports = {
      env: { browser: true, es2020: true },
      extends: [
        "eslint:recommended",
        "plugin:react/recommended",
        "plugin:react/jsx-runtime",
        "plugin:react-hooks/recommended"
      ],
      parserOptions: { ecmaVersion: "latest", sourceType: "module" },
      settings: { react: { version: "18.2" } },
      plugins: ["react-refresh"],
      rules: {
        "react-refresh/only-export-components": "warn",
        "multiline-ternary": "off",
        indent: "off",
        semi: [2, "always"],
        "space-before-function-paren": [
          "error",
          { anonymous: "always", named: "never" }
        ],
        quotes: ["error", "double", { allowTemplateLiterals: true }]
      }
    };
---------
|> .prettierrc.cjs

    module.exports = {
        trailingComma: "none",
        tabWidth: 2,
        semi: true,
        printWidth: 70 // перенос строк 
    };

---------
Отформатировать все документы согласно правилам:

    $ npx prettier --write .
    $ npx prettier --write "src/**/*.{js,jsx,ts,tsx}"

Отформатирует все файлы в директории src, включая все поддиректории. Опция --write означает, что Prettier изменит файлы напрямую, без создания копий.
-------------------
/=/=/ Если Prettier не форматирует:
---------
!!! Проверить название и расширение файла, должно быть: 

    .prettierrc.cjs 

---------
// OR
---------
В settings.json vs_code:
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "eslint.alwaysShowStatus": true

---------------------------------------------------------
/=/=/ useEffect() - вызывается каждый раз когда мы монтируем что-то в DOM
---------------------------------------------------------
Метод useEffect предназначен отслеживания этапа на котором находится наблюдаемый элемент (1й рендер / изменение компонента / демонтаж) и вызова тела функции useEffect 

useEffect() может срабатывать при:
    *каждом ререндере компонента
    *первом рендере
    *изменении какой-то зависимости
    *демонтаже компонента

    useEffect(()=>{
        // При первом рендере компонента
    }, [])

    useEffect(()=>{
        // При каждом рендере компонента
    })

    useEffect(()=>{
        // При изменении зависимостей someProps1, someProps2
    }, [someProps1, someProps2, наблюдаемый_элемент_3]) 

    useEffect(()=>{
        return () => {
            // вызовется при демонтаже компонента 
        }
    })
---------------------------------------------------------
/=/=/ new Map() - это встроенный объект в JavaScript, который представляет собой коллекцию пар "ключ-значение"
---------------------------------------------------------
Ключом может быть любое значение, включая объекты и функции, а значением - любое значение, включая другие Map-ы.

Map обычно используется, когда вам нужно хранить пары "ключ-значение" и обращаться к ним по ключу. 
Map также может быть полезен, когда вам нужно создать словарь или кеш, где ключами и значениями являются произвольные объекты.

---------
Например, вы можете использовать Map для хранения информации о клиентах, где ключом будет id клиента, а значением - объект, содержащий информацию о клиенте:

    const clients = new Map();

    clients.set(1, { name: "John", age: 30, email: "john@example.com" });
    clients.set(2, { name: "Alice", age: 25, email: "alice@example.com" });
    clients.set(3, { name: "Bob", age: 40, email: "bob@example.com" });

    console.log(clients.get(2)); 
    // выведет { name: "Alice", age: 25, email: "alice@example.com" }

---------
Map для подсчета количества вхождений элементов в массиве или другой коллекции:

    const arr = [1, 2, 3, 2, 1, 3, 2, 1];
    const counts = new Map();

    for (let elem of arr) {
        if (counts.has(elem)) {
            counts.set(elem, counts.get(elem) + 1);
        } else {
            counts.set(elem, 1);
        }
    }

    console.log(counts.get(2)); // выведет 3

Map поддерживает множество методов для работы с коллекцией, таких как 
set, get, has, delete и clear.

    set(key, value) - добавляет новую пару "ключ-значение" в Map. Если ключ уже существует в Map, то его значение обновляется.
    
    get(key) - возвращает значение, связанное с заданным ключом. Если ключ не существует в Map, то возвращается undefined.

    has(key) - возвращает true, если заданный ключ существует в Map, иначе возвращает false.

    delete(key) - удаляет пару "ключ-значение", связанную с заданным ключом из Map. Если ключ не существует в Map, то метод ничего не делает.

    clear() - удаляет все пары "ключ-значение" из Map.
    
---------------------------------------------------------
/=/=/ Алгоритм Ньютона вычисления квадратного корня из числа
-------------------
    x(0) = 8 / 2 = 4
    x(1) = 0.5 * (4 + 8 / 4) = 2.5
    x(2) = 0.5 * (2.5 + 8 / 2.5) = 2.05
    x(3) = 0.5 * (2.05 + 8 / 2.05) = 2.803
    x(4) = 0.5 * (2.803 + 8 / 2.803) = 2.8284
---------------------------------------------------------
/=/=/ console.assert() - метод для проверки утверждений.
-------------------
    const num = 10;
    console.assert(num === 5, "num должно быть равно 5");
---------
    const num = 10;
    console.assert(num === 5, num);
---------
    console.assert(climbStairs(2) === 2);
    console.assert(climbStairs(3) === 3);
    console.assert(climbStairs(4) === 5);
    console.assert(climbStairs(5) === 8);
    console.assert(climbStairs(6) === 13);
---------------------------------------------------------
// Создать Массив и заполнить его 
-------------------
    const table = new Array(5).fill(0);
    console.log(table) [ 0, 0, 0, 0, 0 ]

-------------------
/=/=/ .padStart() / .padEnd() - дополняет длину строки, если не хватает 
---------
    const str1 = '5';

    console.log(str1.padStart(2, '0')); // Expected output: "05"
    console.log(str1.padEnd(2, '0')); // Expected output: "50"

---------
    const fullNumber = '2034399002125581';
    const last4Digits = fullNumber.slice(-4);
    const maskedNumber = last4Digits.padStart(fullNumber.length, '*');

    console.log(maskedNumber);
    // Expected output: "************5581"

---------------------------------------------------------
/=/=/ .flatMap() + .map() - Замена двух циклов с выравниванием 
-------------------
    const x = ['2', '3', '6'];
    const y = ['3', '5', '6', '9', '6', '8', '9'];

    const result = x.flatMap(elemX => y.map(elemY => elemX + elemY));

    console.log(result);
    // Output: [ '23', '25', '26', '29', '26', '28', '29', '33', '35', '36', '39', '36', '38', '39', '63', '65', '66', '69', '66', '68', '69' ]

---------------------------------------------------------
/=/=/ Слой абстракции — минимум, необходимый для взаимодействия с компонентами, без лишних деталей.
-------------------

return (
    <div className="d-flex">
        {professions && (
            <div className="d-flex flex-column flex-shrink-0 p-3">
            <GroupList
                items={professions}
                selectedItem={selectedProf}
                onItemSelect={handleProfessionSelect}
            />
            <button
                className="btn btn-secondary btn-sm mt-2"
                onClick={handleResetFilters}
            >
                Очистить
            </button>
            </div>
        )}
        <div className="d-flex flex-column">
            {isLoaded && <SearchStatus numberOfUsers={pageSize} />}
            {pageSize > 0 && (
            <UsersTable usersCurntPage={itemsCurntPage} {...rest} />
            )}
            <div className="d-flex justify-content-center">
            <Pagination
                pageSize={pageSize}
                itemsPerPage={itemsPerPage}
                onPageChange={handlePageChange}
                currentPage={currentPage}
            />
            </div>
        </div>
    </div>
    );
};

Например, руководитель не разрабатывает приложение и не рисует дизайн. Он говорит, какому отделу что нужно сделать. Так и в нашем примере. В users.jsx мы пишем высокоуровневый код, в котором следим, только за самой логикой, не отвлекаясь на отображение.

---------------------------------------------------------
/=/=/ React Router Dom (RRD) - позволяет перемещаться между страницами без их перезагрузки 
---------------------------------------------------------
Тем самым мы реализуем SinglePageApplication (SPA)

    $ yarn add react-router-dom@5.3.0

    $ npm install react-router-dom
-------------------
! Внимание! 
!!! Для задействования React Router необходимо обернуть наше приложение в

    <BrowserRouter>
        <App />
    </BrowserRouter>

---------
// main.jsx
    import React from "react";
    import ReactDOM from "react-dom/client";
    import App from "./app/App";
    import { BrowserRouter } from "react-router-dom";

    ReactDOM.createRoot(document.getElementById("root")).render(
        <React.StrictMode>
            <BrowserRouter>
                <App />
            </BrowserRouter>
        </React.StrictMode>,
    );

---------------------------------------------------------
/=/=/ Route -  используется для создания маршрутов на веб-странице, т.е. чтобы определить, какой компонент React будет отображаться при изменении URL-адреса в браузере.
-------------------
То есть, если URL меняется на определенный, то на страницу выводится установленный Компонент со своим контентом.
А пример с `NavBar`, при клике на "href" <a href="/">Главная</a>, лишь позволяет сменить URL в браузере. 
Но сам `NavBar` здесь не играет роли.

    import Home from "./components/navBar/home";
    import { Route } from "react-router-dom";

    <Route path="/" exact component={Home} />
        
---------
Если нет атрибута `exact`, то Route будет вызываться и на вложенные страницы. 

Например, путь “/post/id” тоже будет срабатывать для роута:
<Route path="/post" component={Posts} />

-------------------
// Отличие `Switch` и `exact`
---------
    
---------------------------------------------------------
/=/=/ Switch -  коммутатор. Будет отображать `один из`
-------------------
Может выступать как аналог для атрибута `exact`. 
! Внимание! Но Switch работает последовательно!

!!! Switch и Route всегда должны возвращаться. Иначе не будут работать!

Сработает:
return (
    <Switch>
        <Route path="/login" component={Login} />
        <Route path="/posts" component={Posts} />
        <Route path="/dashboard" component={Dashboard} />
        <Route path="/" component={Home} />
    </Switch>
)
return (
    <Switch>
        <Route exact path="/" component={Home} />
        <Route path="/login" component={Login} />
        <Route path="/posts" component={Posts} />
        <Route path="/dashboard" component={Dashboard} />
    </Switch>
)

Не сработает:
    <Switch>
        <Route path="/" component={Home} />
        <Route path="/login" component={Login} />
        <Route path="/posts" component={Posts} />
        <Route path="/dashboard" component={Dashboard} />
    </Switch>

Тк Switch находит совпадение по первому символу и оставляет его.

!!! Из этого следует, что при использовании Switch необходимо упорядочить наши маршруты от наиболее Конкретизированных => к наиболее Общим
---------------------------------------------------------
/=/=/ Link to="" - позволяет загружать элементы без обновления стр. Тк берет их из памяти и обновляет только нужные элементы.
-------------------
При вбивании URL напрямую или все остальные способы без метода `Link` - будет происходить перезагрузка стр.

    <li>
      <a href="/">Home</a>
    </li>
    
    const NavBar = () => {
      return (
        <ul>
            <li>
                <Link to="/">Home</Link>
            </li>
        </ul>
      )
    }
-------------------
// Разница между <Link/> и history.push() 
---------
<Link/> обрабатывает клик на ссылку, обновляет URL и перенаправляет пользователя на новую страницу)
history.push() изменяет URL вручную, но перенаправляет пользователя на новую страницу без необходимости клика на ссылку.

В вашем случае, если вы хотите, чтобы пользователь перешел на другую страницу при клике на кнопку "Редактировать", вы можете использовать <Link/>. 
Если вы хотите *программно* перенаправить пользователя на другую страницу при выполнении какого-либо действия, то вы можете использовать history.push().

---------------------------------------------------------
/=/=/ Route путь и передача через него Props
-------------------
1) Отображение Компонента без доп параметров
    
    /=/ Передаются history, location, match. 
     >- Не передаются мои Props
    <Route path="/dashboard" component={Dashboard} />
    
    /=/ Через атрибут render. 
     >- Не передаются history, location, match
    <Route path="/" render={() => <Home withSidebar/>} />

    /=/ Передать как потомка. 
     >- Не передаются history, location, match
        Но их можно получить через методы React Router.
    <Route path="/">
        <Home withSidebar/>
    </Route>

2) Когда необходимо не просто передать компонент, а что-то с ним сделать 
    (Передать пропсы/add условия отображения/итд)

    <Route
        path="/dashboard"
        render={(props) => {
            return true && <Dashboard isAdmin={false} {...props} />;
        }}
    />

    /=/ Передать потомка как render-функцию. 
     >- Передаются history, location, match
    <Route path="/">
        { (routeProps) =>  <Home {...routeProps} withSidebar/> }
    </Route>

    /=/ Необязательно возвращать Компонент, можно вернуть что угодно
    <Route path="/catalog/:category?/:subCategory?">
        {({ match }) => <pre>{JSON.stringify(match.params)}</pre>}
    </Route>

-------------------
Вызывая функцию мы возвращаем в нее Компонент вместе с его пропсами (history,  location, match). 
Результат(Компонент) данной функции будет передан для отображения.

С помощью вызова функции и передачи в нее аргументов (props) - мы получаем объекты history и location и свойство match из библиотеки React Router.

    *Объект history содержит информацию о текущей и предыдущих страницах в истории браузера. Он имеет методы для навигации по истории браузера, такие как push, replace и goBack.

    *Объект location содержит информацию о текущем URL-адресе(где мы сейчас находимся), такую как хэш, путь и строку запроса.

    *Свойство match содержит информацию о том, как текущий URL соответствует маршруту в компоненте <Route>. 
    Оно имеет свойства, такие как isExact, которое указывает, соответствует ли текущий URL точно маршруту Route, и params, которое содержит параметры маршрута.

---------------------------------------------------------
/=/=/ Использование Route для настройки URL путей
-------------------
Допустим, мы хотим на странице “/posts” выводить все статьи.
А например на “/posts/123” хотим выводить какую-то конкретную запись. 

Для этого мы должны указать URL-параметры. Добавим новый роут и у него укажем:

return (
    <Switch>
        <Route path="/" exact component={Home} />
        <Route path="/signin" component={SignIn} />
        <Route path="/posts/:postId" component={Posts} />
        <Route path="/posts" component={Posts} />
        <Route path="/contacts" component={Contacts} />
    </Switch>
)

URL-параметры указываются в виде “:{param}” (двоеточие, название переменной). 

Теперь, перейдя по адресу “/posts/231”, мы увидим, что в props в matсh по ключу params попало postId:231

---------------------------------------------------------
/=/=/ Указание опциональных параметров
-------------------
=<< path="/posts/:postId?" - говорит маршрутизатору о том что, независимо есть ли `postId` или `postId` нет - он должен отобразить Компонент <Posts {...props}/>

return (
    <Switch>
        <Route
            path="/posts/:postId?"
            render={(props) => <Posts {...props} />}
        />
    </Switch>
)
-------------------
// Отличие userId? и userId
---------
    path="/users/:userId?" 
    path="/users/:userId"

Если вы хотите, чтобы userId был опциональным параметром в пути, вы можете использовать знак вопроса ? после параметра :userId в пути: "/users/:userId?".

Это означает, что путь "/users/" и "/users/123" будут оба допустимыми, а параметр :userId будет опциональным. 
Если userId не указан в пути, он будет undefined. Если userId указан в пути, его значение будет соответствовать значению, указанному после /users/.

Если же вы хотите, чтобы userId был обязательным параметром в пути, то используйте путь "/users/:userId". В этом случае, только путь "/users/123" будет допустимым, а запросы к "/users/" будут несоответствующими.
-------------------
// Отличие 
    /catalog/category - Фиксированный, статический путь
    /catalog/:category - Динамический, необходимый путь
    /catalog/:category? - Динамический опциональный путь
---------
=<< Фиксированный путь:

    ~~> "/catalog/category"
    -> "https://example.com/catalog/category"

=<< Динамический, но необходимый параметр пути:

    ~~> "/catalog/:category"
    -> "https://example.com/catalog/books"

=<< Динамический, не необходимый, опциональный параметр пути:

    ~~> "/catalog/:category?"
    -> "https://example.com/catalog"
    -> "https://example.com/catalog/books"

-------------------
// При каких условиях URL откроется этот компонент?
---------
    ~> <Route path="/users/:userId?/edit" component={Users} />

Этот компонент будет отображаться при любом URL, который начинается с /users/, за которым следует необязательный параметр userId, а затем /edit.

    -> /users/edit 
    -> /users/john.doe/edit
    /=/ Допустим пропуск параметра `userId`

---------
    ~> <Route path="/users/:userId/edit" component={UserEditPage} />

    -> /users/123/edit
    -> /users/john.doe/edit
    /=/ Недопустим пропуск параметра `userId` 

-------------------
// Указать путь с id пользователя
---------
   <Link to={`/users/${userId}/edit`} />

---------------------------------------------------------
/=/=/ Указание нескольких опциональных параметров
-------------------
Вопросительный знак "?" после каждого параметра указывает на необязательность параметра

|> App.jsx

    return (
        <Switch>
            <Route path="/posts/:postId?/:display?" component={Posts} />
        </Switch>
    )
---------
|> posts.jsx

    import PostList from "../postsList";
    import Post from "../post";

    const Posts = ({ match }) => {
      const posts = [
        { id: 1, title: "Post 1" },
        { id: 2, title: "Post 2" },
        { id: 3, title: "Post 3" },
      ];

      const postId = match.params.postId;
      const display = match.params.display;

      return (
        <>
          {/* Передаем ли мы опциональный URL адрес поста? */}
          {postId ? (
            <>
              {display && <h2>{display}</h2>}
              <Post posts={posts} id={postId} />
            </>
          ) : (
            <PostList posts={posts} />
          )}
        </>
      );
    };
    
-------------------
=<< Refactoring App.jsx
---------
|> App.jsx

  const App = () => {
    return (
      <>
        <Switch>
Стало ==> <Route path="/users/:userId?" component={Users} />   
          <Route path="/login" component={Login} />
          <Route path="/" component={Main} />
          <Route component={Page404} />
        </Switch>
      </>
    );
  };

|> Users.jsx

  const Users = () => {
    const params = useParams();
    const { userId } = params;
  
    return <>{userId ? <UserPage userId={userId} /> : <UsersListPage />}</>;
  };
  export default Users;
---------
Было:
|> App.jsx
    <Switch>
        <Route path="/users/:userId" component={User} />
        <Route path="/users/" component={UsersListPage} />
    </Switch>

-------------------
function App() {
    return (
        <Switch>
            <Route path="/catalog/:category?/:subCategory?">
                {({ match }) => <pre>{JSON.stringify(match.params)}</pre>}
            </Route>
        </Switch>
    );
}

    path=                     "/catalog/:category?/:subCategory?"
    URL: http://localhost:5174/catalog/tools/hammer

    {"category":"tools","subCategory":"hammer"}

-------------------
    // Последовательность параметров в URL
    const pathConfig = ['year', 'month', 'date', 'slug']

    // Паттерн для роута
    const routePath = "/:" + pathConfig.join('/:') // -> /:year/:month/:date/:slug

    <Route path={routePath} component={Post}/>

При обращении на URL “/2022/02/12/my-post” будет срабатывать наш роут. 

---------------------------------------------------------
/=/=/ Query-параметры - параметры запроса в URL, перечисленные после знака “?” 
---------------------------------------------------------
(очень часто таким образом организуют хранение фильтров или страниц пагинации).
! С помощью него можно проверить передается ли опциональный параметр в URL.

    $ yarn add query-string 

    import query from "query-string";

-------------------
// query.parse() - Преобразует строку запроса  в Объект 
---------
    const search = query.parse("name=John&age=30") 

    console.log(search) // { name: 'John', age: '30' }
-------------------
! Внимание! 
! Как проверить передается ли опциональный параметр в URL:

Передаем опциональный параметр в URL:
    http://localhost:5173/posts/?count=1
    const search = query.parse(location.search); // { count: '1' }

Не передаем опциональный параметр в URL:
    http://localhost:5173/posts 
    const search = query.parse(location.search); // {}

Необходимо проверить есть ли в нашем пропарсеном Объекте наш опциональный параметр-ключ. В частности `count` (тк в URL пишем count=1)

  const cropPosts = search.count
    ? _(posts).slice(0).take(search.count).value()
    : posts;

Иначе будет всегда выдаваться true. Тк просто `search` даже без передачи опциональный параметров (http://localhost:5173/posts) выдаст пустой Объект. 
А пустой Объект {} === true

-------------------
    Параметры запроса: /posts/?name=John&count=30"

    query.parse(location.search) => // {count: '30', name: 'John'}
-------------------
Удобная деструктуризация

  const search = query.parse(location.search); 
  // { block: 'pr_1', fromUrl: 'https://example.partner.com' }

  const { block, fromUrl } = search;

---------------------------------------------------------
/=/=/ Redirect - перенаправляет пользователя на другую страницу
-------------------
Когда пользователь попадает на страницу, содержащую компонент "Redirect", его браузер автоматически перенаправляется на указанный в компоненте URL. 

    <Switch>
        <Route path="/dashboard" component={Dashboard} />
        <Redirect from="/admin" to="/dashboard" /> 
          // Перенаправит со старого адреса: /admin на новый: /dashboard

          // Если ничего не найдено         => Redirect на путь /404 
          // Если мы перешли по path="/404" => отобразить Компонент 
        <Route path="/404" component={NotFound} />
        <Redirect to="/404" /> 
          // Всегда в самом низу
    </Switch>
---------------------------------------------------------
/=/=/ Перенаправление на страницу 404
-------------------
Есть два варианта. Добавляем в конце

    <Switch>
        ...
        <Route path="/404" component={NotFound} />
        <Redirect to="/404" /> 
    </Switch>
---------
     <Switch>
        ...
        <Route component={NotFound} />
    </Switch>         

---------------------------------------------------------
/=/=/ location, history и match - содержат информацию о текущем маршруте и позволяют вашим компонентам взаимодействовать с историей браузера и URL.
-------------------
Маршрут: /users/:userId
    URL: /users/123

Текущий Маршрут: В объекте `match` вы можете получить доступ к текущему маршруту с помощью свойства `path`
---------
Текущий URL-адрес: В объекте `location` вы можете получить доступ к текущему URL-адресу с помощью свойства `pathname`.
---------

    * location - Все про URL. Содержит информацию о текущем URL, включая pathname, search, hash и state.
      - `search` - содержит параметры Запроса. 
      Параметры Запроса: запрос добавляется к URL-адресу после символа (?) и разделяются знаком (&). 
      Например, если текущий URL /users/123?name=John, то `search` будет равен '?name=John'.
      - `pathname` - указывает на текущий маршрут. 
      Например, если текущий URL /users/123, то `pathname` будет равен /users/123.
      - `hash` - это часть URL-адреса, которая содержит хэш. Хэш используется для прокрутки к определенному элементу на странице. Хэш добавляется после знака (#). 
      Например, если текущий URL /users/123#profile, то hash будет равен #profile.
      - `state` - это объект, который может быть использован для передачи данных между маршрутами. 
      Например, вы можете установить `state` в объект, содержащий данные о пользователе, при переходе на страницу пользователя.

    * history используется для управления историей браузера и переходами между страницами.
      - `push`(path, [state]) - перенаправляет на указанный маршрут, добавляет новую запись в историю браузера. Необязательный параметр `state` - предназначен для сохранения необходимой информации при переходе между страницами.
      - `replace`(path, [state]) - заменяет текущую запись в истории браузера на новую и перенаправляет на указанный маршрут.
      - `location` - описывает текущий URL-адрес.
      - `go`(n) - перемещается в истории браузера на указанное количество записей. Если n равно -1, то перемещается на одну запись назад, если n равно 1, то перемещается на одну запись вперед.
      - `goBack`() - перемещается на одну запись назад в истории браузера.
      - `goForward`() - перемещается на одну запись вперед в истории браузера.
      - `action` - это строка, указывающая на тип действия, приведшего к текущей записи в истории. 
      Возможные значения: PUSH (добавление новой записи), POP (перемещение на другую запись в истории), REPLACE (замена текущей записи на другую).
      - `length` - количество записей в истории браузера.

    * match - соответствие текущего URL и маршрута. Он содержит параметры, переданные в URL, данные о самом маршруте и т.д.
      - `params` - определить параметры переданные в URL. 
      Например, если маршрут определен как /users/:userId, а 
      текущий URL /users/123, то params будет содержать { userId: '123' }.
      - `path` - это строка, которая определяет шаблон маршрута. Шаблон маршрута  сопоставляется с текущим URL-адресом и позволяет определить, какой Компонент должен быть отображен на странице.
      Например, если маршрут определен как /users/:userId, то
      `path` будет равен /users/:userId. 
      - `url` - это строка, которая содержит фактический URL-адрес, соответствующий маршруту. 
      Например, если маршрут определен как /users/:userId, и текущий URL /users/123, то url будет равен /users/123.
      - `isExact` - это булевое значение, которое указывает, соответствует ли текущий URL полностью маршруту. Если isExact равен true, то URL точно соответствует маршруту. Если isExact равен false, то URL соответствует маршруту только частично.

---------------------------------------------------------
/=/=/ {History} - используется для переадресации пользователя на другую стр.
-------------------
push() - перенаправить пользователя на другую страницу, без перезагрузки

// При клике вернет на страницу /posts с возможностью возврата на прошлую стр.
    <button onClick={() => history.push(`/posts`) }>
        Save
    </button> 

---------
// При клике вернет на страницу /posts без возможности возврата на прошлую стр.
    <button onClick={() => history.replace(`/posts`) }>
        Save
    </button> 

replace() - перенаправляет, но пользователь не сможет вернуться обратно (заменяем текущую страницу)

То есть при replace(), в Объекте `history` не добавляется новое событие что пользователь перешел на другую стр, а заменяется текущая стр.

---------------------------------------------------------
/=/=/ Хуки react-router-dom - получение информации о текущем маршруте, истории браузера и для перенаправления на другой маршрут
-------------------
Используя их, отпадает необходимость передавать через пропсы `{history} {location} {match}` в дочерние компоненты   

    * useHistory() - позволяет получить доступ к объекту истории браузера, который можно использовать для перехода на другой маршрут или для получения информации о предыдущих маршрутах.
---------
        const history = useHistory();

        <button
           type="submit"
           onClick={() => history.push(`/users/${userId}`)}
        >
           Сохранить
        </button>
-------------------
    * useLocation() - позволяет получить текущий объект `location`, который содержит информацию о текущем URL-адресе и параметрах запроса.

        const location = useLocation();
        const isEdit = location.pathname.endsWith("/edit");
-------------------
    * useRouteMatch() - позволяет получить информацию о совпадении маршрута.
-------------------
    * useParams() - позволяет получить доступ к параметрам маршрута, определенным с помощью Route.
    (Выведет то, что указано после ":", но не статические параметры.
    /posts/ - статический. /:postId - динамический)

      URL: .../posts/231
      <Route path="/posts/:postId" component={Posts} />
---------
    Так выдаст `edit` из `useParams()`:

    |> App.jsx
        <Route path="/users/:userId?/:edit?" component={Users} />

    |> Users.jsx
        const Users = () => {
            const params = useParams();
            const { userId, edit } = params; 
            /=/ { userId: '67rdca3eeb7f6fgeed471817', edit: undefined }

            return <>{userId ? <UserPage {...params} /> : <UsersListPage />}</>;
        };
---------
    Так ==/НЕ/== выдаст `edit` из `useParams()`:

    |> App.jsx
        <Route path="/users/:userId?/edit?" component={Users} /> 
        /=/ Убрали ':' из `edit`

    |> Users.jsx
        const Users = () => {
            const params = useParams();
            const { userId, edit } = params; 
            /=/ { userId: '67rdca3eeb7f6fgeed471817', edit: undefined }

            return <>{userId ? <UserPage {...params} /> : <UsersListPage />}</>;
        };
-------------------
Получить доступ к истории браузера в компоненте React:

    import { useHistory } from 'react-router-dom';

    function MyComponent() {
        const history = useHistory();

        function handleClick() {
            history.push('/my-new-route');
        }

        return (
            <button onClick={handleClick}>Go to my new route</button>
        );
    }

---------------------------------------------------------
/=/=/ endsWith() - проверяет, заканчивается ли строка определенным элементом true/false.
-------------------
    const str = "Hello, world!";

    console.log(str.endsWith("world!")); // true
    console.log(str.endsWith(", world!")); // true

    console.log(str.endsWith("World!")); // false
    console.log(str.endsWith("Hello")); // false

---------------------------------------------------------
/=/=/ Вложенные пути (маршруты)
-------------------
Для того чтобы не писать здесь весь роут ("/dashboard/edit"), мы можем перенести его в компонент 

// App.jsx
    <Switch>
        <Route path="/contacts" component={Contacts} />
    <Switch />

// Contacts.jsx
    const Contacts = () => {
      return (
        <>
          <h1>Contacts</h1>
          <ul>
            <li>
              <Link to={"/contacts/departments-1"}>Depart 1</Link>
            </li>
            <li>
              <Link to={"/contacts/departments-2"}>Depart 2</Link>
            </li>
          </ul>
          <Switch>
            <Route
              path="/contacts/departments-1"
              component={() => <h3>Department 1</h3>}
            />
            <Route
              path="/contacts/departments-2"
              component={() => <h3>Department 2</h3>}
            />
          </Switch>
        </>
      );
    };
---------------------------------------------------------
/=/=/=/ Формы в React <label> <input>
---------------------------------------------------------
Формы в React создаются так же, как и в обычном HTML

    form>(div>label+input)*2

    <form action="">
      <div>
        <label htmlFor="email">Email</label>
        <input type="text" id="email" />
      </div>
---------
// <input> также можно указывать внутри <label>. В таком случае не нужно будет добавлять htmlFor/for. 
      <div>
        <label>
            Пароль{" "}
            <input type="password" id="password" />
        </label>
      </div>
    </form>
---------
`placeholder` это <label>, но только внутри поля и исчезает при вводе.

В случае с `<label>` мы:
    * Добавляем в верстку отдельный элемент <label>
    * У <input> добавляем атрибут id
    * Для <label> добавляем атрибут htmlFor с нужным id, чтобы связать <input>, к которому он относится. При клике на <label> происходит фокус на соответствующий <input>. 

Примечание: атрибут htmlFor в JSX является аналогом атрибута for в HTML.

---------------------------------------------------------
/=/=/ Идентификация полей. 
-------------------
Решение через добавление `<label>` и/или добавление атрибута `placeholder`.

    import React from "react";

    const MyForm = () => {
        // обработка события отправки формы
        const handleSubmit = (e) => {
            // do something
        };

    return (
        <p>
            <label htmlFor="email">Email</label>
            <input id="email" type="text" name="email" />
        </p>
        <p>
            <input placeholder="Email" type="text" name="email" />
        </p>

        <p>
            <label htmlFor="password">Пароль</label>{" "}
            <input id="password" type="password" name="password" />
        </p>
        <p>
            <input
              placeholder="Пароль"
              id="password"
              type="password"
              name="password"
            />
        </p>

        <p>
            <button type="submit">Отправить</button>
        </p>
    );
    };

    export default MyForm;

---------------------------------------------------------
/=/=/ Атрибут <input name="">
-------------------
// Назначение атрибутов `name` и `value` для элементов формы заключается в идентификации поля ввода на стороне сервера при отправке формы.

// Атрибут `id` должно быть уникальным на странице. 
Этот идентификатор используется для связи поля ввода с его меткой <label>. 
И для идентификации его на стороне клиента, но он не используется для отправки данных на сервер!

Поэтому мы не можем указать для переключателя `type="radio"` id="color".
Но можем написать `name`

    <form onSubmit={handleSubmit}>
        <label>
            Красный{' '}
            <input type="radio" name="color" />
        </label>
        <br />
        <label>
            Синий{' '}
            <input type="radio" name="color" />
        </label>
        <p>
            <button type="submit">Отправить</button>
        </p>
    </form>
};
---------------------------------------------------------
/=/=/ Атрибут defaultValue и defaultChecked
-------------------
С помощью атрибутов `defaultValue` и `defaultChecked` для <input type="text"> и <input type="checkbox">, соответственно, мы можем задавать начальное значение. 

! Если вы хотите создать управляемый компонент, вы должны использовать только свойство `value`. 
! Если вы хотите создать неуправляемый компонент, в котором значение элемента ввода задается по умолчанию, используйте только свойство `defaultValue`.

    <form onSubmit={handleSubmit}>
        <p>
            <label htmlFor="email">Email</label>{' '}
            <input
                id="email"
                name="email"
                defaultValue="mail@mail.ru"
            />
        </p>
    <form/>
---------------------------------------------------------
/=/=/ Контролируемые и Неконтролируемые Компоненты
-------------------
Чаще всего для решения наших задач неуправляемый режим не подходит.
(например, если мы хотим валидировать поля)
-------------------
// Контролируемый Компонент:
  (Идет через виртуальный DOM, оповещая React об изменении)
---------
    import React, { useState } from 'react';

    function ControlledComponent() {
        const [value, setValue] = useState(''); 
          // Указываем начальное значение в качестве пустой строки.
          // Так мы говорим React, что форма управляемая, иначе будет получена ошибка

        function handleChange(event) {
          setValue(event.target.value);
        }

        function handleSubmit(event) {
          event.preventDefault();
          console.log('Submitted value:', value);
        }

        return (
          <form onSubmit={handleSubmit}>
            <label>
              Enter a value:
              <input type="text" value={value} onChange={handleChange} />
            </label>
            <button type="submit">Submit</button>
          </form>
        );
    }

---------
/=/=/ onSubmit={} - свойство которое срабатывает при отправке формы
---------
/=/=/ onChange={} - свойство которое срабатывает при изменении в поле ввода. Передает в переданную функцию событие `event`
---------
В этом примере создается контролируемый компонент формы, который состоит из текстового поля и кнопки отправки. 
Значение текстового поля хранится в состоянии компонента, а обновляется через аттрибут `onChange` обратный вызов `handleChange()`. При отправке формы значение выводится в консоль.

-------------------
// Неконтролируемый Компонент:
  (Идет в обход виртуального DOM)
---------
    import React, { useRef } from 'react';

    function UncontrolledComponent() {
        const inputRef = useRef(null);
    
        function handleSubmit(event) {
          event.preventDefault();
          console.log('Submitted value:', inputRef.current.value);
        }
    
        return (
          <form onSubmit={handleSubmit}>
            <label>
              Enter a value:
              <input type="text" ref={inputRef} />
            </label>
            <button type="submit">Submit</button>
          </form>
        );
    }

В этом примере создается неконтролируемый компонент формы, который также состоит из текстового поля и кнопки отправки. Однако, в отличие от контролируемого компонента, значение текстового поля не хранится в состоянии компонента useState(), а получается из DOM через ссылку `inputRef`. При отправке формы значение выводится в консоль.

Хук useRef() создает объект, который хранит ссылку на выбранный элемент DOM. 
Для того чтобы создать ссылку на элемент, в него необходимо в качестве атрибута передать `ref={}`.

    const inputRef = useRef();
    console.log(inputRef.current.value); // Выдаст `value` поля <input />

    <input type="text" ref={inputRef} />

---------------------------------------------------------
/=/=/ useRef() - позволяет создавать изменяемые ссылки на элементы и значения, которые могут быть сохранены между рендерами компонента 
-------------------
Это может быть полезно для сохранения предыдущего значения переменной, хранения ссылки на DOM-элемент, или для хранения ссылки на значение, которое не вызывает рендеринг.

---------
=<< Пример использования useRef() для сохранения предыдущего значения переменной:
---------
    import React, { useRef, useEffect } from 'react';

    function MyComponent() {
        const [count, setCount] = useState(0);
        const prevCountRef = useRef(); 
        /=/ Будет хранить предыдущее значение переменной `count`

        useEffect(() => {
            prevCountRef.current = count;
            /=/ Показываем `useRef` переменную для запоминания
        });

        const prevCount = prevCountRef.current;
        /=/ Получаем предыдущее значение указанной переменной для запоминания

        return (
            <div>
                <p>Current count: {count}</p>
                <p>Previous count: {prevCount}</p>
                <button onClick={() => setCount(count + 1)}>Increment</button>
            </div>
        );
    }

---------
=<< Пример использования useRef() для сохранения ссылки на DOM-элемент:
---------
    import React, { useRef, useEffect } from 'react';

    function MyComponent() {
        const inputRef = useRef();
        /=/ Будет хранить ссылку на элемент <input>

        useEffect(() => {
            inputRef.current.focus(); 
            /=/ Фокус на поле ввода
        }, []);

        return (
            <div>
                <label htmlFor="my-input">Enter your name:</label>
                <input type="text" id="my-input" ref={inputRef} />
            </div>
        );
    }
-------------------
/=/ Содержит ли `ref` ссылка элемент - 
    ref.current.contains(target) 
---------
  const dropdownRef = useRef(null);

  useEffect(() => {
    const handleClickOutside = (event) => {
      if (dropdownRef.current && !dropdownRef.current.contains(event.target)) {
        setIsOpen(false);
      }
    };

    document.addEventListener("mousedown", handleClickOutside);

    return () => {
      document.removeEventListener("mousedown", handleClickOutside);
    };
  }, []);
  /=/ Мы удаляем слушатель, чтобы избежать утечек памяти. 
  Когда вы добавляете слушатель событий на DOM-элемент, это может привести к утечкам памяти, если слушатель не будет удален при размонтировании компонента или при необходимости перестроения компонента.

dropdownRef.current.contains(event.target) - это проверка, содержит ли ссылка dropdownRef.current элемент, на который было сделано нажатие (event.target).

---------------------------------------------------------
/=/=/ Обработка значений множества полей
-------------------
Каждый раз создавать новые обработчики для изменения каждого поля слишком неудобно и расточительно по времени. Нам нужно единое состояние для хранения всех значений полей и метод для их изменения:

import React, { useState } from "react";

const MyForm = () => {
    const [values, setValues] = useState({
        email: "",
        link: "",
        description: ""
    });

    const handleSubmit = () => {
        // do something...
    };

    const handleChange = (e) => {
        const { value, name } = e.target;
        setValues((prev) => ({
            ...prev,
            [name]: value
        }));
    };

    // Деструктуризируем для удобства
    const { email, link, description } = values;

    return (
        <div>
            <h2>Отчёт об ошибке</h2>

            <form onSubmit={handleSubmit}>
                <p>
                    <label htmlFor="email">Email</label>{' '}
                    <input
                        id="email"
                        name="email"
                        value={email}
                        onChange={handleChange}
                    />
                </p>
                <p>
                    <label htmlFor="link">
                        Ссылка на страницу с ошибкой
                    </label>{' '}
                    <input
                        id="link"
                        name="link"
                        value={link}
                        onChange={handleChange}
                    />
                </p>

                <p>
                    <label htmlFor="description">Описание</label>{' '}
                    <input
                        id="description"
                        name="description"
                        value={description}
                        onChange={handleChange}
                    />
                </p>

                <button type="submit">Отправить</button>
            </form>
        </div>
    );
};
export default MyForm;

В объекте values ключи совпадают со значениями атрибутов name. Таким образом, зная name, в функции handleChange() мы можем определенному полю в объекте values обновлять значение. 

Если мы захотим добавить ещё поля, то нужно будет только добавить состояния в values и вывести в верстку новые поля. 

---------------------------------------------------------
/=/=/ Переиспользуемое поле ввода (Переиспользуемый Компонент)
-------------------
// login.jsx
  const { email, pass } = data;

  return (
    <form className="d-inline-block mx-3" onSubmit={handleSubmit}>
      <div className="form-group">
        <label htmlFor="email">Email: </label>
        <input
          className="form-control"
          type="text"
          id="email"
          name="email"
          value={email}
          onChange={handleInputChange}
        />
      </div>
    <form/>
  )
                    \/ \/ \/
  return (
    <form className="d-inline-block mx-3" onSubmit={handleSubmit}>
        <div className="form-group">
          <TextField
            label={"Email:"}
            type="text"
            name="email"
            value={email}
            onChange={handleInputChange}
          />
        </div>
      <form/>
  )

// textField.jsx
  const TextField = ({ label, type, name, value, onChange }) => {
    return (
      <>
        <label htmlFor="email">{label}</label>
        <input
          className="form-control"
          type={type}
          id={name}
          name={name}
          value={value}
          onChange={onChange}
        />
      </>
    );
  };
  
  TextField.defaultProps = {
    type: "text"
  };
---------------------------------------------------------
/=/=/ Обработка отправки формы
-------------------
Нативный способ:
---------
Нативный HTML также позволяет отправлять формы с помощью специальных атрибутов `action` и `method`:

    const MyForm = () => {
        // ...

        return (
            <form action="html/send-form" method="post">
                {/* ... */}
            </form>
        );
    };

    * action – ссылка на скрипт, который обрабатывает форму. В данном случае у нас указана относительная ссылка, но также возможно указать полный URL. Пока что это просто информация для ознакомления, отправлять данные по ссылкам будем в следующих уроках.
    * method – способ отправки данных на сервер. В нативном HTML есть 2 основных метода: get и post (с ними познакомимся в следующих уроках).

! Но у такого подхода есть очень важная особенность. Отправка формы происходит синхронно, т. е. браузер отправляет запрос по адресу и отрисовывает на экран все, что вернется в ответ. Это приводит к полной перезагрузке страницы!
-------------------
В современном React-приложении в большинстве случаев формы отправляются именно асинхронно, используя методы REST API 

Процесс отправки начинается в момент события onSubmit и состоит из следующих шагов: 
    1. Предотвращение перезагрузки страницы // preventDefault() 
    2. Обработка данных, например валидация
    3. Отправка по API
    4. Получение ответа и обработка результатов (опционально)

    const [data, setData] = useState({ email: "", pass: "" });

    const handleSubmit = (e) => {
        e.preventDefault();
        console.log(data); // {email: 'Email', pass: 'Пароль'}
    };

    <form onSubmit={handleSubmit}>
        ...
    <form/>
---------------------------------------------------------
/=/=/ Валидация форм
-------------------
У валидации есть несколько подходов, заключающихся в том, в какой момент она срабатывает. Это может быть непосредственно перед отправкой, во время изменения данных или при переключении между полями. У каждого из этих способов есть свои недостатки и преимущества, мы будем использовать комбинированный способ. 

Для начала создадим состояние для хранения ошибок:
// issueForm.jsx
    const [errors, setErrors] = useState({});

// utils/validateRules.js
    export const isFilledField = (value) => Boolean(value.trim());

Реализуем саму функцию validate(). Она будет:
 * Принимать наши значения полей
 * Проверять, что они не являются пустой строкой
 * Возвращать объект с ошибками, если они есть

// utils/validator.js
    import { isFilledField } from "./validateRules";

    export const validate = (inputFields) => {
      const errors = {};

      for (const field in inputFields) {
        const value = inputFields[field];
        const hasError = !isFilledField(value);

        if (hasError) {
          errors[field] = `Поле ${field} обязательно`;
        }
      }
      return errors;
    };

Теперь можем использовать нашу функцию в компоненте формы. При изменении values мы будем вызывать функцию validate() и получать ошибки:

    import React, { useEffect, useState } from "react";
    import TextField from "../../utils/templates/textField";
    import { validate } from "../../utils/validators/validator";

    const IssueForm = () => {
        const [inputFields, setInputFields] = useState({
            email: "",
            link: "",
            description: ""
        });
        
        const [errors, setErrors] = useState({});

        const handleInputChange = (e) => {
            const { name, value } = e.target;
            setInputFields((prev) => ({
            ...prev,
            [name]: value
            }));
        };

        const foundErrors = validate(inputFields);

        useEffect(() => {
            setErrors(foundErrors);
        }, [inputFields]);

        const handleSubmit = (e) => {
            e.preventDefault();
            const hasErrors = Object.keys(foundErrors).length !== 0;
            if (hasErrors) return;
            console.log(inputFields);
        };

        const { email, link, description } = inputFields;

        return (
            <div>
            <h2>Отчёт об ошибке</h2>

            {/* Для удобства просмотра */}
            <div>
                <pre>{JSON.stringify(errors, null, 2)}</pre>
            </div>

            <form onSubmit={handleSubmit}>
                <TextField
                    label={"Email:"}
                    type="text"
                    name="email"
                    value={email}
                    onChange={handleInputChange}
                />
            </div>
        );
    };

    export default IssueForm;

---------------------------------------------------------
/=/=/ Отображение ошибки валидации
-------------------
// validationSchema.js

    export const validationSchema = {
        email: {
            isRequired: {
                message: "Электронная почта обязательна для заполнения"
            }
        },
        link: {
            isRequired: {
                message: "Ссылка обязательна для заполнения"
            }
        },
        description: {
            isRequired: {
                message: "Описание обязательно для заполнения"
            }
        }
    };

-------------------
// validateRules.js

    export const isRequired = (value) => Boolean(value.trim());
    export const isEmail = (value) => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value);
---------
// Refactoring 

    export default {
        isRequired: (value) => Boolean(value.trim()),
        isEmail: (value) => /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value),
        isUrl: (value) => /^https?:\/\/(www.)?[^\s]+$/g.test(value),
        isStrongPass: (value) => /(?=.*[A-ZА-Я])(?=.*[a-zа-я])(?=.*\d)/g.test(value),
        minLength: (value, allowValue) => value.length > allowValue,
        maxLength: (value, allowValue) => value.length < allowValue,
        isFio: (value) =>
          /^(([a-zA-Zа-яА-Я]+)\s){1,}(([a-zA-Zа-яА-Я]+)\s?){1,}$/.test(value)
    };

-------------------
// validate.js

    import { isRequired } from "./validateRules";

    export const validate = (inputFields, config) => {
    const errors = {};

    for (const field in inputFields) {
        const fieldVal = inputFields[field];
        const rulesForField = config[field];

    // Смотрим поле на установленные правила для него
        for (const rule in rulesForField) {
            const { message, allowValue } = rulesForField[rule];

        // Запускаем проверку значения поля по набору названий правил установленных него. (isRequired, isEmail).
            const hasError = !validator(rule, fieldVal);

            if (hasError) {
                errors[field] = message;
                break;
            }
        }
    }
        return errors;
    };

    const validator = (ruleName, value) => {
        switch (ruleName) {
        // Для ruleName === "isRequired" вызываем таковую функцию проверки
            case "isRequired":
                return isRequired(value);
            case "isEmail":
                return isEmail(value);
            default:
            return true;
        }
    };
---------
// Refactoring

    import validateRules from "./validateRules";

    export const validate = (inputFields, config) => {
    const errors = {};

    for (const field in inputFields) {
        const fieldVal = inputFields[field];
        const rulesForField = config[field];

        for (const ruleName in rulesForField) {
        const { message, allowValue } = rulesForField[ruleName];

    // Получение нужного валидатора
        const validator = validateRules[ruleName];
    // Вызываем валидатор, если он есть    
        const hasError = validator && !validator(fieldVal, allowValue);

        // Если из Объекта  с проверочными методами {validateRules} пытаются вытащить несуществующий метод rulesForField[undefined_ruleName], то логическая конструкция validator && ... вернет undefined. 
        А if (hasError) не выдаст false и итерация пойдет на следующий круг.
        
            if (hasError) {
                errors[field] = message;
                break;
            }
        }
    }
        return errors;
    };

-------------------
// login.jsx

const Login = () => {
    // ...

    // Возвращает { fieldName: message_error }
    const foundErrors = validate(inputFields, loginSchema);

    useEffect(() => {
        setErrors(foundErrors);
    }, [inputFields]);

    const handleSubmit = (e) => {
        e.preventDefault();
        const hasErrors = Object.keys(foundErrors).length !== 0;
        if (hasErrors) return;
        console.log(inputFields);
    };

    // ...
}
---------------------------------------------------------
/=/=/ Продвинутая Валидация. Regexp.
-------------------
Валидация RegExp email: 

    function validateEmail(email) {
        const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return regex.test(email);
    }

    console.log(validateEmail("example@gmail.com")); // true
    console.log(validateEmail("john.doe@example.co.uk")); // true
    console.log(validateEmail("jane+doe@example.net")); // true

    console.log(validateEmail("example")); // false
    console.log(validateEmail("example@")); // false
    console.log(validateEmail("example.com")); // false
    console.log(validateEmail("example@com")); // false

    >- ^[^\s@]+ означает, что строка должна начинаться с одного или более символов, которая не должна содержать пробелов или @
    >- @[^\s@]+ означает, что после символа @ должно следовать один или более символов, которые не являются пробелами или символами @.
    >- \.[^\s@]+$ означает, что после `точки` должно следовать один или более символов, которые не являются пробелами или символами @.
---------
    >- \S Соответствует чему угодно, кроме символа пробела, табуляции или новой строки.
---------
    >- \s Соответствует любому символу пробела, табуляции или новой строки.
---------
    >- /n/ - разбиения текста на параграфы 

        text.split(/\n/);
    /=/ Не Забывай про Экранизацию!
---------
    >- /+/ Соответствует одному или нескольким последовательным символам «a».
---------
    >- /^/ Частица "не". 
        [^abc] Соответствует любому символу, кроме a, b или c
        [^a-z] Соответствует любым символам, кроме символов в диапазоне от a до z.
---------    
    >- \d - обозначает все цифры
---------    
    >- \D - соответствует любому символу, не являющемуся цифрой (0-9)
---------     
    >- /./ - любой символ.
        /a.b/ - будет соответствовать строке "acb"
---------
    >- /.+/ - любые символы
--------- 
    >- /\./ - точка
---------    
    >- .{n,} - проверяет длину. 
        a{3,} Соответствует как минимум 3 последовательным символам «a».
        Example: /.{8,}/.test("123456") // false
---------
    >- /.*/ - любой символ (включая буквы, цифры, пробелы, знаки препинания и т.д.) любое количество раз, включая ноль раз.
        /a.*b/ - будет соответствовать строкам, которые начинаются с символа "a", затем идет любая последовательность символов (включая ноль символов), и заканчивается символом "b".
---------
    Квантификатор * означает "ноль или более повторений", тогда как квантификатор + означает "одно или более повторений".

Например, если вам нужно проверить, что строка начинается с определенной последовательности символов, вы можете использовать ^ в начале выражения, а затем указать эту последовательность символов, за которой следует .*, чтобы описать оставшуюся(...rest) часть строки.
---------
    >- / /g - флаг g указывает глобальный поиск, что означает, что будут возвращены все совпадения во входной строке, а не только первый 

! Важно !
! Если пользуемся флагом `g` в комбинации с методом test(), то не следует выносить регулярное выражение в отдельную переменную. Таким образом, можно получить неочевидное поведение функции валидации.

    var str = 'test';
    var pattern = /te/gi; 

    pattern.test(str) // true  | /te/gi.test(str) // true  
    pattern.test(str) // false | /te/gi.test(str) // true
    pattern.test(str) // true  | /te/gi.test(str) // true
---------
    >- (?=...) - некий switch/case. Если при проверки строки, все условия выполняются, то выражение возвращает true.

Проверить, что в строке есть как минимум одна заглавная, строчная буква и как минимум 10 цифр:
    >- /(?=.*[A-ZА-Я])(?=.*[a-zа-я])(?=.*\d{10}).+/g

    1) (?=.*[A-ZА-Я]) мы проверяем, что в любом месте, в строке есть как минимум одна заглавная буква (латинская или кириллическая). 
    2) Аналогично, (?=.*[a-zа-я]) проверяет наличие как минимум одной строчной буквы (латинской или кириллической). 
    3) (?=.*\d{10}) проверяет, что в строке есть как минимум 10 цифр, независимо от их расположения в строке. 
    .* перед \d{10} означает, что между началом строки и первой цифрой может быть любое количество любых символов.

    4) Использование .+ в конце регулярного выражения означает, что мы проверяем наличие одного или более любых символов в строке.
---------

---------------------------------------------------------
// RegExp выражение для ссылки
-------------------
    https://example.com/page/?id=1
    http://asd.com/
    https://sub.asd.com/asd/asd

Такая ссылка состоит из:
    1. Протокол (http или https)
    2. Двоеточие (:)
    3. 2 слеша (//)
    4. Домен (example.com) + опционально поддомены (sub.example.com) + опционально поддиректории (example.com/page) + опционально query-параметры (?id=1)

---------
Создадим простое регулярное выражение для проверки того, что в начале будет http:/=/=/https://

    1. Напишем определение http и https. У них общая часть http и s опционально. 
    2. Для опционального символа добавляем ? – https?
    3. Далее должно идти ://. Добавим в регулярное выражение этот набор символов, экранируя слэши https?:\/\/
    4. После должна быть остальная часть адреса страницы – https?:\/\/\S+
    И чтобы поле было в одну строку, добавим проверку, что строка началась и закончилась – ^https?:\/\/\S+$

    /^https?://(www.)?[^\s]+$/g.test(value)

---------------------------------------------------------
/=/=/ Валидация в нативном HTML
-------------------
    <form>
        <input 
            type="text"
            pattern="^S+@S+.S+$" // Проверка на соответствие
            required // Поле обязательно
        >
        <button type="submit" disabled={!isValid}> // Отключает кнопку 
            Отправить
        </button>
    </form>

Если значение не будет соответствовать регулярному выражению, то при попытке отправить форму мы увидим ошибку.
---------
    <form>
        <input 
            type="email" // Проверяет емаил
            required
        >
        <button type="submit">Отправить</button>
    </form>
---------
    <form>
        <input 
            type="text"
            minlength="6" // Указывает минимальное количество символов
            required
        >
        <button type="submit">Отправить</button>
    </form>

---------------------------------------------------------
/=/=/ Скрыть/Показать пароль
-------------------
const TextField = ({ label, type, name, value, onChange, error }) => {
  const [showPass, setShowPass] = useState(false);

  const getInputClasses = () => {
    return "form-control " + (error ? "is-invalid" : "is-valid");
  };

  const toggleShowPass = () => {    // Меняем статус show/hide при нажатии 
    setShowPass((perv) => !perv);
  };

  return (
    <div className="mb-4">
      <label htmlFor={name}>{label}</label>
        // связываем поле ввода и кнопку 
        // исправляем баг квадратной кнопки при отображении текста с ошибкой 
      <div className="input-group has-validation"> 
        <input
          className={getInputClasses()}
          type={showPass ? "text" : type} 
            // Если нажали `show`, меняем type с `password` на "text"
          id={name}
          name={name}
          value={value}
          onChange={onChange}
        />
        {type === "password" && (   // отображаем только для поля `password`
          <button
            type="button"
            className="btn btn-outline-secondary"
            onClick={toggleShowPass}
          >
            {showPass ? eyeSlash : eyeFill}  // меняем значок кнопки скрытия 
          </button>
        )}
        <div className="invalid-feedback">{error}</div> // отображение ошибок
      </div>
    </div>
  );
};
---------------------------------------------------------
/=/=/ Реструктуризация проекта
-------------------   

    

---------------------------------------------------------
/=/=/ Выстраивание уровней Абстракции 
-------------------
/=/ Структуризация проекта
---------

    <*> `common` - Переиспользуемые компоненты

    <*> `ui` - Конкретные, не переиспользуемые компоненты имеющие специфические данные.

    <*> `page` - Компоненты, которые будут вызваны на конкретной странице

    <*> `layout`  - это компонент, который определяет структуру и расположение других компонентов на странице. В этом смысле он может быть рассмотрен как компонент высокого уровня.
    Компоненты Layout также могут содержать компоненты UI, чтобы определить, как они располагаются на странице.

-------------------
/=/ Важное понятие о layouts:
---------
Папка "layouts" может содержать компоненты React, которые являются обертками для других компонентов, и определяют общий макет страницы.

Например, если у вас есть приложение с несколькими страницами, каждая страница может иметь общий Макет (шапка, подвал, навигационное меню и т.д.), который можно вынести в компонент Layout. Затем вы можете создать отдельные компоненты для каждой страницы, которые будут отображаться внутри компонента Layout.

Компоненты в папке "layouts" обычно не используются напрямую в маршрутизации вашего приложения. Вместо этого, они используются внутри компонентов, которые находятся в папке "pages" или "components".

    src/
    components/
        Button.jsx
        Input.jsx
        ...
    layouts/
        Layout.jsx
    pages/
        Home.jsx
        About.jsx
        Contact.jsx
    App.jsx
    index.js

В этом примере компонент Layout находится в папке layouts, а компоненты Home, About и Contact находятся в папке "pages". Каждый из этих компонентов использует компонент Layout для определения общего макета страницы.

-------------------
/=/ layouts OR components?
---------
Если вы используете компонент NavBar в качестве общего макета для всех страниц вашего приложения, то рекомендуется поместить его в папку "layouts". Если вы используете NavBar только на некоторых страницах, то поместите его в папку "components".

При организации файловой структуры вашего проекта, рекомендуется группировать компоненты по их функциональности и использованию, чтобы проще было найти нужный компонент. Например, вы можете создать папку "components" для компонентов, которые используются повторно на разных страницах, и папку "pages" для компонентов, которые используются только на конкретной странице.
---------

    layouts (Высокоуровневые компоненты)
        \/
    components
        \/
    ui <--> common

---------
// layouts/login.jsx

    import React from "react";
    import LoginForm from "../components/ui/loginForm";

    const Login = () => {
        return <LoginForm />;
        };
    export default Login;

// ui/loginForm.jsx

    const LoginForm = () => {
    const [inputFields, setInputFields] = useState(
        { email: "", password: "" }
    );

    const [errors, setErrors] = useState({});

    const handleInputChange = (e) => {
        const { name, value } = e.target;
        setInputFields((prevState) => ({
        ...prevState,
        [name]: value
        }));
    };

    const foundErrors = validate(inputFields, loginSchema);

    useEffect(() => {
        setErrors(foundErrors);
    }, [inputFields]);

    const hasErrors = Object.keys(foundErrors).length !== 0;
    const handleSubmit = (e) => {
        e.preventDefault();
        if (hasErrors) return;
        console.log(inputFields);
    };

    const { email, password } = inputFields;

    return (
        <div className="container mt-5">
        <div className="row">
            <div className="col-md-6 offset-md-3 shadow p-4">
            <form className="mx-3" onSubmit={handleSubmit}>
                <h3 className="mb-4">Login</h3>
                <TextField
                    label={"Email:"}
                    type="text"
                    name="email"
                    value={email}
                    onChange={handleInputChange}
                    error={errors.email}
                />
                <TextField
                    label={"Пароль:"}
                    type="password"
                    name="password"
                    value={password}
                    onChange={handleInputChange}
                    error={errors.password}
                />
                <button
                disabled={hasErrors}
                className={"btn btn-primary w-100 mx-auto"}
                type="submit"
                >
                Вход
                </button>
            </form>
            </div>
        </div>
        </div>
        );
    };

    export default LoginForm;


-------------------
// Для чего создание index.js в папке с файлами
---------
// table/index.js
    import tableShell from "./tableShell";
    import tableBody from "./tableBody";
    import tableHeader from "./tableHeader";

    export default tableShell;
    export { tableBody, tableHeader };

Теперь мы можем не дублировать каждый путь к файлу, а лишь ссылаться к папке с данными файлами и вытаскивать необходимые.
Это некая своеобразная деструктуризация файлов.

// usersTable.jsx
    import TableShell, { TableHeader, TableBody } from "../common/table";

---------------------------------------------------------
/=/=/ Выстраивание уровней Абстракции для Компонента "FeedbackPage"
-------------------
       Form (стандартная обертка формы)
        \/
    FeedbackForm (передаем тело и название в шаблон/ опционально add elems)
        \/
    FeedbackPage (передаем форму и опционально добавляем специфические элементы на итоговую страницу)
-------------------
|> Компонент "Form" - содержит общую разметку формы, которая может быть использована для различных форм на сайте. Это позволяет избежать дублирования кода и упрощает поддержку кода в будущем.
---------
=<< Form выполняет функцию обертки и принимает содержание `children`

  const Form = ({ children, title }) => { 
    return (
      <div className="container mt-5">
        <div className="row">
          <div className="col-md-6 offset-md-3 shadow p-4">
            <h2>{title}</h2>
            {children}
          </div>
        </div>
      </div>
    );
  };

  export default Form;

-------------------
|> Компонент "FeedbackForm" - содержит логику обработки данных и валидации для конкретной формы обратной связи. 
---------
  const FeedbackForm = () => {
    const [inputFields, setInputFields] = useState({
      email: "",
      link: "",
      description: "",
      password: ""
    });
  
    const [errors, setErrors] = useState({});
  
    const handleInputChange = (e) => {
      const { name, value } = e.target;
      setInputFields((prev) => ({
        ...prev,
        [name]: value
      }));
    };
  
    const foundErrors = validate(inputFields, issueFormSchema);
  
    useEffect(() => {
      setErrors(foundErrors);
    }, [inputFields]);
  
    const hasErrors = Object.keys(foundErrors).length !== 0;
    const handleSubmit = (e) => {
      e.preventDefault();
      if (hasErrors) return;
      console.log(inputFields);
    };
  
    const { email, link, description, password } = inputFields;
  
    return (
      <div className="container p-4">
  
      // Передаем в `Form` `children` и `title`  
        <Form title="Отчет об ошибке">
          <form onSubmit={handleSubmit}>
              <TextField
                label="Ссылка на страницу с ошибкой:"
                type="text"
                name="link"
                value={link}
                onChange={handleInputChange}
                error={errors.link}
              />
              <TextField
                label="Описание:"
                type="text"
                name="description"
                value={description}
                onChange={handleInputChange}
                error={errors.description}
              />
            <button
              disabled={hasErrors}
              className="btn btn-primary w-100 mx-auto"
              type="submit"
            >
              Отправить
            </button>
          </form>
        </Form>
      </div>
    );
  };

  export default FeedbackForm;

-------------------
|> Компонент "FeedbackPage" - отвечает за создание страницы обратной связи, включая в себя компонент `FeedbackForm` и другие возможные
---------
=<< FeedbackPage определяет макет и внешний вид страницы, а также может содержать дополнительную логику, связанную с роутингом или взаимодействием с другими компонентами.

  const FeedbackPage = () => {
    return <FeedbackForm />;
  };
  
  export default FeedbackPage;

---------
// Почему просто не разместить `FeedbackForm` напрямую?
---------
Использование FeedbackPage имеет несколько преимуществ:

    1) Масштабируемость: если в будущем появится необходимость добавить дополнительную логику на страницу обратной связи, вы можете легко добавить это внутри компонента FeedbackPage, не затрагивая логику компонента FeedbackForm.

    2) Гибкость: если в будущем вы захотите использовать компонент FeedbackForm на других страницах, вы можете просто вставить его туда, не заботясь о том, как правильно оформить страницу.

    3) Читаемость: использование FeedbackPage делает код более читаемым и понятным, поскольку он группирует логику, связанную с определенной страницей, в отдельном компоненте.

---------------------------------------------------------
/=/=/ Создание Контролируемого `Select-form`
-------------------
<select name="fruit">
    <option value=""> -- Выберите фрукт -- </option>
    <option value="banana">Банан</option>
    <option value="orange">Апельсин</option>
    <option value="apple">Яблоко</option>
</select>
---------
У <select> помимо атрибута `name`,  есть и другие, например `multiple` или  `required` (обязательное поле).

У <option> также есть атрибуты, например: 
    -< value – значение, которое будет отправлено вместе с формой, если выбран этот <option>. Если этого атрибута нет, значение берется из текстового содержимого элемента <option>.
    -< selected – задает изначально выбранный элемент.
    -< disabled – элемент недоступен для самостоятельного выбора.

-------------------
// Контролируемый элемент <select>
---------
import React, { useState } from "react";

const Example = () => {
  const [value, setValue] = useState("");

  const handleChange = (event) => {
    setValue(event.target.value);
  };

  return (
    <form>
      <p>Выбранное значение: {value}</p>
      <select name="fruit" value={value} onChange={handleChange}>
        <option value=""> -- Выберите фрукт -- </option>
        <option value="banana">Банан</option>
        <option value="orange">Апельсин</option>
        <option value="apple">Яблоко</option>
      </select>
      <button type="submit">Отправить</button>
    </form>
  );
};

export default Example;

    * Внутри <select> находятся несколько <option>, у которых установлен собственный атрибут `value`.
    * Если внутри <select> есть <option> с таким же значением `value` (как у самого <select>), то он будет отображен выбранным. 
    В данном примере изначально будет выбран “-- Выберите фрукт --”, так как у него `value` === "", так же как `value` из useState("").

-------------------
// Создание Компонента "SelectField"
---------
|> registerForm.jsx

const RegisterForm = ({ text }) => {
  const [inputFields, setInputFields] = useState({
    email: "",
    password: "",
    profession: "" /=/ Добавили для поля выбора профессии
  });

  const {
    email: emailValue,
    password: passwordValue,
    profession: selectedProfession
  } = inputFields;

  const [errors, setErrors] = useState({});
  
  /=/ Получаем список профессий
  const [professions, setProfessions] = useState();
  useEffect(() => {
    API.professions.fetchAll().then((profs) => {
      setProfessions(profs);
    });
  }, []);

  const handleInputChange = (e) => {
    const { name, value } = e.target;
    setInputFields((prevState) => ({
      ...prevState,
      [name]: value
    }));
  };

  const foundErrors = validate(inputFields, loginSchema);

  useEffect(() => {
    setErrors(foundErrors);
  }, [inputFields]);

  const hasErrors = Object.keys(foundErrors).length !== 0;
  const handleSubmit = (e) => {
    e.preventDefault();
    if (hasErrors) return;
    console.log(inputFields);
  };

  return (
    <form onSubmit={handleSubmit}>
      <TextField
        label={"Email:"}
      />
      <TextField
        label={"Пароль:"}
      />
      <SelectField
        label="Ваша профессия:"
        name="profession"
        value={selectedProfession}
        options={professions}
        onChange={handleInputChange}
        error={errors.profession}
      />
      <button
        disabled={hasErrors}
        className={"btn btn-primary w-100 mx-auto"}
        type="submit"
      >
        {text}
      </button>
    </form>
  );
};

---------
|> selectField.jsx

const SelectField = ({
  label,
  name: fieldName,
  value,
  onChange,
  defaultOptions,
  options,
  error
}) => {
  const getInputClasses = () => {
    return "form-select " + (error ? "is-invalid" : "is-valid");
  };

  ***
  const optionsArray =
    !Array.isArray(options) && typeof options === "object"
        ? Object.values(options)
        : options;
  ***

  return (
    <div className="mb-4">
      <label htmlFor={fieldName} className="form-label">
        {label}
      </label>

      <select   /=/ Обертка для вариантов-`option`
        className={getInputClasses()}
        id={fieldName} /=/ Скрепляет поле с `label`
        name={fieldName} /=/ Имя поля. По нему будет искаться Объект с правилами для поля.
        value={value} /=/ `option._id` - Значение в <option>, которое будет отправлено вместе с формой.
        onChange={onChange}
      >
        <option disabled value="">
          {defaultOptions}
        </option>

        ***
        {optionsArray &&
            optionsArray.map((option) => (
                <option key={option._id} value={option._id}>
                    {option.name}
                </option>
        ))}
        ***

        ==/delete/==
        {options &&
          (Array.isArray(options)
            ? options.map((option) => (
                <option key={option._id} value={option._id}>
                  /=/ Если <option value> сходится с <select value>, `el` отображается как выбранный
                  
                  {option.name} 
                </select>
              ))
            : Object.keys(options).map((optionName) => {
                const optionInfo = options[optionName];
                return (
                  <option key={optionInfo._id} value={optionInfo._id}>
                    {optionInfo.name}
                  </option>
                );
            }))}
        ==/delete/==

      </select>
      <div className="invalid-feedback">{error}</div>
    </div>
  );
};

SelectField.defaultProps = {
  defaultOptions: "Choose..."
};
---------------------------------------------------------
/=/=/ Получить данные Формы
-------------------
Правильный Вариант:
  const [inputFields, setInputFields] = useState({
    fio: "",
    email: "",
    deliveryType: ""
  });

  const handleSubmit = (e) => {
    e.preventDefault();
    if (isFormValid) {  /=/ Выводим все значения формы из `inputFields`
      console.log(inputFields);
    }
  };
---------
Other:
    const handleSubmit = (e) => {
        e.preventDefault();

        const formData = new FormData(e.target);
        const fio = formData.get("fio");
        const email = formData.get("email");

        console.log({ fio, email });
    ==/OR/==
        const allFormData = new FormData(e.target);

        for (const [key, value] of allFormData.entries()) {
            console.log(`${key}: ${value}`);  /=/ Выведет все данные Формы
        }
    };

---------------------------------------------------------
/=/=/ Radio form-check
-------------------
Чтобы значения устанавливались корректно, требуется указывать одинаковый атрибут `name` каждому <input type="radio">, относящемуся к одному “полю”
---------
    const options = [
        { label: "Да", value: "yes" },
        { label: "Нет", value: "no" }
    ];

|> radioField.jsx

const RadioField = ({ options, label, name: fieldName, value, onChange }) => { 
    /=/ Получаем более уникальный `id` из `label + value`
  const getOptionId = (option) => `${option.label}_${option.value}`;

    /=/ Создаем класс для опционального показа <div> с ошибкой
  const getInputClasses = () => {
    return "form-check form-check-inline " + (error ? " is-invalid" : "");
  };

  return (
    <div className="mb-4">
      <label className="form-label">{label}</label>
      <div>
      {options.map((option) => (
        <div key={option.value} className={getInputClasses()}> 
        /=/ Оборачиваем каждый radio в <div>, он определяет показ ошибок
          <input
            className="form-check-input"
            type="radio"
            name={name} 
            /=/ У каждого поля должен быть одинаковый `name`
            id={getOptionId(option)} 
            /=/ `id` должно быть уникальным
            value={option.value} 
            /=/ Внутреннее значение выбранного варианта, `id` этого варианта. Будет отправлено вместе с формой.
            checked={option.value === value} 
            /=/ Если `id` рендерящегося элемента === `id` `el` который был передан через обработчик `onChange` и установлен в состояние поля, которое было передано сюда как `value`, то отметить вариант как выбранный
            onChange={onChange} 
          />
          /=/ Отображает название пункта `radio`
          <label className="form-check-label" htmlFor={getOptionId(option)}>
            {option.label}
          </label>
        </div>
      ))}
      </div>
      /=/ При наличии ошибок отображает <div> с ошибкой
      {error && <div className="invalid-feedback">{error}</div>}
    </div>
  );
};

---------------------------------------------------------
/=/=/ Множественный Select
-------------------
    $ yarn add react-select
    $ npm i --save react-select
---------
Import the default export and render in your component:

    import React from 'react'
    import Select from 'react-select'

    /=/ В <Select/> важно передавать именно такой формат:
    const options = [ 
        { value: 'chocolate', label: 'Chocolate' },
        { value: 'strawberry', label: 'Strawberry' },
        { value: 'vanilla', label: 'Vanilla' }
    ]

-------------------
// Правильная передача `value` и `defaultValue`
---------
import Select from "react-select";

const options = [
  { label: "Option 1", value: "option1" },
  { label: "Option 2", value: "option2" },
  { label: "Option 3", value: "option3" }
];

const defaultValues = [
  { label: "Option 1", value: "option1" },
  { label: "Option 2", value: "option2" }
];

const SelectWithDefaultValues = () => {
  const [selectedValues, setSelectedValues] = useState(defaultValues);

  const handleChange = (selectedOptions) => {
    setSelectedValues(selectedOptions);
  };

  return (
    <Select
      options={options}
      isMulti
      defaultValue={defaultValues}
      value={selectedValues}
      onChange={handleChange}
    />
  );
};

-------------------
|> registerForm.jsx

const RegisterForm = ({ entryBtnText }) => {
  const [inputFields, setInputFields] = useState({
    email: "",
    password: "",
    profession: "",
    gender: "other",
    qualities: []
  });
  
  const [errors, setErrors] = useState({});
  const [professions, setProfessions] = useState();
  const [qualities, setQualities] = useState({});

  useEffect(() => {
    API.professions.fetchAll().then((profs) => setProfessions(profs));
    API.qualities.fetchAll().then((quals) => setQualities(quals));
  }, []);

  const handleInputChange = (e) => {
    const { name, value } = e.target;
    setInputFields((prevState) => ({
      ...prevState,
      [name]: value
    }));
  };

  //...

  return (
    <form onSubmit={handleSubmit}>
        //...

        <MultiSelectField
            isMulti="isMulti"
            options={qualities}
            name="qualities"
            label={"Ваши качества:"}
            className="basic-multi-select"
            classNamePrefix="select"
            onChange={handleInputChange}
        />
        
        //...
    </form>
  );
};

---------
|> multiSelectField.jsx

const MultiSelectField = ({ options, name: fieldName, label, onChange }) => {

    /=/ Опционально преобразуем данные в Массив
    const optionsArray =
        !Array.isArray(options) && typeof options === "object"
        ? Object.keys(options).map((key) => {
                const option = options[key];
                return {
                    value: option._id,
                    label: option.name
                };
            })
        : options;

    /=/ Создаем доп. фейковую прослойку, тк <Select onChange/> вместо `event` выдает конечные значения. Это нарушает нашу дальнейшую деструктуризацию в проекте.
    const handleChange = (event) => {
        const fakeEvent = {
            target: {
                name: fieldName,
                value: event
            }
        };
        onChange(fakeEvent); 
        /=/ Передаем измененный ответ в функцию которую мы передали в Компонент 
    };

    return (
        <div className="mb-4">
            <label className="form-label">{label}</label>
            /=/ Нужен класс `form-label` чтобы был отступ 
            <Select
                isMulti
                closeMenuOnSelect={false}
                options={optionsArray}
                className="basic-multi-select"
                classNamePrefix="select"
                onChange={handleChange} 
                /=/ Слушатель должен передать свой `не-event` в нашу функцию для модификации и создания прослойки.
            />
        </div>
    );
};

---------------------------------------------------------
/=/=/ Метод проверки входных данных и преобразования Объекта в Массив 
-------------------
const options =  {
    strange: { _id: '67rdс1100', name: 'Странный', color: 'warning' },
    humorist: { _id: '67rdс11012', name: 'Юморист', color: 'success' },
    handsome: { _id: '67rdс1102', name: 'Красавчик', color: 'info' },
    uncertain: { _id: '67rdс1103', name: 'Робкий', color: 'dark' }
}

/=/ Переменная `optionsArray` говорит что это Массив из `options`
  const optionsArray =
    /=/ Массив и Объект, оба имеют typeof "object". Поэтому тут 2 проверки.
    /=/ Первая на то что это Массив да/нет. Вторая, если нет => то возможно это Объект, а возможно и Строка?
    !Array.isArray(options) && typeof options === "object"
        ? Object.keys(options).map((key) => {
            const option = options[key];
            return {
              name: option.name,
              value: option._id,
            };
          })
        : options;

---------------------------------------------------------
/=/=/ Создание одиночного Checkbox
-------------------
|> registerForm.jsx

const RegisterForm = ({ entryBtnText }) => {
    const [inputFields, setInputFields] = useState({
        email: "",
        password: "",
        profession: "",
        gender: "other",
        qualities: [],
        privacyPolicy: false
    });

    /* |> validateRules.jsx

        isRequired: (value) =>
            typeof value === "boolean" ? value : Boolean(value.trim())
    */
    
    //...

    return (
        <form onSubmit={handleSubmit}>
            //...

            <CheckboxField
                name="privacyPolicy"
                value={inputFields.privacyPolicy}
                onChange={handleInputChange}
                error={errors.privacyPolicy}
            >
                Согласен с <a href="#">политикой конфиденциальности</a>
            </CheckboxField>
            
            //...
        </form>
    );
};

---------
|> checkboxField.jsx

const CheckboxField = ({ name: fName, value: fValue, onChange, children, error }) => {
    const handleChange = () => {
        onChange({
        target: {
            name: fName,
            value: !fValue
        }
        });
    };

    const getInputClasses = () => {
        return "form-check-input " + (error ? "is-invalid" : "");
    };

    return (
        <div className="mb-4">
            <div className="form-check has-validation">
                <input
                    className={getInputClasses()}
                    type="checkbox"
                    value="" /=/ Для одиночного оставляем пустам 
                    id={fName}
                    checked={fValue} /=/ Передаем значение состояния
                    onChange={handleChange}
                />
                <label
                    className="form-check-label"
                    htmlFor={fName}
                    style={{ fontSize: "14px" }}
                >
                    {children}
                </label>
                <div className="invalid-feedback">{error}</div>
            </div>
        </div>
    );
};

CheckboxField.propTypes = {
    //...

    children: PropTypes.oneOfType([
        PropTypes.arrayOf(PropTypes.node),
        PropTypes.node
    ]),
};

---------------------------------------------------------
/=/=/ Создание переиспользуемого Checkbox
-------------------
У Checkbox мы можем хранить значения как массив (несколько Checkbox’ов для одного поля) или как Boolean (true/false). 

const ExampleCheckbox = () => {
  /=/ Начальное состояние – пустой массив
  const [checkboxValues, setCheckboxValues] = useState([]);  

  const handleChange = (e) => {   /=/ Обработчик события onChange
    const { value } = e.target;  /=/ Получаем значение нажатого checkbox
    setCheckboxValues((prevValues) => { /=/ Устанавливаем новое значение
 
      /=/ Если такое значение есть в `state` checkboxValues
      const newValues = prevValues.includes(value) 
          /=/ то удаляем это значение из массива
        ? prevValues.filter((prevValue) => prevValue !== value)
          /=/ иначе добавляем новое значение в Массив
        : [...prevValues, value]; 

      return newValues; /=/  Возвращаем новое значение
    });
  };

  //...
}

-------------------
export const agreements = [
  { label: "Согласие на обработку данных", value: "1" },
  { label: "Сохранить данные для будущих заказов", value: "2" }
];
---------
|> orderForm.jsx

const OrderForm = () => {
  const [inputFields, setInputFields] = useState({
    //...
    
    agreements: [], /=/ Массив для принятых соглашений
    test: false /=/ ! Обязательно true/false Состояние для одиночного Checkbox. 
  });

return (
    <Form title="Оформление заказа">
      <form onSubmit={handleSubmit}>
        //...
        <CheckboxField  
        /=/ Если передать один `elem` [{label: "name", value: 1}], то тоже получится singleCheckbox
          options={agreements} 
          name="agreements" 
          /=/ Имя поля. Чтобы найти данные Компонента в состоянии `inputFields`
          value={inputFields.agreements} 
          /=/ Значения поля. Передаем Массив с принятыми соглашениями
          onChange={handleChange}
          error={errors.agreements}
        />
        <SingleCheckboxField
          name="test"
          onChange={handleChange}
          value={inputFields.test}
          label="Проверка" 
          /=/ Для одиночного Checkbox передаем его `label` сразу
          checked={inputFields.test}
          /=/ Принимает `boolean` значение. В Компоненте при срабатывании `onChange`, будем менять полученное значение `value` из `state` на противоположное и возвращать его обратно к `state`. Так круг замкнется и значение для `checked={inputFields.test}` обновится.
          error={errors.test}
        />
        //...
      </form>
    </Form>
  );
};

---------
|> validationSchema.js/orderFormSchema

const orderFormSchema = {
    //...
    agreements: {
        isContainValue: {
            message: "Необходимо согласие с политикой конфиденциальности",
            param: "1" 
            /=/ Устанавливаем значение поля которое нужно проверить
        }
    },
    test: {
        isRequired: {
            message: "Проверка работоспособности полей"
        }
    }
};

---------
|> checkboxField.jsx - Для создания нескольких `checkbox-ов`

const CheckboxField = ({ options, name, value, onChange, error }) => {

  const handleChange = (e) => {
    /=/ Создаем прослойку чтобы 
    const { name, value: eventVal } = e.target;

    const newValue = value.includes(eventVal)
    /=/ Проверяем, есть ли в состоянии поля значение, которое поступает с событием.
      ? value.filter((val) => val !== eventVal)
      /=/ Если значение есть, то возвращаем Массив без него.
      : [...value, eventVal];
      /=/ Если нет, то добавляем.
      
    /=/ Воссоздаем формат `event` для соответствия формам в Компонентах
    /=/ И передаем новое состояние поля в `handleChange` в род. Компоненте
    onChange({
      target: {
        name, 
        /=/ Название поля, для нахождения в `state`
        value: newValue 
        /=/ Обновленное значение поля, которое будет иметь в себе Массив из `value`(id предметов) для отображения // [1, 2]
      }
    });
  };

  const getIsChecked = (inputVal) => value.includes(inputVal);
  /=/ Есть ли в состоянии поля значение которое сейчас ренерится? 

  const getInputClasses = () => "" + (error ? " is-invalid" : "");

  return (
    <div className="mb-4">
      <p className={getInputClasses()}></p>
      /=/ Если нет возможности поменять класс в <input> для отображения `is-invalid`
      /=/ То передаем класс в созданный тег перед мапированием.
      {options &&
        options.map((option) => (
          <SingleCheckboxField
            key={option.value}
            name={name}
            label={option.label}
            value={option.value}
            checked={getIsChecked(option.value)}
            /=/ Если true, то отображаем помеченным 
            onChange={handleChange}
            /=/ Пропускаем `event` слушателя событий сначала через нашу прослойку
          />
        ))}
      {error && <div className="invalid-feedback">{error}</div>}
    </div>
  );
};

CheckboxField.propTypes = {
  name: PropTypes.string.isRequired,
  value: PropTypes.array.isRequired,
  onChange: PropTypes.func.isRequired,
  label: PropTypes.string,
  options: PropTypes.arrayOf(
    PropTypes.shape({
      label: PropTypes.string.isRequired,
      value: PropTypes.string.isRequired
    }).isRequired
  ),
  error: PropTypes.string
};

export default CheckboxField;

---------
|> singleCheckboxField.jsx
      
const SingleCheckboxField = ({
  name,
  label,
  value,
  checked,
  onChange,
  error
}) => {
  /=/ Если используется `singleCheckbox`, то его значение поля === true/false. Их состояние меняем на противоположное. 
  /=/ Если `singleCheckbox` используется внутри `multiCheckbox`, то передаем `event` далее в род Компонент для его модификации в Массив [1,2]
  const handleChange = (e) => {
    typeof value === "boolean"
      ? onChange({
          target: {
            name,
            value: !value
          }
        })
      : onChange(e);
  };

  const getOptionId = () => `${label}_${value}`;
  /=/ Создаем более уникальный id

  const getInputClasses = () =>
    "form-check-input " + (error ? "is-invalid" : "");

  return (
    <div className="form-check">
      <input
        className={getInputClasses()}
        type="checkbox"
        id={getOptionId()}
        name={name}
        value={value}
        checked={checked}
        /=/ Получает значение от род Компонента 
           /* checked={getIsChecked(option.value)}
           /* Если true, то отображаем помеченным 
        onChange={handleChange}
        /=/ Так же запускаем нашу прослойку для проверки event-a
      />
      <label className="form-check-label" htmlFor={getOptionId()}>
        {label}
      </label>
      {error && <div className="invalid-feedback">{error}</div>}
    </div>
  );
};

SingleCheckboxField.propTypes = {
  name: PropTypes.string.isRequired,
  label: PropTypes.string.isRequired,
  value: PropTypes.oneOfType([PropTypes.string, PropTypes.bool]).isRequired,
  checked: PropTypes.bool,
  onChange: PropTypes.func,
  error: PropTypes.string
};

---------------------------------------------------------
/=/=/ Yup - Библиотека для валидации Форм
---------------------------------------------------------
    $ yarn add yup
    $ npm i yup
---------
    import * as yup from 'yup'

    const schema = yup
      .string()
      .min(15, "Минимум 15 символов")
      .required("Поле обязательно");

    schema
      .validate("some string")
      .then()
      .catch((err) => {
        // const { inner } = err;
        console.log(err.message);
      });
          
    * .validate(inputFields, { abortEarly: false })
      /=/ `abortEarly: false` - Вывести все ошибки полей

-------------------
/=/=/ Задать сообщения ошибок по-умолчанию
---------
yup.setLocale({
  mixed: {
    default: `Некорректное значение`,
    required: `Обязательное поле`
  },
  string: {
    length: `Должно быть длиной в ${length} символов`,
    min: `Должно быть не менее ${min} символов`,
    max: `Должно быть не более ${max} символов`,
    email: `Некорректный email`
  },
  number: {
    min: `Должно быть не менее ${min}`,
    max: `Должно быть не более ${max}`
  }
});

-------------------
Вернемся к нашим правилам формы заказа:

|> orderForm.jsx
  const [inputFields, setInputFields] = useState({ /=/ Объект с полями
    fio: "",
    email: "",
    deliveryType: "",
    needLift: "",
    gifts: [],
    agreements: [],
  });
---------
1) Можно увидеть, что мы собираем значения формы в Объект.
Поэтому нужно начать описывать схему с того, что мы ожидаем объект с определёнными полями:

|> validationSchema.js
    import * as yup from 'yup'

    export const validationSchema = yup.object().shape({ // объект с полями
        fio: yup.string(), /=/ Все поля у нас строки, кроме...
        email: yup.string(), 
        deliveryType: yup.string(), 
        needLiftFloor: yup.string(), 
        agreement: yup.array() /=/ ...кроме agreement, он массив
    });

2) Далее добавим всем полям требование, что они обязательны и добавим правило для email.
И укажем текст ошибки.

    export const validationSchema = yup.object().shape({
        fio: yup.string().required("ФИО обязательно для заполнения"),
        email: yup
            .string()
            .required("Электронная почта обязательна для заполнения")
            .email("Email введён некорректно"),
        deliveryType: yup.string().required("Выберите вариант доставки"),
        needLiftFloor: yup.string().required("Укажите нужен ли подъём на этаж"),
        agreement: yup.array()
    });

3) Для проверки ФИО у нас есть свое регулярное выражение. 
Для того, чтобы задать проверку на соответствие регулярному выражению, в библиотеке есть метод `matches()`.

    export const validationSchema = yup.object().shape({
        fio: yup
            .string()
            .required("ФИО обязательно для заполнения")
            .matches(
                /^(([a-zA-Zа-яА-Я]+)s){1,}(([a-zA-Zа-яА-Я]+)s?){1,}$/g,
                "Введите корректное ФИО"
            ),
        //...
    });

4) Осталось лишь проверить поле `agreement` на наличие значения в массиве. 
-------------------
/=/ test() Пишем кастомное правило для yup
---------
Такую проверку можно сделать через метод `test() `, это самый простой способ написать кастомное правило Yup:

export const validationSchema = yup.object().shape({
    //...
    agreement: yup.array().test(
        "contains value", 
         /=/ Название проверки
        "Согласие на обработку данных обязательно", 
         /=/ Текст ошибки
        (value) => value.includes("1") 
         /=/ Функция, которая проверит валидность
    )
});

---------
Мы перенесли все правила. Вызовем проверку 

|> orderForm.jsx

useEffect(() => {
    validationSchema /=/ На месте вызова validate() в orderForm
        .validate(inputFields, { abortEarly: false }) /=/ `abortEarly: false` - Вывести все ошибки полей
        .then(() => setErrors({})) /=/ Если ошибок нет, очищаем состояние ошибок
        .catch((yupError) => { /=/ Если ошибки есть, добавляем их в состояние
            const { inner } = yupError;
            const foundErrors = Array.isArray(inner) /=/ Создаём объект с ошибками
                ? inner.reduce((acc, item) => {
                    const { path, errors } = item;
                        if (!acc.hasOwnProperty(path) && errors.length) { /=/ Проверяем есть ли ошибка уже в объекте
                            acc[path] = errors[0]; /=/ Если нет, то добавляем первую
                        }
                        return acc;
                    }, {})
                : {};

            setErrors(foundErrors);
        });
}, [inputFields]);

    ==/OR/== (не факт что корректно, но работает)

    useEffect(() => { 
        validationSchema
        .validate(inputFields, { abortEarly: false })
        .then(setErrors({}))
        .catch(({ inner }) => {
            for (const error of inner) {
            setErrors((prev) => ({
                ...prev,
                [error.path]: error.message
            }));
            }
        });
    }, [inputFields]);

---------
Получилось довольно громоздко. Перенесём получение ошибки в отдельную утилиту: 
|> utils/parseYupError.js

export const parseYupError = (yupError) => {
    const { inner } = yupError;

    return Array.isArray(inner)
        ? inner.reduce((acc, item) => {
              const { path, errors } = item;
 
              if (!acc.hasOwnProperty(path) && errors.length) {
                  acc[path] = errors[0];
              }

              return acc;
          }, {})
        : {};
};

|> orderForm.jsx

    useEffect(() => {
        validationSchema
            .validate(values, { abortEarly: false })
            .then(() => setErrors({}))
            .catch((yupError) => {
                const errors = parseYupError(yupError);
                setErrors(errors);
            });
    }, [values])

---------------------------------------------------------
/=/=/ Делаем Компоненты `selectField` и `multiSelectField` полностью переиспользуемыми
-------------------
Для того, чтобы компоненты `selectField` и `multiSelectField` сделать полностью переиспользуемыми, мы рекомендуем перенести преобразование данных из этих компонентов в `registerForm`
---------
|> registerForm.jsx

const RegisterForm = ({ entryBtnText }) => {
  const [inputFields, setInputFields] = useState({
    email: "",
    password: "",
    profession: "",
    gender: "other",
    qualities: [],
    privacyPolicy: false
  });
  
  const [errors, setErrors] = useState({});
  *** /=/ Меняем на Массив
  const [professions, setProfessions] = useState([]);
  const [qualities, setQualities] = useState([]); 
  ***

  /=/ Реализуем чтобы в Компоненты приходили готовые Массивы 
  ***
  useEffect(() => {
    API.professions.fetchAll().then((profs) => {
      const professionsList = Object.keys(profs).map((profName) => ({
        label: profs[profName].name,
        value: profs[profName]._id
      }));
      setProfessions(professionsList);
    });
    
    API.qualities.fetchAll().then((quals) => {
      const qualitiesList = Object.keys(quals).map((profName) => ({
        label: quals[profName].name,
        value: quals[profName]._id,
        color: quals[profName].color
      }));
      setQualities(qualitiesList);
    });
  }, []);
  ***

  const handleInputChange = (e) => {
    const { name, value } = e.target;
    setInputFields((prevState) => ({
      ...prevState,
      [name]: value
    }));
  };

  useEffect(() => {
    const foundErrors = validate(inputFields, loginSchema);
    setErrors(foundErrors);
  }, [inputFields]);

  const hasErrors = Object.keys(errors).length !== 0;

  const handleSubmit = (e) => {
    e.preventDefault();
    if (hasErrors) return;
    const { profession: profId, qualities: selectedQuals } = inputFields;

    console.log({
      ...inputFields,
      profession: getProfessionById(profId),
      qualities: getQualities(selectedQuals)
    });
  };

  const getProfessionById = (id) => {
    for (const prof of professions) {
      if (prof.value === id) {
        return { _id: prof.value, name: prof.label };
      }
    }
  };

  const getQualities = (elements) => {
    const qualitiesArray = [];
    for (const elem of elements) {
      for (const quality in qualities) {
        if (elem.value === qualities[quality].value) {
          qualitiesArray.push({
            _id: qualities[quality].value,
            name: qualities[quality].label,
            color: qualities[quality].color
          });
        }
      }
    }
    return qualitiesArray;
  };

  return (
    <form onSubmit={handleSubmit}>
      <TextField
        label={"Email:"}
        type="text"
        name="email"
        value={inputFields.email}
        onChange={handleInputChange}
        error={errors.email}
      />
      <TextField
        label={"Пароль:"}
        type="password"
        name="password"
        value={inputFields.password}
        onChange={handleInputChange}
        error={errors.password}
      />
      <SelectField
        label="Ваша профессия:"
        name="profession"
        value={inputFields.profession}
        onChange={handleInputChange}
        options={professions}
        error={errors.profession}
      />
      <RadioField
        label="Ваш пол:"
        name="gender"
        value={inputFields.gender}
        options={genderOptions}
        onChange={handleInputChange}
        error={errors.gender}
      />
      <MultiSelectField
        label={"Ваши качества:"}
        name="qualities"
        defaultValue={inputFields.qualities}
        options={qualities}
        onChange={handleInputChange}
        className="basic-multi-select"
        classNamePrefix="select"
      />
      <CheckboxField
        name="privacyPolicy"
        value={inputFields.privacyPolicy}
        onChange={handleInputChange}
        error={errors.privacyPolicy}
      >
        Согласен с <a href="#">политикой конфиденциальности</a>
      </CheckboxField>
      <button
        disabled={hasErrors}
        className={"btn btn-primary w-100 mx-auto"}
        type="submit"
      >
        {entryBtnText}
      </button>
    </form>
  );
};

---------
В компонентах selectField и multiSelectField заменяем преобразование в массив optionsArray на следующее:
    const optionsArray =
        !Array.isArray(options) && typeof options === "object"
            ? Object.values(options)
            : options;
---------

|> selectField.jsx

const SelectField = ({
  label,
  name: fName,
  value: fValue, /=/ Должно передавать `string`. 
                /=/ Точнее `_id ` относящиеся к отображаемому `name`
  onChange,
  defaultOptions, /=/ Почти не играет роли. 
                 /=/ Лишь высвечивает некий `label` для поля Select
  options,
  error
}) => {

  const getInputClasses = () => {
    return "form-select " + (error ? "is-invalid" : "is-valid");
  };

  ***
  const optionsArray =
    !Array.isArray(options) && typeof options === "object"
      ? Object.values(options)
      : options;
  ***

  return (
    <div className="mb-4">
      <label htmlFor={fName} className="form-label">
        {label}
      </label>
      <select
        className={getInputClasses()}
        id={fName}
        name={fName}
        value={fValue}
        onChange={onChange}
      >
        <option disabled value="">
          {defaultOptions}
        </option>
        /=/ Заменяем преобразование в массив на:
        ***
        {optionsArray.length > 0 &&
          optionsArray.map((option) => (
            <option value={option.value} key={option.value}>
              {option.label}
            </option>
          ))}
        ***
      </select>
      <div className="invalid-feedback">{error}</div>
    </div>
  );
};

SelectField.propTypes = {
  label: PropTypes.string,
  name: PropTypes.string,
  value: PropTypes.string,
  onChange: PropTypes.func.isRequired,
  defaultOptions: PropTypes.string,     /=/ Строка
  options: PropTypes.oneOfType([PropTypes.object, PropTypes.array]),
  error: PropTypes.string
};

---------
const MultiSelectField = ({
  options,
  name: fName,
  defaultValue,
  label,
  onChange
}) => {

  ***
  const optionsArray =
    !Array.isArray(options) && typeof options === "object"
      ? Object.values(options)
      : options;
  ***

  ==/delete/==
  const optionsArray =
    !Array.isArray(options) && typeof options === "object"
      ? Object.keys(options).map((key) => {
          const option = options[key];
          return {
            value: option._id,
            label: option.name
          };
        })
      : options;
  ==/delete/==

  const handleChange = (event) => {
    const fakeEvent = {
      target: {
        name: fName,
        value: event
      }
    };
    onChange(fakeEvent);
  };

  return (
    <div className="mb-4">
      <label className="form-label">{label}</label>
      <Select
        isMulti
        closeMenuOnSelect={false}
        ***
        defaultValue={defaultValue}
        ***
        options={optionsArray}
        className="basic-multi-select"
        classNamePrefix="select"
        onChange={handleChange}
      />
    </div>
  );
};

Теперь в компоненты селекторов будут приходить сразу Массивы.
---------
Но теперь получается, что professions и qualities в API имеют отличную от исходной структуру. 
Согласуем исходные и отправляемые данные из формы. 

В registerForm в handleSubmit() нам необходимо преобразовать данные.  

    const handleSubmit = (e) => {
        e.preventDefault();
        const isValid = validate();
        if (!isValid) return;
        const { profession, qualities } = data;
        console.log({
            ...data,
            profession: getProfessionById(profession),
            qualities: getQualities(qualities)
        });
    };
    
Таким образом мы получим новый объект. В дальнейшем его нужно будет выводить не в консоль, а в функцию регистрации.

Создаем функции getProfessionById() и getQualities().

    const getProfessionById = (id) => {
        for (const prof of professions) {
            if (prof.value === id) {
                return { _id: prof.value, name: prof.label };
            }
        }
    };
    const getQualities = (elements) => {
        const qualitiesArray = [];
        for (const elem of elements) {
            for (const quality in qualities) {
                if (elem.value === qualities[quality].value) {
                    qualitiesArray.push({
                        _id: qualities[quality].value,
                        name: qualities[quality].label,
                        color: qualities[quality].color
                    });
                }
            }
        }
        return qualitiesArray;
    };

Теперь Объект имеет первоначальную структуру.


---------------------------------------------------------
/=/=/ Combobox - текстовое поле со списком вариантов выбора, из которых пользователь может выбрать один или несколько элементов.
-------------------
-> Библиотеки:
==<< Reach UI
    https://reach.tech/

    $ yarn add @reach/combobox
    $ npm install @reach/combobox

==<< React Widgets
    https://jquense.github.io/react-widgets/
    
    $ yarn add react-widgets
    $ npm install react-widgets --save

==<< react-bootstrap-combobox
    $ yarn add @fdefelici/react-bootstrap-combobox
    $ npm install @fdefelici/react-bootstrap-combobox --save
---------
При заполнении Формы, сможет ли пользователь заполнить адрес так, чтобы он удовлетворял требованиям службы доставки?

Обычно в таких случаях используют элементы управления формой, похожие на <input> и <select> одновременно. При вводе данных происходит запрос на сервер, он отдаёт несколько вариантов и, когда пользователь выбирает один из вариантов, значение устанавливается в форму. 
---------------------------------------------------------
/=/=/ Как заменить ключи и значения в Объекте 
-------------------
    const profsObject = {
        doctor: { _id: "67rdca3eeb7f6fgeed471818", name: "Доктор" },
        waiter: { _id: "67rdca3eeb7f6fgeed471820", name: "Официант" }
    };

    const formatData = (obj, id = "_id", name = "name") => {
        return Object.values(obj).map(({ id, name, ...rest }) => ({
            value: id,
            label: name,
            ...rest
        }));
    }; 
    /=/ На самом деле происходит не "замена", а "не передача" `_id` и `name`
    /=/ Тк при деструктуризации мы изъяли их свойства и возвращаем `...rest` без них.

    formatData(profsObject) 
     // { value: "67rdca3eeb7f6fgeed471818", label: "Доктор" },
     // { value: "67rdca3eeb7f6fgeed471820", label: "Официант" }

---------------------------------------------------------
/=/=/=/ Расширенные Хуки и Базовая Оптимизация
---------------------------------------------------------
Для вызова повторного рендера нужно обновить `props` или `state` компонента. 
---------
=<< Бесконечный ререндер 

    const RenderCountExample = () => {
        const [renderCount, setRenderCount] = useState(0);

        useEffect(() => {
            setRenderCount(
                (prev) => prev + 1 /=/ Изменяет `state` =>> Ререндер
            );  
        }); /=/ Вызывается при каждом рендере Компонента 

        return (
            <CardWrapper>
                <SmallTitle>Подсчет количества рендеров</SmallTitle>
                <p>{`render count ${renderCount}`}</p>
            </CardWrapper>
        );
    };
---------
Чем чаще вызывается рендер, тем больше создаётся нагрузка, и тем самым падает производительность.
Одним из способов оптимизации: предотвращение ненужного изменения `props` и/или `state`.

-------------------
// Обновление данных в React зависит от типа данных. 
---------
=<< У примитивных типов данных нет никаких особенностей по обновлению:

    const Parent = () => {
        const [count, setCount] = useState(0);

        return (
            <div>
                <button onClick={() => setCount((prevCount) => prevCount + 1)}>
                    +
                </button>
                <Child count={count} />
            </div>
        );
    };

    const Child = ({ count }) => {
        return <div>Count: {count}</div>;
    };

-------------------
=<< Но особенность есть у ссылочных типов данных: Объекты, Массивы, Функции. 

Чтобы ререндерить Компонент с ссылочными типами данных, нужно передать обновленные данные с измененной на них ссылкой:

    const Parent = () => {
        const [values, setValues] = useState({ email: "" });

        const handleChange = (event) => {
            const { value, name } = event.target;
            
            /=/ Передаем новый объект
            setValues({
                ...values,
                [name]: value
            });
        };

        return (
            <div>
                <input value={values.email} onChange={handleChange} />
                <Child values={values} />
            </div>
        );
    };

    const Child = ({ values }) => {
        return <div>Почта: {values.email}</div>;
    };
    
Важный момент – когда родительский компонент заново рендерится, он вызывает рендер своих потомков.
-------------------
>- Новую ссылку на Объект можно сделать одним из вариантов:
    const obj0 = { name: "John" }; // объект
    const obj1 = Object.assign({}, obj0); // новый объект
    const obj2 = { ...obj0 }; // новый объект

>- Для Массивов:
    const arr0 = []; // массив
    const arr1 = [...arr0]; // новый массив
    const arr2 = arr0.slice(); // новый массив

---------------------------------------------------------
/=/=/ Сериализация — это преобразование Объекта или Дерева Объектов в другой формат таким образом, чтобы потом его можно было восстановить в исходное состояние.
-------------------
Если Объект или Массив не содержит функций, то можно сказать, что он может быть сериализован. 

Т. е. например сериализованные данные будут пригодны для хранения и передачи по сети. 
Прежде чем хранить или передавать структуру данных, её сериализуют. Чаще всего в JS под этим будет подразумеваться преобразование объекта в строку JSON:

    const user = { name: "John", age: "24" };
    const serializedUser = JSON.stringify(user);
    console.log(serializedUser); // Строка -> '{"name":"John","age":"24"}'

    /=/ Восстанавливаем из строки
    console.log(JSON.parse(serializedUser)); // { name: "John", age: "24" }

=<< Функции (или экземпляры классов) – несериализуемы. Их нельзя превратить в структуру для передачи по сети. 
-------------------
=<< Выводы темы:

    * Чтобы вызвать ререндер достаточно обновления `props` и/или `state`
    * Ссылочные типы данных будут считаться новыми, если у них изменится ссылка 
        (иначе ререндер может не произойти, тк ссылка осталась прежней)
    * Ссылочные типы данных в контексте оптимизации React-приложения можно разделить на 2 вида: 
        - Сериализуемые (Объект/Массив без функций) 
        - Несериализуемые (Функции или Экземпляры Классов)
    * Ререндер родителя вызывает ререндер children

---------------------------------------------------------
/=/=/=/ useRef() - в нем можно сохранять любое значение и хранить/изменять его в течение всей жизни Компонента. 
При изменении значения не произойдет повторный рендер.
-------------------
Хук useRef() возвращает изменяемый ref-объект. 
В его свойстве `current` будет находится заданное значение

! Важная особенность useRef() – ссылка на ref-объект неизменна, и поэтому сам он не может быть передан в useEffect() в качестве зависимости (так как useEffect() попросту не будет вызываться вновь). 
! Но можно передать его свойство `current` и его изменение будет влиять на вызов useEffect()

-------------------
// useRef().current.style - установка стилей
---------
const UseRefExercise = () => {
    const blockRef = useRef();

    const handleChange = () => {
        blockRef.current.style.width = "150px";
        blockRef.current.style.height = "150px";
        blockRef.current.children[0].innerText = "text";
    ==/OR/==
        const { style, children } = blockRef.current;
        style.width = "150px";
        style.height = "150px";
        children[0].innerText = "text";
        /=/ Установка текста для Дочернего компонента
        /=/ Не переназначаем `color`, тк устраивает исходный "white"
    };

    return (
        <div
            className="bg-primary d-flex flex-row justify-content-center align-items-center rounded"
            style={{
                height: 40,
                width: 60,
                color: "white"
            }}
            ref={blockRef}
        >
            <small>Блок</small>
        </div>
        <button className="btn btn-primary mt-2" onClick={handleChange}>
            Change
        </button>
    );
};

-------------------
=<< Подсчет кол-ва рендеров

    const RenderCountExample = () => {
        const renderCount = useRef(0); /=/ Будет хранить кол-во рендеров 
        const [otherState, setOtherState] = useState(false);

        useEffect(() => {
            renderCount.current += 1;
            // renderCount.current++;
        }); 
        /=/ При каждом ререндере Компонента +1

        const handleChange = () => {
            setOtherState((prev) => !prev);
        }; 
        /=/ Вызываем изменение `state` для провоцирования ререндера Компонента

        return (
            <CardWrapper>
                <SmallTitle>Подсчет количества рендеров</SmallTitle>
                <p>{`Render count: ${renderCount.current}`}</p>
                <button className="btn btn-primary" onClick={handleChange}>
                    Toggle other state
                </button>
            </CardWrapper>
        );
    };

-------------------
=<< Сохранение предыдущего состояния переменной

    const PrevStateExample = () => {
        const prevState = useRef("");
        const [currentState, setCurrentState] = useState("false");

        useEffect(() => {
            prevState.current = currentState; /=/ Указываем переменную для сохранения прошлого состояния
        }, [currentState]); /=/ Вызывается только при изменении нашей переменной

        const handleChange = () => {
            setCurrentState((prev) => (prev === "false" ? "true" : "false"));
        }; /=/ Провоцируем изменение состояния переменной 

        return (
            <CardWrapper>
                <SmallTitle>Предыдущее состояние</SmallTitle>
                <p>{`prevState: ${prevState.current}`}</p> /=/ Отображаем предыдущее значение переменной
                <p>{`currentState: ${currentState}`}</p> /=/ Отображаем текущее значение
                <button className="btn btn-primary" onClick={handleChange}>
                    Toggle other state
                </button>
            </CardWrapper>
        );
    };

-------------------
=<< Сохранение предыдущего состояния <div>, обращение к нему и управление им

const ProgrammableActionsExample = () => {
    const inputRef = useRef(); /=/ Экземпляр useRef()

    const prevInputDiv = inputRef.current; /=/ Переменная для хранения prevState <input>

    const handleClick = () => {
        console.log(prevInputDiv); /=/ Отобразит <input id="email" type="email" class="form-control">
        prevInputDiv.focus(); /=/ Установит `focus()` для `prevInputDiv` которое хранит в себе ссылку на <input>. 
    };

    const handleClickWidth = () => {
        prevInputDiv.style.width = "100px"; /=/ Добавит стиль в тег который хранится в useRef() в виде ссылки на него. 
        console.log(prevInputDiv); /=/ <input id="email" type="email" class="form-control" style="width: 100px;">
    };

    return (
        <CardWrapper>
            <SmallTitle className="card-title">
                Программируемые действия и свойства
            </SmallTitle>
            <label htmlFor="email" className="form-label">
                Email
            </label>
            <input
                ref={inputRef} /=/ Указываем переменную для сохранения его prevState
                id="email"
                type="email"
                className="form-control"
            />
            <button className="btn btn-primary" onClick={handleClick}>
                Фокус Input
            </button>
            <button className="btn btn-primary" onClick={handleClickWidth}>
                Изменить Ширину
            </button>
        </CardWrapper>
    );
};

-------------------
Самый распространенный способ использования – получение доступа к потомку в компоненте

=<< Доступ к потомку

    export const ExampleFileInput = () => {
        const inputRef = useRef(null);
        const [isValueSet, setIsValueSet] = useState(false);

        const handleSend = () => {
            const file = inputRef.current.files; /=/ `inputRef.current` - ссылка на тег <input>
            console.log(file);
        };

        return (
            <div>
                <h2>Получения доступа к потомку</h2>
                <label htmlFor="file">Выберите файл</label>
                <input
                    ref={inputRef}
                    type="file"
                    onChange={() => setIsValueSet(true)}
                />
                <button onClick={handleSend} disabled={!isValueSet}>
                    Отправить файл
                </button>
            </div>
        );
    };

---------------------------------------------------------
/=/=/=/ useMemo() - в нем можно сохранять любое значение и хранить/изменять его в течение всей жизни Компонента. 
-------------------
useMemo() используется для мемоизации `вычислений`, чтобы предотвратить повторное `вычисление` той же функции или значения при каждом рендеринге компонента, если зависимости не изменились.
---------
Перед вызовом функции проверяется, вызывалась ли функция ранее:

    * если не вызывалась, то функция вызывается, и результат её выполнения сохраняется;
    * если вызывалась, то используется сохранённый результат.

useMemo будет повторно вычислять мемоизированное значение только тогда, когда значение какой-либо из зависимостей изменилось. 

---------
useMemo() обычно используется для хранения результата выполнения сложнонагруженных функций. Но применять его стоит только при необходимости и оправданности перекрытия затрат.
-------------------

    const myParam = useMemo(() => { 
        return calcAnyByCount(count); 
    }, [count]); 

=<< useMemo() вычисляет значение `myParam` при изменении `count`. Если `count` не изменяется, то значение `myParam` возвращается из кэша без вычисления функции calcAnyByCount().
-------------------
// Почему не передать зависимости сразу в useEffect()?
---------
В реальном проекте для запроса потребуется подготовить данные, например, привести параметры к требуемому формату. Во избежании написания большого количества кода внутри useEffect(), можно воспользоваться useMemo()

-------------------
Давайте на примере посмотрим, как работает useMemo(). Для имитации тяжёлых вычислений мы будем использовать функцию:

    function myLoop(n) {
        console.time("Выполнялось: ");
        let i = 0;
        do {
            i++;
        } while (i !== n);
        console.timeEnd("Выполнялось: ");
        return i;
    }

---------
Методом “научного тыка” можно увидеть, что со значением n равным 1000000000 время на выполнение функции равно ~500 ms, что уже заметно глазу (точное время зависит от вашего ПК и среды исполнения). 

    import React, { useMemo, useState } from "react";

    function myLoop(n) {
        console.time("Выполнялось: ");
        let i = 0;
        do {
            i++;
        } while (i !== n);
        console.timeEnd("Выполнялось: ");
        return i;
    }

export const ExampleUseMemoFeb = () => {
    // В JS большие числа для удобства можно разделять с помощью "_" 
    const [value, setValue] = useState(1_000_000_000);
    const [anotherState, setAnotherState] = useState(1);

    const result = useMemo(() => {
        return myLoop(value);
    }, [value]);

    return (
        <div>
            <div>
                Результат: <b>{result}</b>
                <p>
                    value: <b>{value}</b>
                </p>
            </div>
            <div>
                <button onClick={() => setValue((v) => v + 1000)}>
                    Increment
                </button>
                <button onClick={() => setValue((v) => v - 1000)}>
                    Decrement
                </button>
            </div>
            <div>
                {anotherState}
                <p>
                    <button onClick={() => setAnotherState((p) => p + 1)}>
                        Обновить
                    </button>
                </p>
            </div>
            <hr />
        </div>
    );
};

Нажимая на кнопку “Обновить”, мы вызываем изменение состояния anotherState, но у нас нет никакой задержки отрисовки интерфейса. Это происходит из-за того, что тяжелое вычисление не происходит еще раз в хуке useMemo(), так как его зависимости не изменились (в нашем случае value). При новом рендере хук возвращает мемоизированное значение. 

------------------- 
/=/ Имитация API
const myFakeApi = ({ id, param }) => {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve({
                id,
                param,
                items: [1, 2, 3, 4, 5]
            });
        }, 1000);
    });
};

/=/ Параметры, которые будем менять
const mockParam1 = { id: 1, param: 2 };
const mockParam2 = { id: 2, param: 3 };

/=/ Родительский компонент, который будет передавать props в дочерний
export const ExampleUseMemoUseEffectDeps = () => {
    const [childProps, setChildProps] = useState(mockParam1);

    const handleSwitchChildProps = () => {
        if (childProps === mockParam1) {
            setChildProps(mockParam2);
        } else {
            setChildProps(mockParam1);
        }
    };

    return (
        <div>
            <button onClick={handleSwitchChildProps}>Обновить</button>
            <hr />
            <Child {...childProps} />
        </div>
    );
};


/=/ Дочерний компонент
const Child = ({ id, param }) => {
    const [values, setValues] = useState(null);

   ==//==
    // Создаём параметры запроса
    const requestParams = {
        id,
        param
    };

    // Вызываем, когда обновятся параметры
    useEffect(() => {
        console.log("Request");
        myFakeApi(requestParams).then((r) => setValues(r));
    }, [requestParams]);
   ==//==

    ***
    /=/ Мемоизируем параметры запроса
    const requestParams = useMemo(() => {
        return {
            id,
            param
        };
    }, [id, param]);
    
    useEffect(() => {
        myFakeApi(requestParams).then((r) => setValues(r));
    }, [requestParams]);
    ***

    return (
        <div>
            {values ? (
                <pre>{JSON.stringify(values, null, 2)}</pre>
            ) : (
                <div>Загрузка...</div>
            )}
        </div>
    );
};

У нас есть родительский компонент, который передаёт props в дочерний, и там создаются параметры запроса requestParams. При клике на “Обновить” происходит обновление параметров запроса, и мы обращаемся к API. Полученные данные из API устанавливаются в `state`, и тут начинается проблема. 

После установки нового состояния происходит ререндер и… создаётся новый объект с requestParams(обновляется его ссылка), это триггерет useEffect() и тот выполняется заново. У нас получается бесконечный цикл. 
---------
Чтобы избежать такого поведения, нам нужно мемоизировать requestParams:

    const requestParams = useMemo(() => {
        return {
            id,
            param
        };
    }, [id, param]);

    useEffect(() => {
        myFakeApi(requestParams).then((r) => setValues(r));
    }, [requestParams]);

   ==/OR/==

    const handleRequest = useCallback(() => {
        const requestParam = {
            id,
            param
        };

        myFakeApi(requestParam).then((r) => setValues(r));
    }, [id, param]);

    useEffect(() => {
        console.log("Request");
        handleRequest();
    }, [handleRequest]); 
    /=/ Вызовем когда id или param изменятся, тогда handleRequest будет пересоздан с новыми значениями id и param

---------------------------------------------------------
/=/=/=/ useCallback() - используется когда необходимо сохранить ссылку на функцию, чтобы предотвратить повторное создание этой функции при каждом рендеринге компонента.
-------------------
useCallback() возвращает мемоизированную версию функции, которая будет сохраняться между рендерами, если зависимости не изменились.

Возвращает: 
    * Закэшированное значение выполненной функции, которое обновляется только при изменении зависимостей.
    * Саму закэшированную функцию, чтобы не тратить ресурсы на ее повторный рендер

-------------------
=<< Если необходимо сохранить `function` для передачи дочернему элементу или для передачи ее в зависимости (чтобы на всех рендерах она была одна и та же):

    useCallback(fn, deps)

=<< Если нужен один и тот же `result` на протяжении нескольких ререндеров:

    useMemo(() => fn, deps)

-------------------
// Получить мемоизированную функцию с помощью useMemo()
---------
    
    const handleSome = useMemo(() => {
        return (args) => { /* ... */ }
    }, [deps]);

    const myParam = useMemo(() => {  
        return calcAnyByCount(count);  
    }, [count]); 

-------------------
// Получить мемоизированную функцию с помощью useCallback()
---------

    const handleSome = useCallback((args) => { 
        /* ... */
    }, [deps])

     const myParam = useMemo(() => {  
        calcAnyByCount(count);  
    }, [count]); 

В отличие от useMemo(), хук useCallback() сразу принимает callback-функцию, которую нужно мемоизировать, а не анонимную функцию, из которой нужно вернуть необходимое значение.

-------------------
// Отличие useMemo() и useCallback()
---------
Принципиально можно определить, что useCallback() используют для сохранения ссылки на несериализуемые объекты (функции), а useMemo() для сериализуемых.

---------------------------------------------------------
/=/=/=/ HOC (Компоненты высшего порядка) – это один из продвинутых способов для повторного использования логики. 
-------------------
HOC - некий высокоуровневый коммутатор
---------
`Higher-Order Component` представляет собой Функцию, которая принимает  другую Функцию в качестве аргумента и возвращает новый обернутый Компонент.

Также HOC не только хорошо подходят для создания переиспользуемой логики, но и приводят к тому, что их дочерние компоненты легче тестировать.

---------
-< HOC начинаю название с "with" // (withLogin)
Название пишется с маленькой буквы тк это Функция, а не Компонент
---------
Вместо такой записи:
    const withLogin = (Component) => (props) => { 
        
        return (
            //...
        )
     }

Мы можем написать:
    const withLogin = function(Component) {
        return function (props) { 
            
            return (
                //...
            )
         }
    }

---------
-< В HOC передаем Компонент, а не Экземпляр компонента
-------------------
// Отличие Компонента от Экземпляра компонента
---------
=<< Компонент Button
    const Button () => {
            return (
                <button onClick={this.props.onClick}>
                    {this.props.label}
                </button>
            );
        }
    }

=<< Экземпляры компонента Button
    const button1 = 
        <Button 
            label="Нажми меня" 
            onClick={() => alert('Вы нажали кнопку 1')} 
        />;

-------------------
->> Пример простого HOC
---------

const HocExercise = () => {
    const ComponentWithHoc = withFunctions(SimpleComponent);

    return (
        <ComponentWithHoc label="Login form" />
    );
};

const withFunctions = (Component) => {
    return (props) => {
        const [isAuth, setIsAuth] = useState(!!localStorage.getItem("auth"));

        const toggleAuth = () => {
            setIsAuth((prev) => !prev);
        };

        const handleLogin = () => {
            localStorage.setItem("auth", "token");
            toggleAuth();
        };

        const handleLogOut = () => {
            localStorage.removeItem("auth");
            toggleAuth();
        };

        return (
            <CardWrapper>
                <Component
                    {...props}
                    onLogin={handleLogin}
                    onLogOut={handleLogOut}
                    isAuth={isAuth}
                />
            </CardWrapper>
        );
    };
};

withFunctions.propTypes = {
   children: PropTypes.oneOfType([
      PropTypes.arrayOf(PropTypes.node),
      PropTypes.node
   ])
};

const SimpleComponent = ({ onLogin, onLogOut, isAuth, label }) => {
    return (
        <>
            {label && <h3>{label}</h3>}
            {!isAuth ? (
                <button className="btn btn-primary" onClick={onLogin}>
                    Войти
                </button>
            ) : (
                <button className="btn btn-primary" onClick={onLogOut}>
                    Выйти из системы
                </button>
            )}
        </>
    );
};

SimpleComponent.propTypes = {
    onLogin: PropTypes.func.isRequired,
    onLogOut: PropTypes.func.isRequired,
    isAuth: PropTypes.bool.isRequired,
    label: PropTypes.string
};

-------------------
->> Создание и внедрение HOC Компонента
---------
|> Обычный переиспользуемый Компонент
const UserMeta = ({ name, email, phone }) => {
    return (
        <div>
            <h4>{name}</h4>
            <p>
                Tel.: {phone}, email: {email}
            </p>
            <div></div>
            <hr />
        </div>
    );
};
---------
|> Компонент Высшего Порядка
const withQuery = (Component) => {
   return ({ userGuid }) => {
      const [user, setUser] = useState(null);
      const [error, setError] = useState(null);

      useEffect(() => {
         getUser(userGuid)
            .then((r) => {
               setUser(r);
            })
            .catch((e) => {
               setError(e.message);
            });
      }, [userGuid]);

      if (error) {
         return <div>{error}</div>;
      }

      return <>{user ? <Component {...user} /> : <div>Загрузка...</div>}</>;
   };
};
---------
|> Родительский Компонент
const UserMetaWithQuery = withQuery(UserMeta);

const ParentComponent = () => {
    return (
        <>
            <p>Пользователь:</p>
            <CardWrapper>
                <UserMetaWithQuery 
                    serGuid="userGuid_0" 
                />
            </CardWrapper>
        </>
    );
};
---------
|> fake.API
import { faker } from "@faker-js/faker";

const fakeUsers = Array.from({ length: 10 }, (_, i) => {
   const gender = faker.person.sex();
   const user1Name = faker.person.firstName(gender);
   const user2Name = faker.person.lastName(gender);
   const userPhone = faker.phone.number("501-###-###");
   const userEmail = `${user1Name.toLowerCase()}@mail.com`;

   return {
      name: `${user1Name} ${user2Name}`,
      userGuid: `userGuid_${i}`,
      phone: userPhone,
      email: userEmail
   };
});

if (!localStorage.getItem("fakeUsers")) {
   localStorage.setItem("fakeUsers", JSON.stringify(fakeUsers));
}

export const getAllUsers = () =>
   new Promise((resolve) => {
      setTimeout(function () {
         resolve(JSON.parse(localStorage.getItem("fakeUsers")));
      }, 1000);
   });

export const getUser = (userGuid) =>
   new Promise((resolve, reject) => {
      setTimeout(function () {
         const user = JSON.parse(localStorage.getItem("fakeUsers")).find(
            (user) => user.userGuid === userGuid
         );
         if (user) {
            resolve(user);
         } else {
            reject(new Error("User not found"));
         }
      }, 1000);
   });

-------------------
->> Создание 2х HOC для редактирования телефона польз-ля.
---------
Данный HOC будет принимать пользователя и давать нам кнопку для редактирования его поля. Пусть это будет телефон.


/**
 * Компонент поля редактирования телефона.
 * Просто управляемый <input> и кнопка сохранить.
 */
export const EditUserPhone = ({ value, onChange, onSuccess }) => {
    return (
        <div className="alert alert-success mt-2">
            <h4>Введите новый телефон</h4>
            <div className="d-flex justify-content-between">
                <input
                    value={value}
                    onChange={onChange}
                    className="w-100 me-2 form-control"
                />
                <button className="btn btn-primary" onClick={onSuccess}>
                    Сохранить
                </button>
            </div>
        </div>
    );
};


/**
 * Кнопка для перехода в режим редактирования, когда появляется поле
 */
export const UserEditBtn = ({ onClick }) => {
    return (
        <div className="d-flex justify-content-end mt-2">
            <button className="btn btn-primary" onClick={onClick}>
                Редактировать телефон
            </button>
        </div>
    );
};


/**
 * Новый HOC для редактирования телефона.
 * Принимает Component и возвращает новый, которому 
 * нужно передать props как у UserMeta.
 */
export const withEditUserPhone = (Component) => {
    return (props) => {
        const [isEdit, setIsEdit] = useState(false);
        const [phone, setPhone] = useState(props.phone);
        const [fieldValue, setFieldValue] = useState(props.phone);

        /=/ Если придут новые данные то установить их
        useEffect(() => {
            setPhone(props.phone);
            setFieldValue(props.phone);
        }, [props.phone]);
				

        /=/ Переключение режима редактирования
        const handleToggleEdit = () => {
            setIsEdit((prevEdit) => !prevEdit);
        };
				
        const handleSuccess = () => {
            handleToggleEdit();
            setPhone(fieldValue);
        };

        const handleInputChange = (event) => {
            const { value } = event.target;
            setFieldValue(value);
        };

        return (
            <>
                <Component {...props} phone={phone} />
                {
                     /**
                      * Если в режиме редактирования, то 
                      * вернёт форму редактирования,
                      * иначе - кнопку "редактировать телефон"
                      */
                }
                {isEdit ? (
                    <EditUserPhone
                        value={fieldValue}
                        onChange={handleInputChange}
                        onSuccess={handleSuccess}
                    />
                ) : (
                    <UserEditBtn onClick={handleToggleEdit} />
                )}
            </>
        );
    };
};


/** 
 * Просто нужно обернуть UserMeta в withEditUserPhone(), а потом 
 * получившееся обернуть в withQuery(),
 * так как в withQuery() мы получаем пользователя
 */
const UserMetaWithQuery = withQuery(UserMeta);
const UserMetaWithEditUserPhone = withQuery(withEditUserPhone(UserMeta));

const ParentComponent = () => {
   return (
      <>
         <p>Пользователи:</p>
         <UserMetaWithQuery 
            userGuid="userGuid_0" 
         />
         <br />
         <UserMetaWithEditUserPhone
            userGuid="userGuid_1" 
         />
      </>
   );
};
---------------------------------------------------------
/=/=/=/ Faker.js - генерация фиктивных данных для пользователей
-------------------
    $ yarn add @faker-js/faker --dev
    $ npm install @faker-js/faker --save-dev

    Faker functions(): https://fakerjs.dev/api/
---------
    import { faker } from '@faker-js/faker';

    const users = [];

    for (let i = 0; i < 10; i++) {
        const user = {
            id: i + 1,
            name: faker.name.findName(),
            email: faker.internet.email(),
            phone: faker.phone.phoneNumber()
        };
        users.push(user);
    }

    console.log(users);

В этом примере мы используем функцию faker.name.findName() для генерации фиктивных имен для каждого пользователя в цикле. Остальные поля, такие как email и phone, также генерируются с помощью функций из библиотеки Faker.js.

-------------------
/=/=/ Сгенерировать Аватар
---------
    function getAvatar() {
        return `https://avatars.dicebear.com/api/avataaars/${(Math.random() + 1)
            .toString(36)
            .substring(7)}.svg`;
    }

.toString(36) используется для преобразования случайного числа в строку. В нее могут быть закодированы все буквы латинского алфавита и цифры от 0 до 9

Таким образом, случайная строка длиной в 13 символов генерируется с помощью Math.random() и .toString(36), а затем из нее извлекается подстрока длиной 6 символов, начиная с седьмого с помощью .substring(7)
-------------------
/=/=/ NanoId
---------
    import { nanoid } from 'nanoid'
    nanoid() //=> "V1StGXR8_Z5jdHi6B-myT"
    nanoid(10) //=> "IRFa-VaY2b"
    
    import { customAlphabet } from 'nanoid'
    const nanoid = customAlphabet('1234567890abcdef', 10)
    nanoid(5) //=> "f01a2"
---------------------------------------------------------
/=/=/=/ React.Memo - мемоизирует Компонент
-------------------
 ! React.memo() ререндерит Компонент только если изменились его пропсы. Именно поэтому передаваемые пропсы нужно мемоизировать, чтобы компонент не перерисовывался, когда это не нужно.
---------
 React.Memo - это higher order component.
 Он служит для прерывания лишних рендеров. Если твой компонент всегда рендерит одно и то же с теми же props, ты можешь обернуть твой компонент в React.memo(), тем самым мемоизируя результат рендера. 
---------
=<< Когда рекомендуется использовать:
     * Если компонент часто ререндерится
     * Компоненту передаются одинаковые `props` при одинаковых ререндерах
     * Компонент не имеет собственного состояния
---------
 !>- Если функциональный компонент обёрнут в React.memo() и используют useState(), useReducer() или useContext(), он будет повторно рендериться при изменении состояния или контекста. Это просто необходимо, ведь мы хотим, чтобы наш контент менялся, если мы изменим, например, состояние.

 >- Функциональный объект равен только самому себе (Это ссылочный Компонент)

-------------------
/=/=/ Простейший пример применения React.memo()
---------
    import React, { useEffect, useState } from "react";

    const Parent = () => {
        const [count, setCount] = useState(0);

        return (
            <div>
                <h2>Count: {count}</h2>
                <button
                    className="btn btn-primary"
                    onClick={() => setCount((c) => c + 1)}
                >
                    +
                </button>
                <div>
                    <Children />
                </div>
            </div>
        );
    };

    const Children = () => {
        useEffect(() => {
            console.log("render");
        });

        return <div>Children</div>;
    };

У нас есть родительский компонент и потомок. В родительском есть кнопка, которая изменяет некоторое состояние. В потомке useEffect(), который при каждом рендере компонента выводит сообщение в консоль. 

Когда мы будем нажимать кнопку для изменения состояния, мы увидим, что каждый раз будет вызываться рендер потомка. Нам это не нужно, так как от этого ничего не меняется. Давай воспользуемся React.memo() для избежания лишних рендеров:

    const Children = React.memo(() => {
        useEffect(() => {
            console.log("render");
        });

        return <div>Children</div>;
    });

-------------------
// Усложним задачу
---------
Будем передавать в потомок некоторую сущность, пусть это будет user:

import React, { useEffect, useState } from "react";

const Parent = () => {
    const [count, setCount] = useState(0);

    const user = {
        name: "Sarah Sullivan",
        phone: "1-976-631-1449",
        email: "fringilla.purus.mauris@protonmail.com",
        address: "2660 Fringing Av."
    };

    return (
        <div>
            <h2>Count: {count}</h2>
            <button
                className="btn btn-primary"
                onClick={() => setCount((c) => c + 1)}
            >
                +
            </button>
            <div>
                <Children user={user} />
            </div>
        </div>
    );
};

const Children = React.memo(({ user }) => {
    useEffect(() => {
        console.log("render");
    });

    return <div>{user.name}</div>;
});

export default Parent;

Мы видим, что у нас объявлен объект user, и он передаётся в дочерний компонент. Теперь, при нажатии на кнопку в родителе, опять повторно рендерится дочерний компонент, тк ссылка props обновляется.
-------------------
// Как это можно исправить:
---------

=<< Вариант 1

Мы видим, что в дочернем компоненте используется только поле name. Мы можем сравнить, равно ли новое значение name к предыдущему. Для этого вторым аргументом в React.memo() нужно передать специальную функцию areEqual(). Она принимает два аргумента: предыдущие props и новые. Внутри нужно провести сравнение. Если мы не хотим, чтобы компонент ререндерился, то нужно вернуть true, иначе false:

function areEqual(prevProps, nextProps) {
    /=/ Изменилось ли свойство name у новых props 
    return prevProps.user.name === nextProps.user.name;
}

const Children = React.memo(({ user }) => {
    useEffect(() => {
        console.log("render");
    });

    return <div>{user.name}</div>;
}, areEqual);

Такой способ сработает только для примитивных типов данных или сериализуемых объектов (для них можно, например, использовать isEqual из библиотеки lodash).


=<< Вариант 2

Наш user – ссылочный тип данных, и мы можем его мемоизировать. В useMemo() есть “поверхностная сверка” для ссылочных типов данных, и если ссылка всегда будет одна и та же, то повторного рендера не случится:
 import React, { useEffect, useState, useMemo } from "react";

const Parent = () => {
    const [count, setCount] = useState(0);

    const user = useMemo(
        () => ({
            name: "Sarah Sullivan",
            phone: "1-976-631-1449",
            email: "fringilla.purus.mauris@protonmail.com",
            address: "2660 Fringilla Av."
        }), [] /=/ "Вычисляем" результат только при первом рендере 
    );

    return (
        <div>
            <h2>Count: {count}</h2>
            <button
                className="btn btn-primary"
                onClick={() => setCount((c) => c + 1)}
            >
                +
            </button>
            <div>
                <Children user={user} />
            </div>
        </div>
    );
};

const Children = React.memo(({ user }) => {
    useEffect(() => {
        console.log("render");
    });

    return <div>{user.name}</div>;
});
/=/ Ссылка Объекта user больше не изменяется в род компоненте, поэтому пропс не реагирует и не заставляет ререндерится дочерний компонент 

---------
Также мы можем поступить с функциями. 
Функции нельзя сравнить с помощью areEqual(), можно только использовать “поверхностное сравнение” по ссылке.

=<< Поэтому нужно обернуть функцию в useCallback(): 

import React, { useEffect, useState, useMemo, useCallback } from "react";

const Parent = () => {
    const [count, setCount] = useState(0);

    const handleCount = useCallback(() => {
        setCount((c) => c + 1);
    }, []);

    const user = useMemo(
        () => ({
            name: "Sarah Sullivan",
            phone: "1-976-631-1449",
            email: "fringilla.purus.mauris@protonmail.com",
            address: "2660 Fringilla Av."
        }), []
    );

    return (
        <div>
            <h2>Count: {count}</h2>

            <div>
                <Children onIncrement={handleCount} user={user} />
            </div>
        </div>
    );
};

const Children = React.memo(({ user, onIncrement }) => {
    useEffect(() => {
        console.log("render");
    });

    return (
        <div>
            {user.name}
            <div>
                <button className="btn btn-primary" onClick={onIncrement}>
                    +
                </button>
            </div>
        </div>
    );
});

export default Parent;
-------------------
 Наш проект может иметь сложную композицию компонентов c многими потомками. Если не сохранять ссылки на объекты, то это может вызывать утечки памяти или свести на нет использование React.memo(). 

 >>- В коммерческой разработке можно нередко увидеть следование правилу — все объекты, передаваемые в потомки, должны быть мемоизированы. Ты тоже можешь следовать ему, это избавит от некоторых проблем с производительностью. 

  * React.memo() нужен для оптимизации рендеров Компонента.
  * Если мы передаём в него объекты, то обязательно нужно их мемоизировать или создавать функцию для сравнения данных – areEqual(). 
-------------------
// Рассмотрим пример:
---------
Предположим, у вас есть компонент React, который принимает объект prop и рендерит его содержимое. Если объект не меняется между рендерами компонента, то можно использовать React.memo() для предотвращения лишнего рендеринга компонента.

    const MyComponent = React.memo(({ myObj }) => {
      return (
        <div>
          <p>{myObj.name}</p>
          <p>{myObj.age}</p>
        </div>
      );
    });

Каждый раз, когда `myObj` меняется, компонент будет перерисовываться.
---------
Однако, если мы мемоизируем myObj, используя, например, React.useMemo(), то компонент не будет перерисовываться, если myObj не изменился.

    const App = () => {
      const myObj = useMemo(() => {
        return {
          name: 'John',
          age: 30
        };
      }, []);

      return (
        <div>
          <MyComponent myObj={myObj} />
        </div>
      );
    };

    const MyComponent = React.memo(({ myObj }) => {
      return (
        <div>
          <p>{myObj.name}</p>
          <p>{myObj.age}</p>
        </div>
      );
    });

В этом примере myObj мемоизирован с помощью React.useMemo(). При первом рендеринге компонента MyComponent объект myObj создается, а затем сохраняется в памяти. Если myObj не изменится, то компонент MyComponent не будет перерисовываться.

---------------------------------------------------------
/=/=/=/ React.cloneElement() - с помощью него можно клонировать React элемент, добавляя или изменяя его параметры
-------------------
React.cloneElement() клонирует и возвращает новый React-элемент. 
---------
Первым параметром он принимает элемент, вторым config и третьим потомков (опционально):

    React.cloneElement(element, {config}, ...children);

 >- `config` может содержать все новые пропсы, key и ref. Полученный таким способом элемент будет иметь пропсы исходного элемента (element) и также новые пропсы из config. 
 >- Если в `config` совпадет название пропса, который уже есть у element, то применится проп из config. 
 >- `key` и `ref` из исходного элемента (element) будут сохранены, если в config они не были переданы. 
 >- Новые дочерние элементы (children) заменят существующие (у element). 

 ---------
    React.cloneElement(myText, {
        text: isSubscribe
            ? myText.props.text  
            : getTwoParagraph(myText.props.text)  
    });

-------------------
Допустим, мы делаем сайт для журнала по подписке. У нас есть компонент, который просто выводит тест статьи на странице:

    const Text = ({ text }) => {
        return <p>{text}</p>;
    };

Если у пользователя нет подписки, то вернуть ему только первые 2 параграфа и текст о том, что нужно оплатить подписку для дальнейшего чтения. 

---------
Утилита получения 2-х параграфов и сообщения вот такая:

    const getTwoParagraph = (text) => {
        const arrParagraph = text.split(/\n/);
        return arrParagraph.length > 2
            ? [
                  ...arrParagraph.slice(0, 2),
                  "Для продолжения оформите подписку"
              ].join("\n")
            : text;
    };

---------
const CheckSubscribe = () => {
    const [isSubscribe, setIsSubscribe] = useState(false);

    /=/ Получаем элемент
    const myText = <Text text={someText} />;

    /=/ Клонируем его
    const nextText = React.cloneElement(myText, {
        text: isSubscribe   <<- /=/ Меняем пропс `text`
            ? myText.props.text  
            : getTwoParagraph(myText.props.text)  
    });

    return (
        <>
            <div>
                <button
                    className="btn btn-primary mb-2"
                    onClick={() => setIsSubscribe((s) => !s)}
                >
                    Подписаться{" "}
                </button>
            </div>
            {nextText}
        </>
    );
};

React.cloneElement() нужно использовать в тех случаях, когда невозможно изменить `props` с помощью HOC, что часто происходит при написании переиспользуемых компонентов.

---------------------------------------------------------
/=/=/=/ React.Children - позволяет управлять дочерними элементами Компонента, извлекать информацию о них и проверять их тип.
-------------------
=<< React.Children - это не функция, а объект, который содержит методы для работы с дочерними элементами. 

Например, React.Children.map(children, fn) - это вызов метода map у объекта React.Children.
---------
props.children — это объект, содержащий описание детей. Это ненастоящие потомки, не компоненты, а всего лишь описание. Мы не можем изменить какие-либо параметры или редактировать какие-либо функции у них. Мы имеем доступ к чтению.

React нам предоставляет несколько API-методов для работы с непрозрачной структурой данных props.children. Она называется непрозрачной, так как мы заранее не знаем, что придёт к нам в children. 
-------------------
->> Пример мапирования `children` Компонента и передачи ему props с его порядковым `i` через React.Children.map()
---------

const ChildrenExercise = () => {
   return (
      <CollapseWrapper title="Упражнение">
         <p className="mt-3">
            У вас есть компоненты Списка. Вам необходимо к каждому из них
            добавить порядковый номер, относительно того, как они располагаются
            на странице. Вы можете использовать как{" "}
            <code>React.Children.map</code> так и{" "}
            <code>React.Children.toArray</code>
         </p>

         <ListComponent>
            <Component />
            <Component />
            <Component />
         </ListComponent>
      </CollapseWrapper>
   );
};

const ListComponent = ({ children }) => {
    return React.Children.map(children, (child, i) =>
        React.cloneElement(child, {
                num: i,
                ..child.props, 
                /=/ Все неизмененные `props` переносятся автоматически, но рекомендуется делать очевидный перенос вручную
            })
    );
};

const Component = ({ num }) => {
   return <div>Компонент списка {num}</div>;
};

-------------------
->> Пример мапирования `children` Компонента и передачи ему props с его порядковым `i` через React.toArray() и map() 
---------

const ChildrenExercise = () => {
   return (
      <CollapseWrapper title="Упражнение">

        //...

         <ListComponent>
            <Component />
            <Component />
            <Component />
         </ListComponent>
      </CollapseWrapper>
   );
};

const ListComponent = ({ children }) => {
   const childrenArray = React.Children.toArray(children);
   return (
      <div>
         {childrenArray.map((child) =>
            React.cloneElement(child, {
               ...child.props,
               num: Number(child.key.replace(".", "")) + 1
               /=/ У `child` есть свойство `key` (.0 .1 .2)
            })
         )}
      </div>
   );
};

const Component = ({ num }) => {
   return <div>Компонент списка {num}</div>;
};

-------------------
/=/=/ React.Children.map()
---------

    React.Children.map(children, (child) => { 
        /* ... */ 
    });

Вызывает функцию для каждого непосредственного потомка в children, передавая их по очереди в child. 
Возвращаемое значение из функции — обновленный потомок (аналогично методу map() в JS). 

Если children — это массив, он будет пройден, функция будет вызвана для каждого потомка в массиве, и вернется обновленный массив. 
Если children равен null или undefined, этот метод вернёт null или undefined, а не массив.
---------
! Важно! 
! Если children — это Fragment, он будет рассматриваться как целый потомок, а элементы внутри не будут пройдены.

<Fragment> в React - это компонент, который позволяет группировать несколько элементов вместе без необходимости создавать дополнительный DOM-узел.  
-------------------
->> Пример с <Fragment>
---------
    const ParentComponent = ({ children }) => {
      return (
        <div>
        /=/ Функция будет вызвана один раз для всего <Fragment>
          {React.Children.map(children, (child) => {
            return child;
          })}
        </div>
      );
    };

    const ChildComponent = () => {
      return <div>Child component</div>;
    };

    const App = () => {
      return (
        <ParentComponent>
          <>
            <ChildComponent />
            <ChildComponent />
          </>
        </ParentComponent>
      );
    };

В этом примере, React.Children.map() будет вызван только один раз для Fragment, а не для каждого ChildComponent.

-------------------
->> Передать новые props элементам дочернего Компонента
---------

/=/ Дочерний Компонент принимающий в props элементы
const FormComponent = ({ children }) => {
   const [data, setData] = useState({});

   const handleChange = (target) => {
      setData((prev) => ({ ...prev, [target.name]: target.value }));
   };


   return React.Children.map(children, (child) => {
    /=/ С помощью метода `map()` объекта React.Children, проходим по массиву элементов `children`
    И через React.cloneElement() добавляем каждому элементу `props` 

      return React.cloneElement(
       /=/ Возвращаем новый измененный элемент, в который добавили нужные `props`
        child, { onChange: handleChange }
      );
   });
};

FormComponent.propTypes = {
   children: PropTypes.oneOfType([
      PropTypes.arrayOf(PropTypes.node),
      PropTypes.node
   ])
};

const ReactChildrenExample = () => {
   return (
      <CardWrapper>
         <SmallTitle>Clone form and add props</SmallTitle>
         <hr />
         /=/ Дочерний Компонент
         <FormComponent>
            /=/ Элементы дочернего Компонента
        =>> <TextField name="email" label="Email" />
            <TextField name="password" label="Password" type="password" 
            />
         </FormComponent>
      </CardWrapper>
   );
};

-------------------
/=/=/ React.Children.forEach()
---------

    React.Children.forEach(
        children, (child) => { /* ... */ }
    );

Похож на React.Children.map(), но не возвращает обновленный массив. 
Также можно сравнить с методом массивов forEach() в обычном JS. Проходит по каждому элементу и вызывает callback-функцию. 

-------------------
/=/=/ React.Children.toArray()
---------

   React.Children.toArray(children)

Возвращает непрозрачную структуру данных children в виде плоского массива с ключами, заданные каждому дочернему элементу.
Преобразует дочерние элементы компонента React в массив. Это может быть полезно, когда вам нужно выполнить операции на массиве, такие как .map, .filter или .reduce.

---------
Например, если у вас есть следующий компонент:

    function Component({ children }) {
      const childrenArray = React.Children.toArray(children);
      return (
        <div>
          {childrenArray.map((child, index) => (
            <div key={index}>{child}</div>
          ))}
        </div>
      );
    }
    
То вы можете передать дочерние элементы в компонент, используя теги, как показано ниже:

    <Component>
        <div>Первый элемент</div>
        <div>Второй элемент</div>
        <div>Третий элемент</div>
    </Component>

Метод React.Children.toArray() в компоненте Component преобразует дочерние элементы в массив, который затем можно использовать для выполнения операций на массиве.

-------------------
/=/=/ React.Children.count() - позволяет узнать количество дочерних элементов в компоненте
---------

    React.Children.count(children);

Возвращает общее количество компонентов в children, равное количеству вызовов callback, переданного в React.Children.map, которые будут совершены.
---------
Например, предположим, что у вас есть компонент List, который принимает в качестве дочерних элементов несколько элементов ListItem. Вы хотите узнать, сколько элементов находится в List.

    import React from "react";

    const List = ({ children }) => {
      const count = React.Children.count(children);
      return (
        <div>
          <p>Number of items in the list: {count}</p>
          <ul>{children}</ul>
        </div>
      );
    };

    const ListItem = ({ children }) => {
      return <li>{children}</li>;
    };

    const App = () => {
      return (
        <List>
            <ListItem>Item 1</ListItem>
            <ListItem>Item 2</ListItem>
            <ListItem>Item 3</ListItem>
        </List>
      );
    };

-------------------
->> Создание пошагового ToDo списка
---------
|> SomeComponent.jsx
const SomeComponent = () => {
   const [doneValue, setDoneValue] = useState(0);

   const handleClickDone = (stepValue) => {
      setDoneValue(stepValue);
   };
   /=/ При нажатии на элемент списка, в `StatusItem` передаем value-шага по которому кликнули. 
   /=/ Принимаем value-шага в `Statusbar`, который определяет для элемента класс (выполнено/нет) посредством вычисления и передачи дочернему элементу пропса isDone: value >= child.props.value,

   return (
      <CardWrapper>
         <Statusbar value={doneValue} onDone={handleClickDone}>
            <StatusItem value={1}>Шаг 1</StatusItem>
            <StatusItem value={2}>Шаг 2</StatusItem>
            <StatusItem value={3}>Шаг 3</StatusItem>
            <StatusItem value={4}>Шаг 4</StatusItem>
            <StatusItem value={5}>Шаг 5</StatusItem>
         </Statusbar>
      </CardWrapper>
   );
};

|> Statusbar.jsx
const Statusbar = ({ children, value, onDone }) => {
   
   const countChildren = React.Children.count(children);
   /=/ Проверка на наличие items в списке дел

   if (!countChildren) {
      return <div>Нет элементов</div>;
   }

   return (
      <div className="wrapper">
         <ul className="step-progress">
            {React.Children.map(children, (child) => {
               if (child.type === StatusItem) {
               /=/ Делаем проверку чтобы мы работали именно с StatusItem, а не с любыми дочерними компонентами Statusbar-а

                  return React.cloneElement(child, {
                     isDone: value >= child.props.value,
                     onDone: onDone
                  });
               }
               return null;
            })}
         </ul>
      </div>
   );
};

Statusbar.propTypes = {
   children: PropTypes.node.isRequired,
   value: PropTypes.number.isRequired,
   onDone: PropTypes.func
};

|> StatusItem.jsx
const StatusItem = ({ children, value, isDone, onDone }) => {
   const className = `step-progress-item ${isDone ? "is-done" : "current"}`;

   const handleClickDone = () => {
      onDone && onDone(value);
   };
   /=/ Тк props не передается по-умолчанию, и он не обязан быть там, а мы его добавляем, делаем проверку на то что мы его передали

   return (
      <div className={className} onClick={handleClickDone}>
         <strong style={{ cursor: "pointer" }}>
            {children} /=/ это "Шаг 1"
         </strong>
      </div>
   );
};

StatusItem.propTypes = {
   children: PropTypes.string.isRequired,
   value: PropTypes.number.isRequired,
   isDone: PropTypes.bool,
   onDone: PropTypes.func
};

---------------------------------------------------------
/=/=/ FK Formik
-------------------
    $ npm install formik --save
    $ yarn add formik 

    import { Formik } from 'formik';

---------
->> Пример Формы 

import { Formik, Field as FormikField, Form as FormikForm } from "formik";
import * as Yup from "yup";
import { Button, Form, Row, Col, InputGroup } from "react-bootstrap";

const RegisterSchema = Yup.object().shape({
  firstName: Yup.string().required("Required"),
  lastName: Yup.string().required("Required"),
  email: Yup.string().email("Invalid email").required("Required"),
  password: Yup.string()
    .min(8, "Password must be at least 8 characters")
    .required("Required"),
  terms: Yup.bool().oneOf([true], "You must accept the terms and conditions")
});

const RegisterForm = () => {
  return (
    <Formik
      initialValues={{
        firstName: "",
        lastName: "",
        email: "",
        password: "",
        terms: false
      }}
      validationSchema={RegisterSchema}
      onSubmit={console.log}
    >
      {({ errors, touched }) => {
        const getClass = (name) => {
          return `form-control ${
            errors[name] && touched[name] ? "is-invalid" : ""
          }`;
        };

        const getErrorDiv = (name, isCheckbox = false) => {
          const getClass = () => (isCheckbox ? "" : "invalid-feedback");

          return errors[name] && touched[name] ? (
            <div className={getClass()}>{errors[name]}</div>
          ) : null;
        };

        return (
          <FormikForm>
            <Row>
              <Col md={6}>
                <Form.Group>
                  <Form.Label>First Name</Form.Label>
                  <FormikField
                    className={getClass("firstName")}
                    name="firstName"
                  />
                  {getErrorDiv("firstName")}
                </Form.Group>
              </Col>
              <Col md={6}>
                <Form.Group>
                  <Form.Label>Last Name</Form.Label>
                  <FormikField
                    className={getClass("lastName")}
                    name="lastName"
                  />
                  {getErrorDiv("lastName")}
                </Form.Group>
              </Col>
            </Row>

            <Form.Group>
              <Form.Label>Email</Form.Label>
              <FormikField className={getClass("email")} name="email" />
              {getErrorDiv("email")}
            </Form.Group>

            <Form.Group>
              <Form.Label>Password</Form.Label>
              <FormikField
                type="password"
                className={getClass("password")}
                name="password"
              />
              {getErrorDiv("password")}
            </Form.Group>

             <Form.Group controlId="terms">
              <InputGroup hasValidation>
                <Form.Check
                  type="checkbox"
                  id="terms"
                  name="terms"
                  label="Согласен с условиями"
                  as={FormikField}
                  isInvalid={errors.terms && touched.terms}
                  feedbackType="invalid"
                  feedback={errors.terms}
                />
              </InputGroup>
            </Form.Group>

            <Button type="submit" className="w-100">
              Submit
            </Button>
          </FormikForm>
        );
      }}
    </Formik>
  );
};

export default RegisterForm;

-------------------
-<< !!!Создание Checkbox для Formik
---------
    <Form.Group controlId="terms">
      <InputGroup hasValidation>
        <Form.Check
          type="checkbox"
          id="terms"
          name="terms"
          label="Согласен с условиями"
          as={FormikField}
          isInvalid={errors.terms && touched.terms}
          feedbackType="invalid"
          feedback={errors.terms}
        />
      </InputGroup>
    </Form.Group>

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------  

---------------------------------------------------------
/=/=/ MirageJS
-------------------
    $ npm install --save-dev miragejs
    $ yarn add --dev miragejs
---------

    import { Server } from "miragejs";

    const server = new Server({ timing: 2000 }); 
    /=/ Добавить задержку


    export default function () {
        server.get("api/reminders", {
            reminders: [
            { id: 1, text: "Walk the dog" },
            { id: 2, text: "Take out the trash" },
            { id: 3, text: "Work out" },
            ],
        });
    }

Этот код говорит MirageJS, что при обращении клиента к пути "api/reminders" по методу GET нужно вернуть список напоминаний в формате JSON. 
Вы передаете этот список в объекте { reminders: [...] }.

Таким образом, когда клиент делает запрос на "/api/reminders" с помощью fetch, он обращается к MirageJS-серверу, который возвращает список напоминаний в ответ на этот запрос.

-------------------
/=/=/ Методы update и create
---------
Метод `create` в MirageJS используется для обработки HTTP-запросов типа POST и обычно используется для создания новых ресурсов на сервере.
Когда отправляется POST-запрос на указанный эндпоинт, вызывается обработчик метода create, который позволяет определить, как обрабатывать создание нового ресурса и какой ответ отправить обратно клиенту.

->> Пример:
routes() {
    this.post('/api/users', (schema, request) => {
        const requestBody = JSON.parse(request.requestBody);
        const newUser = schema.create('user', requestBody); 
        /=/ Создание новой записи пользователя в схеме MirageJS

        return newUser;
        /=/ Возврат нового пользователя в качестве ответа
   });
},
---------
    // Маршрут создания транзакции
    this.post("/users/:user_id/transactions", (schema, request) => {
        const userId = request.params.user_id;
        const user = schema.users.find(userId);

        const newTransaction = JSON.parse(request.requestBody);

        user.transactions.push(newTransaction);
        user.save();
        return user;
    });
-------------------
Метод `update` в MirageJS используется для обработки HTTP-запросов типа PUT или PATCH и обычно используется для обновления существующих ресурсов на сервере. 
Когда отправляется PUT- или PATCH-запрос на указанный эндпоинт с идентификатором существующего ресурса, вызывается обработчик метода update, который позволяет определить, как обновить ресурс и какой ответ отправить обратно клиенту.

->> Пример:
routes() {
    this.put('/api/users/:id', (schema, request) => {
        const userId = request.params.id;
        const requestBody = JSON.parse(request.requestBody);
        const user = schema.find('user', userId);

        if (user) {
            user.update(requestBody); 
            /=/ Обновление записи пользователя в схеме MirageJS
            return user; 
            /=/ Возврат обновленного пользователя в качестве ответа
        } else {
            return new Response(404, {}, { 
                message: 'Пользователь не найден' 
            }); 
            /=/ Возврат ответа 404, если пользователь не существует
        }
    });
}
-------------------
->> Создание сервера с 10 пользователями

|> main.jsx
    import { makeServer } from "./app/api/server.js";

    if (process.env.NODE_ENV === "development") {
        makeServer({ environment: "development" });
    }

|> server.js
    import { createServer, Model } from "miragejs";
    import { faker } from "@faker-js/faker";

export function makeServer({ environment = "development" } = {}) {
  const server = createServer({
    environment,

    models: {
      user: Model
    },

    seeds(server) {
      for (let i = 0; i < 10; i++) {
        const gender = faker.person.sex();
        const firstName = faker.person.firstName({ sex: gender });
        const lastName = faker.person.lastName({ sex: gender });

        server.create("user", {
          name: `${firstName} ${lastName}`,
          email: faker.internet.email({
            firstName,
            lastName: "_",
            provider: "example.com"
          }),
          password: faker.internet.password(),
          gender,
          avatarUrl: `https://avatars.dicebear.com/api/avataaars/${(
            Math.random() + 1
          )
            .toString(36)
            .substring(7)}.svg`
        });
      }
    },

    routes() {
      this.namespace = "api";

      this.get(
        "/users",
        (schema) => {
          return schema.users.all();
        },
        { timing: 2000 }
      );

      this.post("/users/:id", (schema, request) => {
        const attrs = JSON.parse(request.requestBody);
        const user = schema.users.find(request.params.id);
        user.update(attrs);
        return user.attrs;
      });
    }
  });

  return server;
}
---------
/=/ Получение пользователей
    const response = await fetch("/api/users");
    const users = await response.json();
    console.log(users);

/=/ Изменение пользователя с id = 1
    const user = { name: "Новое имя" };
    await fetch("/api/users/1", {
      method: "POST",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify(user)
    });

-------------------
->> Классовая версия MirageJS

import { Model, createServer } from "miragejs";

const reminders = [
  { text: "Walk the dog" },
  { text: "Take out the trash" },
  { text: "Work out" },
];

export default function () {
  createServer({
    models: {
      list: Model.extend({
        reminders: hasMany() /=/ может быть несколько
      }),

      reminder: Model.extend({
        list: belongsTo() /=/ принадлежит
      })
      /=/ у одного списка может быть много напоминаний, а каждое напоминание относится к одному списку
    },
    /=/ Объект `models` хранит все БД

   
    factories: {
      reminder: Factory.extend({
        text(i) {
          return `Reminder ${i}`;
        }
      })
    },

    /=/ Метод seeds() заполняет выбранную БД
    seeds(server) {
      server.createList("reminder", 5);
      /=/ Вызов генерации `factories`

      // remindersArr.forEach((el) => {
      //   server.create("reminder", el);
      // });
    }

    /**
    * Объект `schema` имеет доступ к БД
    * Для обращения ко всем элементам выбранной БД 
    * необходимо исп-ть постфикс 's' 
    * reminder =>> reminders
    */
    routes() {
      this.get("/api/reminders", (schema) => {
        return schema.reminders.all();
        /=/ Получение всех элементов `reminder`
      });

      this.post("/api/reminders", (schema, request) => {
        let attrs = JSON.parse(request.requestBody);
        return schema.reminders.create(attrs);
      });
      /=/ Используем метод create() для создания новой записи в БД, используя данные полученные из тела запроса 

      this.delete("/api/reminders/:id", (schema, request) => {
        const id = request.params.id;
        return schema.reminders.find(id).destroy();
      });
    },
  });
}

-------------------
->> Создание сервера используя готовую базу JSON

export function makeServer({ environment = "development" } = {}) {
  const server = createServer({
    environment,

    models: {
      user: Model,
      account: Model,
      category: Model,
      transaction: Model
    },

    seeds(server) {
      server.db.loadData({
        users,
        accounts,
        categories,
        transactions
      });
    },

    routes() {
      this.namespace = "api";

      // Маршруты для пользователей
      this.get("/users", (schema) => {
        return schema.users.all();
      });

      this.get("/users/:id", (schema, request) => {
        const id = request.params.id;
        return schema.users.find(id);
      });

      // Маршруты для счетов
      this.get("/accounts", (schema) => {
        return schema.accounts.all();
      });

      // this.get("/accounts/:id", (schema, request) => {
      //   const id = request.params.id;
      //   return schema.accounts.find(id);
      // });

      this.get("/accounts/:id", (schema, request) => {
        const id = request.params.id;
        const accounts = schema.accounts.where({ userId: id });
        return accounts.models;
      });
      /=/ Здесь мы используем метод schema.accounts.where({ userId: id }), чтобы получить все объекты модели account, у которых свойство ключа `userId` равно значению `id`. Затем мы возвращаем массив моделей, которые удовлетворяют условию поиска.
      
      /=/ Обратите внимание, что возвращает этот обработчик запроса массив объектов модели account, а не один объект. Если вы хотите получить только один объект, вы можете использовать метод find, как я показал ранее.

      // Маршруты для категорий
      this.get("/categories", (schema) => {
        return schema.categories.all();
      });

      this.get("/categories/:id", (schema, request) => {
        const id = request.params.id;
        return schema.categories.find(id);
      });

      // Маршруты для транзакций
      this.get("/transactions", (schema) => {
        return schema.transactions.all();
      });

      this.get("/transactions/:id", (schema, request) => {
        const id = request.params.id;
        return schema.transactions.find(id);
      });
    }
  });
  return server;
}

-------------------
/=/ Как fetch понимает куда делать запрос
---------
    function App() {
        let [users, setUsers] = useState([])

        useEffect(() => {
            fetch("/api/users")
            .then((response) => response.json())
            .then((json) => setUsers(json))
        }, [])

        return (
            <ul>
            {users.map((user) => (
                <li key={user.id}>{user.name}</li>
            ))}
            </ul>
        )
    }

Когда вы используете fetch для отправки запроса на сервер, вы обращаетесь к тому же серверу, на котором была загружена страница. Это происходит потому, что fetch отправляет запрос на относительный URL-адрес, который указывает на путь на сервере, а не на полный URL-адрес, который указывает на конкретный сервер.

Например, если ваша страница была загружена с сервера https://example.com, и вы используете fetch("/api/users"), то запрос будет отправлен на этот же сервер example.com, а не на другой сервер.

-------------------
/=/ Как это выглядит вместе с React Route
---------
    function Reminders() {
      const [reminders, setReminders] = useState([]);

      useEffect(() => {
        fetch("/api/reminders")
          .then((response) => response.json())
          .then((data) => setReminders(data.reminders))
          .catch((error) => console.error(error));
      }, []);

      return (
        <div>
          {reminders.map((reminder) => (
            <div key={reminder.id}>{reminder.text}</div>
          ))}
        </div>
      );
    }

    function App() {
      return (
        <Router>
          <Route path="/api/reminders" component={Reminders} />
        </Router>
      );
    }

    export default App;

---------------------------------------------------------
/=/=/ this - что-то вроде метода `new`, но не создает новый экземпляр, а вызывает например функцию в новом заданном контексте.
-------------------
Нет, this не создает экземпляр объекта. this является ссылкой на текущий объект, который вызывает метод или используется в контексте функции.

Это означает, что если у вас есть объект `person` с методом `getName()`, то когда вы вызываете этот метод через объект person с помощью person.getName(), this будет ссылаться на объект person. Если вы вызываете этот метод без контекста объекта, например, просто getName(), то this ссылается на глобальный объект.
---------
->> const person = {
      name: 'John',
      age: 30,
      getName() {
        return this.name;
      }
    };

    console.log(person.getName()); /=/ выводит "John"

    const getName = person.getName;
    console.log(getName()); 
    /=/ Выводит "undefined", потому что this ссылается на глобальный объект

---------
->> class Person {
      constructor(name, age) {
        this.name = name;
        this.age = age;
      }

      greet() {
        console.log(
          `Hello, my name is ${this.name} and I'm ${this.age} years old.`
        );
      }
    }

    const john = new Person("John", 30);
    const jane = new Person("Jane", 25);

    john.greet(); 
    // "Hello, my name is John and I'm 30 years old."
    jane.greet(); 
    // "Hello, my name is Jane and I'm 25 years old."

---------------------------------------------------------
/=/=/=/ DarkReader Theme 
-------------------
    https://github.com/darkreader/darkreader

    import {
        enable as enableDarkMode,
        disable as disableDarkMode,
        auto as followSystemColorScheme,
        exportGeneratedCSS as collectCSS,
        isEnabled as isDarkReaderEnabled
    } from 'darkreader';

    enableDarkMode({
        brightness: 100,
        contrast: 110,
        sepia: 0,
    });

    disableDarkMode();

    followSystemColorScheme();

    const CSS = await collectCSS();

    const isEnabled = isDarkReaderEnabled();
    
---------------------------------------------------------
/=/=/=/ useContext()
-------------------
    import React, { createContext, useState } from 'react';

    export const ThemeContext = createContext();

    const App = () => {
    const [darkTheme, setDarkTheme] = useState(false);

    const toggleTheme = () => {
        setDarkTheme(prevDarkTheme => !prevDarkTheme);
    };

    return (
        <ThemeContext.Provider value={{ darkTheme, toggleTheme }}>
        <Switcher />
        </ThemeContext.Provider>
    );
    };

    const Switcher = () => {
    const { darkTheme, toggleTheme } = useContext(ThemeContext);

    return (
        <div>
        <label>
            <input type="checkbox" checked={darkTheme} onChange={toggleTheme} />
            Dark Theme
        </label>
        </div>
    );
    };

---------------------------------------------------------
/=/=/=/ RB React Bootstrap
-------------------
/=/=/ Получить id из eventKey из Button при клике
---------
const MyButtonComponent = () => {
  const handleClick = (event) => {
    const buttonId = event.currentTarget.id;
    console.log('Button ID:', buttonId);
  };

  return (
    <Button id="my-button" onClick={handleClick}>
      Click me
    </Button>
  );
};

-------------------
/=/=/ Оформление Формы textField 
---------
const TextField = ({
  label,
  type,
  name,
  value,
  onChange,
  error,
  as,
  md,
  className
}) => {
  const [showPass, setShowPass] = useState(false);
  const [isBlur, setIsBlur] = useState(false);

  const handleClick = () => {
    setShowPass((prev) => !prev);
  };

  const handleChange = (e) => {
    onChange(e);
  };

  const handleBlur = () => {
    setIsBlur(true);
  };

  return (
    <>
      <Form.Group controlId={name} as={as} md={md} className={className}>
        <Form.Label
          // htmlFor={name}
        >
          {label}
        </Form.Label>
        {/* <label htmlFor={name}>{label}</label> */}
        <InputGroup hasValidation>
          <Form.Control
            // id={name}
            name={name}
            value={value}
            type={showPass ? "text" : type}
            onChange={handleChange}
            onBlur={handleBlur}
            isValid={!error && isBlur}
            isInvalid={!!error && isBlur}
          />
          {type === "password" && (
            <Button variant="outline-secondary" onClick={handleClick}>
              {showPass ? eyeSlash : eyeFill}
            </Button>
          )}
          <Form.Control.Feedback type="invalid">{error}</Form.Control.Feedback>
        </InputGroup>
      </Form.Group>
    </>
  );
};

TextField.defaultProps = {
  type: "text",
  className: "mb-3"
};

TextField.propTypes = {
  label: PropTypes.string,
  type: PropTypes.string,
  name: PropTypes.string,
  value: PropTypes.string,
  onChange: PropTypes.func,
  error: PropTypes.string,
  as: PropTypes.object,
  md: PropTypes.string,
  className: PropTypes.string
};

export default TextField;


 * Form.Group используется для обертывания лейбла и поля ввода вместе. 
 * InputGroup используется для создания группировки элементов ввода, таких как поля ввода текста, кнопки, выпадающие списки и т.д.
 * Form.Control используется для создания поля ввода

 * Form.Text используется для создания дополнительного текста под полем ввода, который может использоваться для предоставления дополнительной информации о поле ввода.
 * Form.Label - Не рекомендуется! Устанавливает свой margin-bottom. Лучше использовать обычный label

-------------------
-<< <Col md={{ span: 6, offset: 3 }}>
---------
    * span: 6 указывает на то, что элемент должен занимать ширину в 6 колонок сетки
    * offset: 3 указывает на то, что элемент должен быть отцентрован относительно левого края сетки на 3 колонки.

    <Container>
      <Row>
        <Col md={{ span: 6, offset: 3 }}></Col>
      </Row>
    </Container>
-------------------
-<< Оформление Формы Checkbox
---------
    const handleChange = ({ target }) => {
        onChange({
            target: {
                name,
                value: target.checked
            }
        });
    };

    <Form.Group
        // className="position-relative" /=/ 1)
        controlId={`form-group-${name}-id`}
    >     
      <Form.Check
        label={children}
        name={name}
        checked={value}
        onChange={handleChange}
        isInvalid={!!error}
        feedback={error}
        feedbackType="invalid"
        // feedbackTooltip /=/ 2)
        className={className}
      />
    </Form.Group>

    /=/ 1) и 2) - если оба вкл будет плавающее окно ошибки
-------------------
/=/ Полная Форма Checkbox
---------
import PropTypes from "prop-types";
import { Form } from "react-bootstrap";

const CheckboxField = ({
  as,
  name,
  value,
  onChange,
  error,
  children,
  className,
  style
}) => {
  const handleChange = ({ target }) => {
    onChange({
      target: {
        name,
        value: target.checked
      }
    });
  };

  return (
    <Form.Group controlId={`form-group-${name}-id`}>
      <Form.Check
        as={as}
        label={<div style={{ ...style }}>{children}</div>}
        name={name}
        checked={value}
        onChange={handleChange}
        isInvalid={!!error}
        feedback={error}
        feedbackType="invalid"
        className={className}
      />
    </Form.Group>
  );
};

CheckboxField.defaultProps = {
  style: { fontSize: "15px" }
};

CheckboxField.propTypes = {
  label: PropTypes.string,
  name: PropTypes.string.isRequired,
  value: PropTypes.bool.isRequired,
  onChange: PropTypes.func.isRequired,
  error: PropTypes.string,
  children: PropTypes.oneOfType([
    PropTypes.arrayOf(PropTypes.node),
    PropTypes.node
  ]),
  className: PropTypes.string,
  as: PropTypes.oneOfType([PropTypes.func, PropTypes.object]),
  style: PropTypes.object
};

export default CheckboxField;

-------------------
-<< Оформление Формы Login/Register
---------
  const [formType, setFormType] = useState("login");

  return (    
    <Container className="mt-3">
      <Row>
        <Col md="7" className="shadow p-4" style={{ maxWidth: "500px" }}>
          <Nav
            fill
            variant="tabs"
            defaultActiveKey="login"
            activeKey={formType}
            onSelect={(selectedKey) => setFormType(selectedKey)}
          >
            <Nav.Item>
              <Nav.Link eventKey="login">Login</Nav.Link>
            </Nav.Item>
            <Nav.Item>
              <Nav.Link eventKey="register">Register</Nav.Link>
            </Nav.Item>
          </Nav>
          <div className="mt-2">
            {formType === "login" ? <LoginForm /> : <RegisterForm />}
          </div>
        </Col>
      </Row>
    </Container>
  )
-------------------
-<< Установить css только на указанный элемент 
---------
/=/ Только на указанный элемент 
    form > div {
        margin-bottom: 1rem;
    }

/=/ Распространится на потомков
    form div {
        margin-bottom: 1rem;
    }
-------------------
-<< OverlayTrigger - добавление всплывающей подсказки с полным текстом
---------
const OverlayTooltip = ({ text, children }) => {
  const [showTooltip, setShowTooltip] = useState(false);
  const ref = useRef(null);

  const handleMouseEnter = () => {
    const { current } = ref;
    if (current.offsetWidth < current.scrollWidth) {
      setShowTooltip(true);
    }
  };
  /=/ offsetWidth - это свойство элемента, которое возвращает его текущую ширину в пикселях
  /=/ scrollWidth - это свойство элемента, которое возвращает полную ширину содержимого элемента, включая неотображаемую часть, которая обычно скрыта за границами элемента
  
  const handleMouseLeave = () => {
    setShowTooltip(false);
  };

  const tooltip = <Tooltip id="tooltip">{text || children}</Tooltip>;

  return (
    <OverlayTrigger 
      placement="bottom" 
      overlay={tooltip} 
      show={showTooltip} /=/ Отображать или нет подсказку
    >
      <div
        style={{
          whiteSpace: "nowrap",
          overflow: "hidden",
          textOverflow: "ellipsis"
        }}
        ref={ref}
        onMouseEnter={handleMouseEnter}
        onMouseLeave={handleMouseLeave}
      >
        {text || children}
      </div>
    </OverlayTrigger>
  );
};

OverlayTooltip.propTypes = {
  text: PropTypes.oneOfType([
    PropTypes.string.isRequired,
    PropTypes.node.isRequired
  ]),
  children: PropTypes.oneOfType([
    PropTypes.string.isRequired,
    PropTypes.node.isRequired
  ])
};

OverlayTooltip.propTypes = (props, componentName) => {
  if (!props.text && !props.children) {
    return new Error(
      `One of 'text' or 'children' is required in '${componentName}'.`
    );
  }

  if (props.text && props.children) {
    return new Error(
      `Only one of 'text' or 'children' is allowed in '${componentName}'.`
    );
  }
};

---------
/=/ !!! Важно указать истинные размеры контейнера p-0
    <Container>
      <Row>
        <Col md="4" 
          className="p-0 d-flex justify-content-center"
        >
          <OverlayTooltip text="Расход" />
        </Col>
      </Row>
    </Container>

-------------------
-<< Dropdown
---------
    <Dropdown 
        className="d-inline mx-2" 
        show={isOpen} 
        drop="down-centered" 
        onClick={handleOpen}
    >
        <Dropdown.Toggle>
            Default Dropdown
        </Dropdown.Toggle>
        <Dropdown.Menu>
            <Dropdown.Item href="#">Item</Dropdown.Item>
        </Dropdown.Menu>
    </Dropdown>
-------------------
    const [isOpen, setIsOpen] = useState(false);

    const handleOpen = () => {
        setIsOpen((prev) => !prev);
    };
  
    <div
      className="user-select-none"
      style={{
        cursor: "pointer",
        whiteSpace: "nowrap",
        overflow: "hidden",
        textOverflow: "ellipsis"
      }}
      onClick={handleOpen}
    >
      <OverlayTooltip>Dropdown_sssssss</OverlayTooltip>
    </div>
    
    <NavDropdown onClick={handleOpen} show={isOpen} drop="down-centered">
      <NavDropdown.Item eventKey="1">Action</NavDropdown.Item>
    </NavDropdown>

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

-------------------
-<< 
---------

---------------------------------------------------------
/=/=/ .useImperativeHandle() - вызов функции из Родительского компонента в дочернем  
-------------------
const ChildComponent = React.forwardRef((props, ref) => {
  const myFunctionInChild = () => {
    console.log('Функция в дочернем компоненте была вызвана');
  };

  React.useImperativeHandle(ref, () => ({
    myFunctionInChild,
  }));

  return (
    <div>
      {/* Компонент содержимого */}
    </div>
  );
});


const ParentComponent = () => {
  const childRef = React.useRef(null);

  const callFunctionInChild = () => {
    childRef.current.myFunctionInChild();
  };

  return (
    <div>
      {/* Дочерний компонент с привязкой рефа */}
      <ChildComponent ref={childRef} />

      {/* Кнопка для вызова функции в дочернем компоненте */}
      <button onClick={callFunctionInChild}>Вызвать функцию в дочернем компоненте</button>
    </div>
  );
};

---------------------------------------------------------
/=/=/ Создать Компонент StickyFooter
-------------------
|> StickyFooter
    const StickyFooter = ({ body, footer }) => {
        return (
            <div className="d-flex flex-column min-vh-100">
            <div className="flex-grow-1">{body}</div>
            {footer}
            </div>
        );
    };

    StickyFooter.propTypes = {
        body: PropTypes.oneOfType([
            PropTypes.arrayOf(PropTypes.node),
            PropTypes.node
        ]),
        footer: PropTypes.oneOfType([
            PropTypes.arrayOf(PropTypes.node),
            PropTypes.node
        ])
    };

|> App.js
    return (
        <>
        <NavBar onToggleTheme={handleToggleTheme} darkTheme={darkTheme} />
        <StickyFooter
            body={
            <Switch>
                <Route path="/login/:type?" component={Login} />
                <Route path="/profile" />
                <Route path="/settings" />
                <Route path="/history" />
                <Route path="/analysis" />
                <Route path="/main" />
                <Route path="/" component={Welcome} />
            </Switch>
            }
            footer={<Route path="/" component={Footer} />}
        />
        </>
    );

---------------------------------------------------------
/=/=/ DataPicker
-------------------

    $ yarn add react-datepicker
    
    import "react-datepicker/dist/react-datepicker.css";
---------

    import ReactDatePicker, {
        registerLocale,
        setDefaultLocale
    } from "react-datepicker";
    import ru from "date-fns/locale/ru";
    registerLocale("ru", ru);

    const [selectedDate, setSelectedDate] = useState(new Date());

    const handleDateChange = (date) => {
        setSelectedDate(date);
    };

    <ReactDatePicker
        selected={selectedDate}
        onChange={handleDateChange}
        calendarStartDay={1}
        locale="ru"
        showTimeSelect
        dateFormat="dd.MM.yyyy"
    />
-------------------
/=/ Создание Компонента DatePicker
---------
import PropTypes from "prop-types";
import ReactDatePicker, { registerLocale } from "react-datepicker";
import ru from "date-fns/locale/ru";
import { forwardRef, useEffect, useRef, useState } from "react";
import { MdOutlineDateRange } from "react-icons/md";
import { toReadableDate } from "../../../utils";
registerLocale("ru", ru);

const CustomInput = forwardRef(({ value, onClick }, ref) => (
  <div className="flex items-center cursor-pointer" onClick={onClick}>
    <MdOutlineDateRange
      size={20}
      className="flex items-center justify-center mr-0.5"
    />
    <span className="select-none">{value}</span>
  </div>
));

const DatePicker = () => {
  const [selectedDate, setSelectedDate] = useState(new Date());
  const [isOpen, setIsOpen] = useState(false);

  console.log(toReadableDate(selectedDate).dateOnly);

  const onInputClick = () => {
    setIsOpen((prev) => !prev);
  };

  const handleDateChange = (date) => {
    setSelectedDate(date);
  };

  const calendarRef = useRef(null);

  useEffect(() => {
    const handleClickOutside = ({ target }) => {
      if (!calendarRef?.current?.contains(target)) {
        setIsOpen(false);
      }
    };

    document.addEventListener("mousedown", handleClickOutside);

    return () => {
      document.removeEventListener("mousedown", handleClickOutside);
    };
  }, [isOpen]);

  return (
    <div className="inline-block" ref={calendarRef}>
      <ReactDatePicker
        selected={selectedDate}
        customInput={<CustomInput />}
        locale="ru"
        calendarStartDay={1}
        todayButton="Сегодня"
        dateFormat="dd.MM.yyyy"
        onChange={handleDateChange}
        onInputClick={onInputClick}
        open={isOpen}
      />
    </div>
  );
};

CustomInput.displayName = "CustomInput";

export default DatePicker;

---------------------------------------------------------
/=/=/=/ Sass
-------------------
$spacer: 5vh;
$spacer-scale: 20;
$step: 5;

@for $i from 0 through $spacer-scale {
  .vh-#{$i * $step} {
    height: $i * $spacer;
  }
}
@for $i from 0 through $spacer-scale {
  .vw-#{$i * $step} {
    height: $i * $spacer;
  }
}

-------------------
-<< $variable - переменная
-------------------
-<< @mixin - позволяет определить набор свойств CSS, которые можно повторно использовать в других частях кода. 
---------
@mixin border-radius($radius) {
  border-radius: $radius;
  -moz-border-radius: $radius;
  -webkit-border-radius: $radius;
}

.box {
  @include border-radius(10px);
}
-------------------
-<< @extend - позволяет наследовать свойства CSS из одного класса в другой. 
---------
.error {
  border: 1px solid #f00;
  background-color: #fcc;
}

.error-message {
  @extend .error;
  font-size: 14px;
}

-------------------
-<< @function - позволяет определить функцию, которая возвращает значение переменной. 
---------
@function calculate-width($width, $padding) {
  @return $width + ($padding * 2);
}

.container {
  width: calculate-width(100px, 10px);
}

-------------------
-<< @if и @else - позволяют использовать условия в Sass. 
---------
$width: 100px;

.box {
  @if $width > 300px {
    font-size: 24px;
  } @else {
    font-size: 16px;
  }
}

-------------------
-<< @for - позволяет создавать циклы в Sass. 
---------
@for $i from 1 through 3 {
  .box-#{$i} {
    width: 100px * $i;
  }
}

-------------------
-<< @each - позволяет перебирать списки и карты в Sass. 
---------
$colors: (
  "red": #f00,
  "green": #0f0,
  "blue": #00f
);

@each $name, $color in $colors {
  .text-#{$name} {
    color: $color;
  }
}

-------------------
-<< @import - позволяет импортировать другие файлы в текущий Sass-файл. 
---------
@import "reset";
@import "variables";
@import "mixins";

// основной код

---------------------------------------------------------
/=/=/=/ Tailwind
---------------------------------------------------------
/=/=/ Создание Dropdown
-------------------
const getIdAllItem = (type) => {
  return {
    id: "all-" + (type ? `${type}-ids` : "ids"),
    type,
    name: "Все"
  };
};

const Dropdown = ({ items, type, onSelect, reset }) => {
  const ALL_ITEM = getIdAllItem(type);
  const isInitialRender = useRef(true);
  const [isOpen, setIsOpen] = useState(false);
  const [selectedItem, setSelectedItem] = useState(ALL_ITEM);

  const handleClick = ({ target }) => {
    const { id: eventKey } = target;
    if (eventKey) {
      setSelectedItem(JSON.parse(eventKey));
    }
    setIsOpen((prev) => !prev);
  };

  useEffect(() => {
    // Вызов onSelect только после первого рендера
    if (!isInitialRender.current) {
      onSelect(selectedItem);
    } else {
      isInitialRender.current = false;
    }
  }, [selectedItem]);

  useEffect(() => {
    // Сброс title в dropdown на изначальное, при смене счета.
    if (reset) {
      setSelectedItem(ALL_ITEM);
    }
  }, [reset]);

  const dropdownRef = useRef(null);

  // Слушатель для закрытия dropDownList при клике вне него
  useEffect(() => {
    const handleClickOutside = ({ target }) => {
      if (!dropdownRef?.current?.contains(target)) {
        setIsOpen(false);
      }
    };

    document.addEventListener("mousedown", handleClickOutside);

    return () => {
      document.removeEventListener("mousedown", handleClickOutside);
    };
  }, [isOpen]);

  return (
    <div className="relative" ref={dropdownRef}>
      <button
        className="flex items-center justify-center w-full px-1 py-0.5 text-black"
        onClick={handleClick}
      >
        <OverlayTooltip text={selectedItem?.name || selectedItem} />
        <RiArrowDropDownLine size="20px" />
      </button>
      {isOpen && (
        <div
          className="dropdown-menu show bg-white rounded-md shadow-lg cursor-pointer absolute left-1/2 transform -translate-x-1/2 z-10 w-44 py-1 mt-1"
          onClick={handleClick}
        >
          <a
            id={JSON.stringify(ALL_ITEM)}
            className="block px-4 py-1.5 text-black hover:bg-gray-200 no-underline border-b border-gray-300"
          >
            Все
          </a>
          {items.map((item) => (
            <a
              id={JSON.stringify(item)}
              key={item.id}
              className="block px-4 py-1.5 text-black hover:bg-gray-200 no-underline"
            >
              {item.name}
            </a>
          ))}
        </div>
      )}
    </div>
  );
};


---------------------------------------------------------
/=/=/=/ TypeScript
---------------------------------------------------------
    $ npm install -g typescript
    $ yarn add typescript

-------------------
/=/=/ tsconfig.json
---------
{
  "compilerOptions": {
    "target": "ES6",
    // Версия ECMAScript, к которой будет компилироваться код
    "module": "ESNext",
    // Формат модулей (ESNext для использования import/export)
    "allowJs": true,
    // "sourceMap": true,
    // "noEmitOnError": true,
    // Не создает файлы JS, если во время компиляции возникают ошибки.
    "forceConsistentCasingInFileNames": true,
    // Гарантирует, что при импорте будет указан правильный регистр имени файла.
    "jsx": "react",
    // Тип JSX, используемый в React
    "strict": true,
    // Включить строгие настройки TypeScript
    "esModuleInterop": true,
    // Разрешить импорт модулей в стиле ES6
    "moduleResolution": "node",
    // Отключение ошибок для импортов
    "outDir": "./dist",
    // Создает файлы JS в папке, а не рядом (иначе может заменять исходники)
    "skipLibCheck": true
    // Отключение проверок библиотек
  },
  "include": ["src/**/*"],
  "exclude": ["**/*.spec.ts"]
  // Папки, которые нужно включить в компиляцию
}

-------------------
/=/ Пример типизирования функции
-------------------
export const cropDate = (date: Date): string => {
  const day: number = date.getDate();
  const month: number = date.getMonth() + 1;
  const year: number = date.getFullYear();

  return `${day}.${month}.${year}`;
};

Мы добавили тип Date для параметра date. Также мы указали типы переменных day, month и year как number, поскольку они представляют числовые значения. Возвращаемое значение функции указано как string, так как вы возвращаете строку в формате даты.

---------------------------------------------------------
/=/ Пример типизирования функции 
-------------------
interface DataItem {
  date: string;
}

interface UniqDateItem extends DataItem {
  name: string;
}

const getUniqDates = (data: DataItem[]): UniqDateItem => {
  return chain(data)
    .uniqBy("date")
    .map((uniq: DataItem) => ({
      ...uniq,
      name: toReadableDate(uniq.date).dateOnly
    }))
    .reverse()
    .value();
};

/=/ DataItem[] обозначает, что это описывает массив элементов. Такая нотация указывает на то, что функция getUniqDates принимает аргумент data, который должен быть массивом
---------
/=/ extends
  Ключевое слово extends используется для создания интерфейсов, которые расширяют другие интерфейсы.

  В данном случае "interface UniqDateItem extends DataItem" говорит о том, что интерфейс UniqDateItem наследует свойства из интерфейса DataItem. Это означает, что все свойства, указанные в интерфейсе DataItem, такие как date, будут также доступны и в интерфейсе UniqDateItem.

---------------------------------------------------------
/=/=/ Разбор Типизации TS
-------------------
-< type Fn = () => void
---------
type ClickOutsideAction = () => void означает, что ClickOutsideAction - это тип функции, которая не принимает аргументов и не возвращает никакого значения (void).

const useClickOutside = (
  elemRef: RefObject<HTMLElement>,
  outsideAction: ClickOutsideAction,
  insideAction?: ClickOutsideAction
) => {
  useEffect(() => {
    // ...
    
      if (!elemRef?.current?.contains(target)) {
        outsideAction();
      } else if (insideAction) {
        insideAction();
      }
    };
    
    // ...

)};
-------------------
-< Type Guard.
---------
    function isBoolean(value: string | boolean): value is boolean {
        return typeof value === 'boolean'
    }

    function logFlag(flag: string | boolean) {
        if (isBoolean(flag)) {
            console.log('Hey it is boolean')
        } else {
            console.log('Hey it is string')
        }
    }

    logFlag(true)
    logFlag("true")

-------------------
-< type vs interface
---------
    - type используется при записи в строку (number | string)
    - interface для описания классов и обьектов 
-------------------
-< Union Type
---------
    type NumberOrString = number | string;

    function printNumberOrString(value: NumberOrString) {
        console.log(value);
    }

    printNumberOrString(42);  
    printNumberOrString("hello");  

-------------------
-< Generic Type - позволяет работать с различными типами данных (коллекциями) без потери типовой безопасности
---------
    const arr: Array<number> = [1, 2, 3, 4]
    const arr: Array<number | string | boolean> = [1, 2, "3", false]
---------
    function identity<T>(arg: T): T {
        return arg;
    }

    let result = identity("hello"); // result имеет тип string

В этом примере T - это параметр типа, который можно использовать как тип аргумента функции и как тип возвращаемого значения. Вызов identity("hello") возвращает значение типа string, потому что тип T был заменен TS на string.

-------------------
/=/=/ Более строгие Generic
---------
    function log<T extends string | number>(data: T): T {
        console.log(data)
        return data
    }

    const res1 = <string>log('a')
    let res2 = log(42) as number
    // let res3 = log(false) // error

-------------------
/=/ Обобщенная функция с ограничением типа
---------
    function multiply<T extends number>(
        value: T,
        multiplier: T
    ): number {
        return value * multiplier;
    }

    let result = multiply(5, 3); /=/ result имеет тип number

В этом примере T extends number означает, что обобщение T ограничено типом number. Это позволяет использовать функцию multiply только с аргументами типа number и возвращать значение типа number.
-------------------
/=/ Пример Generic с Class-ми
---------
    class Collection<T extends number | string> {
        constructor(private _items: T[]) {}

        add(value: T): void {
            this._items.push(value)
        }

        get items(): T[] {
            return this._items
        }
    }

    const res1 = new Collection<number>([1, 2, 3])
    res1.add(4)

    const res2 = new Collection<string>(['2'])
    res2.add('4')
-------------------
-< R extends keyof T
---------
    const obj = {
        a: 1,
        b: 2,
        c: 3,
    };

    const getValue = <T extends object, R extends keyof T>(obj: T, key: R) => {
        return obj[key];
    };

    const valueC = getValue(obj, "c");

R extends keyof T означает, что R может быть только одним из ключей, определенных в объекте типа T
-------------------
-< Record<K, V> - используется для создания объектов с определенными типами ключей и значений
---------
    Syntax:
    type MyRecord = Record<KeyType, ValueType>;
---------
    type FruitPrices = Record<string, number>;

    const fruitPrices: FruitPrices = {
        apple: 0.5,
        banana: 0.3,
        orange: 0.8,
    };

    const applePrice: number = fruitPrices.apple; 
    /=/ OK

    const invalidFruitPrices: FruitPrices = {
        apple: 0.5,
        banana: 'cheap',
    };
    /=/ Ошибки компиляции, так как ключи с разными типами


-------------------
-< 
---------

-------------------
-< 
---------

-------------------
-< 
---------

-------------------
-< 
---------

-------------------
-< 
---------

-------------------
-< 
---------

-------------------
-< 
---------

-------------------
-< 
---------

-------------------
-< 
---------

---------------------------------------------------------
/=/=/=/ Redux
-------------------
/=/ Пример создания PipeLine и Каррирования
---------
const App = () => {
    const x = 2;
    const double = (num) => num * 2;
    const square = (num) => num * num;
    const half = (num) => num / 2;
    const divide = (num2) => {             
            return function divide(num1) {
            return num1 / num2;
        };
    }; /=/ Каррирование

    // const mathCalculate = half(square(double(x)))
    // const mathCalculate = compose(half, square, double);
    
    const mathCalculate = pipe(double, square, half, divide(3));

    return <h1>{mathCalculate(x)}</h1>;
};
-------------------
/=/ Pure Functions - Чистые функции 
---------
Чистые функции имеют следующие свойства:

    * Deterministic (Однозначность): Для одного и того же набора входных данных, чистая функция всегда возвращает одинаковый результат. Это означает, что функция не зависит от каких-либо скрытых состояний, исключая переданные аргументы.

    * No Side Effects (Отсутствие побочных эффектов): Чистая функция не влияет на внешние переменные, файлы, базы данных или любой другой источник данных. Она не должна модифицировать состояние вне своей области действия.

    * No Dependency on State (Нет зависимости от состояния): Чистая функция не зависит от состояния программы. Это означает, что результат функции зависит только от переданных ей аргументов.
---------
Пример чистой функции:

    function add(a, b) {
        return a + b;
    }
    /=/ Это чистая функция, так как она не имеет побочных эффектов и всегда возвращает одинаковый результат для одинаковых входных данных.
---------
Пример функции, которая не является чистой:

    let total = 0;

    function addToTotal(value) {
        total += value;
    }
    /=/ Эта функция зависит от глобальной переменной и имеет побочный эффект, так как она изменяет состояние вне своей области действия.


---------------------------------------------------------
/=/=/=/ HTML
-------------------
/=/=/ Определение кодировки и языка страницы
-------------------
    * Кодировка определяется в теге head > meta через атрибут charset
    * Язык страницы определяется в теге html через атрибут lang=""

-------------------
/=/=/ Метатеги SEO
---------
    * <title> - Определяет заголовок страницы который отображается в поисковике.
    * <meta name="description" content=""> - Краткое описание страницы 
    * <meta name="keywords" content="1,2,3"> - Ключевые слова для поиска
    * <meta name="robots" content="index/noindex, follow/nofolow"> -
        - Разрешение на индексацию страницы (отображение в поиске).
        - Разрешение на индексацию ссылок внутри и отображение связанных страниц 
    * <meta name="viewport" content="width=device-width, initial-scale=1.0">
        - width=device-width - использовать ширину экрана устройства в качестве ширины просмотра страницы.
        - initial-scale - начальнй масштаб

    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <meta name="description" content="Описание страницы">
            <meta name="keywords" content="ключевое слово1, ключевое слово2, ...">
            <meta name="robots" content="index, follow">
            <title>Заголовок страницы</title>
        </head>
        <body>
            <!-- Содержимое страницы -->
        </body>
    </html>



---------------------------------------------------------
/=/=/=/ Accessibility и Семантика. Доступность сайта. 
---------------------------------------------------------
Это необходимо для скринридеров, корректного перевода, переключением по темам заголовков, для SEO (лучшей выдачи в поисковиках), для управления клавиатурой через Tab и Enter.
---------------------------------------------------------
    *** Указывать на каком языке написан документ
-------------------
    <html lang="ru"></html>
** Если встречаются несколько языков:
    <p>В воздухе витало <i lang="fr">je ne sais quoi</i>.</p>
---------------------------------------------------------
    *** Если нужна кнопка, используй элемент `<button>`
---------------------------------------------------------
    *** Структурировать разметку при помощи Заголовков:
-------------------
    <!-- Делайте так: -->
        <body>
            <h1>Мой сайт</h1>
            <h2>Заголовок</h2>
                <h3>Подзаголовок</h3>
            <h2>Заголовок</h2>
        </body>
    <!-- Не пропускайте уровни: -->
        <body>
            <h1>Мой сайт</h1>
            <h4>Заголовок</h4>
                <h2>Подзаголовок</h2>
            <h3>Заголовок</h3>
        </body>
    <!-- Не полагайтесь на несуществующие алгоритмы: -->
        <body>
            <h1>Мой сайт</h1>
            <section>
                <h1>Заголовок</h1>
                <section>
                    <h1>Подзаголовок</h1>
                </section>
            </section>
            <section>
                <h1>Заголовок</h1>
            </section>
        </body>
--------------------------------------------------------- 
    *** Использование ориентиров для передвижения по сайту.
-------------------
Разметка тематических секций:

<article> - для содержимого которое может быть распространено как отдельная единица. 
Используется для статей, блогов, новостей и других подобных контентных блоков.

    <article>
        <h2>Заголовок статьи</h2>
        <p>Текст статьи...</p>
        <p>Дополнительный текст статьи...</p>
        <footer>Автор: Имя автора</footer>
    </article>
---------
<aside> - доп инфа, которая не является основным содержимым страницы, но связана с ним.
    
    <aside>
        <h2>Дополнительная информация</h2>
        <p>Это блок с дополнительной информацией, который может содержать сайдбар, рекламу, ссылки и т.д.</p>
    </aside>
---------
<nav> - обозначение навигации 

    <nav>
        <ul>
            <li><a href="#">Главная</a></li>
            <li><a href="#">О нас</a></li>
            <li><a href="#">Услуги</a></li>
            <li><a href="#">Контакты</a></li>
        </ul>
    </nav>
---------
<section> - Выделение разделов и блоков информации.

    <body>
        <article>
            <section>...</section>
        </article>

        <section>
            <h2>Заголовок раздела</h2>
            <p>Текст и содержимое раздела...</p>
        </section>
        <section>
            <h2>Еще один раздел</h2>
            <p>Другой текст и содержимое раздела...</p>
        </section>
    </body>

<section> — более крупный логический контейнер, объединяющий содержание по смыслу. 
Например, блок «О компании», список товаров, раздел личной информации в профиле и так далее.

---------
`role` - для специфических секций, например, поиск.

    <div role="search">
        <input type="text" placeholder="Search...">
        <button>Search</button>
    </div>

---------
`main, `header` и `footer` также являются ориентирами
    «Элемент main указывает на секцию с основным контентом в документе или приложении» и не должен использоваться больше одного раза.

    <body>
        <header>
            <h1>Шапка</h1>
            <nav>
                <!-- основная навигация -->
            </nav>
        </header>   

        <!-- Основной контент нашей страницы -->
        <main>
            <!-- На ней есть статьи -->
            <article>
                <h2>Заголовок статьи</h2>
            </article>
            <aside>
                <h2>Связанный второстепенный контент</h2>
            </aside>
            <section>        
                <h2>Посты в блоге</h2>
                ...
            </section>
        </main> 

        <footer>
            &copy; 2023 Developer_Name
        </footer>
    </body>
---------------------------------------------------------
    *** Используйте `div` для разметки больших кусков связанного контента, отличающегося от остального контента на странице. Не злоупотребляйте секционными элементами. Используйте <div>
---------------------------------------------------------
    ***`fieldset` для группировки элементов формы и придания им большего контекста.
-------------------
    <form>
        <fieldset>
            <legend>Размеры рубашек</legend>
            <input type="radio" id="s" name="shirtsize" />
            <label for="s">S</label>  
            <input type="radio" id="m" name="shirtsize" />
            <label for="m">M</label>  
            <input type="radio" id="l" name="shirtsize" />
            <label for="l">L</label>   
        </fieldset>
    </form>

    Точно также как с <section>, при оборачивании элементов формы в <fieldset> нужно быть внимательным. Группируйте элементы при помощи <fieldset> если у вас есть необходимость связать элементы в группу и добавляйте лейбл для этой группы при помощи <legend>.

    Если обернуть все в `fieldset` и поместить «Размеры рубашек» в тег <legend>, то экранные читалки будут знать, что <legend> относится к радиокнопкам и прочитает их значения вне зависимости от того, какая из них выбрана.
---------------------------------------------------------
    *** Использование понятного языка
-------------------
    * Не используйте тире, если можете избежать этого. Вместо «5-7», напишите «от 5 до 7».
    * Не пишите сокращения: вместо «Янв» пишите «Январь».
    * Расшифровывайте аббревиатуры, как минимум один или два раза. Вместо «HTML» при первом употреблении, пишите «Hypertext Markup Language».
---------------------------------------------------------
    *** Описание для элементов интерфейса
-------------------
==/Good/==:
    <p>
        Киты очень классные существа. 
        <a href="whales.html">Узнать больше о китах</a>.
    </p>
==/Bad/==:
    <p>
        Киты очень классные существа. Чтобы узнать больше о китах,
        <a href="whales.html">нажмите здесь</a>.
    </p>

---------------------------------------------------------
    *** Доступные таблицы
-------------------
    <thead>
        <tr>
            <th scope="col">Band</th>
            <th scope="col">No. of Albums</th>
            <th scope="col">Most famous song</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">Buzzcocks</th>
            <td>1976</td>
            <td>9</td>
        </tr>
    </tbody>

---------------------------------------------------------
    *** Необходимость атрибутов `alt` в <img>
-------------------
Атрибут `alt` - это страховка в случае если важный визуальный элемент пропадает, чтобы его важная часть сохранилась в html виде и была доступна для ридеров. 
Так же наличие описание в атрибуте отражает приоритет или вторичность контента.

    - Контентное изображение - при исчезновении которого теряется функциональность
    - Декоративное - функциональность доступна, потеряна лишь визуальная состовляющая

    * Содержание атрибута `alt` должно всегда предоставлять прямое представление изображения и то, что оно визуально передаёт.  
    * Если изображениt декоративное, лучше оставить значение атрибута `alt=""` пустым или вставить как background-image.

-------------------
/=/ Спорные моменты
---------
->> Изображение в промослайдере

В элементах слайдера нам часто встречаются изображения товаров. Они несут в себе важную визуальную информацию о товаре, поэтому в таком случае нам следует отнести их к контентному типу <img>.
---------
->> Пример `alt` для изображения местоположения на карте

    Реализация: <img> (атрибут alt должен описывать изображение, в данном случае — Карта офиса по адресу улица Строителей, 15)

-------------------
    ==/OR/==
    ** Cвязывание <img> и <p> через id
---------
    <img src="dinosaur.png" aria-labelledby="dino-label" />
    <p id="dino-label">Красный тираннозавр Mozilla ...</p>

В этом случае мы вообще не используем атрибут alt. Вместо этого мы представили наше описание изображения как обычный параграф, указали id, и потом использовали атрибут aria-labelledby, сославшись на тот id. Это вынуждает скринридеры использовать параграф как альтернативный текст/описание изображения.

-------------------
    ==/OR/==
    ** <figure> и <figcaption> 
---------
Должны связывать какую-любо фигуру (всё что угодно, необязательно изображение) с заголовком фигуры

    <figure>
        <img 
            src="dinosaur.png" 
            alt="Тираннозавр организации Mozilla" 
        />
        <figcaption>
            Красный тираннозавр Рекс: стоящий как человек двуногий динозавр, с
            маленькими передними лапами и большой головой с большим количеством острых
            зубов.
        </figcaption>
    </figure>

---------------------------------------------------------
    *** `hover` и `focus`. Писать сразу 2 стиля
-------------------
    Необходимо использовать стилизование сразу для двух типов действий. Так будут охвачены все виды тачпадов и устройств 

---------------------------------------------------------
    *** Ссылка и Кнопка
-------------------
Что выбрать?
    0) Начинаем с кнопки <button/>.
    1) Если чего-то не хватает в функционале, то <a/>

    Ссылка - то у чего есть адресс
    У Кнопки нет адреса
---------------------------------------------------------
    *** <button type="button" /> - обязателен
-------------------
    type="button" обязателен, тк по умолчанию стоит type="submit" и он будет отправлять форму

---------------------------------------------------------
/=/=/=/ SVG - Масштабируемая Векторная Графика 
(Scalable Vector Graphics)  
---------------------------------------------------------
 SVG - формат графики, основан на XML.

    * Растровые картинки состоят из фиксированного числа пикселей. (JPEG, GIF, PNG)
      - Изменение размера картинки влияет на качество.

    * Векторное изображение не зависит от разрешения устройства. 
      - Они построены на использовании геометрических фигур — линий, прямоугольников, кривых или последовательности команд. 
      - Их атрибуты поддаются изменению (цвет, заливка и рамка)
-------------------
/=/=/ SVG-теги
---------
/=/ <svg> - является контейнером для создания графики на основе векторов
---------   
<svg>:
    * Задает ширину и высоту холста.
    * Может содержать любое количество других SVG-элементов, таких как 
    <circle>, <rect>, <line>, <path>, <text>.
    * Поддерживает анимацию, стилизацию и интерактивность.


    <svg xmlns="http://www.w3.org/2000/svg width="200" height="150"">
        <circle cx="50" cy="50" r="40" fill="blue" />
        <rect x="10" y="10" width="80" height="80" fill="red" />
        <line x1="10" y1="110" x2="190" y2="110" stroke="green" stroke-width="2" />
        <text x="10" y="140" font-family="Arial" font-size="16" fill="black">Hello, SVG!</text>
        <path d="M110 140 Q 152.5 70, 195 140 T 280 140" fill="purple" />
    </svg>
-------------------
/=/ Фигура(элемент) <path> - определяет путь, состоящий из координат точек для формирования фигуры.
---------
Примеры команд:

    M - Move To (переместиться в указанные координаты)
    L - Line To (нарисовать линию к указанным координатам)
    H - Horizontal Line To (нарисовать горизонтальную линию)
    V - Vertical Line To (нарисовать вертикальную линию)
    C - Cubic Bezier Curve To (нарисовать кубическую кривую Безье)
    Q - Quadratic Bezier Curve To (нарисовать квадратичную кривую Безье)
    A - Arc To (нарисовать дугу)
    Z - Close Path (закрыть путь)
---------
    <svg height="210" width="400">
        <path d="M150 0 L75 200 L225 200 Z" />
    </svg>

    «M150 0» — переместись на (150,0);
    «L75 200» — нарисуй линию к (75,200) от предыдущей точки (которая имела координаты (150,0));
    «L255 200» — нарисуй линию к (225,200) от предыдущей точки (которая имела координаты (75,200));
    «Z» — закрой путь (нарисуй линию к начальной точке).
-------------------
/=/ <g> - обьединяет элементы, чтобы применить к ним одни и те же атрибуты или преобразования.
---------
<g> не имеет графической видимости и сам не рисует ничего. 
Он просто организует элементы внутри себя.

    <svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
        <g fill="blue">
            <circle cx="50" cy="50" r="40" />
            <rect x="100" y="20" width="60" height="60" />
        </g>
    </svg>

-------------------
/=/ <use> - позволяет клонировать и повторно использовать графические элементы
---------

    <svg xmlns="http://www.w3.org/2000/svg" width="200" height="200">
        <circle id="myCircle" cx="50" cy="50" r="40" fill="blue" />
        
        <use href="#myCircle" x="100" y="100" />
    </svg>

-------------------
/=/ SVG CSS3-анимация
---------
SVG может быть анимирован с помощью добавления атрибута id или class SVG-тегам, и последующей стилизации их в CSS.

    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta 
                name="viewport" 
                content="width=device-width, initial-scale=1.0"
            >
            <style>
                .circle {
                    fill: #3498db;
                    transition: fill 0.3s ease;  
                }
                
                .circle:hover,
                .circle:focus {
                    fill: #e74c3c;
                }
            </style>
        </head>
        <body>
            <svg width="100" height="100">
                <circle class="circle" cx="50" cy="50" r="40"/>
            </svg>
        </body>
    </html>

---------------------------------------------------------
/=/=/=/ JPEG и PNG - разница форматов
---------------------------------------------------------
    * JPG - Фотографии и изображения с большим количеством цветов.
    Сжимает изображения с потерей качества, НО без потери в цветовой гамме.
    * PNG 24 - Иконки, схемы, картинки с большим количеством текста и изображения с прозрачностью оптимальнее сохранять в PNG 24. Сжимает изображения без потери качества, НО с потерей в цветовой гамме
    
---------------------------------------------------------
/=/=/=/ Скрытие элементов в вебе
---------------------------------------------------------
При скрытии элемента существует три разных состояния:

    - Полностью скрыт и удален из потока документа.
    - Доступен только для ридеров, но скрыт визуально
    - Скрыт для ридеров, но видим визуально
-------------------
/=/ Разница между `display: none` и `hidden`
---------
    <img 
        src="example.jpg" 
        alt="Пример изображения" 
        hidden
    >
    <img 
        src="example.jpg" 
        alt="Пример изображения" 
        style="display: none"
    >

Аттрибут hidden надежней, тк даже если css не загрузится, то 
элемент все равно будет скрыт через html.

-------------------
/=/ Методы скрытия элементов визуально и/или для ридеров
---------
    * display: none и hidden 
        - Элемент и все его потомки будут скрыты 

    * opacity: 0 
        - Элемент и все его потомки будут визуально скрыты.
        - Доступен для ридеров и Tab, скрыт визуально.

->> * visibility: hidden/visible 
        - Элемент может быть скрыт частично/полностью, его потомки могут отображаться, если `visible`.

    Когда используется `visibility: hidden` к родительскому элементу, все скрыто.
    Но когда к дочернему элементу этого родителя применен `visibility: visible`, этот дочерний элемент будет показан.

->> * aria-hidden - удаляет элемент из дерева специальных возможностей
        - Не скрывает элемент визуально, исключает ридеры

    Варианты использования aria-hidden:

        - Скрыть декоративный контент (иконки, изображения).
        - Скрыть дублированный текст.
        - Скрыть закадровый или свернутый контент.

---------------------------------------------------------
/=/=/=/ Единицы измерения 
---------------------------------------------------------
/=/=/ rem (от "root em") 
---------
Использует размер шрифта корневого элемента (обычно <html>) в качестве базового значения. 

`rem` позволяет управлять размерами для всего сайта, так как он опирается на изменение размера шрифта корневого элемента.

->> Например, если размер шрифта <html> установлен на 16 пикселей, то 1rem будет равно 16 пикселям.

-------------------
/=/=/ Относительно шрифта: em
---------
Использует размер шрифта родительского элемента в качестве базового значения.
`em` позволяет более гибко настраивать размеры шрифта для каждого элемента, исходя из размера его родителя.

-------------------
/=/=/ % - берется относительно размера шрифта родителя или свойств родительского элемента
---------
Отличие между `%` и `em` заключается в том, что `%` масштабируются относительно свойств родительского элемента, в то время как `em` масштабируется относительно размера шрифта родительского элемента.

->> Процент берётся от размера шрифта родителя:
    <div style="font-size:150%">
        Страусы
        <div style="font-size:150%">Живут в Африке</div>
    </div>
---------
->> Процент берётся относительно свойств родителя:

Если у родительского элемента задана ширина в 200 пикселей, и вы установите ширину дочернего элемента на 50%, то ширина дочернего элемента будет равна 100 пикселям (50% от 200 пикселей).

---------------------------------------------------------
/=/=/=/ Веса селекторов 
---------------------------------------------------------
Вес селекторов (по убыванию):

    - style=""     1,0,0,0
    - #id          0,1,0,0
    - .class       0,0,1,0
    - [attr=value] 0,0,1,0 — селектор по атрибуту 
    - LI           0,0,0,1 — селектор по тегу
    - *            0,0,0,0

---------
У стилей, заданных в атрибуте `style`, на первой позиции будет единица — 1,0,0,0. Это самая высокая специфичность, которая перевешивает свойства, заданные другими способами.

Переопределить стили, заданные в style, можно дописав !important к значению свойства в таблице стилей (не рекомендуется).
---------------------------------------------------------    
/=/=/ Разрешение конфликтов свойств селекторов
-------------------
    - Авторские стили приоритетнее браузерных.
    - Сравнивается специфичность и вес селектора. 
    - Побеждает то свойство, которое находится ниже в коде.
-------------------
/=/ Использование .class в селекторах
---------
Для избежания перекрытий и конфликтов необходимо обращаться по классам и не использовать в стилях селекторы с ID.
---------
Более специфичные и последние стили будут перевешивать более общие

    /* Общие стили */
    p {
        color: blue;
    }

    /* Более специфические стили */
    p.special {
        color: red;
    }
---------------------------------------------------------
/=/=/=/ Ссылки
---------------------------------------------------------
/=/ Абсолютный адрес (Absolute Address):
    - Полный путь к файлу, начиная с корневого уровня. 
    - Выстраивается независимо от текущего местоположения

    https://site.ru/blog/index.html 
---------
/=/ Относительный адрес (Relative Address):
    - Указывает местоположение данных относительно текущего контекста или местоположения.

    /blog/index.html
---------------------------------------------------------
/=/=/ Открыть PDF в браузере/скачать
-------------------
    <a href="file.pdf" download>
        Браузер скачает файл
    </a>
-------------------
/=/ Атрибут rel="noopener" - безопасность скачивания
--------- 
Атрибут rel="noopener" позволяет браузеру отключить доступ к родительскому window для дочернего нового окна или вкладки. 

Когда вы используете атрибут target="_blank" для открытия ссылки в новом окне или вкладке, браузер может предоставить доступ к `window.opener`. 
Это может создать потенциальную уязвимость безопасности, поскольку злоумышленник может использовать `window.opener` для выполнения вредоносного кода в контексте исходного окна или вкладки.

    <a 
        href="https://example.com" 
        target="_blank" 
        rel="noopener"
    >
        Ссылка
    </a>

* window.opener - это свойство объекта window в браузере, которое предоставляет доступ к родительскому окну, через дочернюю вкладку в новом окне.
---------------------------------------------------------
/=/=/ Якорные ссылки (href="#...") - прокручивают страницу к определенному элементу.
-------------------
    <a href="#section-1">Перейти к разделу 1</a>
        ...
    <h2 id="section-1">Раздел 1</h2>
    <p>Содержимое раздела 1</p>

---------
Якорные ссылки также могут использоваться с абсолютными адресами, чтобы прокрутить страницу к определенной части другой страницы.

    https://www.example.com/page#section-1

---------------------------------------------------------
/=/=/ Атрибут `title` - задает название элемента и отображает его в всплывающем Tooltip
-------------------
Атрибут title также может использоваться для добавления всплывающей подсказки, которая отображается, когда пользователь наводит курсор на элемент.
    <a  
        title="Фото в галерее закончились"
    >
        Вперёд &gt;
    </a>

---------------------------------------------------------
/=/=/ Вычисления в CSS
-------------------
    :root {
        --promo-width: calc(350px / 2);
    }
    .b-promo > div {
        width: var(--promo-width);
    }

---------------------------------------------------------
/=/=/ Наследуемые свойства
-------------------   
К наследуемым относятся в основном свойства, определяющие параметры отображения текста:
 
Font:
    - font-size
    - font-family
    - font-style
    - font-weight

Text:
    - text-align
    - text-transform
    - text-indent
    - line-height
    - letter-spacing
    - word-spacing
    - white-space
    - direction,
    - color


-------------------
/=/=/ Ненаследуемые свойства
---------   
Основные ненаследуемые свойства — это параметры позиционирования, размеров, отступов, фона, рамок:

    - background
    - border
    - padding
    - margin
    - width
    - height
    - position  

Не наследуются они из соображений здравого смысла. 
Например, если для какого-либо блока установлен внутренний отступ, автоматически выставлять такой же отступ каждому вложенному элементу нет никакой надобности. Эти параметры чаще всего уникальны для каждого отдельного блока.

-------------------
/=/=/ Сделать ненаследумое свойство CSS - наследуемым?
---------
Необходимо передать в дочерний элемент значение inherit.

    .parent {
        padding-top: 10px;
    }
    .children {
        padding-top: inherit;
    }

---------------------------------------------------------
/=/=/=/ Составные свойства CSS
CSS - (Cascading Style Sheets)
-------------------
Свойство `font-size` — обычное, оно управляет только размером шрифта. 
А свойство `font` — составное, оно задаёт сразу шесть параметров: размер и название шрифта, высоту строки и некоторые другие. 

    font: 16px/26px "Arial", sans-serif;

Браузер «расшифрует» в такой набор обычных свойств и их значений:

    font-size: 16px;                  /* было задано в font */
    line-height: 26px;                /* было задано в font */
    font-family: "Arial", sans-serif; /* было задано в font */
    font-weight: normal;              /* не было задано в font */
    font-style: normal;               /* не было задано в font */
    font-variant: normal;             /* не было задано в font */
---------
Составные свойства нужно использовать с осторожностью. 
Например, если забыть описать высоту строки:

    font: 16px "Arial", sans-serif;

То для line-height браузер возьмёт исходное значение, и внешний вид текста может оказаться плохим.

-------------------
/=/=/ Каскадирование CSS - процесс комбинирования стилей из разных источников в итоговый набор 
---------
Когда браузер отрисовывает страницу, он собирает все CSS-правила, которые относятся к каждому элементу.
После того, как все правила для элемента собраны, браузер комбинирует свойства и применяет их к элементу. 

    p { font-size: 14px; }
    .beloved-color { color: green; }

Итоговый набор свойств для абзаца:

    font-size: 14px; /* из правила для p в наших стилях */
    color: green;    /* из правила для .beloved-color в наших стилях */
    margin: 1em 0;   /* из правила для p в браузерных стилях */

-------------------
/=/=/ Написание селекторов в комбинации 
---------
Допустим, у нас есть теги <pre> и <code>.
->> Для них задаются стили:

    pre,
    code {
        background-color: #fafaff;
        border: 1px solid #c6c4f4;
        border-radius: 4px;
        color: #3632ad;
        font-family: "Courier New", "Courier", monospace;
    }

    pre code {
        background-color: transparent;
        border-radius: 0;
        border: none;
    }

    - pre, code {} выбирает и стилизует все элементы pre и code на странице.
    - pre code {} выбирает и стилизует только code элементы, которые являются потомками pre элементов.

---------------------------------------------------------
/=/=/ Селекторы CSS
-------------------
/=/ Контекстные селекторы (вложенные)
---------
Используются для вложенных друг в друга элементов

    <div class="shooter-1">
      <ul class="target">
        <li class="first">1</li>
        <li class="second">2</li>
        <li class="third">3</li>
        <li class="fourth">4</li>
        <li class="fifth">5</li>
      </ul>
    </div>

---------
    .shooter-1 .first, .third, .fourth {
        background-color: white;
    }
    .shooter-1 .second, .fifth {
        background-color: red;
    }

-------------------
/=/ Соседние селекторы
---------
Когда мы пишем .selecor1 + .selector2, то на самом деле пишем стили лишь для последнего, а первый является ориентиром который должен располагаться перед ним
---------
Контекстные селекторы используются для вложенных друг в друга элементов, а соседние — для расположенных рядом.

Например, теги <li> в списке являются соседними по отношению друг к другу и вложенными в тег <ul>.

    <ul>
        <li class="hit"></li>
        <li class="miss"></li>
    </ul>

---------
Селектор .hit + .miss применит стили к элементу с классом miss, так как перед ним есть элемент с классом hit.

Селектор .hit + li, а также селектор li + .miss, или даже li + li тоже применит стили к элементу с классом miss, то есть ко второму элементу списка.

А вот селектор .miss + .hit не сработает, так как элемент с классом miss находится после элемента с классом hit в разметке.

-------------------
/=/ Контекстные и соседние селекторы
---------
Селектор .player-1 .hit + .miss сработает для тега с классом miss, если сразу перед ним расположен тег с классом hit и оба тега расположены внутри тега с классом player-1.

-------------------
/=/ Дочерние селекторы
---------
    * Потомком называются любые элементы, расположенные внутри родительского элемента. 
    * Дочерними элементами называются ближайшие потомки. 
---------
->> Пример:
    <ul>
        <li><span>...</span></li>
        <li><span>...</span></li>
    </ul>

По отношению к списку <ul> элементы <li> являются дочерними элементами и потомками, а <span> — потомки.

Контекстные селекторы влияют на всех потомков, что не всегда удобно. Иногда необходимо задать стили только для дочерних элементов. Особенно это полезно при работе с вложенными списками.

Для этого существует селектор для обозначения дочерней связи: '>'
->> Например: 
    ul > li 
    ul > li > span

---------------------------------------------------------
/=/=/=/ Псевдоэлементы 
-------------------
Псевдоэлементы - "Псевдо" тк элемент не существует в исходном DOM, а создается и контролируется через CSS

Псевдоэлементы направлены на управление или добавление уже существующих элементов. 

    * ::before: Используется для добавления контента перед содержимым выбранного элемента.
    * ::after: Используется для добавления контента после содержимого выбранного элемента. 
    * ::first-letter: Стилизирует первую букву выбранного элемента.
    * ::first-line: Стилизирует первую строку содержимого выбранного элемента.
    * ::placeholder - применяет стили к плейсхолдеру внутри элемента формы.
    * ::marker - применяет стили к маркерам списка.

    .element::after {
        content: "Добавленный контент";
    }


---------------------------------------------------------
/=/=/=/ Псевдоклассы
-------------------
Псевдоклассы — это дополнения к обычным селекторам, которые делают их ещё точнее и мощнее. 
Обычный селектор — это снайперский прицел, а с псевдоклассом он становится прибором ночного видения.

Псевдокласс добавляется к селектору c помощью символа :, вот так селектор:псевдокласс. 

->> Например:

    a:visited { ... }
    li:last-child { ... }
    .alert:hover { ... }

-------------------
/=/=/ first-child и last-child
---------
Псевдокласс `first-child` позволяет выбрать первый дочерний элемент родителя, а `last-child `— последний дочерний элемент. 

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
 
-------------------
/=/=/ Псевдокласс :nth-child
---------
С помощью псевдокласса nth-child можно выбирать теги по порядковому номеру, не используя классы. 
---------
    селектор:nth-child(выражение). 
---------
Выражением может быть число или формула.  

    li:nth-child(2) - выберет 2й элемент
    li:nth-child(2n) — чётные элементы
    li:nth-child(n+3) - все после 3-го  
    li:nth-child(n+3):nth-child(-n+6) - диапазон от 3 до 6

-------------------
/=/=/ Динамические эффекты с помощью :hover
---------
Как с помощью CSS создаются выпадающие меню?

    li.top ul.submenu {
        display: none;
    }
    li.top:hover ul.submenu {
        display: block;
    }

Первое правило прячет список-подменю. Второе правило гласит: «если на верхний пункт меню, в котором находится подменю, наведут курсор, то надо показать подменю». Вот так всё просто.

Общий принцип такой: родительский элемент реагирует на наведение мыши и изменяет свойства элементов-потомков. То есть всё работает на контекстных селекторах вида селектор1:hover селектор2.

-------------------
/=/=/ Псевдокласс :focus
---------
Псевдокласс :focus позволяет выбрать элемент, который в данный момент в фокусе. Например, текстовое поле, на которое поставлен курсор, находится в фокусе.

В фокусе могут быть не только текстовые поля. Если вы переключаетесь между элементами веб-страницы с помощью клавиши Tab, то в фокус будут попадать ссылки.

-------------------
/=/=/ Псевдоклассы :link, :visited и :active
---------

   * :link - ещё не посещённые ссылки.    
   * :visited - посещённые ссылки.    
   * :active - активная под нажатием

    a:link { ... }
    a:visited { ... }
    a:hover { ... }
    a:active { ... }

Обратите внимание на порядок правил. Если их расположить по-другому, то некоторые могут не сработать.

-------------------
/=/=/ Селекторы атрибутов
---------
Чаще всего такие селекторы используются при работе с формами, так как поля форм имеют атрибут type с разными значениями.

    form input[checked] { ... }
    form input[type="password"] { ... }

    * Первый выберет поля формы, у которых есть атрибут `checked` 
    * Второй выберет поля формы, у которых атрибут `type="password"`

---------
Использование элемента <input> с атрибутом type="submit" вместо элемента <button> является одной из возможных практик в HTML. 
Основное различие заключается в том, что элемент <input> предназначен специально для отправки формы,

    <form class="login" action="https://echo.htmlacademy.ru/courses" method="post">
        <label for="academy-login">Логин</label>
        <input type="text" id="academy-login" name="academy-login" required>

        <label for="academy-password">Пароль</label>
        <input type="password" id="academy-password" name="password">

        <input type="submit" value="Войти">
    </form>
---------------------------------------------------------
/=/=/=/ Font
---------------------------------------------------------
    - serif — шрифт с засечками;
    - sans-serif — шрифт без засечек.
    - monospace — моноширинный шрифт;
    - cursive — шрифт с неформальным начертанием, например, имитация рукописного текста;
    - fantasy — декоративный шрифт, например Comic Sans.

-------------------
/=/=/ Использование нестандартных шрифтов (font-family)
---------
При использовании веб-шрифтов необходимо указывать «фоллбэк»-шрифты — стандартные шрифты, которые будут отображаться, если веб-шрифт недоступен. 

Для этого нужно перечислить их через запятую после нестандартного шрифта:

    font-family: "PT Sans", "Arial", sans-serif;

-------------------
/=/=/ Правило @font-face
---------
Технически подключение веб-шрифтов производится с помощью CSS-правила @font-face. Читается как «эт-правило font-face». 

->> Вот пример:

    @font-face {
        font-family: "Roboto";
        src:
            local("Roboto Regular"),
            url("roboto.woff") format("woff");
    }
---------
Получается, что можно хранить шрифты и подключать их со своего сервера. Это особенно полезно, когда шрифт очень редкий и его нет ни в одном из шрифтовых сервисов. В этом случае поступают так:

    - Берут файл шрифта (например, .ttf) и конвертируют в веб-формат в сервисе наподобие Font Squirrel (для кириллических шрифтов надо указать дополнительные параметры конвертации).
    - Затем сконвертированные файлы шрифта размещают у себя на сервере.
    И подключают шрифт с помощью @font-face.
---------------------------------------------------------
/=/=/ Выравнивание элементов и текста
-------------------
 >- align-items - вертикальное выравнивание элементов внутри только flex-контейнера. 
-------------------
 >- justify-content - горизонтальное выравнивание элементов внутри только flex-контейнера. 
-------------------
 >- text-align - горизонтальное выравнивание текста внутри блочного элемента.
-------------------
 >- float - Используется для обтекания элементов другими элементами. Для блочных элементов.

---------------------------------------------------------
/=/=/=/ Палитра Color
---------------------------------------------------------
Цвет формируется из красной, зелёной и синей составляющих.

У функции rgb есть расширенная версия — rgba. В этом случае помимо указания цвета последним значением указывается степень непрозрачности цвета — alpha.

    color: rgba(0, 0, 0, 0.5)      /* чёрный, непрозрачный на 50% */
    color: rgba(255, 0, 0, 0.3)     /* красный, непрозрачный на 30% */
    color: rgba(255, 255, 255, 0.9) /* белый, непрозрачный на 90% */

---------------------------------------------------------
/=/=/=/ Управление пробелами. white-space
---------------------------------------------------------
    >- nowrap — схлопывает лишние пробелы и отображает весь текст одной строкой без переносов;
    >- pre — сохраняет пробелы и переносы как в исходном коде аналогично тегу <pre>;
    >- pre-wrap — работает как значение pre, но добавляет автоматические переносы, если текст не помещается в контейнер;
    >- normal — режим по умолчанию: лишние пробелы и переносы строк схлопываются, текст переносится, пробелы в конце строк удаляются.
---------------------------------------------------------
/=/=/=/ Свойства текста 
---------------------------------------------------------
 >- text-decoration
---------
Свойство text-decoration — составное. Оно раскладывается на отдельные свойства:

    * text-decoration-line — вид линии: 
        - underline — подчёркивание;
        - line-through — зачёркивание;
        - overline — надчёркивание;
        - none — убирает вышеперечисленные эффекты.

    * text-decoration-style — стиль линии, может принимать значения:
        - solid — сплошная линия;
        - double — двойная линия;
        - dotted — точечная линия;
        - dashed — пунктирная линия;
        - wavy — волнистая линия.

    * text-decoration-color — цвет линии.
-------------------
 >- text-transform
---------
    - lowercase — все строчные;
    - uppercase — все заглавные;
->> - capitalize — каждое слово начинается с большой буквы;
    - none — отменяет изменение регистра.
-------------------
 >- font-style
---------
    - normal — обычное начертание;
    - italic — курсивное начертание;
    - oblique — наклонное начертание.

---------------------------------------------------------
/=/=/=/ Тег time (Помогает SEO и Ридерам)
-------------------
В HTML есть специальный тег для обозначения даты и времени — <time>. С помощью <time> можно описывать даты одновременно и для человека, и для машины, например:

    <div>
        <time datetime="2014-04-20">Вчера</time> мы готовили тренажёр к публикации.
    </div>

---------------------------------------------------------
/=/=/=/ Тег video/audio
-------------------
Для вставки видео предназначен специальный парный тег <video>. 

Его основные атрибуты:
    * width - и height	задают ширину и высоту видео
    * controls - пустой атрибут, при наличии которого отображается панель управления видео
    * preload - задаёт режим предзагрузки видео, имеет 3 возможных значения:
     
        - none — не загружать ничего;
        - metadata — загрузить служебную мета-информацию (длительность, первый кадр и так далее);
        - auto — можно загрузить всё видео.

        (значение по умолчанию зависит от браузера)

    * src - задаёт адрес видеофайла
    * autoplay - пустой атрибут, при наличии которого воспроизведение видео начинается автоматически
    * poster - задаёт адрес картинки-обложки, которая отображается, когда видео ещё не загрузилось или не воспроизводится

-------------------
/=/=/ Форматы и источники видео <source src="">
---------
В текущий момент существует несколько форматов видео, каждый из которых хорошо поддерживается лишь некоторыми браузерами. Вот три самых распространённых формата и их поддержка:

    MPEG-4/H.264
    OGG/Theora
    WebM

Поэтому мы должны в видео указывать адреса файлов во всех этих форматах (и конвертировать исходное видео в эти форматы, конечно). Делается это с помощью тегов <source>:

    <video controls>
        <source src="video.mp4" type="video/mp4">
        <source src="video.ogv" type="video/ogg">
        <source src="video.webm" type="video/webm">
    </video>

В атрибуте `src` указывается адрес видеофайла, а в атрибуте `type` его тип (также там могут указываться и кодеки). 
Браузер из списка видеофайлов выбирает первый, который может проиграть и загружает его.

Атрибут type не является обязательным, так как браузер умеет сам определять тип и кодеки, но указывая тип явно, мы помогаем ему не ошибиться.

-------------------
/=/=/ Форматы и источники звука
---------
Для охвата большинства современных браузеров, достаточно использовать всего два формата:

    MP3
    OGG

 Мы должны так же, как и в случае с видео, перечислить адреса звуковых файлов в разных форматах с помощью тегов <source>:

    <audio controls>
        <source src="sound.mp3" type="audio/mpeg">
        <source src="sound.oga" type="audio/ogg">
    </audio>

---------------------------------------------------------
/=/=/=/ Управление потоком документа
-------------------
Поток — это порядок отображения элементов на странице. 

    * Блочные элементы растягиваются на всю доступную ширину родителя. (Может принимать width/height)
    * Строчные элементы занимают лишь необходимую область и при необходимости переносятся на новую строку. 
    (Не изменяются под width/height)

---------
Существует несколько способов управлять потоком и строить сетки:

    * флоаты;
    * инлайн-блоки;
    * табличная вёрстка;
    * флексбоксы.

---------------------------------------------------------
/=/=/ float - свойство, включающее режим обтекания
-------------------
Флоатные элементы становятся невидимыми для блочных элементов и видимыми для текста. 
---------
Изначально float было предназначено для того, чтобы включать обтекание элементов текстом. 
Но, как часто бывает, судьба уготовила ему совсем другую роль.

Свойство float имеет следующие значения:

    * left — прижимает элемент к левому краю родителя, другие элементы обтекают его справа;
    * right — прижимает элемент к правому краю родителя, другие элементы обтекают его слева;
    * none — отключает режим обтекания и возвращает элементу нормальное поведение.

    * Зафлоатить элемент по центру нельзя.

-------------------
/=/ Тонкости float
---------
Для того, чтобы флоатный блок мог обтекаться обычным, он должен в коде располагаться Выше обычного.

-------------------
/=/ float и ширина
---------
Если мы задаём элементу свойство float:left или float:right, то он прижимается к краю, а также начинает ужиматься по ширине под своё содержимое. С той стороны, которая не прижата к краю родителя, появляется свободное место. Это место может быть занято другими элементами.

Зафлоаченному элементу можно явно задавать размеры и отступы.

Есть тонкость, связанная со строчными элементами. 
Если зафлоатить строчный элемент, то он начинает вести себя как блочный, а именно: воспринимать размеры и отступы.

-------------------
/=/ float и выпадание из потока
---------
Зафлоаченные элементы выпадают из потока, но лишь частично:

    * Блочные элементы, которые идут в коде после зафлоаченного блока, перестают его замечать. Они подтягиваются вверх и занимают его место, как будто его и нет.
    * Строчные же элементы, расположенные в коде после зафлоаченного блока, начинают обтекать его со свободной стороны.

Ещё раз: для блочных элементов float не существуют, но текст внутри блоков float обтекает.
---------
Такое поведение флоатов даёт интересные эффекты:

    * Эффект прохождения сквозь блоки. 
      Проявляется, когда зафлоаченный элемент выше, чем несколько последующих за ним блоков.
    * Эффект выпадания из родителя или схлопывания родителя.    
      Проявляется тогда, когда все дочерние блоки в родителе зафлоачены. В этом случае родитель схлопывается по высоте, как будто в нём нет содержимого, а блоки выпадают из него.

---------------------------------------------------------
/=/=/ Взаимодействие float'ных элементов между собой
-------------------
Флоатные элементы становятся невидимыми для блочных элементов и видимыми для текста. 
Но флоатные элементы видят друг друга.

Идущие друг за другом флоаты выстраиваются в ряд, пока им хватает свободного места. Если места не хватает, то они начинают переноситься на следующую строчку. Почти как текст.

-------------------
/=/ Когда флоатов много, а места мало
---------
Следует отметить, что поведение нескольких флоатов, когда им не хватает места в одной строке, является очень странным.

Когда не влезающий флоат переносится на новую строку, возможно несколько вариантов и не все из них логичны. 
Например, флоат может «зацепиться» за один из предшествующих флоатов и встать ниже не в самом начале строки, а за предшествующим.

-------------------
/=/=/ Распорки - Борьба с выпаданием флоатов (устарело)
---------

    .clearfix {
        height: 0px;
        clear: both;
    }

    <div class="container"> - блок-контейнер
        <div class="column1">...</div> - колонка, флоат
        <div class="column2">...</div> - колонка, флоат
        <div class="clearfix"></div> - распорка с clear:both
    </div>


 Стали добавлять пустой элемент-распорку с использованием свойства `clear:both` после зафлоаченных колонок. 
 Этот элемент видит колонки, блокирует их прохождение и при этом растягивает родительский блок по высоте.  

Для таких распорок прижилось специальное название класса — clearfix.

-------------------
/=/=/ Псевдораспорки
---------

    .clearfix::after {
      content: "";
      display: table;
      clear: both;
    }

А затем класс clearfix добавляется к контейнеру, внутри которого лежат флоатные колонки. После этого в контейнер не нужно добавлять дополнительный элемент-распорку, так как распорка создаётся с помощью псевдоэлемента.

-------------------
/=/=/ after/before / first-line/first-letter
---------

    * ::before: Используется для добавления контента перед содержимым выбранного элемента.
    * ::after: Используется для добавления контента после содержимого выбранного элемента. 
    * ::first-letter: Стилизирует первую букву выбранного элемента.
    * ::first-line: Стилизирует первую строку содержимого выбранного элемента.

    .element::after {
        content: "Добавленный контент";
    }

В этом примере после элемента с классом element будет добавлен текст "Добавленный контент".

---------------------------------------------------------
/=/=/ clear - запрещает обтекание элемента другими элементами. 
-------------------
    * left — запрещено обтекание слева;
    * right — запрещено обтекание справа;
    * both — запрещено обтекание с обеих сторон;
    * none — обтекание разрешено.

Если после флоатного элемента расположен элемент с запрещённым обтеканием, то последний опускается под флоатный.

Свойство clear учит блочные элементы «видеть» зафлоаченные.



---------------------------------------------------------
/=/=/ inline-block - блочно-строчные элементы
-------------------
Блочно-строчные элементы ведут себя двояко. Снаружи они выглядят как обычные строчные, но внутри они ведут себя как блочные.

От строчных им достались следующие черты:
    - по ширине они ужимаются под своё содержимое;
    - могут располагаться в одну строку;
    - реагируют на вертикальное выравнивание, vertical-align;
    - реагируют на горизонтальное выравнивание, text-align, заданное у родителя.

От блочных:
    - им можно задавать размеры с помощью width и height;
    - а также внешние и внутренние отступы и рамки, которые работают во всех направлениях и увеличивают размер элемента.

-------------------
/=/ Тонкости inline-block и пробелы в коде
---------
Мы рассчитали всё правильно, однако по три товара в строку не помещается.

Причина заключается в пробелах после тегов в HTML-коде. 
Блочно-строчные ведут себя как текст, поэтому если в коде есть пробел между элементами, то он отображается и на странице. Этот пробел увеличивает отступы между товарами, не давая им поместиться в одну строку.
---------
Бороться с пробелом после блочно-строчных можно несколькими способами:
    - удалять пробелы в коде;
    - обнулять размер шрифта;
    - играться с маргинами после блочно-строчного.

Мы попробуем последние два способа.
-------------------
/=/ Способ со Шрифтом
---------
    <div class="container">
      <h1>Каталог в три колонки</h1>
      <div class="catalog">
        <div class="item">Товар</div>
        <div class="item">Товар</div>
        <div class="item">Товар</div>
        <div class="item">Товар</div>
        <div class="item">Товар</div>
        <div class="item">Товар</div>
        <div class="item">Товар</div>
        <div class="item">Товар</div>
      </div>
    </div>

    .catalog {
        font-size: 0;
        vertical-align: top;
        width: 400px;
        background-color: #ecf0f1;
        box-shadow: 0 0 3px #999999;
    }

    .item {
        font-size: initial;
        margin-right: 20px;
        display: inline-block;
        width: 116px;
        min-height: 75px;
        margin-bottom: 20px;
        text-align: center;
        color: white;
        background-color: #3498db;
        border: 2px solid #2c3e50;
    }
    .item:nth-child(3n) {
        margin-right: 0;
    }

Способ со шрифтом заключается в том, что мы задаём нулевой размер шрифта у контейнера инлайн-блоков, а самим инлайн-блокам задаём исходный размер шрифта. Способ не работает, если вы используете относительные размеры шрифта.

-------------------
/=/ Способ с margin
---------
Способ с маргинами заключается в том, что мы уменьшаем (подгоняем) отступ после инлайн-блока на ширину пробела, около 4-5px. 
А если нам нужно, чтобы элементы стояли вплотную друг к другу, то задаём отрицательный отступ. 
Проблема с этим способом заключается в том, что размер пробела может быть разным в разных шрифтах и может изменяться при изменении размера шрифта.
-------------------
/=/=/ Сетка — это взаимное расположение крупных блоков сайта. 
---------

---------------------------------------------------------
/=/=/=/ БЭМ (Блок, Элемент, Модификатор) 
---------------------------------------------------------
БЭМ - Компонентный подход к веб-разработке. 
В его основе лежит принцип разделения интерфейса на независимые блоки. Он позволяет легко и быстро разрабатывать интерфейсы любой сложности и повторно использовать существующий код, избегая «Copy-Paste».

БЭМ-сущность - собирательное для блоков, элементов и модификаторов. 
---------------------------------------------------------
/=/=/ Блок - Функционально независимый компонент страницы
-------------------
/=/ Особенности:
---------
    * Название блока характеризует смысл 
      - «Что это?» — «меню»: menu, «кнопка»: button.

    * Блок не должен влиять на свое окружение.
      - Блоку не следует задавать внешнюю геометрию (в виде отступов, границ, влияющих на размеры) и позиционирование. 
      Это позволит свободно переносить переиспользуемый элемент в любое окружение.

    * В CSS рекомендуется использовать .class, и не использовать селекторы по тегам или id

---------
    <!-- Верно. Семантически осмысленный блок `error` -->
    <div class="error">Error #404</div>
    <!-- Неверно. Описывается внешний вид -->
    <div class="red-text">Error #404</div>

-------------------
/=/ Вложенность:
---------
    * Блоки можно вкладывать друг в друга.
    * Блок может быть без элементов

---------------------------------------------------------
/=/=/ Элемент - Составная часть блока
-------------------
Элемент не может использоваться отдельно от блока.

-------------------
/=/ Особенности:
---------
    * Название блока характеризует смысл («что это?» — «меню»: menu, «кнопка»: button).
    * Структура полного имени элемента соответствует схеме: имя-блока__имя-элемента. 
    Имя элемента отделяется от имени блока двумя подчеркиваниями (__).

---------
    <!-- Блок `search-form` -->
    <form class="search-form">
        <!-- Элемент `input` блока `search-form` -->
        <input class="search-form__input">

        <!-- Элемент `button` блока `search-form` -->
        <button class="search-form__button">Найти</button>
    </form>
    
-------------------
/=/ Вложенность:
---------
    * Элементы можно вкладывать друг в друга.
    * Элемент — всегда часть блока, а не другого элемента. Это означает, что в названии элементов нельзя прописывать

---------------------------------------------------------
/=/=/ Принципы работы с элементами
-------------------
/=/ Вложенность
---------
    * В названии элементов нельзя прописывать иерархию вида block__elem1__elem2. Элемент — всегда часть блока.

    <form class="search-form">
        <div class="search-form__content">
            <input class="search-form__input">
            <button class="search-form__button">Найти</button>
        </div>
    </form>
-------------------
/=/ Принадлежность
---------
    * Элемент — всегда часть блока и не должен использоваться отдельно от него.
-------------------
/=/ Необязательность
---------
    * Элемент — необязательный компонент блока. Не у всех блоков должны быть элементы.

    <!-- Блок `search-form` -->
    <div class="search-form">
        <!-- Блок `input` -->
        <input class="input">

        <!-- Блок `button` -->
        <button class="button">Найти</button>
    </div>

---------------------------------------------------------
/=/=/ Блок или Элемент?
-------------------
    * Создавайте блок
      - Если фрагмент кода может использоваться повторно и не зависит от реализации других компонентов страницы. (Переиспользуемый)

    * Создавайте элемент
      - Если фрагмент кода не может использоваться самостоятельно, без родительской сущности. (Спецефический UI)

---------------------------------------------------------
/=/=/ Модификатор - Определяет внешний вид, состояние или поведение блока либо элемента.
-------------------    
/=/ Особенности:
---------
    * Название модификатора характеризует 
      - Внешний вид: «какой размер?», «какая тема?» — «размер»: size_s, «тема»: theme_islands
      - Состояние: «чем отличается от прочих?» — «отключен»: disabled, «фокусированный»: focused 
      - Поведение: «как ведет себя?», «как взаимодействует с пользователем?» — «направление»: directions_left-top.

    * Имя модификатора отделяется от имени блока или элемента одним подчеркиванием (_).
      - имя-блока_модификатор 
      - имя-блока__имя-элемента_модификатор

-------------------
/=/ Типы модификаторов
---------
    * Булевый
      Например, «отключен»: disabled. 
      Считается, что при наличии булевого модификатора у сущности его значение равно true.

    * Структура полного имени модификатора соответствует схеме:
      - имя-блока_имя-модификатора;
      - имя-блока__имя-элемента_имя-модификатора.
    ==/OR Стиль Two Dashes/==
      - block-name__elem-name--mod-name--mod-val

---------
    <!-- Блок `search-form` имеет булевый модификатор `focused` -->
    <form class="search-form search-form_focused">
        <input class="search-form__input">

        <!-- Элемент `button` имеет булевый модификатор `disabled` -->
        <button class="search-form__button search-form__button_disabled">Найти</button>
    </form>

-------------------
/=/ Ключ-значение в Модификаторах
---------
Используют, когда важно значение модификатора. 
Например, «меню с темой оформления islands»: menu_theme_islands.

    Структура полного имени модификатора соответствует схеме:
      - имя-блока_имя-модификатора_значение-модификатора;
      - имя-блока__имя-элемента_имя-модификатора_значение-модификатора.
    ==/OR Стиль Two Dashes/==
      - block-name__elem-name--mod-name--mod-val
    
---------
    <!-- Блок `search-form` имеет модификатор `theme` со значением `islands` -->
    <form class="search-form search-form_theme_islands">
        <input class="search-form__input">

        <!-- Элемент `button` имеет модификатор `size` со значением `m` -->
        <button class="search-form__button search-form__button_size_m">Найти</button>
    </form>

---------------------------------------------------------
/=/=/ Принципы работы с модификаторами
-------------------
/=/ Модификатор нельзя использовать самостоятельно
---------
С точки зрения БЭМ-методологии модификатор не может использоваться в отрыве от модифицируемого блока или элемента. Модификатор должен изменять вид, поведение или состояние сущности, а не заменять ее.

---------
    <!-- Верно. Блок `search-form` имеет модификатор `theme` со значением `islands`-->
    <form class="search-form search-form_theme_islands">
        <input class="search-form__input">

        <button class="search-form__button">Найти</button>
    </form>
---------
    <!-- Неверно. Отсутствует модифицируемый класс `search-form` -->
    <form class="search-form_theme_islands">
        <input class="search-form__input">

        <button class="search-form__button">Найти</button>
    </form>

---------------------------------------------------------
/=/=/ Микс - обьединение 2х и более CSS селекторов в одном блоке.
-------------------
    * Миксы позволяют:
      - Совмещать стили нескольких элементов без дублирования кода;  
      - Создавать новые компоненты интерфейса на основе имеющихся.


    <div class="about">
        <div class="title about__title">
            //...
        </div>

        <div class="subtitle about__subtitle">
            //...
        </div>
    </div>

    * About - родительский Блок
    * Title и Subtitle - отдельные Блоки, которые вложены в Блок `About`
    * К Блокам `Title, Subtitle` добавлены кастомные стили Элементов `about__title, about__subtitle` из Блока `About`

---------
    Таким образом, блок можно использовать в любом другом окружении.
    
    Данный подход позволяет задавать ситуативное позиционирование Блоков `Title, Subtitle` в родительском Блоке `About`.

    Это происходит через передачу Блокам классов Элементов которые относятся к Блоку `About`.

    Тем самым происходит некое представление Блоков `Title, Subtitle` как дочерних Элементов `About`.  

    Это позволяет все так же сохранить переиспользуемость Блоков `Title, Subtitle`
    И одновременно смочь адаптировать их в нужный контекст, без потери их универсальности

-------------------
/=/ Запись стилей для кода
---------
    <div class="about">
        <div class="title about__title">
            //...
        </div>

        <div class="subtitle about__subtitle">
            //...
        </div>
    </div>  

---------
->> CSS
---------
    .about {
    /* стили для блока .about */
    }
    .about__title {
    /* стили для элемента .about__title */
    }
    .about__subtitle {
    /* стили для элемента .about__subtitle */
    }

    .title {
        /* стили для блока .title внутри .about */
    }

    .subtitle {
        /* стили для блока .subtitle внутри .about */
    }

---------
->> SCSS
---------
    .about {
        &__title {
            /* стили для элемента .about__title */
        }
        &__subtitle {
            /* стили для элемента .about__subtitle */
        }
    }

    .title {
        /* стили для блока .title внутри .about */
    }

    .subtitle {
        /* стили для блока .subtitle внутри .about */
    }

---------------------------------------------------------
/=/=/ Файловая структура БЭМ - компонентный подход в организации проектов в файловой структуре. 
-------------------
    * Особенности:
    >- Один блок — одна директория.

    >- Имена блока и его директории совпадают. Например, блок header — директория header/, блок menu — директория menu/.

    >- Реализация блока разделяется на отдельные файлы-технологии. Например, header.css, header.js.

    >- Директория блока является корневой для поддиректорий соответствующих ему элементов и модификаторов.

    >- Имена директорий элементов начинаются с двойного подчеркивания (__). Например, header/__logo/, menu/__item/.

    >- Имена директорий модификаторов начинаются с одинарного подчеркивания (_). Например, header/_fixed/, menu/_theme_islands/.

    >- Реализации элементов и модификаторов разделяются на отдельные файлы-технологии. Например, header__input.js, header_theme_islands.css.

---------
->> Пример структуры файлов:

search-form/                           # Директория блока search-form

    __input/                           # Поддиректория элемента 
        search-form__input.css         # Реализация элемента 
                                       # search-form__input в CSS
        search-form__input.js          # Реализация элемента в JS

    __button/                          # Поддиректория элемента search-form__button
        search-form__button.css
        search-form__button.js

    _theme/                            # Поддиректория модификатора
                                       # search-form_theme
        search-form_theme_islands.css  # Реализация блока search-form, 
                                       # имеющего модификатор theme со значением islands
        search-form_theme_lite.css     # Реализация блока search-form, 
                                       # имеющего модификатор theme со значением lite

    search-form.css                    # Реализация блока search-form
                                       # в технологии CSS
    search-form.js                     # Реализация блока search-form
                                       # в технологии JavaScript

Можно использовать любую альтернативную структуру проекта, соответствующую принципам организации файловой структуры БЭМ, например:
    * Flat    * Flex

---------------------------------------------------------    
/=/=/ Пишем плоскую структуру классов без вложенности и каскадов для стилей CSS
-------------------
/=/ Создавать новые родительские блоки. Бить на блоки
---------
    ==/YES/==
    <div class="block">
        <div class="block2">
            <div class="block2__elem2"></div>
        </div>
    </div>

    ==/NO/==
    <div class="block">
        <div class="block__elem1">
            <div class="block__elem1__elem2"></div>
        </div>
    </div>
---------
->> Вложенные элементы одного уровня:

    <div class="block">
        <div class="block2">
            <div class="block2__elem2"></div>
        </div>
    </div>
    <div class="block3_elem3"></div>

Нет каскада:
    .block {}    
    .block__elem1 {}    
    .block__elem2 {}    
    .block__elem3 {}    

Каскады в БЭМ разрешены. Просто это должно быть разумно.

---------------------------------------------------------    
/=/=/ Как добавить модификатор к блоку или элементу
-------------------
Для блоков:
    <div class="block3_elem3_key_value"></div>
---------
Для элементов:
    Делать каскад от модификатора:

    <div 
        class="block3_elem3_key_value block3_elem3_key_value--modifier"
    >
        // ...
    </div>

    .block3_elem3_key_value--modifier {
        background-color: blue;
        color: white;
    }


---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

---------------------------------------------------------

