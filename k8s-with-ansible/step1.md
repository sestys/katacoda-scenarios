
A K8s cluster is included in our environment, we just need to initialize it. For this tutorial, we will use _Minikube_, a tool for local development for K8s, that runs a single-node K8s cluster. It provides the same interface as full K8s cluster.

First, run `minikube start --wait=false`{{execute}} to start the cluster and wait till the K8s cluster is up and running. This could take a while! Take a break and grab a coffee.

<iframe src="https://giphy.com/embed/RMhbmeqWeOBQIiQkS4" width="200"  frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

After the previous command has finished, run `kubectl get nodes`{{execute}} and wait till the `STATUS` is `Ready`. This could also take a while. Run the command several times until it is ready.

<iframe src="https://giphy.com/embed/hGTtqRheOj7KU" width="200"  frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

Kubectl is a K8s command line tool and can be used to communicate with the cluster. Get information about the nodes with `kubectl cluster-info`{{execute}}. The ip-address of the nodes in the cluster will be shown.
