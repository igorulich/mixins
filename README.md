
# ***@mixin*** і ***@include***
**Міксини***дозволяють визначати стилі, які можна повторно використовувати у вашій таблиці стилів. Вони дозволяють легко уникнути використання несемантичних класів, таких як **.float-left**, і поширювати колекції стилів у бібліотеках.*
*Ім’я міксину може бути будь-яким ідентифікатором Scss,Sass, і воно може містити будь -який оператор , крім операторів верхнього рівня . Їх можна використовувати для інкапсуляції стилів, які можна вставити в одне правило стилю ; вони можуть містити власні правила стилю, які можуть бути вкладені в інші правила або включені на верхній рівень таблиці стилів; або вони можуть просто служити для зміни змінних.*

*Міксини визначаються за допомогою **@mixinправила** at, яке записується:*
+ @mixin <name> { ... }
  ### Приклади:
---
<pre>
 @mixin btnreset() {
  background-color: transparent;
  border: none;
  cursor: pointer;
  button,
  button:active,
  button:focus {
    outline: none;
  }
} 
  </pre> 
  <span>@include **btnreset**();</span>
  
   ###### *або*
  Аргументи **Sass,Scss** - Mixin
**@mixin name(<arguments...>) { ... }** ,
 *Значення **SassScript** можна приймати як аргументи в міксинах, які передаються, коли міксин включено, і доступні як змінні в міксині. Аргумент — це ім’я змінної, яке відокремлюється комою при визначенні міксину. Існує два типи аргументів, наприклад*
 + Аргументи ключових слів
 + Змінні аргументи
  ## Аргументи ключових слів
 *Явний аргумент ключового слова можна використовувати для включення в міксини. Аргументи з іменами можна передавати в будь-якому порядку, а стандартні значення аргументів можна пропускати*.
### **Наприклад**,
  *створіть один файл SASS,SCSS із таким кодом* −
  <pre>@mixin bordered($color, $width: 2px) {
   color: #77C1EF;
   border: $width solid black;
   width: 450px;
}

