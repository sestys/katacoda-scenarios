## Into to Ansible playbooks

A playbooks lists plays which is a task that Ansible interprets. The playbook below has one play, which is started by `tasks:`. It simply prints a message saying "Hello World" and installs numpy.

- __Hosts__ lets you state which group in the inventory that the play should apply to. In this case it is set to `all`, to affect all groups.
- __Become__ lets you become another user, and `Become: yes` activates privilege escalation.
- __Name__ is simply the text that is displayed when the playbook is executed, so that it is easy to follow the output.
- __Debug__ is a command that lets you output parts from the cluster. This could be a date, a simple string or other data. The date could for example be out of synk, so scheduled tasks are not executed. Printing the date would find this problem.
- __Pip__ is simply Python's package installer.

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


Now let create a playbook in the next step!
