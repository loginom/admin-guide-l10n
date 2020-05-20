# Loginom Server Installation

## MSI Installation

The installer file name versions:

* LoginomTeam_6.x.x.msi – the installer for the Team editing
* LoginomStandard_6.x.x.msi – the installer for the Standard editing
* LoginomEnterprise_6.x.x.msi – the installer for the Enterprise editing

where 6.x.x – figures denoting the software version and release.

Web server is mandatory for work with [Loginom Studio](../studio/README.md) (web interface for Loginom Server).

It is allowed to use the following web server types:

* **Apache** – standard installation, web server is included into the distribution kit
* **Microsoft IIS** is not included into the distribution kit. It must be [installed and configured](./iis.md) separately.

Loginom Server is installed in a different way using Apache or Microsoft IIS. When installing by default, Loginom Studio is used by means of the Apache web server.

### Graphic Interface

#### The Installer Launch

It is required to press the **Custom** button for installation with nonstandard parameters in the **Installation type** dialog.

#### Selection of components for installation

* **Loginom Server** is compulsory for the *Loginom server* installation.
* **Loginom Studio** installs the web interface.
* The **Documentation** enables to add the platform operation reference section to the web interface.
* The **web server** installs the embedded Apache Httpd web server. If the third-party server is to be used, the component must be disabled.

![](../images/server_msi_features_default.png)

> **Note:** All components are installed by default.

#### Loginom Server Parameters

This dialog is available only on condition of the *Loginom Server* component installation.

![](../images/server_msi_server.png)

* The **Server port** defines the port number for Loginom Integrator and BatchLauncher connection.
* The **WS port** defines the port number for Loginom Studio connection according to the websocket (ws) protocol.
* **Use WebSocket secure** enables to set the ssl parameters for websocket:
   * The **WSS port** defines the port number for Loginom Studio connection according to the websocket secure (wss) protocol.
   * The **SSL certificate**, **SSL key** are the full paths to the certificate file and SSL key in the *pem* format.
* **Install the Guardant x64 driver** enables to launch the installation in the automatic driver mode for the software protection dongle operation.

#### Apache Httpd Web Server Parameters

The dialog is available only on condition of the *Web server* component installation.

![](../images/server_msi_httpd.png)

* The **HTTP port** defines the number of the web server http port.
* **Use WebSocket proxy** activates proxying of the websocket connections.
* **Use HTTPS** enables to set the sssl parameters for http:
   * The **HTTPS port** defines the number of the web server https port.
   * The **SSL certificate**, **SSL key** are the full paths to the certificate file and SSL key in the *pem* format.

#### Loginom Studio Parameters

The dialog is available only on condition of the Loginom Studio component installation without the Web server component installation.

![](../images/server_msi_studio.png)

