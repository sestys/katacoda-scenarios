## K8s and Ansible

Ansible is a tool for automating parts of the DevOps process. It does so by interpreting YAML files, so called playbook.yml files, where a series of tasks are described. The language is declarative and Ansible will strive to reach the desired state declared in the file.

It can be used to automate tasks on the K8s cluster.

First, install Ansible with the following command `apt install ansible`{{execute}}

Verify installation using `ansible -version`{{execute}}, which should display a version if Ansible is properly installed.
