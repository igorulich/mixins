
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
*Якщо включено міксин, аргументи можна передавати за іменем на додаток до передачі їх за позицією в списку аргументів. Це особливо корисно для міксинів із декількома необов’язковими аргументами або з логічними аргументами, значення яких неочевидні без назви. Аргументи ключових слів використовують той самий синтаксис, що й оголошення змінних і додаткові аргументи* .
