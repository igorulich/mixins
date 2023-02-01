
# Міксини
**Міксини** *дозволяють визначати стилі, які можна повторно використовувати у вашій таблиці стилів. Вони дозволяють легко уникнути використання несемантичних класів, таких як .float-left, і поширювати колекції стилів у бібліотеках.*

>> *Міксини визначаються за допомогою @mixinправила at, яке записується* 
+ @mixin <name> { ... } або 
+ @mixin name(<arguments...>) { ... } ,
  ### Приклади:
>> **обнуление стилей button**
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
  >> **підключеня font-family**
  *определяет приоритетный список из одного или нескольких названий семейства шрифтов и/или общее имя шрифта для выбранного элемента.*
  ```
 @mixin gen-fonts {
  @each $font in $fonts-list{
    @font-face {
      font-family: '#{$font}';
      src: url('../fonts/#{$font}.eot'); /* IE9 Compat Modes */
      src: url('../fonts/#{$font}.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
      url('../fonts/#{$font}.woff2') format('woff2'), /* Super Modern Browsers */
      url('../fonts/#{$font}.woff') format('woff'), /* Pretty Modern Browsers */
      url('../fonts/#{$font}.ttf')  format('truetype'), /* Safari, Android, iOS */
      url('../fonts/#{$font}.svg#svgFontName') format('svg'); /* Legacy iOS */
      font-style: normal;
    }
  }
}
@include gen-fonts();
  ```
>> *Ім’я міксину може бути будь-яким ідентифікатором Sass, і воно може містити будь -який оператор , крім операторів верхнього рівня . Їх можна використовувати для інкапсуляції стилів, які можна вставити в одне правило стилю ; вони можуть містити власні правила стилю, які можуть бути вкладені в інші правила або включені на верхній рівень таблиці стилів; або вони можуть просто служити для зміни змінних.*
>*Міксини включаються до поточного контексту за допомогою @includeправила at, яке
  >> пишеться
  + @include <name>або
  + @include <name>(<arguments...>), разом із назвою міксину.
> 
 ### Приклади:
```

  @mixin reset-list {
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
