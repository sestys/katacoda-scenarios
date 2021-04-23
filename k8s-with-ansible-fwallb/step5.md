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
  - name: install numpy
    pip:
      name: numpy
</pre>

NOTE! If you cannot open the file in the editor. Use `nano playbook.yml`{{execute}} to create and open the file. Paste the content above. Save and exit by pressing `ctl-x` followed by `y` and `enter`.

Now the playbook can be executed by running the following command `ansible-playbook -i hosts playbook.yml`{{execute}}. The output should include a message, ok=2 and changed=1. The second time it is run numpy is already installed, and therefore we get no change and instead ok=3. This is one of great Ansible features - you can use the same notebook to both configuring the environment, and checking if everything is as it should be.
