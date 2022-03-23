# Maodun

> Immovable Object or Unstoppable Force?

Deploying a consistent set of baseline configuration and apps to a raw OpenShift Cluster can feel like an immovable object, with much to consider and many different options available to configure and deploy.

Maodun aims to be the unstoppable force, providing a set of Day Zero guides and general application recommendations for the deployment of baseline OpenShift 4 clusters, using GitOps machanisms.

Maodun is constructed as a suite of Kustomize defined Kubernetes resources which describe the baseline tools and applications initialy deployed to an OpenShift cluster. Each tool or application can be deployed either manually using the usual `kubectl` or `oc` command-line tools or automagically using a GitOps workflow, for example by using ArgoCD.

Below is a table of currently available apps. Additional information about each app and its capability is described in the individual directories.

| Name | Description | Subdir |
| ----------- | ----------- | ----------- |
| OpenShift Data Foundation | Installs the ODF Operator and deploys StorageCluster Services | openshift-storage |
| OpenShift Logging | Installs the Logging Operator and deploys all Logging Services | openshift-logging |
