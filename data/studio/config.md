# Конфигурация

Путь к файлу конфигурации Loginom Studio: `%ProgramFiles%\BaseGroup\Loginom 6\Client\server.json`

В файле конфигурации задается URL подключения к [серверу Loginom](../server/README.md).

Значения по умолчанию:

```json
{
    "wsport": null,
    "host": null
}
```

Результрующий url:

* http: `ws://web-server-host:8080`
* https: `wss://web-server-host:8443`

Шифрование протокола `ws` определяется наличием шифрования `http`.

## Параметры

### host

Адрес хоста сервера Loginom. При значении `null` используется адрес хоста веб-сервера.

```json
{
    "wsport": null,
    "host": "lg.domain.org"
}
```

Результрующий url:

* http: `ws://lg.domain.org:8080`
* https: `wss://lg.domain.org:8443`

### wsport

Порт для подключения по протоколу `websocket`. При значении `null` используется порт `8080`.

```json
{
    "wsport": 9999,
    "host": null
}
```

Результрующий url:

* http: `ws://web-server-host:9999`
* https: незащищенные подключения `websocket` запрещены.

### wssport

Порт для подключения по протоколу `websocket secure`. При значении `null` используется порт `8443`.

```json
{
    "wssport": 9443,
    "host": null
}
```

Результрующий url:

* `wss://web-server-host:9443`

### wsproxy

Подключение к серверу Loginom через websocket прокси. В этом случае `host` и `wsport|wssport` будут равны адресу хоста и порту веб-сервера.

```json
{
    "wsproxy": true,
    "host": null
}
```

Результрующий url:

* `ws://web-server-host:443/ws/`

### path

Путь подключения к WebSocket при использовании `wsproxy`. По умолчанию `ws/`.

```json
{
    "wsproxy": true,
    "path": "any/",
    "host": null
}
```

Результрующий url:

* `wss://web-server-host:443/any/`

### secure

Всегда использовать шифрование при подключении к серверу Loginom.

Если параметр не указан, при подключении к веб-серверу по `http` подключение к серверу Loginom будет выполняться без шифрования.

Если параметр указан и установлен в `true`, подключение всегда будет выполняться с шифрованием — по протоколу `websocket secure` на порт `wssport`.

```json
{
    "host": "loginom-server-host",
    "secure": true
}
```

Результрующий url:

* без wsproxy: `wss://loginom-server-host:8443`
* с wsproxy: `wss://web-server-host:443/ws/`