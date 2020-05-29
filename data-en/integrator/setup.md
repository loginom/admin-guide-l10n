# Установка Loginom Integrator

Имя файла инсталлятора: `LoginomIntegrator_6.x.x.msi`, где 6.x.x – цифры, обозначающие версию и релиз программы.

> **Примечание:** Версия Loginom Integrator должна соответствовать версии используемого сервера Loginom.

## Enable IIS Components

Необходимо выполнить в командной строке от имени администратора:

```cmd
dism /online /enable-feature /FeatureName:IIS-WebServerRole /FeatureName:IIS-WebServer /FeatureName:IIS-WebServerManagementTools /FeatureName:IIS-ManagementScriptingTools
```

## Включение компонентов IIS для Loginom Integrator

Для корректной работы Loginom Integrator требуется установленный NetFramework v4.5+.

Необходимо установить следующие компоненты:

Необходимо выполнить в командной строке от имени администратора:

```cmd
:: Для windows 2008/7/2012/8:
dism /online /enable-feature /FeatureName:IIS-ApplicationDevelopment /FeatureName:IIS-ISAPIExtensions /FeatureName:WAS-WindowsActivationService /FeatureName:WAS-ProcessModel /FeatureName:IIS-NetFxExtensibility /FeatureName:WAS-NetFxEnvironment /FeatureName:WAS-ConfigurationAPI /FeatureName:WCF-HTTP-Activation

:: Для windows 2012r2/8.1/2016/10:
dism /online /enable-feature /FeatureName:IIS-ApplicationDevelopment /FeatureName:IIS-ISAPIExtensions /FeatureName:WAS-WindowsActivationService /FeatureName:WAS-ProcessModel /FeatureName:IIS-ASPNET45 /FeatureName:IIS-NetFxExtensibility45 /FeatureName:NetFx4Extended-ASPNET45 /FeatureName:WCF-Services45 /FeatureName:IIS-ISAPIFilter /FeatureName:WCF-HTTP-Activation45 /all

:: Для windows 2008/7/2012/8/2012r2/8.1 регистрируем ASP.NET:
"%WinDir%\Microsoft.NET\Framework64\v4.0.30319\Aspnet_regiis.exe" -iru

:: Для windows 2008/7/2012/8/2012r2/8.1 разрешаем исполнение модулей ISAPI:
"%windir%\system32\inetsrv\appcmd.exe" set config /section:isapiCgiRestriction /[path='%WinDir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_isapi.dll'].allowed:True
```

***

Минимально должны быть установлены следующие роли сервера (windows 2016):

```txt
Веб Сервер (IIS) (Установлено 8 из 43)
- Веб сервер (Установлено 8 из 34)
   - Безопасность (Установлено 1 из 9)
        * Фильтрация запросов
   - Общие функции HTTP (Установлено 3 из 6)
        * Документ по умолчанию
        * Обзор Каталога
        * Статическое содержимое
   - Разработка приложений (Установлено 4 из 11)
        * ASP.NET 4.6
        * Расширения ISAPI
        * Расширяемость .NET4.
        * Фильтры ISAPI
```

## MSI Installation

### Graphic Interface

#### Run the Installer

It is required to press the  **Custom** button for installation with nonstandard parameters in the **Installation type** dialog. Для получения параметров существующих сайтов IIS в интерфейсе инсталлятора требуется запустить его с правами администратора.

#### Installation directory

По умолчанию установка производится в каталог `%ProgramFiles%\BaseGroup\`;

![](../images/integrator_msi_path.png)

#### Параметры установки

![](../images/integrator_msi_parameters.png)

Блок **IIS**:

* **Сайт** — имя существующего сайта IIS, на котором будет развернут Loginom Integrator.
* **IP**, **Порт** — параметры привязки сайта IIS.
* **Приложение** — имя web-приложения.
* **Пул приложений** — имя пула приложений, обслуживающего Loginom Integrator. Если пул не существует, он будет создан.

Блок **Подключение к Loginom Server**:

* **Хост** — адрес хоста сервера Loginom.
* **Порт** — порт сервера Loginom.
* **Логин**, **Пароль** — реквизиты для [подключения к серверу Loginom](../server/setup.md#uchetnye-zapisi).
* **Показать пароль** — переключает режим отображения пароля.

### Command Line

```cmd
msiexec /i "LoginomIntegrator_6.x.x.msi" ключи_msi параметры_integrator
```

* `keys_msi` — it is possible to find the allowable values executing the following command in the command line: `msiexec /?`. The following commands can be especially useful:
   * `/l* "%TEMP%\loginom.msi.log"` — activation of the installation logging.
   * `/qn` — "silent" installation without graphic interface mapping.
* `параметры_integrator` в виде `КЛЮЧ=значение`:

| Key | Default value | Description |
|:--------- |:-------------|:------------- |
| IIS_APPNAME | `lgi` | Имя web-приложения IIS |
| IIS_POOLNAME | `LGI_POOL` | Имя создаваемого пула приложений IIS |
| IIS_WEBSITENAME | `Default Web Site` | Имя сайта IIS |
| IIS_WEBSITEIPADDRESS | `0.0.0.0` | Адрес привязки сайта IIS |
| IIS_WEBSITEPORT | `80` | Порт привязки сайта IIS |
| LGS_HOST | `localhost` | Хост Loginom Server |
| LGS_PORT | `4580` | Порт Loginom Server |
| LGS_USER | `service` | Имя учетной записи Loginom Server |
| LGS_PASS | `service` | Пароль учетной записи Loginom Server |

## Ручная установка

* Поместить содержимое каталога Integrator в требуемое расположение
* Скорректировать содержимое [web.config](./config.md)
* Создать в IIS пул приложений в режиме `Integrated` и версией среды CLR `v4.0`
* Создать в IIS web-приложение в новом пуле, указав путь к расположению файлов Integrator

## Function Test

Для проверки работоспособности необходимо в браузере перейти по URL: `http://<Server>/lgi/service.svc?wsdl`, где `<Server>` — имя хоста Loginom Integrator.

Пример: `http://localhost/lgi/service.svc?wsdl`

Loginom Integrator должен отдать WSDL SOAP веб-сервиса с
предупреждением:

```xml
<wsdl:documentation>
В настоящий момент не опубликовано ни одного пакета. Для
использования пакетов в качестве веб-сервиса необходимо
предварительно опубликовать их в Loginom Server.
</wsdl:documentation>
```

Второй вариант проверки — перейти по URL: `http://<Server>/lgi/service.svc/rest/help`.

Loginom Integrator должен отдать страницу описания работы с REST сервисом.

При установке продукта для этих URL в меню "Пуск" Windows `Все программы\Loginom 6\Integrator` добавляются ярлыки *"Описание WSDL сервиса"* и *"Описание REST сервиса"*.
