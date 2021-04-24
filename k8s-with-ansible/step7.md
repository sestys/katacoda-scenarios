
Containers are Linux systems, almost impossibly minimal in scope, that can be managed by Kubernetes. Now you will pull a docker image with a few lines of code with Ansible.

The image is NginX, a web server used as load balancer, mail and reverse proxy, and HTTP cache. It is one of the most widely used webserver and the docker image has over 1 billions pulls.


Change the _playbook.yml_ with the following code:
<pre class="file"
 data-filename="./playbook.yml"
  data-target="replace">
---
- hosts: all
  become: "yes"
  vars:
    ansible_python_interpreter: '{{ ansible_playbook_python }}'
  tasks:
    - name: Ensure k8s and docker modules' dependencies are installed.
      pip:
        name: openshift==0.4.3 docker-py>=1.7.0
        state: present

    - name: Create K8s namespace
      k8s_raw:
        name: my-new-namespace
        api_version: v1
        kind: Namespace
        state: present


    - name: Pull a nginx docker image
      docker_image:
        name: nginx:1.20-alpine
        state: present
</pre>

There are two changes:
1. in the pip task, we also check if _docker-py_ is installed, as it is needed for the docker_image module
2. we added the docker_image task, which just needs the name of the desired image and it will ensure the image is in the system; if it is missing, it will pull it from the Docker Hub

Now run the playbook again `ansible-playbook -i hosts playbook.yml`{{execute}}.

In the next step, we will show you how to deploy the image into the K8s cluster.
