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

Loginom server host address. In the case of the `null` value the web server host address is used.

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

Port for connection using `websocket` protocol. In case of the `null` value, `8080` port is used.

```json
{
    "wsport": 9999,
    "host": null
}
```

Resulting url:

* http: `ws://web-server-host:9999`
* https: insecure `websocket` connections are forbidden.

### wssport

Port for connection using `websocket secure` protocol. In the case of the `null` value, `8443` port is used.

```json
{
    "wssport": 9443,
    "host": null
}
```

Resulting url:

* `wss://web-server-host:9443`

### wsproxy

Connection to Loginom server by means of websocket proxy. In that case `host` and `wsport|wssport` will be equal to the host address web server port.

```json
{
    "wsproxy": true,
    "host": null
}
```

Resulting url:

* `ws://web-server-host:443/ws/`

### path

Connection path to WebSocket while `wsproxy` using. By default `ws/`.

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

Encryption is always required in the case of connection to Loginom server.

If the parameter is not specified, in the case of connection to the web server `http` connection to Loginom server will be performed without encryption.

If the parameter is specified and set in `true`, connection will be always performed with encryption — using `websocket secure` protocol for `wssport` port.

```json
{
    "host": "loginom-server-host",
    "secure": true
}
```

Resulting url:

* without wsproxy: `wss://loginom-server-host:8443`
* with wsproxy: `wss://web-server-host:443/ws/`