# The work with certificates

Procedure of the certificate receipt and usage for each external web service (for example, CRB) is described in the documents provided by the service provider of the corresponding web service.

The certificates used for the *Adapter* operation can be kept using the following path:

- path in the file system specified to the *Certificate path* parameter. It is recommended to use such method for the certificates that do not contain the private key.
- In the certificate store.

When using the store, it is required to meet the following conditions:

- The certificate store must be available for the user who operates the *Adapter* application pool in IIS.

> **For reference**: the certificate store of the *local computer* is available for all users. It can be edited in the following snap-in: `Certificates - the local computer`, and it can be activated using the `mmc certlm.msc` command. The *user* store is available only for a particular user. It can be edited in the following snap-in: `Certificates – the current user`, and it can be activated using the `mmc certmgr.msc` command.

- It is required to export the certificate from the store to the `.CER` file in the DER coding `X.509` without the private key, but in the *Adapter* settings parameter – the *Certificate path* - a path to this file is specified.  This file serves as a reference to the store certificate for the *Adapter*. While updating the store certificate, it is required to export the new certificate from the store once again and to update the path in the *Certificate path* parameter.