# Interaction of Components

Interaction of Loginom Server and Other Platform Components

## Studio

[Studio](../studio/README.md) enables data exchange with Loginom Server using [websocket](https://ru.wikipedia.org/wiki/WebSocket) protocol. Connection is provided using one of the following two methods - directly from Loginom server or using websocket proxy configured on the web server.

Websocket proxy enables to provide access to Loginom Server via http(s) port of the web server that facilitates the firewall configuration.

To enable wsproxy on the imbedded web server, it is sufficient to select "Use WebSocket proxy" [in the course of installation](../server/setup.md#parametry-web-servera-apache-httpd), IIS will require more complicated [configuration](../server/iis.md#nastroyka-websocket-proxy).

In the case of the default installation websocket proxy is disabled.

### Without wsproxy

![](../images/without-proxy.svg)

* Browser is connected to the web server using `http` protocol; it enables Loginom Studio loading:
   * `http://web-server-host:80/app` - URL connections if http encryption is not enabled;
   * `https://web-server-host:443/app` - URL connections if http encryption is enabled.
* [server.json](../studio/config.md) configuration enables URL formation for connection to Loginom server;
* Loginom Studio enables connection to the Loginom server host using `websocket` protocol:
   * `ws://loginom-server-host:8080/ws` - URL connections if websocket encryption [is not enabled](../server/setup.md#parametry-loginom-server). In the case of http encryption connection is forbidden.
   * `wss://loginom-server-host:8443/ws` - URL connections if websocket encryption [is enabled](../server/setup.md#parametry-loginom-server).

### With wsproxy

![](../images/proxy.svg)

* Browser is connected to the web server using `http` protocol; it enables Loginom Studio loading:
   * `http://web-server-host:80/app` - URL connections if http encryption is not enabled;
   * `https://web-server-host:443/app` - URL connections if http encryption is enabled.
* [server.json](../studio/config.md) configuration enables URL formation for connection to Loginom server;
* Loginom Studio enables connection to the web server host using `websocket` protocol:
   * `ws://web-server-host:80/ws` - URL connections if neither http, nor websocket encryption is enabled;
   * `wss://web-server-host:443/ws`  - URL connections if http or websocket encryption is enabled.
* The web server enables connection to the Loginom server host using `websocket` protocol and retransfer to it traffic of connection with Loginom Studio:
   * `ws://loginom-server-host:8080/ws` - URL connections if websocket encryption [is disabled](../server/setup.md#parametry-loginom-server);
   * `wss://loginom-server-host:8443/ws` - URL connections if websocket encryption [is enabled](../server/setup.md#parametry-loginom-server).

## Integrator

![](../images/service.svg)

* The external service is connected using http protocol to the web server (IIS) on which [Loginom Integrator](../integrator/README.md) web application is deployed;
* Integrator enables request processing and creation of connection to TCP [server port](../server/setup.md#parametry-loginom-server) to the Loginom server host.
