# Activation of Software SP Dongle

The following conditions are required for the successful dongle activation:

* Installed Guardant driver, version 6.0 or higher.
* GuardantActivationWizard.exe utility supplied with SP dongle.
* Programed template of Guardant SP dongle (*.grdvd file).
* Serial number of the following type: `9XZrwR-XXXXX-7NGDyS-XXXXX-qZGBcW-XXXXX-XoLBXF-xwqwXv-8oEO0o-XXXXX`.
* It is required to provide access to the activation server for the computer used for activation at the following address: `https://sp.guardant.ru` in the process of the dongle initialization.

> **Important**: Guardant SP is distinguished by the cryptographic binding to the equipment, namely it is not possible to use the activated dongle on the other computer.

To activate Guardant SP dongle, it is required to run GuardantActivationWizard.exe  activation wizard and to follow its instructions:

**1.** Using the "Specify the license file" button, select the path to *.grdvd file. Check the Internet connections settings and press the "Next" button:

![](../images/guardant-sp-activate-1.png)

**2.** Enter the serial number in the entry field for activation. Press "Next":

![](../images/guardant-sp-activate-2.png)

The wizard will perform the required exchange of information with the dongle driver and activation server. In this respect, among other issues, the entered serial number is checked, and superencryption of the software dongle file is performed using contol values of the computer components.

**3.** If activation is a success, the wizard shows the final dialog window:

![](../images/guardant-sp-activate-3.png)