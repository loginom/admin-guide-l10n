# Description of the Configuration Parameters

## Parameters of the General Settings

To display the *Adapter* general settings it is required to select the `Settings` item in the navigation tree (refer to  Figure 4).

![Figure 4. The general settings](./images/general_settings.png)

The general settings are represented by the following parameters:

* **Folder for logs** — path to the folder for the *Adapter* log files. If a parameter is not set, the logs are not saved. It is possible to select a path by clicking the button. When selecting this parameter it is required to take into account that the user must be entitled to read and write to the folder for log files.
* **Log request** — the flag that shows that it is required to save xml request to the *Adapter* in the log. It is possible to set the `true` or `false` values for this parameter.
* **Log response** — the flag that shows that it is required to save the *Adapter* xml responses in the log. It is possible to set the `true` or `false` values for this parameter.
* **Debug mode** — the flag that shows that it is required to show the debugging information in case of errors during the *Adapter* usage. This information is shown while requesting WSDL service. It is possible to set the `true` or `false` values for this parameter. At the configuration stage it is recommended to enable the debug mode and logging of requests and responses. It will enable you to get the detailed information to resolve possible configuration problems.
* **Max. size of the incoming message ** — maximum allowed size of the incoming xml message in bytes (by default - 10 MB).

## Setting parameters of connection to the external services

To display the settings of connection to the external service, it is required to select the corresponding item in the navigation tree (refer to  Figure 5).

![Figure 5. Settings of connection to one of the external services](./images/connection_settings.png)

The list of (conent of the *Key* column) parameters is the same for connections to all services, and it includes the following parameters:

