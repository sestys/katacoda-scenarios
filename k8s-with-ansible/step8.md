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
        name: openshift==0.4.3 docker-py>=1.7.0
        state: present

    - name: Create K8s namespace
      k8s_raw:
        name: my-new-namespace
        api_version: v1
        kind: Namespace
        state: present

    - name: Pull a nginx image
      docker_image:
        name: nginx:1.20-alpine

    - name: apply kubernetes deployment
      shell: "kubectl apply -f deployment/{{ item }}"
      with_items:
        - hello-k8s-deployment.yml
        - nginx-deployment.yml

</pre>

`kubectl -n my-new-namespace get pods`{{execute}}
