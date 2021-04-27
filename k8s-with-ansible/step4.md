
A playbook lists plays which are tasks that Ansible interprets. The playbook below has one play, which is started by the command `tasks:`. It simply prints a message saying "Hello World", installs _yamllint_ (a tool used to check if your YAML file is correctly formatted), and lastly installs a Python package with pip.

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

  - name: Install something for Python
    pip:
      name: cowsay
      state: present

</pre>

Let's look at the different commands in the playbook:
- __hosts__ lets you state which group in the inventory that the play should apply to. In this case it is set to `all`, to affect all groups.
- __become__ lets you become another user, and `Become: yes` activates privilege escalation. This is similar to the Unix commands _sudo_ and _su_, which also lets you execute commands with the privileges of another user or user account.
- __name__ is simply the text that is displayed when the playbook is executed, so that it is easy to follow the output.
- __debug__ is a command that lets you output parts from the cluster. This could be a date, a simple string or other data. The date could for example be out of sync, so scheduled tasks are not executed. Printing the date would find this problem.
- __apt__ is a module for Ubuntu package manager and is used to install packages.
- __pip__ is simply Python's package installer, it corresponds to running `pip install cowsay`.


Now let create a playbook in the next step!
