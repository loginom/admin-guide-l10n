# Конфигурация

Файлы конфигурации Loginom Server по умолчанию располагаются в каталоге `%AllUsersProfile%\BaseGroup\Loginom 6\Server`.

## Общие настройки сервера

`%AllUsersProfile%\BaseGroup\Loginom 6\Server\Settings.cfg`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Settings>
  <Directories UserStorage="UserStorage" SessionBackup="SessionBackup"/>
  <Bindings Bind="0.0.0.0" Port="4580" WSPort="8080"/>
</Settings>
```

* `Settings`
  * `Directories`
    * `UserStorage` - атрибут определяет расположение каталогов пользователей. Значением может быть полный или относительный путь.
    * `SessionBackup` - определяет расположение каталога резервных копий сессий. Значением может быть полный или относительный путь.
  * `Bindings`
    * `Bind` - определяет IP адрес сетевого интерфейса, используемого сервером Loginom. `0.0.0.0` означает прослушивание на всех интерфейсах.
    * `Port` - определяет номер порта для подключения Loginom Integrator и BatchLauncher.
    * `WSPort` - определяет номер порта для подключения Loginom Studio по протоколу websocket (ws).

Дополнительно в разделе `Bindings` можно определить параметры подключения по протоколу websocket secure (wss):

* `WSSPort` - определяет номер порта для подключения Loginom Studio по протоколу websocket secure (wss)
* `SSLCertificateFile` - полный или относительный путь к файлу сертификата SSL в формате *pem*.
* `SSLPrivateKeyFile` - полный или относительный путь к файлу ключа SSL в формате *pem*.

## Журналирование

Файлы журналов сохраняются в каталоге `%AllUsersProfile%\BaseGroup\Loginom 6\Server\Logs\`

`%AllUsersProfile%\BaseGroup\Loginom 6\Server\Logs.cfg`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Logging>
  <Common/>
  <File/>
</Logging>
```

* `Logging`
  * `Common`
    * `MinLogLevel` - минимальный уровень журналирования. Возможные значения:
      * `llTrace` - трассировка.
      * `llDebug` - отладка.
      * `llInfo` - информация. Значение по умолчанию.
      * `llHint` - событие.
      * `llWarn` - предупреждение.
      * `llError` - ошибка.
      * `llFatal` - авария.
  * `File`
    * `LogFileName` - имя файла журнала. По умолчанию `app.log`.
    * `LogFileRewrite` - если атрибут установлен, при старте Loginom Server файл журнала будет перезаписан. По умолчанию отключен.
    * `LogFileMaxSize` - максимальный размер файла журнала в байтах. По умолчанию 10485760 (10Mb).
    * `LogFileMaxIndex`- максимальное количество файлов журнала. По умолчанию 10.
