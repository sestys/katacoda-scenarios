## Init
* run `launch.sh`{{execute}} and wait till Kubernetes cluster is up and running.
* check K8s nodes `kubectl get nodes`{{execute}}
* check k8s cluster `kubectl cluster-info`{{execute}}
* install k8 module `ansible-galaxy install ansible.kubernetes-modules`{{execute}}
* create host file: first `echo "[group1]" > hosts`{{execute}}, then `echo "IP" >> hosts`{{execute}}, the IP is from the cluster-info
* test connection `ansible all -i hosts -m ping`{{execute}}
* create role: `ansible-galaxy init test-role --offline`{{execute}}
