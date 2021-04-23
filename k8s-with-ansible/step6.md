## Kubernetes and their namespaces

Kubernetes, also called K8s because there are 8 letters between the first and last character, is an open-source tool for container orchestration. It can be used to automate deployment, scaling and management.

Kubernetes supports virtual clusters, so called namespaces. When several teams share a cluster it can be problematic because of different user needs. Namespaces can be created to give each team their own virtual cluster, based on the same physical cluster, which can be used without affecting the other teams.

Before creating a namespace, run the command `kubectl get namespaces`{{execute}} to get the initial status. There will be a default namespace that is part of any basic initialisation of Kubernetes.

Lets create a namespace with
`kubectl create namespace my-new-awesome-namespace`{{execute}}

Another way to create a namespace is with Ansible, which is done by adding commands as a play in a playbook. Below is a playbook that creates a new namespace.
<pre class="file"
 data-filename="./playbook.yml"
  data-target="replace">
---
- hosts: all
  become: "yes"
  vars:
    ansible_python_interpreter: '{{ ansible_playbook_python }}'
  tasks:
    - name: Ensure k8s module dependencies are installed.
      pip:
        name: openshift==0.4.3
        state: present

    - name: Create K8s namespace
      k8s_raw:
        name: my-new-namespace
        api_version: v1
        kind: Namespace
        state: present
</pre>

Run the playbook with `ansible-playbook -i hosts playbook.yml`{{execute}}

Check the outcome with `kubectl get namespaces`{{execute}}. Now there are several namespaces!
