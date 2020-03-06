# Introduction

This guide will give an overview of important information related to the *Nessus* container image.

## How to Deploy to Kubernetes

```shell
kubectl create -f manifest-nessus.yaml
```

### How to Authenticate an Offline Installation
*Full documentation for this can be found [HERE](https://docs.tenable.com/nessus/Content/InstallNessusOffline.htm).*

Offline Nessus Server (A) & Online Computer (B)
1.	SSH tunnel into the Offline instance of Nessus (A)
2.	On the registration page, select the Offline box. Once selected the page displays a unique Challenge code
3.	On an Online Computer (B) go to plugins.nessus.org/v2/offline.php and enter in the Challenge Code and your Activation code and choose Submit
4.	Once submitted, it will display the following elements:
**a.**	Custom URL: The custom URL displayed downloads a compressed plugins file. This file is used by Nessus to obtain plugin information. This URL is specific to your Nessus license and must be saved and used each time plugins need to be updated.
**b.**	License: The complete text-string starting with **-----BEGIN Tenable, Inc. LICENSE-----** and ends with **-----END Tenable, Inc. LICENSE-----** is your Nessus product license information. Tenable uses this text-string to confirm your product license and registration.
**c.**	nessus.license file: At the bottom of the web page, there is an embedded file that includes the license text-string.
5.	While still on the Online Computer (B), select the on-screen custom URL. A compressed TAR file will download .Copy this compressed tar file to the Nessus Offline Server (A) in the /opt/nessus/sbin/ location
6.	Copy the license text-strong starting with **----- BEGIN Tenable, Inc. LICENSE-----** and ends with **----- END Tenable, Inc. LICENSE -----** from the Online Computer (B) and paste to the Offline Nessus Server (A) on the Nessus product registration screen.
7.	Press Continue and Nessus will finish the installation process and it could take several minutes. 

## Additional Documentation
- Documentation - <https://docs.tenable.com/nessus/Content/GettingStarted.htm>
- Running non-root - <https://docs.tenable.com/nessus/Content/NessusNonPrivilegedLinuxSystemd.htm>