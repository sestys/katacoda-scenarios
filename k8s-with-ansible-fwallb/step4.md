## Set up and run a simple playbook

A playbooks lists a list of plays which is a series of tasks that Ansible interprets. The playbook below simply prints a message saying "Hello World".

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


Create a playbook.yml file with the above content by running `nano playbook.yml`{{execute}} create and open the file. Paste the content above. Save and exit nano by pressing `ctl-x` followed by `y` and `enter`.

Now the playbook can be executed by running the following command `ansible-playbook -i hosts playbook.yml`{{execute}}. The output should be ok=1 and a message.
