# Loginom Adapter Configuration

## Loginom Adapter Configurator

Loginom Adapter settings are in [Web.config](https://ru.wikipedia.org/wiki/Web.config) XML file edited by **Loginom Adapter Configurator** (hereafter referred to as the *Configurator*). When installing by default, the *Configurator* is in the following folder: `C:\inetpub\wwwroot\LoginomAdapter\Configurator\`.

When saving the settings, the *Configurator* rewrites `Web.config` file. The requests previously received by the *Adapter* will be completed with the old settings. Subsequent requests to the *Adapter* will be executed taking into account the new settings.

The *Configurator* interface consists of two panels. The navigation tree is on the left window panel of the *Configurator* (refer to  Figure 3). It reflects the settings structure. The settings as such are on the right panel.

![Figure 3. Settings Navigation Tree ](./images/adapter_navigation_tree.png)

The navigation tree is a two-level hierarchical structure that includes the following elements:

* The elements of the first (root) level:
   * The root element `Settings`. contains parameters of the general settings of the *Adapter* represented in the following section: [Parameters of the General Settings](./parameters.md#parametry-obschikh-nastroek).
   * The root elements denoting the external services interacted with (the configuration shown in Figure 3 includes three such elements: `DEMO`, `EquifaxFPS` , `NBCH`). contain parameters of the settings listed in the following section: [Parameters of the Settings of Connection to the External Services](./parameters.md#parametry-nastroek-podklyucheniya-k-vneshnim-servisam).
* The elements of the second level:
   * Methods of interaction with the relevant external services are represented by subordinate elements with method names (there are the following elements in Figure 3: `Value`, `processingApplicationRequest`, `deleteApplicationRequest`, etc). They contain parameters of the settings listed in the following section [Setting Parameters of Methods of Interaction with the External Services](./parameters.md#parametry-nastroek-metodov-vzaimodeystviya-s-vneshnimi-servisami).

Such structure enables *Adapter* to work with several external services and several methods can be defined for each external service.

## Additional files

Apart from the folders and files pre-installed in the installation process when configuring *Adapter* additional files (certificates, XSD-schemes, etc.) required for the work with the external services can be placed into the installation directory.

Connection settings (connectors) for such external services as, for example, [EquifaxFPS](https://www.equifax.ru), *NationalHunter*, [National Bureau of Credit Histories](https://www.nbki.ru/) (NBCH), [Bureau of Credit Histories — Associated Credit Bureau](https://bki-okb.ru) (BCH— ACB), [QiwiScoring](https://corp.qiwi.com/business/banks/scoring.action), etc. can be provided with *Adapter*. As a rule, the additional files of such settings are placed into the following subdirectories: *Data* and *Certificates* of the installation directory (by default it is `C:\inetpub\wwwroot\LoginomAdapter\`). `Web.config` file will include references to such files.

It is allowed to use both absolute paths to the additional files (stating the drive letter) and the relative paths specified according to the location of `Web.config` in `Web.config` file.

> **Note**: it is recommended to place the additional files into the folder in which *Adapter* has been installed and to specify the relative paths to them in `Web.config` configuration file. It enables to transfer *Adapter* from one computer to another just copying the folder with the minimum reconfiguration number.
