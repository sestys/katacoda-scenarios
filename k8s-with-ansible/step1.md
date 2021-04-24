
A K8s cluster is included in our environment, we just need to initialize it. For this tutorial, we will use _Minikube_, a tool for local development for K8s, that runs a single-node K8s cluster. It provides the same interface as full K8s cluster.

First, please wait for the environment to be ready. This could take a while (~1-2 minute)! Take a break and grab a coffee.

<p align="center"><iframe src="https://giphy.com/embed/RMhbmeqWeOBQIiQkS4" width="200"  frameBorder="0" class="giphy-embed" allowFullScreen></iframe></p>


If the environment is ready and you see the shell prompt ($), run `minikube start --wait=false`{{execute}} to start the cluster and wait till the K8s cluster is up and running.
This could also take a while (around another 1-2 minutes), so just chill for a bit and enjoy the day.

<iframe src="https://giphy.com/embed/hGTtqRheOj7KU" width="200"  frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

After the previous command has finished and minimube is up and running, check that everything is ok by execute `kubectl get nodes`{{execute}}. You should see the `STATUS` is `Ready` in the console. If not, rerun the command until it happens.

Kubectl is a K8s command line tool and can be used to communicate with the cluster. Get information about the nodes with `kubectl cluster-info`{{execute}}. The ip-address of the nodes in the cluster will be shown.
