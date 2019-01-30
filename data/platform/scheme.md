# Взаимодействие компонентов

Взаимодействие между Loginom Server и остальными компонентами платформы.

## Studio

### Без wsproxy (при установке с параметрами по умолчанию)

![](../images/without-proxy.svg)

* Браузер подключается к web-серверу по протоколу `http` и загружает Loginom Studio:
  * `http://web-server-host:80/app` - URL подключения, если шифрование http не включено;
  * `https://web-server-host:443/app` - URL подключения, если шифрование http включено.
* Из конфигурации [server.json](../studio/config.md) формируется URL для подключения к серверу Loginom;
* Loginom Studio создает подключение на хост сервера Loginom по протоколу `websocket`:
  * `ws://loginom-server-host:8080/ws` - URL подключения, если шифрование websocket [не включено](../server/setup.md#parametry-loginom-server). При наличии шифрования http подключение запрещено.
  * `wss://loginom-server-host:8443/ws` - URL подключения, если шифрование websocket [включено](../server/setup.md#parametry-loginom-server).

### С использованием wsproxy

![](../images/proxy.svg)

* Браузер подключается к web-серверу по протоколу `http` и загружает Loginom Studio:
  * `http://web-server-host:80/app` - URL подключения, если шифрование http не включено;
  * `https://web-server-host:443/app` - URL подключения, если шифрование http включено.
* Из конфигурации [server.json](../studio/config.md) формируется URL для подключения к серверу Loginom;
* Loginom Studio подключается к хосту web-сервера по протоколу `websocket`:
  * `ws://web-server-host:80/ws` - URL подключения, если не включено шифрование ни http, ни websocket;
  * `wss://web-server-host:443/ws`  - URL подключения, если включено шифрование http либо websocket.
* Web-сервер создает подключение на хост сервера Loginom по протоколу `websocket` и перенаправляет в него траффик соединения с Loginom Studio:
  * `ws://loginom-server-host:8080/ws` - URL подключения, если шифрование websocket [не включено](../server/setup.md#parametry-loginom-server);
  * `wss://loginom-server-host:8443/ws` - URL подключения, если шифрование websocket [включено](../server/setup.md#parametry-loginom-server).

## Integrator

![](../images/service.svg)

* Внешний сервис подключается по протоколу http к web-серверу (IIS), на котором развернуто web-приложение Loginom Integrator;
* Integrator обрабатывает запрос и создает подключение на TCP [порт сервера](../server/setup.md#parametry-loginom-server) к хосту сервера Loginom.
