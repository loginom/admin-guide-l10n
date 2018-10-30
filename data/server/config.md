# Конфигурация

При инсталляции Loginom Server создаются следующие папки и файлы:

* `%ProgramFiles%\BaseGroup\` — каталог установки по умолчанию
  * `Loginom 6\` — каталог компонентов платформы
    * `Server\` — каталог исполняемых файлов Loginom Server
    * `Client\` — каталог Loginom Studio
  * `Apache24\` — каталог web-сервера Apache Httpd
* `%AllUsersProfile%\BaseGroup\` — каталог установки по умолчанию
  * `Loginom 6\` — каталог данных платформы
    * `Server\` — каталог конфигурационных и вспомогательных файлов Loginom Server
      * `UserStorage/` — каталог данных пользователей
      * `Logs/` — каталог логов сервера
      * `Settings.cfg` — основной файл конфигурации серврера
      * `Users.cfg` — файл конфигурации пользователей
      * `SharedFolders.cfg` — файл конфигурации общих каталогов
      * `GnClient.ini` — файл конфигурации сетевого сервера лицензий Guardant
  * `Apache24/` — каталог web-сервера Apache Httpd

## Settings.cfg
