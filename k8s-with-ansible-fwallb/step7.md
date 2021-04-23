

### Todo
* pull image
* deploy it - multiple posibilities, we use deployment file

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
