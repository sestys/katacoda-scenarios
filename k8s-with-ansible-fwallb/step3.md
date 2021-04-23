## Set up inventory file

Create a hosts file that will give Ansible information about the Kubernetes cluster.

Below is a typical layout of a hosts file. Here we have two groups, both with nodes represented by ip-addresses. Group 1 has one node, and group 2 has two nodes.

    [group 1]
    1.2.3.4

    [group 2]
    66.77.88.99
    44.66.22.33

Let us set up a hosts file matching the K8s cluster. The cluster used in the tutorial has one node, a single master node.

First, get the ip-address of the K8s cluster by running `kubectl cluster-info`{{execute}}. Then configure the hosts file to include this ip-address. Create the hosts file and add the group _master_ by running `echo "[master]" > hosts`{{execute}}.

The hosts file is now created and can be found beside the editor. Now add the cluster's ip-address to the _master_ group by opening the hosts file above and, add the ip-address for the cluster that you got by the `kubectl cluster-info`{{execute}} command.

NOTE! If you can't find the file, you can edit it using `nano playbook.yml`{{execute}}, which will open the file, To close and save use `ctl-x`{{execute}} followed by `y`{{execute}} and `enter`{{execute}}.

To verify that the file is configured correctly, run `cat hosts`{{execute}} to see the content of the file, which should be the following:

    [master]
    the ip-address that you got

Now ping the server to verify connection to the cluster `ansible all -i hosts -m ping`{{execute}} - this should display SUCCESS!
