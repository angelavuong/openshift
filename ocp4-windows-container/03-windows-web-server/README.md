# Sample Windows Web Server App
In this demo, we will deploy a simple Windows Web Server on Openshift. We will utilize docker to obtain the Windows Server 2019 container image before deploying the application on OCP.

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

For the app configuration, we will deploy using ```win-webserver-deployment.yaml``` and ```win-webserver-service.yaml```.

Create the Windows Web Server using the YAML files: 
```
$ oc create -n default -f win-webserver-service.yaml
$ oc create -n default -f win-webserver-deployment.yaml
```

Verify a pod was created and deployed on the Windows node:
```
$ oc get pods -n default -o wide 
```

Although the app is deployed, it's not reachable externally without a route. Create a route by exposing the service in OCP:
```
$ oc get services -n default
$ oc expose svc/win-webserver 
$ oc get routes -n default
```

Verify you can reach the external URL provided by OCP to win-webserver: 
```
$ curl -s <host-route>
```

