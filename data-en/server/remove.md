# Удаление Loginom Server

Для удаления Loginom Server требуется остановить службу *loginom* и удалить приложение одним из способов:

* Из окна "Программы и компоненты" в Windows;
* Запустить инсталлятор продукта, нажать кнопку **"Удалить"**

![](../images/server_msi_remove.png)

* To execute the following command in the command line as the administrator:

```cmd
msiexec /x Loginom<Редакця>_6.x.x.msi /qn
```
