
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
  ```
  @mixin connectionFonts($font-family, $url, $weight) {
	@font-face {
		font-family: "#{$font-family}";
		src: url("../fonts/#{$url}.woff2") format("woff2"),
			url("../#{$url}.woff") format("woff");
		font-weight: #{$weight};
		font-display: swap;
		font-style: normal;
		font-weight: normal;
	}
}
  ```
>> *Ім’я міксину може бути будь-яким ідентифікатором Sass, і воно може містити будь -який оператор , крім операторів верхнього рівня . Їх можна використовувати для інкапсуляції стилів, які можна вставити в одне правило стилю ; вони можуть містити власні правила стилю, які можуть бути вкладені в інші правила або включені на верхній рівень таблиці стилів; або вони можуть просто служити для зміни змінних.*
>*Міксини включаються до поточного контексту за допомогою @includeправила at, яке
  >> пишеться
  + @include <name>або
  + @include <name>(<arguments...>), разом із назвою міксину.
> 

  
