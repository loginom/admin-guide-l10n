# Configuration

The Loginom Server configuration files are in the working directory. The default location of the working directory is `%AllUsersProfile%\BaseGroup\Loginom 6\Server`.

## Server General Settings

The server general settings are kept in the XML `Settings.cfg` file.

The directory parameters are set in the attributes of the `Settings/Directories` element:

* **UserStorage** - location of the user directories. The value can be a full or relative path (from the working directory).
* **SessionBackup** - location of the backup session copies directory. The value can be a full or relative path (from the working directory).

Bindings parameters are set in the attributes of the `Settings/Bindings` element:

* **Bind** - the IP address of the network interface used by the Loginom server.
   * Default value: `0.0.0.0`.
* **Port** - port number for the Loginom Integrator and the BatchLauncher connection.
   * Default value: `4580`.
* **WSPort** - port number for the Loginom Studio connection according to the websocket (ws) protocol.
   * Default value: `8080`.
* **WSSPort** - port number for the Loginom Studio connection according to the websocket secure (wss) protocol.
* **SSLCertificateFile** - a full or relative path (from the working directory) to the SSL certificate file in the *pem* format.
* **SSLPrivateKeyFile** - a full or relative path (from the working directory) to the SSL key file in the *pem* format.

## Logging

Logging parameters are kept in the XML `Logs.cfg` file.

The log files are kept in the `Logs` subdirectory of the working directory.

The general settings are set in the attributes of the `Logging/Common` element:

* **MinLogLevel** - the minimum logging level. Possible values:
   * **llTrace** - trace.
   * **llDebug** - debug.
   * **llInfo** - info. Default value.
   * **llHint** - event.
   * **llWarn** - warning.
   * **llError** - error.
   * **llFatal** - fatal.

Parameters of the logging files are set in the attributes of the `Logging/File` element:

* **LogFileName** - the log file name. By default `app.log`.
* **LogFileRewrite** - if the attribute has been set, the log file will be rewritten while the Loginom Server is starting. Disabled by default.
* **LogFileMaxSize** - the maximum size of the log file in bytes. By default, 10485760 (10 Mb).
* **LogFileMaxIndex** - the maximum number of the log files. By default, 10.
