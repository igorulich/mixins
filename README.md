# mixins
приклад деяких корисних міксинів
#Вкладені правила:
ви можете вкладати CSS властивості в кілька наборів дужок {}. Це зробить ваш CSS чистішим і зрозумілішим.
# Змінні:
у стандартному CSS теж є змінні, але змінні Sass куди потужніший інструмент.
Наприклад, можна використовувати змінні в циклах і генерувати значення властивостей динамічно.
Також можна впроваджувати змінні в імена властивостей, наприклад: property-name-N { … }.

#Найкраща реалізація операторів:
ви можете підсумовувати, віднімати, ділити та множити CSS значення. Sass реалізація інтуїтивніша, ніж стандартний функціонал CSS calc().
Функції: Sass дозволяє багаторазово використовувати CSS стилі як функції.

#Тригонометрія:
крім базових операцій (+, -, *, /), SCSS дозволяє писати власні функції. Наприклад, функції sin та cos можна написати,
використовуючи лише синтаксис Sass/SCSS.
Звичайно, вам знадобляться знання тригонометрії. Такі функції можуть знадобитися для створення анімації.
Зручний робочий процес: ви можете писати CSS, використовуючи конструкції, знайомі з інших мов: for-цикли, while-цикли, if-else.
Але майте на увазі, це лише препроцесор, а не повноцінна мова, Sass контролює генерацію властивостей та значень, а на виході ви отримуєте стандартний CSS.
Міксини: дозволяють один раз створити набір правил, щоб потім їх багаторазово або змішувати з іншими правилами.
Наприклад, міксини використовують для створення окремих тем макету.
# Змінні
У Sass/SCSS є змінні, і вони відрізняються від тих, які ви, ймовірно, бачили в CSS — вони починаються з двох тире (--color: #9c27b0).
У SCSS змінна позначається знаком долара ($ color: # 9c27b0).
Ви можете перезаписати ім'я або змінити значення за промовчанням.
Для цього додайте мітку !default до змінної, і якщо її значення не зміниться надалі і не буде порожнім, то використовуватиметься задане значення за промовчанням.
````
$number: 1;
$color: #ff0000;
$text: "tproger forever.";
$text: "IT forever." !default;
$nothing: null;
```
Ви можете перезаписати ім'я або змінити значення за промовчанням. Для цього додайте мітку !default до змінної,
і якщо її значення не зміниться надалі і не буде порожнім, то використовуватиметься задане значення за промовчанням.
#Вложенные правила:
Стандартні вкладені CSS-елементи з використанням пробілу:
/* Вкладені правила */
```
#A {
  color: red;
  #B {
    color: green;
    #C p {
      color: blue;
    }
  }
}
```
#Амперсанд
У SCSS використовується директива &.
```
#p {
  color: black;
  a {
    font-weight: bold;
    &:hover {
      color: red;
    }
  }
}
```
За допомогою символу & можна явно вказати, де має бути вставлений батьківський селектор.
Міксини (вони ж домішки)
Міксини оголошуються директивою @mixin. Після неї має стояти ім'я міксину та, опціонально, його параметри, а також блок, що містить тіло міксину.
Наприклад, можна визначити міксин flexible(), який далі буде включений, наприклад, клас .centered-elements наступним чином:
````
@mixin flexible () {
    display: flex;
    justify-content: center;
    align-items: center;
  }
  ```
  ```
.centered-elements {
    @include flexible ();
    border: 1px solid gray;
  }
  ```
  Тепер щоразу після застосування класу .centered-elements до HTML-елементу, останній буде перетворено на Flexbox.

#Міксини:
можуть також містити селектори, зокрема з властивостями. А селектори можуть містити посилання на батьківський елемент через амперсанд (&), адже ви пам'ятаєте про нього?
Приклад роботи з кількома браузерами
Деякі речі в CSS дуже стомлюючи писати, особливо в CSS3, де плюс до всього часто потрібно використовувати велику кількість вендорних префіксів (-webkit-або-moz-).

