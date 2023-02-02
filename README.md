
# @mixin і @include
**Міксини** *дозволяють визначати стилі, які можна повторно використовувати у вашій таблиці стилів. Вони дозволяють легко уникнути використання несемантичних класів, таких як .float-left, і поширювати колекції стилів у бібліотеках.*

*Міксини визначаються за допомогою @mixinправила at, яке записується*
+ @mixin <name> { ... } або 
+ @mixin name(<arguments...>) { ... } ,
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
 
> *Ім’я міксину може бути будь-яким ідентифікатором Scss, і воно може містити будь -який оператор , крім операторів верхнього рівня . Їх можна використовувати для інкапсуляції стилів, які можна вставити в одне правило стилю ; вони можуть містити власні правила стилю, які можуть бути вкладені в інші правила або включені на верхній рівень таблиці стилів; або вони можуть просто служити для зміни змінних.
>Міксини включаються до поточного контексту за допомогою @includeправила at, яке пишеться*
  >>
  + @include <name>або
  + @include <name>(<arguments...>), разом із назвою міксину.

 ### Приклади:
--- 
<pre><!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
  integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js"
  integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>
</head>

<body>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js"
  integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.min.js"
  integrity="sha384-cVKIPhGWiC2Al4u+LWgxfKTRIcfu0JTxR+EQDz/bgldoEyl4H0zUF0QKbrJ0EcQF" crossorigin="anonymous"></script>
</body>

</html>
<body>
  
</body>
</html></pre>

<pre>@mixin reset-list {
  margin: 0;
  padding: 0;
  list-style: none;
}

@mixin horizontal-list {
  @include reset-list;

  li {
    display: inline-block;
    margin: {
      left: -2px;
      right: 2em;
    }
  }
}

nav ul {
  @include horizontal-list;
}</pre>
  
   <span>***CSS***</span>
   
  <pre>nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
nav ul li {
  display: inline-block;
  margin-left: -2px;
  margin-right: 2em;
}</pre>
*Імена **Mixin**, як і всі ідентифікатори Sass,Scss, трактують дефіси та підкреслення як ідентичні. Це означає, що reset-listі reset_listобидва посилаються на той самий міксин. Це історичний пережиток із самих ранніх днів Sass, коли він дозволяв лише підкреслення в іменах ідентифікаторів. Після того, як Sass додав підтримку дефісів, щоб вони відповідали синтаксису CSS , їх було еквівалентно, щоб спростити міграцію.*
## **Аргументи**
***Міксини** також можуть приймати аргументи, що дозволяє налаштовувати їх поведінку під час кожного виклику. Аргументи вказуються в @mixinправилі після назви міксину у вигляді списку імен змінних у круглих дужках. Потім міксин має бути включено з такою ж кількістю аргументів у формі виразів SassScript . Значення цих виразів доступні в тілі міксину як відповідні змінні.*
   ### Приклади:
--- 
  <span>***SCSS***</span>     <span>***SASS***</span>
  
  <pre>@mixin rtl($property, $ltr-value, $rtl-value) {
  #{$property}: $ltr-value;

  [dir=rtl] & {
    #{$property}: $rtl-value;
  }
}

.sidebar {
  @include rtl(float, left, right);
}</pre>
<span>***CSS***</span>
  <pre>.sidebar {
  float: left;
}
[dir=rtl] .sidebar {
  float: right;
}</pre>
