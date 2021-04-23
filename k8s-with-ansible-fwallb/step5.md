## Create a simple Ansible playbook

Create a playbook.yml file by running `touch playbook.yml`{{execute}}. Open the file in the editor and add the following:

<pre class="file"
 data-filename="./playbook.yml"
  data-target="replace">
---
- hosts: all
  become: yes
  tasks:
  - name: Say hello
    debug:
      msg: 'Hello World'
  - name: Ensure yamllint is installed
    apt:
      name: yamllint
      state: present
</pre>

Now the playbook can be executed by running the following command `ansible-playbook -i hosts playbook.yml`{{execute}}. The output should include a message, ok=3 and changed=1. The second time it is run yamllint is already installed, and therefore we get no change and only ok=3. This is one of great Ansible features - you can use the same notebook to both configuring the environment, and checking if everything is as it should be.
