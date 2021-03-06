# Конфигурация Loginom Integrator

Loginom Integrator настраивается с помощью xml файла [Web.config](https://ru.wikipedia.org/wiki/Web.config). Расположение файла по умолчанию - `%ProgramFiles%\BaseGroup\Loginom 6\Integrator`.

## Соединение с Loginom Server

Loginom Integrator может поддерживать соединения с несколькими экземплярами Loginom Server одновременно.

Для каждого используемого экземпляра Loginom Server в элементе `configuration/loginom` требуется добавить элемент `server` со следующими атрибутами:

* **address** - сетевой адрес хоста Loginom Server. Обязательный атрибут. Значение по умолчанию: localhost.
* **port** - TCP [порт сервера](../server/setup.md#parametry-loginom-server). Значение по умолчанию: 4850.
* **userName** - имя учетной записи с правом на вход в качестве службы. Если атрибут не задан, используются логин и пароль пользователя service.
* **password** - пароль учетной записи с правом на вход в качестве службы. По умолчанию пустая строка.
* **reserved** - атрибут со значением "true" помечает сервер как резервный.

Loginom Integrator поддерживает информацию о работоспособности серверов и опубликованных на них пакетах.

При поступлении запроса сервер выбирается случайным образом среди доступных основных (не резервных) серверов, предоставляющих требуемый пакет.

Если таких нет, то сервер выбирается случайным образом среди доступных резервных серверов.

## Рабочий каталог

Рабочий каталог содержит временные данные, требующиеся для работы приложения.

Путь к каталогу по умолчанию - `%ALLUSERSPROFILE%\BaseGroup\Loginom 6\Integrator`. Переопределить значение можно в атрибуте `workDir` элемента `configuration/loginom`. Значением может быть полный или относительный (от файла конфигурации) путь.

Если используется несколько экземпляров Loginom Integrator, рабочие каталоги у них должны быть разными.

## Журналирование

Параметры журналирования задаются в элементе `configuration/log`.

Возможно включение следующих режимов:

* **fileSystem** - запись в файл;
* **eventLog** - запись в журнал событий Windows;
* **database** - запись в базу данных;
* **internal** - запись в файл событий логирования (к примеру, ошибок при записи логов в базу данных).

Каждому режиму можно задать минимальный уровень детализации:

* **All** - трассировка;
* **Info** - информация;
* **Warn** - предупреждения;
* **Error**- ошибки;
* **Fatal** - критические ошибки;
* **Off** - журналирование отключено.

При установке по умолчанию включена запись в файл с уровнем детализации Info, журналы пишутся в каталог `%ALLUSERSPROFILE%\BaseGroup\Loginom 6\Integrator\Logs\`.

### Запись в файл

Параметры записи в файл задаются в элементе `configuration/log/fileSystem`:

* **path** - полный или относительный (от рабочего каталога) путь к каталогу журналов. Значение по умолчанию: `Logs`.
* **maxArchiveFiles** - максимальное количество архивных журналов. При значении "0" количество файлов не ограничено. Значение по умолчанию: 0;
* **level** - минимальный уровень журналирования. Значение по умолчанию: `All`.

Имя файла журнала - `log.log`.

Новые файлы создаются раз в сутки, старые лог-файлы получают имена вида `log.yyyy-MM-dd.log`.

### Запись в журнал событий Windows

Параметры записи в журнал событий Windows задаются в элементе `configuration/log/eventLog`:

* **level** - минимальный уровень журналирования. Значение по умолчанию: `All`.

Источник событий в журнале Windows: `Loginom Integrator`.

### Запись в базу данных

Параметры записи в базу данных задаются в элементе `configuration/log/database`:

* **connectionString** - строка подключения к базе данных. Обязательный атрибут.
* **level** - минимальный уровень журналирования. Значение по умолчанию: `All`.

Целевые поля для записи данных события можно задать двумя способами: привязать поля журнала к полям таблицы, либо задать SQL запрос.

#### Привязка к полям таблицы

Для привязки требуется задать следующие атрибуты:

* **table** - имя таблицы;
* **dateColumn** - имя поля для записи времени;
* **levelColumn** - имя поля для записи уровня события;
* **machineNameColumn** - имя поля для записи NetBIOS имени хоста, на котором запущен Integrator;
* **userNameColumn** - имя поля для записи пользователя, от имени которого запущен процесс Integrator;
* **appDomainColumn** - имя поля для записи идентификатора домена приложения;
* **requestIdColumn** - имя поля для записи уникального идентификатора запроса;
* **messageColumn** - имя поля для записи текста события;
* **exceptionColumn** - имя поля для записи текста ошибки;

Атрибуты с именами полей могут отсутствовать или содержать пустые значения. В этом случае соответствующие данные не логируются.

#### SQL запрос

SQL запрос задается в атрибуте `sqlCommand`.

Если задан атрибут `table`, `sqlCommand` будет проигнорирован.

В качестве устанавливаемых значений в запросе требуется указывать следующие параметры:

* **:date** - время события;
* **:level** - уровень события;
* **:machinename** - NetBIOS имя хоста, на котором запущен Integrator;
* **:username** - имя пользователя, от имени которого запущен процесс Integrator;
* **:appdomain** - идентификатор домена приложения;
* **:requestid** - уникальный идентификатор запроса;
* **:message** - текст события;
* **:exception** - текст ошибки;

### Запись событий логирования

Параметры записи событий логирования задаются в элементе `configuration/log/internal`:

* **path** - полный или относительный (от рабочего каталога) путь к каталогу журналов. Значение по умолчанию: `Logs`.
* **level** - минимальный уровень журналирования. Значение по умолчанию: `All`.

Имя файла журнала - `logger-internal.log`.