Міксини дозволяють створювати групи декларацій CSS, які доведеться використовувати кілька разів на сайті.
Хорошою практикою буде використання міксину для вендорних префіксів.

##Приклад:
```
@mixin border-radius($radius) {        //Префікси для:
    -webkit-border-radius: $radius;    // Chrome и Safari
       -moz-border-radius: $radius;    // Firefox
        -ms-border-radius: $radius;    // Internet Explorer
         -o-border-radius: $radius;    // Opera
            border-radius: $radius;    // Стандартный CSS
  }
  ```
//Приклад використання міксину border-radius після його створення
.box { @include border-radius(10px); }

#Арифметичні операції
Як і реальному житті, ви можете працювати з числами, які мають несумісні типи даних (наприклад, складання рх і em).

# Сложение и вычитание
p {
    font-size: 10px + 2em;  // ОШИБКА!
    font-size: 10px + 6px;  // 16px
    font-size: 10px + 2;    // 12px
}
Завжди звертайте увагу на тип даних, що складаються. Тобто пікселі до пікселів, слони до слонів. Так само працює віднімання, але зі знаком мінус.
#Приклад віднімання:
div {
    height: 12% - 2%;
    margin: 4rem - 1;
}
Розмноження
Виконується так само, як у CSS, за допомогою calc(a * b), але без calc і круглих дужок. Крім того, можна ще відокремлювати знак множення пробілами від чисел (5 * 6 = = 5 * 6).

Виняток Не можна множити пікселі між собою. Тобто, 10px * 10px! = 100px. 10px * 10 == 100px.
# Приклад множення:
p {
    width: 10px * 10px;           //ПОМИЛКА!
    width: 10px * 10;             // 100px
    width: 1px * 5 + 5px;         // 10px
    width: 5 * (5px + 5px);       // 50px
    width: 5px + (10px / 2) * 3;  // 20px
}
#Поділ
З розподілом справи трохи складніше, але розібратися можна, адже в стандартному CSS коса лінія (слеш) зарезервована для використання короткої форми запису властивостей.



/* стандартна форма запису властивостей */
font-style: italic;
font-weight: bold;
font-size: .8em;
line-height: 1.2;
font-family: Arial, sans-serif;
Є три помічники, які натякнуть на можливість поділу:
Значення (або будь-яка його частина) зберігається у змінній чи повертається функцією.
Значення укладені у круглі дужки.
Значення використовується як частина іншого арифметичного виразу.
Приклад:
$var1: 20;
$var2: 4;

p {
    top: 16px / 24px;          // Відображається без змін у стандартному CSS
     top: (20px/5px); // Виробляється розподіл (але тільки при використанні дужок)
     top: #{$var1} / #{$var2}; // Виводиться як звичайний CSS-код, розподіл не виконується
     top: $var1/$var2; // Розподіл виконується
     top: random(4)/5; // Розподіл виконується (якщо використовувати у парі з функцією)
     top: 2px/4px + 3px; // Розподіл виконується, якщо додано ще одну арифметичну дію
}
        #Директива @if
приймає вираз SassScript і використовує вкладені у ній стилі у разі, якщо вираз повертає будь-яке значення, крім false чи null.

Нижче показано, як працюють директиви @if та @else, вкладені в міксин.
@mixin spacing($padding, $margin) {
    @if ($padding > $margin) {
        padding: $padding;
    } @else {
        padding: $margin;
    }
}

.container {
    @include spacing(10px, 20px);
}
Порівняння у дії. Міксин spacing вибере розміри padding'а, якщо той буде більшим, ніж margin.
.container { padding: 20px; }
Використання логічних операторів Sass для створення кнопки, яка буде змінюватися фон залежно від її ширини.
@mixin button-color ($height, $width) {
    @if (($height < $width) and ($width >= 35px)) {
        background-color: blue;    
    } @else {
        background-color: green;
    }
}

.button {
    @include button-color(20px, 30px)
}
#Рядки
У CSS визначено 2 типи рядків: з лапками та без. Sass розпізнає і те, й інше. В результаті ви отримаєте в CSS той тип рядків, який використовували Sass.

