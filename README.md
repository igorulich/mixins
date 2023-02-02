
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
<pre><!DOCTYPE html
    PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <title>HTML Template</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link href="https://fonts.googleapis.com/css?family=Raleway:300,400,500,600" rel="stylesheet" />
    <style>
        body {
            width: 100% !important;
            -webkit-text-size-adjust: 100%;
            -ms-text-size-adjust: 100%;
            margin: 0;
            padding: 0;
            line-height: 100%;
        }

        [style*="Raleway"] {
            font-family: 'Raleway', arial, sans-serif !important;
        }

        img {
            outline: none;
            text-decoration: none;
            border: none;
            -ms-interpolation-mode: bicubic;
            max-width: 100% !important;
            margin: 0;
            padding: 0;
            display: block;
        }

        table td {
            border-collapse: collapse;
        }

        table {
            border-collapse: collapse;
            mso-table-lspace: 0pt;
            mso-table-rspace: 0pt;
        }

        .menu a {
            color: #6c6c6c;
            font-size: 14px;
            font-weight: 400;
            letter-spacing: 0.28px;
            text-decoration: none;
        }

        .menu td {
            padding-left: 30px;
        }

        .header-td {
            padding-top: 40px;
            padding-bottom: 40px;
        }

        .features-td {
            padding-top: 100px;
            padding-bottom: 30px;
        }

        .features-td p {
            color: #8c8c8c;
            font-size: 14px;
            font-weight: 400;
            line-height: 26px;
            letter-spacing: 0.28px;
        }

        .blockqoute-td {
            padding-top: 150px;
            padding-bottom: 50px;
        }

        .block-td p {
            color: #8c8c8c;
            font-size: 14px;
            font-weight: 400;
            line-height: 30px;
            letter-spacing: 0.28px;
        }

        .block-table td {
            padding-top: 40px;
            padding-bottom: 40px;
        }

        .block-table {
            border-top: 1px solid #e6e6e6;
            border-left: 1px solid #e6e6e6;
            border-right: 1px solid #e6e6e6;
            border-bottom: 1px solid #e6e6e6;
        }

        .author {
            padding-top: 20px;
        }

        .author h3 {
            margin-top: 20px;
            color: #686868;
            font-size: 14px;
            font-weight: 600;
            letter-spacing: 0.56px;
            margin-bottom: 5px;
        }

        .author p {
            color: #8c8c8c;
            font-size: 13px;
            font-weight: 300;
            font-size: 14px;
            letter-spacing: 0.52px;
            margin: 0;
        }

        .footer-td {
            padding-top: 80px;
            padding-bottom: 80px;
        }

        .footer-menu-td {
            padding-top: 60px;
            padding-bottom: 35px;
        }

        .footer-menu-td a {
            color: #bcc9dd;
            font-size: 14px;
            font-weight: 400;
            letter-spacing: 0.36px;
            text-decoration: none;
        }

        .copyright-td {
            color: #bcc9dd;
            font-size: 12px;
            font-weight: 400;
            letter-spacing: 0.31px;
        }

        .copyright-td a {
            font-weight: 600;
            text-decoration: none;
            color: #bcc9dd;
        }

        @media (max-width: 870px) {
            .table-850 {
                width: 600px !important;
            }

            .table-600 {
                width: 550px !important;
            }

            .block-table {
                width: 200px !important;
            }

            .block-table p br {
                display: none !important;
            }

            .features-td td {
                display: block !important;
                margin-bottom: 50px !important;
            }
        }

        @media (max-width: 620px) {
            .table-850 {
                width: 400px !important;
            }

            .table-600 {
                width: 320px !important;
            }

            .block-td {
                display: block !important;
                margin-bottom: 50px !important;
                padding: 0 !important;
            }

            .blockqoute-td tr {
                display: block !important;
            }

            .block-table {
                width: 320px !important;
                display: block !important;
                margin: 0 auto !important;
            }

            .author {
                width: 200px !important;
            }

            .logo {
                display: block !important;
                margin: 0 auto !important;
                text-align: center !important;
                width: 200px !important;
                margin-bottom: 20px !important;
            }

            .logo img {
                margin: 0 auto !important;
            }

            .menu {
                display: block !important;
                margin: 0 auto !important;
            }
        }

        @media (max-width: 420px) {
            .table-850 {
                width: 300px !important;
            }

            .table-600 {
                width: 260px !important;
            }

            .block-table {
                width: 260px !important;
            }

            .author {
                width: 130px !important;
            }

            .blockqoute-td {
                padding-top: 50px !important;
                padding-bottom: 50px !important;
            }

            .footer-menu-td table {
                width: 260px !important;
            }
            
            .menu td {
                padding-left: 10px !important;
                padding-right: 10px !important;
            }
        }
    </style>
</head>

