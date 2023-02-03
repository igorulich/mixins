
# ***@mixin*** і ***@include***
**Міксини***дозволяють визначати стилі, які можна повторно використовувати у вашій таблиці стилів. Вони дозволяють легко уникнути використання несемантичних класів, таких як .float-left, і поширювати колекції стилів у бібліотеках.*
*Ім’я міксину може бути будь-яким ідентифікатором Scss,Sass, і воно може містити будь -який оператор , крім операторів верхнього рівня . Їх можна використовувати для інкапсуляції стилів, які можна вставити в одне правило стилю ; вони можуть містити власні правила стилю, які можуть бути вкладені в інші правила або включені на верхній рівень таблиці стилів; або вони можуть просто служити для зміни змінних.*
*Міксини включаються до поточного контексту за допомогою @includeправила at, яке пишеться
Міксини визначаються за допомогою **@mixinправила** at, яке записується*
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
 *Значення SassScript можна приймати як аргументи в міксинах, які передаються, коли міксин включено, і доступні як змінні в міксині. Аргумент — це ім’я змінної, яке відокремлюється комою при визначенні міксину. Існує два типи аргументів, наприклад*
 + Аргументи ключових слів
 + Змінні аргументи
  
 
