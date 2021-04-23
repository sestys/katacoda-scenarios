## Set up and run a simple playbook

A playbooks lists plays which is a task that Ansible interprets. The playbook below has one play, which is started by `tasks:`. It simply prints a message saying "Hello World" and installs numpy.

__Hosts__ lets you state which group in the inventory that the play should apply to. In this case it is set to `all`, to affect all groups. __Become__ lets you become another user, and `Become: yes` activates privilege escalation.
__Name__ is simply the text that is displayed when the playbook is executed, so that it is easy to follow the output.
__Debug__ is a command that lets you output parts from the cluster. This could be a date, a simple string or other data. The date could for example be out of synk, so scheduled tasks are not executed. Printing the date would find this problem. __Pip__ is simply Python's package installer.

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

Create a playbook.yml file with the above content by running `touch playbook.yml`{{execute}}. Open the file in the editor and paste the above content. NOTE! If you can not open the file in the editor. Use `nano playbook.yml`{{execute}} to create and open the file. Paste the content above. Save and exit by pressing `ctl-x` followed by `y` and `enter`.

Now the playbook can be executed by running the following command `ansible-playbook -i hosts playbook.yml`{{execute}}. The output should be ok=2 and a message and changed=1. The second time it is run numpy is already installed, and therefore we get no change and instead ok=3.
