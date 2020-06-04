# Обновление Loginom Integrator

## Graphic Interface

Для обновления Loginom Integrator необходимо запустить инсталлятор новой версии:

![](../images/integrator_msi_upgrade.png)

Нажатие на кнопку **"Обновить"** выполняет обновление установленного экземпляра Loginom Integrator.

Pressing the **"Reinstall"** button will open a new product [installation](./setup.md) dialog. The earlier version will be removed without saved parameters.

## Command Line

Upgrade is possible using the command line and specifying the `DOUPGRADE=1` key:

```cmd
msiexec /i "LoginomIntegrator.msi" /qn DOUPGRADE=1
```
