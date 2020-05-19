# Remove Loginom Server

To remove Loginom Server it is required to stop the *loginom* service and remove the application using one of the following methods:

* Use the "Programs and Components" window in Windows
* Launch the product installer, pressing the**"Remove"** button

![](../images/server_msi_remove.png)

* To execute the following command in the command line as the administrator:

```cmd
msiexec /x Loginom<Редакця>_6.x.x.msi /qn
```
