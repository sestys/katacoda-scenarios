## Initialize a Kubernetes (K8s) cluster

A K8s cluster is included in the backend and needs to be initialized. Run `launch.sh`{{execute}} and wait till K8s cluster is up and running.

Check the K8s nodes by running `kubectl get nodes`{{execute}}. This will list all nodes present in the cluster.

Get information about the nodes with `kubectl cluster-info`{{execute}}. The ip-address of the nodes in the cluster will be shown.
