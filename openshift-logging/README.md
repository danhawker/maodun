# OpenShift Logging

This directory contains kustomize definitions for the installation of OpenShift Logging.

Logging is deployed using two operators, the ElasticSearch Operator and the OpenShift Logging Operator. Within this directory, there are kustomize definitions for the installation of the two Operators and the installation of the ClusterLogging CR, which is then used by the operator to deploy all Logging resources.


## Install the ElasticSearch Operator using the `oc` CLI
An overlay is provided to to deploy the latest stable  ElasticSearch Operator version (currently 5.3)

```
$ oc create -k elasticsearch-operator/overlays/stable
```

## Install the OpenShift Logging Operator using the `oc` CLI
An overlay is provided to to deploy the latest stable Logging Operator version (currently 5.3)

```
$ oc create -k logging-operator/overlays/stable
```

Verify the two Operators have been deployed successfully. You should see output similar to the below.

```
$ oc get csv -n openshift-logging
NAME                               DISPLAY                            VERSION    REPLACES                           PHASE
cluster-logging.5.3.0-55           Red Hat OpenShift Logging          5.3.0-55                                      Succeeded
elasticsearch-operator.5.3.0-67    OpenShift Elasticsearch Operator   5.3.0-67                                      Succeeded
```

## Install the ClusterLogging Custom Resource using the `oc` CLI

An overlay is provided to to deploy the ClusterLogging CR, using a previously installed ODF Block StorageClass based on Ceph RBD, `ocs-storagecluster-ceph-rbd`. All Logging resources will be deployed.

```
$ oc create -k logging-instance/overlays/default-odf
```

Be aware this step may take a few minutes to complete installation, deployment and setup.

Verify that Logging has been successfully deployed by navigating to the ElasticSearch homepage.
