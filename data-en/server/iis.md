# IIS Web Server

> IIS 8.5 Instructions

## Enable IIS Components

In the command line running as an administrator:

```cmd
dism /online /enable-feature /FeatureName:IIS-WebServerRole /FeatureName:IIS-WebServer /FeatureName:IIS-WebServerManagementTools /FeatureName:IIS-ManagementScriptingTools
```

## Enable IIS Components for the Loginom Studio

In the command line running as an administrator:

```cmd
dism /online /enable-feature /FeatureName:IIS-CommonHttpFeatures /FeatureName:IIS-StaticContent /FeatureName:IIS-DefaultDocument /FeatureName:IIS-Performance /FeatureName:IIS-HttpCompressionStatic
```

### Web.config

It is required to place the `web.config` file with the following content into the `Loginom 6\Client` directory:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <httpProtocol>
            <customHeaders>
                <remove name="Cache-Control" />
                <add name="Cache-Control" value="no-cache,must-revalidate" />
            </customHeaders>
        </httpProtocol>
        <staticContent>
            <remove fileExtension=".json" />
            <mimeMap fileExtension=".json" mimeType="application/json" />
            <remove fileExtension=".woff" />
            <mimeMap fileExtension=".woff" mimeType="application/font-woff" />
            <remove fileExtension=".woff2" />
            <mimeMap fileExtension=".woff2" mimeType="application/font-woff2" />
        </staticContent>
    </system.webServer>
</configuration>
```

### Installation of the Rewrite Module

> The module is required for the Loginom Studio operation in Internet Explorer v11+ / Edge browsers. It is also required for wsproxy usage.

* It is required to download and install the [URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite) module.
* It is to be added to `web.config`:

```xml
<system.webServer>
...
    <rewrite>
        <rules>
            <rule name="ie">
                <match url="^bg/(.+)\.js$" />
                <conditions logicalGrouping="MatchAny">
                    <add input="{HTTP_USER_AGENT}" pattern="(MSIE|Trident)" />
                </conditions>
                <action type="Rewrite" url="bg-ie/{R:1}.js" appendQueryString="false" />
            </rule>
        </rules>
    </rewrite>
</system.webServer>
```

### WebSocket Proxy Configuring

* It is required to download and install the [ARR3.0](https://www.iis.net/downloads/microsoft/application-request-routing#additionalDownloads) module.
* It is required to download and install the [URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite) module.
* The WebSockets component is enabled:

```cmd
dism /online /enable-feature /FeatureName:IIS-WebSockets
```

* IIS is restarted

```cmd
%windir%\system32\iisreset.exe
```

* The proxy function is enabled in ARR:

```cmd
%windir%\system32\inetsrv\appcmd set config -section:system.webServer/proxy /enabled:"True"
```

* The `web.config` file with the following content is added to the site root directory:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="websocket_proxy" patternSyntax="ECMAScript" stopProcessing="false">
                    <match url="ws/" />
                    <conditions logicalGrouping="MatchAny" trackAllCaptures="false">
                        <add input="{CACHE_URL}" pattern="(ws|http)s?://(.*)" />
                    </conditions>
                    <action type="Rewrite" url="{C:1}://127.0.0.1:8080/" appendQueryString="false" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```

### Creation of the Virtual Directory for the Loginom Studio

The following command enables addition of the `/app` virtual directory on the `Default Web Site`:

```cmd
"%windir%\system32\inetsrv\appcmd.exe" add vdir /app.name:"Default Web Site/" / /path:/app /physicalPath:"%ProgramFiles%\BaseGroup\Loginom 6\Client"
```
