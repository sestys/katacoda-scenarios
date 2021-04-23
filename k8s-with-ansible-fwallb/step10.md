### Lets finish with a fun easter egg

<iframe src="https://giphy.com/embed/JoqezKViyMjkahOzD8" width="200" height="200" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

Create a playbook `touch easter_playbook.yml`{{execute}} and add the content bellow by opening the file in the editor.

<pre class="file"
 data-filename="./easter_playbook.yml"
  data-target="replace">
    ---
    - hosts: all
    become: yes
    - name: Say moo
      pip:
        name: cowsay
</pre>

Execute the playbook `ansible-playbook -i hosts easter_playbook.yml`{{execute}}. This will install cowsay.

Now add the following to the playbook:

<pre class="file"
 data-filename="./easter_playbook.yml"
  data-target="add">
    - name: install matplotlib
      pip:
        name: matplotlib
</pre>

Execute the playbook again `ansible-playbook -i hosts easter_playbook.yml`{{execute}}. Cows now announce each play.

<iframe src="https://giphy.com/embed/3ohs4dsfwr3J53qrS0" width="200" height="270" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>
