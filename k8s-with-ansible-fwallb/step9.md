<pre class="file"
 data-filename="./k8s_playbook.yml"
  data-target="replace">
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

      - name: apply kubernetes deployment
        shell: "kubectl apply -f {{ item }}"
        with_items:
          - hello-k8s-deployment.yml
          - nginx-deployment.yml
</pre>

<pre class="file"
 data-filename="./hello-k8s-deployment.yml"
  data-target="replace">
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-k8s
  namespace: my-new-namespace
spec:
  replicas: 1
  selector:
    matchLabels:
      app: hello-k8s
  template:
    metadata:
      labels:
        app: hello-k8s
    spec:
      containers:
      - name: hello-k8s
        image: paulbouwer/hello-kubernetes:1.5
        ports:
        - containerPort: 8080
</pre>

<pre class="file"
 data-filename="./nginx-deployment.yml"
  data-target="replace">
- name: apply kubernetes deployment
      shell: "kubectl apply -f {{ lookup(item) }}"
      wait: true
      with_items:
        - hello-k8s-deployment.yml
        - nginx-deployment.yml

        ---
        apiVersion: apps/v1
        kind: Deployment
        metadata:
          name: nginx
          namespace: my-new-namespace
        spec:
          replicas: 1
          selector:
            matchLabels:
              app: nginx
          template:
            metadata:
              labels:
                app: nginx
            spec:
              containers:
              - name: nginx
                image: nginx:1.20-alpine
                ports:
                - containerPort: 8081
</pre>

`kubectl -n my-new-namespace get pods`{{execute}}