* **The Web Application Directory**
* **URL of the Web Application**
* **Connection to the Loginom server** contains parameters for formation of the [Loginom Studio configuration file](../studio/config.md)
   * **Host** defines the value of the [host](../studio/config.md#host) parameter. If the field value is equal to host of the *URL of the web application* field, it is required to specify `host: null` in `server.json`.
   * The **WS port** and **WSS port** defines the values of the [wsport](../studio/config.md#wsport) and [wssport](../studio/config.md#wssport) parameters correspondingly.
   * **Always use secure connection** activates the [secure](../studio/config.md#secure) parameter.
   * **Use WebSocket proxy** activates the [wsproxy](../studio/config.md#wsproxy) parameter.
   * **Proxy URI** defines the [path](../studio/config.md#path) parameter.

### Command Line

```cmd
msiexec /i "путь_к_msi_файлу" ключи_msi параметры_loginom
```

* `keys_msi` — it is possible to find the allowable values executing the following command in the command line: `msiexec /?`. The following commands can be especially useful:
   * `/l* "%TEMP%\loginom.msi.log"` — activation of the installation logging.
   * `/qn` — "silent" installation without graphic interface mapping.

%spoiler%Параметры_loginom in the form of `КЛЮЧ=значение`%spoiler%

| Key | Default value | Description |
|:--------- |:-------------|:------------- |
| ADDLOCAL | `Server,Studio,Help,Webserver` | List of the installed components |
| INSTALLDIR | `%ProgramFiles%\BaseGroup` | Installation directory |
| SERVER_WS_PORT | `8080` | The websocket port of the Loginom server |
| SERVER_WSS_PORT | `8443` | The websocket secure port of the Loginom server |
| SERVER_PORT | `4580` | The Loginom server port |
| SERVER_USE_SSL | `0` | Use encryption for websocket (`0,1`) |
| SERVER_KEY_PATH | | Path to the SSL key |
| SERVER_CRT_PATH | | Path to the SSL certificate |
| WEBSRV_PORT | `80` | Web server HTTP port |
| WEBSRV_PORT_SSL | `443` | Web server HTTPS port |
| WEBSRV_USE_SSL | `0` | Use encryption (https) (`0,1`) |
| WEBSRV_KEY_PATH | | Path to the SSL key |
| WEBSRV_CRT_PATH | | Path to the SSL certificate |
| WEBAPP_URI | `app/` | URI of the Loginom Studio web interface |
| WEBSRV_USE_WS_PROXY | `0` | Use websocket proxy (`0,1`) |
| WEBSRV_PROXY_URI | `ws/` | URI websocket proxy |

%/spoiler%

%spoiler%Examples%spoiler%

```cmd
:: "silent" installation of Loginom without web server
msiexec /i ".\LoginomEnterprise.msi" /qn ADDLOCAL=Server,Studio,Help

:: "silent" installation with non-standard ports
msiexec /i ".\LoginomEnterprise.msi" /qn WEBSRV_PORT=9080 SERVER_WS_PORT=9081 SERVER_PORT=9082

:: "silent" installation with SSL activation for websocket
msiexec /i ".\LoginomEnterprise.msi" /qn SERVER_USE_SSL=1 SERVER_KEY_PATH="%ALLUSERSPROFILE%\ssl.key" SERVER_CRT_PATH="%ALLUSERSPROFILE%\ssl.crt"

```

%/spoiler%


## Licenses

To launch the **LoginomServer** service it is required to configure the licensing keys (см. [Licensing Keys](../licenses/README.md)).

To use the server network keys it is required to create the [GnClient.ini](https://dev.guardant.ru/pages/viewpage.action?pageId=1277980) file in the `"C:\ProgramData\BaseGroup\Loginom 6\Server"` directory

## Launch of Services

LoginomServer and LoginomHttpd services are not launched in the installation process automatically.

When installing the product in the "Start" Windows menu (`All programs\Loginom 6\Server`) the **"The Loginom server launch"** and **"Web server launch" shortcuts are added**.

To launch the services using the shortcut it is required to select the **"Launch as administrator"** item in the context menu. In the case of the successful launch the following text will appear in the console window: `The "LoginomServer" service was successfully launched`.

To launch the services by means if the command line it is required to run the following commands as administrator:

* The "LoginomServer" service launch: `net start loginom`
* The "LoginomHttpd" service launch: `net start httpd_loginom`

## Firewall

The host with the Loginom server must allow for connections:

* Incoming to the TCP port `8080|8443` (websocket) for the client hosts (browsers)
   * using websocket proxy — only for the web server host.
* Incoming to the  TCP port `4580` for hosts with **Loginom Intergator** or **BatchLauncher**.
* Using the network Guardant keys — to TCP/UDP ports `3186` and `3187` server host of the network keys.

The host with the web server must allow for connections:

* To the TCP port `80|443` (http(s)) for the client hosts (browsers)

Make sure that the installed antivirus software and network firewalls allow for such connections.

%spoiler%Примеры настройки Windows Firewal:%spoiler%

* Connections to the http web server port are allowed

```cmd
netsh advfirewall firewall add rule name="Allow HTTP" dir=in action=allow protocol=TCP localport=80
```

* Connections to Loginom Server websocket are allowed

```cmd
netsh advfirewall firewall add rule name="Allow Loginom WebSocket" dir=in action=allow protocol=TCP localport=8080
```

* Connections to Loginom Server for Integrator are allowed

```cmd
netsh advfirewall firewall add rule name="Allow Loginom Port" dir=in action=allow protocol=TCP localport=4850 remoteip=%lgi_host_ip%
```

* Connections to the network keys server for Loginom Server are allowed

```cmd
netsh advfirewall firewall add rule name="Allow Guardant Net" dir=out action=allow protocol=TCP remoteport=3186-3187 remoteip=%guardant_net_host_ip%
```

%/spoiler%


## Accounts

When Loginom Server installing, the following user accounts are created:

* `user` with blank password — for work with the Loginom workflows
* `admin` with the `admin` password — for the Loginom server administration
* `service` with the `service` password — for connection of the external applications (Integrator and BatchLauncher)

> **Note:** Upon installation it is required to change the administrator account (admin) password.


## Function Test

* Launch the Loginom Studio web client
   * using the `All programs\Loginom 6\Studio\Loginom Studio` shortcut from the "Start" Windows menu,
   * or in the browser (Chrome is recommended) using the following URL: `http://localhost/app/`. If the port was changed in the web server settings, the following URL is used: `http://localhost:<HTTP port>/app/`
* Log in as `user` with blank password.
