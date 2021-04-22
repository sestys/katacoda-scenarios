## Initialize a Kubernetes (K8s) cluster

A K8s cluster is included in the backend and needs to be initialized. Run `minkube start`{{execute}} to start the cluster and wait till the K8s cluster is up and running. This could take a while! Take a break and grab a coffee.

<iframe src="https://giphy.com/embed/RMhbmeqWeOBQIiQkS4" width="480" height="360" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

When it has executed, run `kubectl get nodes`{{execute}} and wait till the `STATUS` is `Ready`.

<iframe src="https://giphy.com/embed/hGTtqRheOj7KU" width="480" height="354" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

Kubectl is a K8s command line tool and can be used to communicate with the cluster. Get information about the nodes with `kubectl cluster-info`{{execute}}. The ip-address of the nodes in the cluster will be shown.