<body style="margin: 0; padding: 0;">
    <div style="font-size:0px;font-color:#ffffff;opacity:0;visibility:hidden;width:0;height:0;display:none;">Тестовое
        письмо</div>
    <table cellpadding="0" cellspacing="0" width="100%" bgcolor="6699cc">
        <tr>
            <td>
                <table class="main table-850" cellpadding="0" cellspacing="0" width="850" align="center">
                    <tr>
                        <td height="30" width="850"></td>
                    </tr>
                    <tr>
                        <td bgcolor="#ffffff" class="header-td">
                            <table class="table-600" cellpadding="0" cellspacing="0" width="600" align="center">
                                <tr>
                                    <td align="left" class="logo">
                                        <img src="bella.png" alt="logo" />
                                    </td>
                                    <td align="right" class="menu">
                                        <table cellpadding="0" cellspacing="0">
                                            <tr>
                                                <td><a href="#" style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">Team</a></td>
                                                <td><a href="#" style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">Features</a></td>
                                                <td><a href="#" style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">Pricing</a></td>
                                                <td><a href="#" style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">Contact</a></td>
                                            </tr>
                                        </table>
                                    </td>
                                </tr>
                            </table>
                        </td>
                    </tr>
                    <tr>
                        <td class="banner-td">
                            <a href="#">
                                <img src="bnr.png" alt="banner" />
                            </a>
                        </td>
                    </tr>
                    <tr>
                        <td class="features-td" bgcolor="#ffffff">
                            <table class="table-600" cellpadding="0" cellspacing="0" width="600" align="center">
                                <tr>
                                    <td align="center">
                                        <img src="return.png" alt="return" />
                                        <p style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">
                                            phoncus ut, imperdiet vel <br /> venenatis vitae justo ullam <br /> dictum felis eu pede
                                            mollis <br /> pretium massa.
                                        </p>
                                        <a href="#"><img src="read-more.png"
                                                alt="read-more"></a>
                                    </td>
                                    <td align="center">
                                        <img src="stopwatch.png"
                                            alt="stopwatch" />
                                        <p style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">
                                            phoncus ut, imperdiet vel <br /> venenatis vitae justo ullam <br /> dictum
                                            felis eu pede
                                            mollis <br /> pretium massa.
                                        </p>
                                        <a href="#"><img src="read-more.png"
                                                alt="read-more"></a>
                                    </td>
                                    <td align="center">
                                        <img src="reminders.png"
                                            alt="reminders" />
                                        <p style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">
                                            phoncus ut, imperdiet vel <br /> venenatis vitae justo ullam <br /> dictum
                                            felis eu pede
                                            mollis <br /> pretium massa.
                                        </p>
                                        <a href="#"><img src="read-more.png"
                                                alt="read-more"></a>
                                    </td>
                                </tr>
                            </table>
                        </td>
                    </tr>
                    <tr>
                        <td class="blockqoute-td" bgcolor="#ffffff">
                            <table class="table-600" cellpadding="0" cellspacing="0" width="600" align="center">
                                <tr>
                                    <td class="block-td" align="center" style="padding-right: 20px;">
                                        <table cellpadding="0" cellspacing="0" class="block-table" align="center" width="280">
                                            <tr>
                                                <td align="center">
                                                    <p style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">
                                                        Donec quam felis ultricies nec pel <br /> lentesque pretium quis
                                                        sem massa <br /> quis
                                                        enim. Donec pede justo fring <br /> illa vel aliquet nec
                                                        vulputate eget <br /> magnis
                                                        montes ligula eget.
                                                    </p>
                                                </td>
                                            </tr>
                                        </table>
                                    </td>
                                    <td class="block-td" align="center" style="padding-left: 20px;">
                                        <table cellpadding="0" cellspacing="0" class="block-table" align="center"
                                            width="280">
                                            <tr>
                                                <td align="center">
                                                    <p style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">
                                                        Donec quam felis ultricies nec pel <br /> lentesque pretium quis
                                                        sem massa <br /> quis
                                                        enim. Donec pede justo fring <br /> illa vel aliquet nec
                                                        vulputate eget <br /> magnis
                                                        montes ligula eget.
                                                    </p>
                                                </td>
                                            </tr>
                                        </table>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="author" align="center" style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">
                                        <img src="author_img.png"
                                            alt="author" />
                                        <h3>Alexander Doe</h3>
                                        <p>Senior UX Developer</p>
                                    </td>
                                    <td class="author" align="center"
                                        style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">
                                        <img src="author_img-2.png"
                                            alt="author" />
                                        <h3>Laurie Doe</h3>
                                        <p>Marketing Expert</p>
                                    </td>
                                </tr>
                            </table>
                        </td>
                    </tr>
                    <tr>
                        <td class="footer-td" bgcolor="#38404b">
                            <table class="table-600" cellpadding="0" cellspacing="0" width="600" align="center">
                                <tr>
                                    <td class="footer-logo" align="center">
                                        <a href="#">
                                            <img src="bella-footer.png" alt="footer-logo" />
                                        </a>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="footer-menu-td" align="center">
                                        <table cellpadding="0" cellspacing="0" width="350" align="center">
                                            <tr>
                                                <td align="center"><a href="#" style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">About Us</a></td>
                                                <td align="center"><a href="#" style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">Team</a></td>
                                                <td align="center"><a href="#" style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">News</a></td>
                                                <td align="center"><a href="#" style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">Contact Us</a></td>
                                            </tr>
                                        </table>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="copyright-td" align="center" style="font-family: Arial, Helvetica, sans-serif, 'Raleway';">© 2014 pixelhint.com. All Rights Reserved</td>
                                </tr>
                            </table>
                        </td>
                    </tr>
                    <tr>
                        <td height="30" width="850"></td>
                    </tr>
                </table>
            </td>
        </tr>
    </table>
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
