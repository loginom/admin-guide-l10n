# Loginom Desktop Installation

The installer file name versions:

* LoginomPersonal_6.x.x_x64.msi — installer for the 64-bit Personal edition
* LoginomPersonal_6.x.x_x86.msi — installer for the 32-bit Personal edition
* LoginomAcademic_6.x.x.msi — installer for the Academic edition

where 6.x.x – figures denoting software version and release.

## MSI Installation

### Graphic Interface

#### Run the Installer

It is required to click the  **Custom** button for installation with non-standard parameters in the **Installation type** dialog.

#### Selection of Components for Installation

![](../images/personal_msi_features_default.png)

* The **"Loginom Personal"** component is compulsory for installation.
* The **"Documentation"** component enables the installation of document files for the platform operation.

All components are installed by default.

### Command Line

```cmd
msiexec /i "LoginomPersonal_6.x.x_x64.msi" ключи_msi
```

* `msi_options` — it is possible to find allowable values executing the following command in the command line: `msiexec /?`. The following commands can be especially useful:
   * `/l* "%TEMP%\loginom.msi.log"` — activation of installation logging.
   * `/qn` — "silent" installation without graphic interface mapping.

## Licenses

To start the **Loginom Desktop** it is required to configure the licensing keys (refer to  [Licensing Dongles](../licenses/README.md)).

To use network dongles server, it is required to create the [GnClient.ini](https://dev.guardant.ru/pages/viewpage.action?pageId=1277980) file in the `"C:\ProgramData\BaseGroup\Loginom 6\Personal"` directory
