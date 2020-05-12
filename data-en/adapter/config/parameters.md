# Description of the Configuration Parameters

## Parameters of the General Settings

To display the *Adapter* general settings it is required to select the `Settings` item in the navigation tree (refer to  Figure 4).

![Figure 4. The general settings](./images/general_settings.png)

The general settings are represented by the following parameters:

* **Folder for logs** — the path to the folder for the *Adapter* log files. If a parameter is not set, the logs are not saved. It is possible to select a path by clicking the button. When selecting this parameter, it is required to take into account that the user must be entitled to read and write to the folder for log files.
* **Log request** — the flag that shows that it is required to save the XML request to the *Adapter* in the log. It is possible to set `true` or `false` values for this parameter.
* **Log response** — the flag that shows that it is required to save the *Adapter* XML responses in the log. It is possible to set `true` or `false` values for this parameter.
* **Debug mode** — the flag that shows that it is required to show the debugging information in the case of errors during the *Adapter* usage. This information is shown while requesting the WSDL service. It is possible to set `true` or `false` values for this parameter. At the configuration stage, it is recommended to enable the debug mode and logging of requests and responses. It will enable you to get detailed information to resolve possible configuration problems.
* **Max. size of the incoming message ** — the maximum allowed size of the incoming XML message in bytes (by default - 10 MB).

## Setting Parameters of Connection to the External Services

To display the connection settings to the external service, it is required to select the corresponding item in the navigation tree (refer to  Figure 5).

![Figure 5. Settings of connection to one of the external services](./images/connection_settings.png)

The list of (content of the *Key* column) parameters is the same for connections to all services, and it includes the following parameters:

