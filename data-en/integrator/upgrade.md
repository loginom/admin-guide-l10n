# Loginom Integrator Upgrade

## Graphic Interface

To upgrade Loginom Integrator, it is required to run the installer (new version):

![](../images/integrator_msi_upgrade.png)

Pressing the **"Upgrade"** button will enable the upgrade of the installed Loginom Integrator.

Pressing the **"Reinstall"** button will open a new product [installation](./setup.md) dialog. The earlier version will be removed without saved parameters.

## Command Line

Upgrade is possible using the command line and specifying the `DOUPGRADE=1` key:

```cmd
msiexec /i "LoginomIntegrator.msi" /qn DOUPGRADE=1
```
