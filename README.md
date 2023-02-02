
# Міксини
**Міксини** *дозволяють визначати стилі, які можна повторно використовувати у вашій таблиці стилів. Вони дозволяють легко уникнути використання несемантичних класів, таких як .float-left, і поширювати колекції стилів у бібліотеках.*

*Міксини визначаються за допомогою @mixinправила at, яке записується*
+ @mixin <name> { ... } або 
+ @mixin name(<arguments...>) { ... } ,
  ### Приклади:
---
```
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
``` 
  ``@include  btnreset();``
 
> *Ім’я міксину може бути будь-яким ідентифікатором Scss, і воно може містити будь -який оператор , крім операторів верхнього рівня . Їх можна використовувати для інкапсуляції стилів, які можна вставити в одне правило стилю ; вони можуть містити власні правила стилю, які можуть бути вкладені в інші правила або включені на верхній рівень таблиці стилів; або вони можуть просто служити для зміни змінних.
>Міксини включаються до поточного контексту за допомогою @includeправила at, яке пишеться*
  >>
  + @include <name>або
  + @include <name>(<arguments...>), разом із назвою міксину.

 ### Приклади:
--- 
 <code><span class="k">@mixin</span> <span class="nf">reset-list</span> <span class="p">{</span>
  <span class="nl">margin</span><span class="p">:</span> <span class="m">0</span><span class="p">;</span>
  <span class="nl">padding</span><span class="p">:</span> <span class="m">0</span><span class="p">;</span>
  <span class="nl">list-style</span><span class="p">:</span> <span class="nb">none</span><span class="p">;</span>
<span class="p">}</span><font></font>
<font></font>
<span class="k">@mixin</span> <span class="nf">horizontal-list</span> <span class="p">{</span>
  <span class="k">@include</span> <span class="nd">reset-list</span><span class="p">;</span><font></font>
<font></font>
  <span class="nt">li</span> <span class="p">{</span>
    <span class="nl">display</span><span class="p">:</span> <span class="n">inline-block</span><span class="p">;</span>
    <span class="nl">margin</span><span class="p">:</span> <span class="p">{</span>
      <span class="nl">left</span><span class="p">:</span> <span class="m">-2px</span><span class="p">;</span>
      <span class="nl">right</span><span class="p">:</span> <span class="m">2em</span><span class="p">;</span>
    <span class="p">}</span>
  <span class="p">}</span>
<span class="p">}</span><font></font>
<font></font>
<span class="nt">nav</span> <span class="nt">ul</span> <span class="p">{</span>
  <span class="k">@include</span> <span class="nd">horizontal-list</span><span class="p">;</span>
<span class="p">}</span>
</code>
