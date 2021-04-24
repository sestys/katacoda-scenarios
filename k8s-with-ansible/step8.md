You're not limited to small maintenance tasks with Ansible.
Any task you are able to do from a shell you can easily do in playbooks as well.

In the previous step, you learned how to pull a docker image. Now the only thing left is to deploy the image. In the _deployment_ folder are two typical deployment configuration files, check them out if you are interested.

To make the deployment possible, add the last task to the playbook.yml file. All it does is to apply the deployment file to k8s. Interesting is how easily you can loop over multiple files with Ansible. The __with_items__ specifies values you want to loop over, and the __{{ item }}__ then substitutes them into the function call. In this way, you can easily run the same command multiple times. Using outputs from previous tasks is done in a similar way.

Now, for the last time, change the _playbook.yml_ to:
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

    - name: Deploy to k8s
      shell: "kubectl apply -f deployment/{{ item }}"
      with_items:
        - hello-k8s-deployment.yml
        - nginx-deployment.yml
</pre>

and then run it `ansible-playbook -i hosts playbook.yml`{{execute}}.

To check that the deployment was successful, let's display all the pods running in our namespace `kubectl -n my-new-namespace get pods`{{execute}}.
