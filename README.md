
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
  **SCSS**  **SASS**
  
  ```@mixin reset-list {
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
}
  ```
<pre><span class="pl-k">var</span> <span class="pl-s1">sass</span> <span class="pl-c1">=</span> <span class="pl-en">require</span><span class="pl-kos">(</span><span class="pl-s">'node-sass'</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-s1">sass</span><span class="pl-kos">.</span><span class="pl-en">render</span><span class="pl-kos">(</span><span class="pl-kos">{</span>
  <span class="pl-c1">file</span>: <span class="pl-s1">scss_filename</span><span class="pl-kos">,</span>
  <span class="pl-kos">[</span><span class="pl-kos">,</span> <span class="pl-s1">options</span><span class="pl-kos">.</span><span class="pl-kos">.</span><span class="pl-kos">]</span>
<span class="pl-kos">}</span><span class="pl-kos">,</span> function<span class="pl-kos">(</span><span class="pl-s1">err</span><span class="pl-kos">,</span> result<span class="pl-kos">)</span> <span class="pl-kos">{</span> <span class="pl-c">/*...*/</span> <span class="pl-kos">}</span><span class="pl-kos">)</span><span class="pl-kos">;</span>
<span class="pl-c">// OR</span>
<span class="pl-k">var</span> <span class="pl-s1">result</span> <span class="pl-c1">=</span> <span class="pl-s1">sass</span><span class="pl-kos">.</span><span class="pl-en">renderSync</span><span class="pl-kos">(</span><span class="pl-kos">{</span>
  <span class="pl-c1">data</span>: <span class="pl-s1">scss_content</span>
  <span class="pl-kos">[</span><span class="pl-kos">,</span> <span class="pl-s1">options</span><span class="pl-kos">.</span><span class="pl-kos">.</span><span class="pl-kos">]</span>
<span class="pl-kos">}</span><span class="pl-kos">)</span><span class="pl-kos">;</span></pre>
