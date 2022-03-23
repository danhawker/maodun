# OpenShift Data Foundation aka OpenShift Container Storage

This directory contains kustomize definitions for the installation of OpenShift Data Foundation (ODF), what was recently called OpenShift Container Storage (OCS).

ODF is deployed using a dedicated Operator. Within this directory, there are kustomize definitions for the installation of the Operator and the installation of the OCS StorageServer CR, which is then used by the operator to deploy all Storage Services.

## Install the Operator using the `oc` CLI
An overlay is provided to to deploy the ODF Operator version 4.10

```
$ oc create -k /ocs-operator/overlays/stable-4.8
```

## Install the StorageCluster using the `oc` CLI

An overlay is provided to to deploy the ODF StorageServer CR, on vSphere. 

```
$ oc create -k ocs-cluster/overlays/stable-4.10-azure
```

