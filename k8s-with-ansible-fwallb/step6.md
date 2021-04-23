## Kubernetes

### Todo
* intro to k8s
* what is Namespace
* create namespace with Kubectl

`kubectl create namespace my-new-awesome-namespace`

* create namespace with ansible

<pre class="file"
 data-filename="./k8s_playbook.yml"
  data-target="replace">
---
- hosts: all
  become: "yes"
  vars:
    ansible_python_interpreter: '{{ ansible_playbook_python }}'
  tasks:
    - name: Check that openshift is installed, if not, install it
      pip:
        name: openshift==0.4.3

    - name: Create K8s namespace
      k8s_raw:
        name: my-new-namespace
        api_version: v1
        kind: Namespace
        state: present
</pre>

Run it `ansible-playbook -i hosts k8s_playbook.yml`{{execute}}

Check outcome `kubectl get namespaces`{{execute}}