* **The web service name** — the unique web service name. The parameter value is used as a part of the names (name) of items and attributes in the WSDL description of the *Adapter* web service. In this regard, the parameter value is subject to the rules of naming of the XML elements under [W3C specification](https://www.w3.org/TR/2008/REC-xml-20081126/#NT-Name). The required parameter.
* **The web service description** — an arbitrary description of the web service. The optional parameter.
* **Timeout** — the maximum allowed time expressed in seconds between a request and response on completion of the request processing. The optional parameter.
* **URL for the request sending** — the web service address for requests sending.
* The **Certificate path** — when using encryption, it is required to specify the path to the client certificate.

> **Note**: specifying the certificate path, it is allowed to use both absolute (including the drive letter) and relative paths. In the latter case, the path is specified to the folder in which the `Web.config` file is located.

* **The certificate password** — a password is required for operations with some certificates.
* **The certificate store** — one of three values can be taken: `none`, `currentUser`, or `localMachine`. If the client certificate has a private key, it is placed into one of the certificate stores - into the local machine store (*localMachine*), or the current user store (*currentUser*) The certificates without a private key can be placed into a separate file in the file system location specified by the *Certificate path* parameter. `none` value is specified for such certificates in the *Certificate store* parameter.

> **Note**: when the client certificate is in the store, DER-encoded `X.509` export from the store to `.CER` file and specification of path to such file in the *Certificate path* parameter are obligatory. Otherwise, the *Adapter* will not be able to refer to the client certificate located in the store (also refer to  the [Certificates Usage](./work-with-certificates.md) section).

* **Message format** can take one of three values: `plainXml`, `soap`, or `soap12`. The value depends on the web service to which you are connecting. The value of `plainXml` parameter enables assignment of mode of the external service operation, as with the REST service. The values of `soap`, `soap12` parameter enable assignment of mode of the external service operation, as with the SOAP service in Specifications 1.1 and 1.2 correspondingly.
* **To transfer the address in the SOAP message header ** — the flag that shows that it is required to transfer the address in the header (the *Header* sections) of the SOAP message. It is required to place the flag for the web services in the WSDL description of which `UsingAddressing` policy is specified.
* **The special message format** is used for the web services with nonstandard message format, in particular, for credit reference bureau "UNITED CREDIT BUREAU". It can take the following values: `default`, and `experianEncoding`. The optional parameter.
* **The incoming message header** is used for credit reference bureau "UNITED CREDIT BUREAU". This type of header can include additional information (e.g., user name, password, etc.).
* **Message encoding** — the message encoding applied by the external service is specified. It can take the following values: `utf-8`, and/or `windows-1251`.  `utf-8` is used by default.
* **targetNamespace in WSDL** — the value is taken from the similarly-named attribute of the WSDL description of the external service. It is used only for the SOAP services.
* **The schema to which the service description will refer** — it specifies the path to the XSD schema of the service description. The schema describes the structure of the XML messages of requests and responses of the *Adapter* web service, and participates in the generation of the WSDL service description. The XSD schema can contain references to the associated XSD schemas. The required parameter.
* **ContentType for transfer in the header** — the value of this parameter is transferred in the `Content-Type` header of the message package to the external service. It is used in the process of work with credit reference bureau "UNITED CREDIT BUREAU".

## Setting Parameters of Methods of Interaction with the External Services

To display the settings of methods of interaction with the external service, it is required to select the corresponding item in the settings tree. (refer to  Figure 6).

![Figure 6. Settings of method of interaction with the external service](./images/method-settings.png)

These settings include the following parameters:

* **Method name** — if the *Method name in Loginom Adapter* parameter is not specified, the parameter value is used as a part of the names (name) of items and attributes in the WSDL description of the *Adapter* web service.  In this regard, the parameter value is subject to the rules of naming of the XML elements under [ W3C specification](https://www.w3.org/TR/2008/REC-xml-20081126/#NT-Name). The required parameter.
* **Method name in Loginom Adapter** is used to form the item names in the WSDL description of the web service in the case of coincidence of values of the *Method name* parameter for different configuration methods of the *Adapter*. If this parameter is left empty to form the item names in WSDL, the *Method name* parameter is used. As the parameter is used as a part of the names (name) of items and attributes of the WSDL description, the parameter value is subject to the naming rules of the XML elements under [W3C specification](https://www.w3.org/TR/2008/REC-xml-20081126/#NT-Name). The optional parameter.
* **Method description** — an arbitrary method description. The optional parameter.
* **URL for the request sending** — the web service address for requests sending. The required parameter.
* **SOAPAction for transfer in the header** — the value of this parameter is transferred in the `SOAPAction` header of the HTTP/HTTPS package transferred to the external service. It defines the called method of the external SOAP service. This parameter must contain the method name taken from the WSDL description of the SOAP service. The parameter is specified under the requirements to the corresponding web service settings.
* **Certificate signed XML message ** — takes `true`, or `false` values. In the case of the `true` value, the algorithm of the response transformation of credit reference bureau "UNITED CREDIT BUREAU", in which the certificate signature is removed from the XML service response is applied. The parameter null value is equal to `false`.
* **The root element name of the SOAP request**, **Namespace of the root element of the SOAP request** — values of these parameters are taken from the XSD schema of the request description.
* **The root element name of the SOAP response**, **Namespace of the root element of the SOAP response** — values of these parameters are taken from the XSD schema of the request description.

> **Note**: the path to the XSD schema is specified in the following parameter: *The schema to which the service description will refer*.

* **The request file source name**, **The resulting name of the request file**, **The request file processing command** — these parameters are used to assign the OS (operational system) command of the preliminary processing of the request text before its sending to the external service.  The detailed information on the application of the parameters is provided in the following section: [Configuration of the Client Role of the External Services](./tuning-principles.md#nastroyka-roli-klienta-vneshnikh-servisov). The command example:

```
"C:\Program Files\7-Zip\7z" a -tzip "%outputFile%" "%inputFile%"

// %inputFile% and %outputFile% templates are replaced with the parameters values
// "The request file source name" and "The resulting name of the request file", while the command is executed correspondingly.
```

* **The response file source name**, **The resulting name of the response file**, **The response processing command** — these parameters are used to assign the OS command of the service response text processing. The parameters application is similar to the request processing command, and it is described in the following section: [Configuration of the Client Role of the External Services](./tuning-principles.md#nastroyka-roli-klienta-vneshnikh-servisov). The command example:

```
"C:\Program Files\7-Zip\7z" e "%inputFile%" -so > "%outputFile%"

// %inputFile% and %outputFile% templates are replaced with the parameters values
// "The response file source name" and "The resulting name of the response file", while the command is executed correspondingly.
```

* **XSLT for the incoming message transformation before its transfer** — the path to corresponding files of the XSLT transformations is specified.
* **XSLT for the response message transformation** — the path to corresponding files of the XSLT transformations is specified.
* **Parameters of the XSLT transformation** are specified only if the XSLT transformations accept the input parameters. The detailed information on the application and configuration of this parameter is provided in the following section: [Configuration of the Client Role of the External Services](./tuning-principles.md#nastroyka-roli-klienta-vneshnikh-servisov).
