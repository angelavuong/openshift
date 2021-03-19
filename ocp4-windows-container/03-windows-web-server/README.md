# Sample Windows Web Server App
In this demo, we will deploy a simple Windows Web Server on Openshift.

## Pre-requisites
In order to do this demo, we assume that:
```
1) Running OCP 4.6+
1) Appropriate networking has been configured for OCP to support Windows Containers (OVN Hybrid)
2) The Windows Machine Config Operator has already been installed via Operator Hub
```

### To access the Windows node:
Locate the Windows node:
```
$ oc get nodes -o wide
```

SSH into the Windows Machine Config Operator to access the Windows node:
```
$ oc get pods -n openshift-windows-machine-config-operator
$ oc rsh -n openshift-windows-machine-config-operator winc-ssh-XXXXX
sh-4.4$
```

Using sshcmd.sh to login to the Windows node:
```
$ sshcmd.sh <name-of-windows-node>
PS C:\Users\Administrator>
```

Install the Windows Server 2019 image via docker:
```
> docker images
> docker pull mcr.microsoft.com/windows/servercore:ltsc2019
> docker images
> exit
> $ exit
```

### Build Windows Server 2019 container using OCP


