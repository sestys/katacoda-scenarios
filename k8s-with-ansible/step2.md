
Ansible is a tool for automating parts of the DevOps process. It does so by interpreting YAML files, so called playbooks, where a series of tasks are described. The language is declarative and Ansible will strive to reach the desired state declared in the file.

It can be used to automate tasks on the K8s cluster.

Ansible is already included in our environment, and that can be verified using `ansible --version`{{execute}}. The version installed should be displayed.

In case Ansible is not installed, `apt install ansible`{{execute}} can be runned.
