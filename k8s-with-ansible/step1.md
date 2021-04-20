## Init
* run `launch.sh`{{execute}} and wait till Kubernetes cluster is up and running.
* check K8s nodes `kubectl get nodes`{{execute}}
* install k8 module `ansible-galaxy install ansible.kubernetes-modules`{{execute}}
* create host file: first `echo "group1" > hosts`{execute}, then `echo "172.17.0.26" >> hosts`
* test connection `ansible all -i hosts -m ping`{{execute}}
