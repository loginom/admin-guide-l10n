# Loginom in Yandex.Cloud

<p><iframe allowfullscreen="" frameborder="0" height="472" src="https://www.youtube.com/embed/rOYXRR-Lzow" width="835"></iframe></p>


Access to the analytical platform is provided by resources of the Yandex Compute Cloud service. The service enables usage of virtual machines in Yandex.Cloud infrastructure for operation on the Loginom platform. Depending on the complexity of computations, it is possible to define the required number of cores, storage capacity, size and amount of discs and accessibility zone of the virtual machine. As appropriate, these parameters can be changed without a system reinstallation.

[Loginom Platform in Yandex.Cloud](https://cloud.yandex.ru/marketplace/products/f2esjn14f4ekcb53igdt)

## Start Operation

Upon deployment and start of the virtual machine in Yandex.Cloud, it is required to perform the following actions:

1. Go to the remote desktop using RDP protocol

2. Open `ReadMe.txt` file (the shortcut is on the desktop). The file contains the following information:

* Loginom Web Admin Password: "admin" user password – administrator of Loginom web application
* Password for system user .\loginom: password of the Windows OS user, on whose behalf Loginom Server services and web servers are started and used

If Loginom Studio start failed, it is required to use the [manual](https://help.loginom.ru/adminguide/server/setup.html#zapusk-sluzhb) and check availability of the started services.
`Web server start` and `Loginom server start` shortcuts (on the desktop) enable start of the services required for Loginom Studio operation.

## Operational Continuity

There are additional shortcuts on the desktop in RDP session:

1. `GuardantActivationWizard` shortcut is an application for activation of the software SP dongle for Loginom software, [manual](https://help.loginom.ru/adminguide/licenses/sp-activate.html) concerning the activation process is in the "Activation of SP dongles" file.
   https://help.loginom.ru/adminguide/licenses/sp-activate.html

2. `Set admin password` shortcut runs script of the forced setting and upgrading of the user `admin` password. A new password can be required, for example, in the case of current password loss.

3. `Loginom Studio` shortcut enables opening of the page with Loginom Studio web application. Google Сhrome is the recommended browser.

> Attention: The Loginom version located in the software image has a limited period of effect, and you will need to request a licence renewal for effective operational continuity of the software by sending an e-mail to the following address: help@loginom.ru.

## Additional Support

All technical support concerning deployment, startup and usage issues is available by emailing the relevant enquiry to the following address: help@loginom.ru.

