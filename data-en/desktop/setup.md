# Установка Loginom Desktop

The installer file name versions:

* LoginomPersonal_6.x.x_x64.msi — инсталлятор для редакции Personal 64-битной версии
* LoginomPersonal_6.x.x_x86.msi — инсталлятор для редакции Personal 32-битной версии
* LoginomAcademic_6.x.x.msi — инсталлятор для редакции Academic

where 6.x.x – figures denoting the software version and release.

## MSI Installation

### Graphic Interface

#### The Installer Launch

Для установки с нестандартными параметрами в диалоге **"Тип установки"** нажимаем кнопку **"Выборочная"**.

#### Selection of components for installation

![](../images/personal_msi_features_default.png)

* Компонент **"Loginom Personal"** обязателен для установки.
* Компонент **"Документация"** устанавливает файлы документации по работе с платформой.

По умолчанию устанавливаются все компоненты.

### Command Line

```cmd
msiexec /i "LoginomPersonal_6.x.x_x64.msi" ключи_msi
```

* `keys_msi` — it is possible to find the allowable values executing the following command in the command line: `msiexec /?`. The following commands can be especially useful:
   * `/l* "%TEMP%\loginom.msi.log"` — activation of the installation logging.
   * `/qn` — "silent" installation without graphic interface mapping.

## Licenses

Для запуска **Loginom Desktop** требуется настройка ключей лицензирования (см. [Licensing Keys](../licenses/README.md)).

При использовании сервера сетевых ключей требуется создать файл [GnClient.ini](https://dev.guardant.ru/pages/viewpage.action?pageId=1277980) в каталоге `"C:\ProgramData\BaseGroup\Loginom 6\Personal"`
