### Lets finish with a fun easter egg

<iframe src="https://giphy.com/embed/JoqezKViyMjkahOzD8" width="200" height="200" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

Create a playbook `touch easter_playbook.yml` and add the content bellow by opening the file in the editor.

    ---
    - hosts: all
    become: yes
    - name: Say moo
      pip:
        name: cowsay

Execute the playbook `ansible-playbook -i hosts easter_playbook.yml`{{execute}}. This will install cowsay.

Now add the following to the playbook:

    - name: install matplotlib
      pip:
        name: matplotlib

Execute the playbook again `ansible-playbook -i hosts easter_playbook.yml`{{execute}}. Cows now announce each play.

<iframe src="https://giphy.com/embed/3ohs4dsfwr3J53qrS0" width="200" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
