# Loginom Adapter

There are [components of integration with the SOAP and REST services](https://help.loginom.ru/userguide/integration/web-services/) in the analytical Loginom platform that implement the most wide-spread variants of interaction with the web services. But some web services, for example, CRB, use the individual protocols and data encryption which preclude from interaction using the standard Loginom means. Loginom Adapter enables to solve this problem (hereafter referred to as the *Adapter*).

The *Adapter* is an intermediate web service between the workflow executed in Loginom and the external web services. Interaction with the *Adapter* from the Loginom workflow is performed according to the standard SOAP protocol using the [Web service invocation](https://help.loginom.ru/userguide/processors/integration/calling-web-service.html) node. In return the *Adapter performs the following tasks:*:

- Transforms the SOAP request received from the Loginom workflow to the request format of the external web service;
- Sends the transformed request to the external web service;
- Receives the response of the external web service;
- Transforms the received response and returns it to the Loginom workflow in the SOAP format.

![Figure 1. Typical scheme of interaction of the system components using the Adapter](component_interaction_scheme.png)

## System Requirements

### Hardware

| Component | Minimum | Recommended |
|:--- |:---|:--- |
| Processor | Intel Core 2 Duo | Intel Xeon |
| Immediate-access store | 1 GB | 8 GB |
| Hard disk drive | 10 GB | 500 GB |
| Management | Keyboard, mouse | &nbsp; |

### Compulsory software

| Component | Minimum | Recommended |
|:--- |:---|:--- |
| Operating system | Windows 7 | Windows Server 2008 and higher |
| Microsoft IIS | Version 5.1 or higher | Версия 7.5 and higher |
| .Net Framework | Version 3.5 | &nbsp; |

> **Note**: Loginom Adapter uses .Net Framework, version 3.5 in the process of work. The evidence from application usage practice shows that compatibility with.Net Framework, version 4.5 is possible.

Availability of some IIS and .Net Framework components is required for the  *Adapter* operation. The detailed description is provided in the [Installation](.\setup\README.md) section.

### Optional software

The external cryptography service providers (Cryptography Service Provider, CSP) and Java Runtime Environment (JRE) can be used for the work with some web services. In such cases, these components must be installed with the *Adapter*.

#### Cryptography Service Provider (CSP)

Such cryptography service providers as Signal-COM CSP or CryptoPro CSP are used for data encryption in case of integration with the external web services. Selection of cryptography service provider and its version is stipulated by the support of the definite encryption algorithms required for interaction with the particular web services.

Corresponding certificates will be required for usage of these or that web service with encryption.

#### Java Runtime Environment (JRE)

Java Runtime Environment (JRE) version 6 or higher is a mandatory requirement for connection to the [National Hunter](https://bki-okb.ru/corp/services/national-hunter) and [Equifax FPS](https://www.equifax.ru) services.