У деяких випадках можна додати рядки в допустимі значення CSS без лапок, але якщо доданий рядок є завершальним елементом.
p {
    font: 50px Ari + "al"; // Компилируется в 50px Arial
}
#Оператори керування потоками
У SCSS є функції (function()) та директиви (@directive). Трохи вище ми розглядали приклад функції, коли вивчали передачу аргументів усередині міксинів.

Функції зазвичай полягають у дужки, що йдуть відразу за її ім'ям. А директива починається із символу @.

Подібно до JavaScript, SCSS дозволяє працювати зі стандартним набором операторів управління потоками.
if()
if() — це функція (і іноді основа штучного інтелекту).

Її використання виглядає досить примітивним: оператор поверне одне із двох позначених за умови значень.
/* Використання функції if() */
if (true, 1px, 2px) => 1px;
if (false, 1px, 2px) => 2px;
@if
@if —це директива, що використовується для розгалуження на основі умов.

/* Використання директиви @if */
p {
    @if 1 + 1 == 2 { border: 1px solid;  }
    @if 7 < 5      { border: 2px dotted; }
    @if null       { border: 3px double;  }
}
Нижче показано розгалуження комбо з додаванням директиви @else.
/* Створення змінної $type */
$type: river;

/* Фарбування контейнерів у синій у разі, якщо значення для змінної $type - river */
div {
    @if $type == river {
        color: blue;
    }
}

/* Условные цвета для текста в теге <p> */
p {
    @if $type == tree {
        color: green;
    } @else if $type == river {
        color: blue;
    } @else if $type == dirt {
        color: brown;
    }
}

#Перевірка на наявність батьківського елемента
Амперсанд вибирає батьківський елемент, якщо існує. В іншому випадку поверне null. Тому може використовуватися разом із директивою @if.

У наведених прикладах розглянемо створення умовних CSS-стилів залежно від наявності батьківського елемента.

/* Перевірка на наявність батьківського елемента */
@mixin does-parent-exist {
    @if & {
        /* Застосування блакитного кольору батьківському елементу, якщо він існує */
        &:hover {
            color: blue;
        }
    } @else {
        /* Батьківський елемент відсутній, застосування блакитного кольору до посилань */
        a {
            color: blue;
        }
    }
}
#Директива @for
Директива @for виводить набір стилів задану кількість разів. Для кожного повторення використовується змінна-лічильник зміни виведення.

Директива @for ітерується 5 разів.

@for $i from 1 through 5 {
     .definition-#{$i} { width: 10px * $i; }
}
Результат компіляції CSS:
.definition-1 { width: 10px; }
.definition-2 { width: 20px; }
.definition-3 { width: 30px; }
.definition-4 { width: 40px; }
.definition-5 { width: 50px; }
# Директива @each
Директива @each встановлює $var у кожне зі значень списку або словника і виводить стилі, що містяться в ній, використовуючи відповідне значення $var.

@each $animal in platypus, lion, sheep, dove {
     .#{$animal}-icon {
         background-image: url("/images/#{$animal}.png")
     }
}
# Директива @while
Директива @while приймає вираз SassScript і циклічно виводить вкладені у ній стилі, поки вираз обчислюється як true. Вона може бути використана для створення більш складних циклів, ніж таких, для яких підходить @for, хоча вона необхідна досить рідко. Наприклад:
$index: 5;
@while $index > 0 {
    .element-#{$index} { width: 10px * $index; }
    $index: $index - 1;
}
# Функції у Sass/SCSS
Використовуючи Sass/SCSS, можна використовувати функції так само, як і в інших мовах.

Створимо функцію three-hundred-px(), що повертає 300px.
@function three-hundred-px() {
    @return 300px;
}

.name {
    width: three-hundred-px();
    border: 1px solid gray;
    display: block;
    position: absolute;
}

Функції Sass можуть повертати будь-яке коректне значення CSS і можуть бути призначені будь-якій властивості. Вони можуть бути розраховані з урахуванням переданого аргументу.
@function double($width) {
    @return $width * 2;
}
