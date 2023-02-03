
# ***@mixin*** і ***@include***
**Міксини** *дозволяють визначати стилі, які можна повторно використовувати у вашій таблиці стилів. Вони дозволяють легко уникнути використання несемантичних класів, таких як .float-left, і поширювати колекції стилів у бібліотеках.*

*Міксини визначаються за допомогою @mixinправила at, яке записується*
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
   **або** 
+ @mixin name(<arguments...>) { ... } ,
 
> *Ім’я міксину може бути будь-яким ідентифікатором Scss, і воно може містити будь -який оператор , крім операторів верхнього рівня . Їх можна використовувати для інкапсуляції стилів, які можна вставити в одне правило стилю ; вони можуть містити власні правила стилю, які можуть бути вкладені в інші правила або включені на верхній рівень таблиці стилів; або вони можуть просто служити для зміни змінних.
>Міксини включаються до поточного контексту за допомогою @includeправила at, яке пишеться*
  >>
  + @include <name>або
  + @include <name>(<arguments...>), разом із назвою міксину.

 ### Приклади:
--- 
***SCSS***  ***SASS***

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
  
   ***CSS***
   
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
  ***SCSS***     ***SASS***
  
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

  <!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
    integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
</head>

<body >
<table class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">First</th>
      <th scope="col">Last</th>
      <th scope="col">Handle</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Mark</td>
      <td>Otto</td>
      <td>@mdo</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Jacob</td>
      <td>Thornton</td>
      <td>@fat</td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td colspan="2">Larry the Bird</td>
      <td>@twitter</td>
    </tr>
  </tbody>
</table>
</body>

</html>
