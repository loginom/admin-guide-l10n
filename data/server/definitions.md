# Определения

## Сервер Loginom

### Хост сервера

Сетевой адрес (DNS, NetBios, IP) хоста, где установлен сервер Loginom.

### Порт websocket

Порт для подключения Loginom Studio по протоколу `ws` ([websocket](https://ru.wikipedia.org/wiki/WebSocket)).

### Порт websocket secure

Порт для подключения Loginom Studio по протоколу `wss` (websocket secure).

### Ключ SSL websocket

Ключ шифрования SSL для протокола `wss` в формате `pem`.

### Сертификат SSL websocket

Сертификат SSL для протокола `wss` в формате `pem`.

### Порт сервера

Порт для подключения Loginom Integrator и BatchLauncher.

## Loginom Studio

Web-интерфейс для работы со сценариями на сервере Loginom.

## Web-сервер

Web-сервер предоставляет клиенту web-интерфейс Loginom Studio. Также он может использоваться в качестве [websocket proxy](#websocket-proxy) для подключения к серверу Loginom.

### Хост web-сервера

Сетевой адрес (DNS, NetBios, IP) хоста, где установлен web-сервер.

Web-сервер и сервер Loginom могут располагаться как на одном хосте, так и на разных.

### Порт web-сервера

### URI Loginom Studio

### Ключ SSL http

Ключ шифрования SSL для протокола `https` в формате `pem`.

### Сертификат SSL http

Сертификат SSL для протокола `wss` в формате `pem`.

### WebSocket proxy

