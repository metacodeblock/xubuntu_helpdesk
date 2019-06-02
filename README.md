# xubuntu_helpdesk  [https://realyvirt.github.io/xubuntu_helpdesk/]
About Xubuntu (some tip &amp; tricks) [Некоторые советы по настройке Xubuntu]



**1. Замена загрузочного фона и логотипа Xubuntu штатными средствами (актуально на июнь 2019г.)**

     Всё что требуется для этого находится по пути  "/usr/share/plymouth/themes/xubuntu-logo/"
     Для замены обоев требуется заменить файл изображения "wallpaper.png" на любой свой файл формата 
     png,предварительно переименовав его в "wallpaper.png". Для замены логотипа Xubuntu (крысы) на 
     свой потребуется заменить файлы "logo.png" и "logo_16bit.png". Для удаления логотипа Xubuntu нужно 
     заменить вышеназванные "logo*.png" файлы на прозрачные (можно использовать один прозрачный пиксель).
     За круг анимации загрузки отвечает файл "spinner.png", можно изменить его тон/цвет в любом 
     редакторе либо заменить на прозрачное изображение для удаления с экрана загрузки/отключения.
     
     
**2. Устранение рассинхрона изображения (тиринга) видеоадаптеров Intel в Xubuntu (актуально на июнь 2019г.)**

     Ключевой каталог для устранения эффекта тиринга (разрыва/рассинхрона динамичного изображения)
     располагается по пути "/usr/share/X11/xorg.conf.d/". Если обратить внимание на список файлов по данному
     пути, то можно заметить, что авторы дистрибутива вложили в каталог конфигурационные файлы 
     "10-amdgpu.conf" и "10-radeon.conf", но словно забыли вложить конфигурационный файл для GPU от Intel. 
     Чтобы исправить это необходимо создать в данном каталоге файл с именем "20-intel.conf", далее открыть 
     его в любом текстовом редакторе (потребуются права администратора) и добавить в файл следующее:
```
Section "Device"
   Identifier "Intel Graphics"
   Driver "intel"
   Option "TearFree" "true"
EndSection
```
     Далее требуется сохранить файл "20-intel.conf" и перезагрузить компьютер.
     
     
**3. Отключение лампочки "Scroll Lock" при смене (языка) раскладки клавиатуры (актуально на июнь 2019г.)**

     Для отключения лампочки при смене раскладки требуется отредактировать (под администратором) файл
     "keyboard", расположенный по пути "/etc/default/". В данном файле нужно отредактировать строку с
     "XKBOPTIONS", убрав в ней символы между кавычек, а именно "grp_led:scroll". После редактирования
     строка должна выглядеть так:
```
XKBOPTIONS=""
```
     Для применения изменений нужно сохранить отредактированный файл "keyboard" и перезагрузить компьютер.
