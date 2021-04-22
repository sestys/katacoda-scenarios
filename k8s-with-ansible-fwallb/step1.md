## Initialize a Kubernetes (K8s) cluster

A K8s cluster is included in the backend and needs to be initialized. Run `minkube start`{{execute}} and wait till K8s cluster is up and running. This could take a while! Grab a coffee, take a break or go for a walk.  

Kubectl is K8s command line tool and can be used to communicate with the cluster.
  * List the nodes by running `kubectl get nodes`{{execute}}.

* Get information about the nodes with `kubectl cluster-info`{{execute}}. The ip-address of the nodes in the cluster will be shown.
