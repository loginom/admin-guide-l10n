# Configuration

Path to the Loginom Studio configuration file: `%ProgramFiles%\BaseGroup\Loginom 6\Client\server.json`

URL connection to [Loginom server](../server/README.md) is set in the configuration file.

Default values:

```json
{
    "wsport": null,
    "host": null
}
```

Resulting url:

* http: `ws://web-server-host:8080`
* https: `wss://web-server-host:8443`

Encryption of `ws` protocol is defined by the availability of `http` encryption.

## Parameters

### host

Адрес хоста сервера Loginom. При значении `null` используется адрес хоста веб-сервера.

```json
{
    "wsport": null,
    "host": "lg.domain.org"
}
```

Resulting url:

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

Resulting url:

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

Resulting url:

* `wss://web-server-host:9443`

### wsproxy

Подключение к серверу Loginom через websocket прокси. В этом случае `host` и `wsport|wssport` будут равны адресу хоста и порту веб-сервера.

```json
{
    "wsproxy": true,
    "host": null
}
```

Resulting url:

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

Resulting url:

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

Resulting url:

* без wsproxy: `wss://loginom-server-host:8443`
* с wsproxy: `wss://web-server-host:443/ws/`