.style  {
   @include bordered($color:#77C1EF, $width: 2px);
}</pre>
*Наведений вище код буде скомпільовано у файл **CSS**, як показано нижче* −
  <pre>.style {
   color: #77C1EF;
   border: 2px solid black;
   width: 450px;
}</pre>
## Змінні аргументи
  *мінний аргумент використовується для передачі будь-якої кількості аргументів у mixin. Він містить ключові аргументи, передані функції або міксину. Аргументи ключових слів, передані до mixin, можна отримати за допомогою функції **keywords($args)**, яка повертає значення, зіставлені з String*.
### Наприклад, 
  *створіть один файл SASS,SCSS із таким кодом* −
  <pre>@mixin colors($background) {
   background-color: $background;
}

$values: magenta, red, orange;
.container {
   @include colors($values...);
}</pre>
*Наведений вище код буде скомпільовано у файл **CSS**, як показано нижче* −
  <pre>.container {
   background-color: magenta;
}</pre>
## Необов'язкові аргументи
 *Зазвичай кожен аргумент, оголошений міксином, повинен бути переданий, коли цей міксин включено. Однак ви можете зробити аргумент необов’язковим, визначивши значення за умовчанням , яке використовуватиметься, якщо цей аргумент не передано. Стандартні значення використовують той самий синтаксис, що й оголошення змінних : ім’я змінної, двокрапка та вираз SassScript . Це полегшує визначення гнучких API міксинів, які можна використовувати як простими, так і складними способами*. 
 ### Приклади:
 *створіть один файл SASS,SCSS із таким кодом* −
  <pre>@mixin replace-text($image, $x: 50%, $y: 50%) {
  text-indent: -99999em;
  overflow: hidden;
  text-align: left;

  background: {
    image: $image;
    repeat: no-repeat;
    position: $x $y;
  }
}

.mail-icon {
  @include replace-text(url("/images/mail.svg"), 0);
}</pre>
*Наведений вище код буде скомпільовано у файл **CSS**, як показано нижче* −
  <pre>.mail-icon {
  text-indent: -99999em;
  overflow: hidden;
  text-align: left;
  background-image: url("/images/mail.svg");
  background-repeat: no-repeat;
  background-position: 0 50%;
}
</pre>
## Аргументи ключових слів
*Якщо включено міксин, аргументи можна передавати за іменем на додаток до передачі їх за позицією в списку аргументів. Це особливо корисно для міксинів із декількома необов’язковими аргументами або з **логічними аргументами**, значення яких неочевидні без назви. Аргументи ключових слів використовують той самий синтаксис, що й **оголошення змінних** і **додаткові аргументи*** .
 ### Приклади:
 *створіть один файл SASS,SCSS із таким кодом* −
  <pre>@mixin square($size, $radius: 0) {
  width: $size;
  height: $size;

  @if $radius != 0 {
    border-radius: $radius;
  }
}

.avatar {
  @include square(100px, $radius: 4px);
}</pre>
  *Наведений вище код буде скомпільовано у файл **CSS**, як показано нижче* −
  <pre>.avatar {
  width: 100px;
  height: 100px;
  border-radius: 4px;
}
</pre>
## Логічні значення
  *Логічні значення – це логічні значення **true** та **false**. Крім літеральних форм, булеві значення повертаються операторами рівності та відношення , а також багатьма вбудованими функціями, такими як **math.comparable()і map.has-key()***.
 ### Приклади:
 *створіть один файл SASS,SCSS із таким кодом* −
  <pre>@use "sass:math";

@debug 1px == 2px; // false
@debug 1px == 1px; // true
@debug 10px < 3px; // false
@debug math.comparable(100px, 3in); // true</pre>
*Ви можете працювати з логічними значеннями за допомогою логічних операторів . Оператор and повертає , trueякщо обидві сторони є true, і orоператор повертає  , trueякщо будь - яка сторона є true. Оператор notповертає значення, протилежне одному логічному значенню*.
*створіть один файл SASS,SCSS із таким кодом* −
<pre>@debug true and true; // true
@debug true and false; // false

@debug true or false; // true
@debug false or false; // false

@debug not true; // false
@debug not false; // true</pre>
## Використання логічних значень
*Ви можете використовувати логічні значення, щоб вибрати, чи робити різні речі в Sass. Правило обчислює блок стилів, якщо його  **@ifаргументtrue*** :
 *створіть один файл SASS,SCSS із таким кодом* −
 <pre>@mixin avatar($size, $circle: false) {
  width: $size;
  height: $size;

  @if $circle {
    border-radius: $size / 2;
  }
}

.square-av {
  @include avatar(100px, $circle: false);
}
.circle-av {
  @include avatar(100px, $circle: true);
}</pre>
  *Наведений вище код буде скомпільовано у файл **CSS**, як показано нижче* −
  <pre>.square-av {
  width: 100px;
  height: 100px;
}

.circle-av {
  width: 100px;
  height: 100px;
  border-radius: 50px;
}</pre>
*Функція повертає одне значення, якщо її аргумент дорівнює, **if()іtrue**  інше, якщо її аргумент дорівнює  **false**:
 *створіть один файл SASS,SCSS із таким кодом* −
 <pre>@debug if(true, 10px, 30px); // 10px
@debug if(false, 10px, 30px); // 30px</pre>
## Прийняття довільних аргументів
*Іноді корисно, щоб міксин міг приймати будь-яку кількість аргументів. Якщо останній аргумент в @mixinдекларації закінчується на ..., тоді всі додаткові аргументи цього міксину передаються цьому аргументу як список . Цей аргумент відомий як список аргументів* .
### **Наприклад**,
  *створіть один файл SASS,SCSS із таким кодом* −
  <pre>@mixin order($height, $selectors...) {
  @for $i from 0 to length($selectors) {
    #{nth($selectors, $i + 1)} {
      position: absolute;
      height: $height;
      margin-top: $i * $height;
    }
  }
}

@include order(150px, "input.name", "input.address", "input.zip");
</pre>
 *Наведений вище код буде скомпільовано у файл **CSS**, як показано нижче* −
 <pre>input.name {
  position: absolute;
  height: 150px;
  margin-top: 0px;
}

input.address {
  position: absolute;
  height: 150px;
  margin-top: 150px;
}

input.zip {
  position: absolute;
  height: 150px;
  margin-top: 300px;
}</pre>
## Отримання довільних аргументів ключових слів
*Списки аргументів також можна використовувати для отримання довільних ключових аргументів. Функція приймає список аргументів і повертає будь-які додаткові ключові слова, які були передані до міксину, як **meta.keywords()** карту від імен аргументів (не включаючи $) до значень цих аргументів.*
### **Наприклад**,
  *створіть один файл SASS,SCSS із таким кодом* −
  <pre>@use "sass:meta";

@mixin syntax-colors($args...) {
  @debug meta.keywords($args);
  // (string: #080, comment: #800, variable: #60b)

  @each $name, $color in meta.keywords($args) {
    pre span.stx-#{$name} {
      color: $color;
    }
  }
}

@include syntax-colors(
  $string: #080,
  $comment: #800,
  $variable: #60b,
)</pre>
