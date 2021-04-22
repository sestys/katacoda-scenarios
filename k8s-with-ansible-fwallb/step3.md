## Set up inventory file

Create a hosts file that will give Ansible information about the Kubernetes cluster.

Below is a typical layout of a hosts file. Here we have two groups, both with nodes represented by ip-addresses. Group 1 has one node, and group 2 has two nodes.

    [group 1]
    1.2.3.4

    [group 2]
    66.77.88.99
    44.66.22.33

Let us set up a hosts file matching the K8s cluster.

First, get the ip-address of the K8s cluster by running `kubectl cluster-info`{{execute}}. Then configure the hosts file with the following commands:
* create the hosts file and add the group _master_  `echo "[master]" > hosts`{{execute}}.
* add the cluster's ip-address to the _master_ group `echo "<ip-address of cluster>" >> hosts`. NOTE! change <ip-address of cluster> to the ip-address displayed when running `kubectl cluster-info`.

To verify that the file is configured correctly, run `cat hosts`{{execute}} to see the content of the file, which should be the following:

    [master]
    172.17.0.96

Now ping the servers to verify connection to the cluster `ansible all -i hosts -m ping`{{execute}} - this should display SUCCESS!
