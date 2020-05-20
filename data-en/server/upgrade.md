# Loginom Server Upgrade

**1.** It is required to stop the `loginom` service.

**2.** Loginom installer (new version) is started:

![](..\images\server_msi_upgrade.png)

* Pressing the **"Upgrade"** button will enable to upgrade the installed Loginom product.
* Pressing the **"Reinstall"** button will open the new product [installation](./setup.md) dialog. The earlier version will be removed without saved parameters.

**3.** After the upgrade it is required to start the`loginom` service

## Command Line

Upgrade is possible using the command line and specifying the `DOUPGRADE=1` key:

```cmd
net stop loginom
msiexec /i "LoginomEnterprise.msi" /qn DOUPGRADE=1
net start loginom
```
