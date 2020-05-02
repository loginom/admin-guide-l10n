# Loginom Adapter Deinstallation

It is possible to deinstall Loginom Adapter in several ways:

* To deinstall the application from the "Applications and components" window in Windows
* To launch the product installer having pressed the **"Deinstall"** button
* To execute the following command in the command line as the administrator:

   ```cmd
   msiexec /x LoginomAdapter.msi /qn
   ```

Then it is required to delete in *IIS service manager* the earlier located *Loginom Adapter* site that is located by default in the `sites` -> `Default Web Site` group. It is also required to delete the application pool created specially for the *Adapter*.
