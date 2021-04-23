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

    - name: Check that docker is installed
      pip:
        name: docker-py>=1.7.0

    - name: pull an image
      docker_image:
        name: nginx
</pre>