* **The Web service name** — the unique Web service name. The parameter value is used as a part of names (name) of elements and attributes in WSDL description of the *Adapter* Web service. In this regard, the parameter value is subject to the rules of naming of XML elements in accordance with [W3C specification](https://www.w3.org/TR/2008/REC-xml-20081126/#NT-Name). The required parameter.
* **The Web service description** — an arbitrary description of the Web service. The optional parameter.
* **Timeout** — maximum allowed time expressed in seconds between a request and response on completion of the request processing. The optional parameter.
* **URL for the request sending** — the Web service address for requests sending.
* **The certificate path** — when using encryption, it is required to specify the path to the client certificate.

> **Note**: specifying the certificate path it is allowed to use both absolute (including the drive letter) and relative paths. In the latter case the path is specified to the folder in which `Web.config` file is located.

* **The certificate password** — a password is required for operations with some certificates.
* **The certificate store** — one of three values can be taken: `none`, `currentUser`, `localMachine`. If the client certificate has a private key, it is placed into one of the certificate stores - in the local machine store (*localMachine*) or the current user store (*currentUser*). The certificates without a private key can be placed into a separate file in the file system location specified in the *certificate Path* parameter. `none` value is specified for such certificates in *Certificate store* parameter.

> **Note**: when the client certificate is in the store, DER-encoded `X.509` export from the store to `.CER` file and specification of path to such file in *Certificate path* parameter are obligatory. Otherwise, the *Adapter* will not be able to refer to the client certificate located in the store (also refer to   [Certificates operation](./work-with-certificates.md) section).

* **Message format** — can take one of three values: `plainXml`, `soap`, `soap12`. The value depends on the Web service to which you are connecting. The value of `plainXml` parameter enables to assign the mode of the external service operation as REST service. The values of `soap`, `soap12` parameter enable to assign the mode of the external service operation as SOAP service in Specifications 1.1 and 1.2 correspondingly.
* **To transfer the address in SOAP message header ** — the flag that shows that it is required to transfer the address in the header (*Header* sections) of SOAP message. It is required to place the flag for the Web services in WSDL description of which `UsingAddressing` policy is specified.
* **The special message format** — it is used for the Web services with nonstandard message format, in particular, for credit reference bureau "UNITED CREDIT BUREAU". It can take the following values: `default`, `experianEncoding`. The optional parameter.
* **The incoming message header** — it is used for credit reference bureau "UNITED CREDIT BUREAU". Such header can include the additional information (e.g., user name, password, etc.).
* **Message encoding** — the message encoding applied by the external service is specified. It can take the following values: `utf-8`, `windows-1251`.  `utf-8` is used by default.
* **targetNamespace в WSDL** — the value is taken from the similarly-named attribute of WSDL description of the external service. It is used only for SOAP services.
* **The schema referenced by the service description ** — it specifies the path to XSD schema of the service description. The schema describes the structure of XML messages of requests and responses of the *Adapter* Web service and participates in generation of WSDL service description. XSD schema can contain references to the associated XSD schemas. The required parameter.
* **ContentType for transfer in the header** — the value of this parameter is transferred in the `Content-Type` header of the message package to the external service. It is used in the process of work with credit reference bureau "UNITED CREDIT BUREAU".

## Setting parameters of methods of interaction with the external services.

To display the settings of methods of interaction with the external service, it is required to select the corresponding item in the settings tree. (refer to  Figure 6).

![Figure 6. Settings of method of interaction with the external service](./images/method-settings.png)

These settings include the following parameters:

* **Method name** — if *Method name in Loginom Adapter* parameter is not specified, the parameter value is used as a part of names (name) of elements and attributes in WSDL description of the *Adapter* Web service.  In this regard, the parameter value is subject to the rules of naming of XML elements in accordance with [specification W3C](https://www.w3.org/TR/2008/REC-xml-20081126/#NT-Name). The required parameter.
* **Method name in Loginom Adapter** — it is used to form the element names in WSDL description of the Web service in case of coincidence of values of *Method name* parameter for different configuration methods of the *Adapter*. If this parameter is left empty, to form the element names in WSDL *Method name* parameter is used. As the parameter is used as a part of names (name) of elements and attributes of WSDL description, the parameter value is subject to the naming rules of XML elements in accordance with [W3C specification](https://www.w3.org/TR/2008/REC-xml-20081126/#NT-Name). The optional parameter.
* **Method description** — arbitrary method description. The optional parameter.
* **URL for the request sending** — the Web service address for requests sending. The required parameter.
* **SOAPAction for transfer in the header** — value of this parameter is transferred in the header `SOAPAction` HTTP/HTTPS package transferred to the external service. It defines the called method of the external SOAP service. This parameter must contain the method name taken from wsdl description of SOAP service. The parameter is specified in accordance with the requirements to the corresponding web service settings.
* **Certificate signed XML message ** — takes the `true`, `false` values. In case of the `true` value the algorithm of the response transformation of credit reference bureau "UNITED CREDIT BUREAU" in which the certifcate signature is removed from XML service response is applied. The parameter null value is equal to `false`.
* **The root element name of SOAP request**, **Namespace of the root element of SOAP request** — values of these parameters are taken from XSD schema of the request description.
* **The root element name of SOAP response**, **Namespace of the root element of SOAP response** — values of these parameters are taken from XSD schema of the request description.

> **Note**: path to XSD schema is specified in the parameter *The schema to which the service description will refer to*.

* **The request file source name**, **The resulting name of the request file**, **The request file processing command** — these parameters are used to assign the OS (operational system) command of the preliminary processing of the request text prior to its sending to the external service.  The detailed information on the parameters application is provided in section [Configuration of the client role of the external services](./tuning-principles.md#nastroyka-roli-klienta-vneshnikh-servisov). The command example:

```
"C:\Program Files\7-Zip\7z" a -tzip "%outputFile%" "%inputFile%"

// templates %inputFile% and %outputFile% are replaced with the parameters values while the command execution
// "The request file source name" and "The resulting name of the request file", correspondingly.
```

* **The response file source name**, **The resulting name of the response file**, **The response processing command** — these parameters are used to assign the OS command of the service response text processing. The parameters application is similar to the request processing command and it is described in the section [Configuration of the client role of the external services](./tuning-principles.md#nastroyka-roli-klienta-vneshnikh-servisov). The command example:

```
"C:\Program Files\7-Zip\7z" e "%inputFile%" -so > "%outputFile%"

// templates %inputFile% and %outputFile% are replaced with the parameters values while the command execution
// "The response file source name" and "The resulting name of the response file", correspondingly.
```

* **XSLT for the incoming message transformation before its transfer** — the path to corresponding files of xslt transformations is specified.
* **XSLT for the response message transformation** — the path to corresponding files of xslt transformations is specified.
* **Parameters of XSLT transformation** are specified only if xslt transformations accept the input parameters. The detailed information on application and configuration of this parameter is provided in section [Configuration of the client role of the external services](./tuning-principles.md#nastroyka-roli-klienta-vneshnikh-servisov).
