# Uninstalling Loginom Adapter

Loginom Adapter can be uninstalled in several ways:

* Uninstall the application from the "Programs and Features" window in Windows
* To run the product installer having pressed the **"Uninstall"** button
* Execute the following command in the command line as an administrator:

   ```cmd
   msiexec /x LoginomAdapter.msi /qn
   ```

Then it is required to delete in *IIS service manager*; the earlier located *Loginom Adapter* site that is located by default in the `sites` -> `Default Web Site` group. It is also required to delete the application pool created specially for the *Adapter*.
