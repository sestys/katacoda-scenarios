
Create a hosts file that will give Ansible information about the Kubernetes cluster.

Below is a typical layout of a hosts file. Here we have two groups, both with nodes represented by ip-addresses. Group 1 has one node, and group 2 has two nodes.

    [group 1]
    1.2.3.4

    [group 2]
    66.77.88.99
    44.66.22.33

Let us set up a hosts file matching the K8s cluster. The cluster used in the tutorial has one node, a single master node.

First, get the ip-address of the K8s cluster by running `kubectl cluster-info`{{execute}}. To find the ip-address, look at the URL in the output. For example, the ip-address in this output _https://172.17.0.33:8443_ is 1.2.3.4.

Then configure the hosts file to include the ip-address. Create the hosts file and add the group _master_ by running `echo "[master]" > hosts`{{execute}}.

The hosts file is now created and can be found beside the editor. Open the hosts file and add the cluster's ip-address that you got by the `kubectl cluster-info`{{execute}} command. If you cannot find the file, try to refresh the file tree.

To verify that the file is configured correctly, run `cat hosts`{{execute}} to see the content of the file, which should be the following:

    [master]
    the ip-address that you got

Now ping the server to verify connection to the cluster `ansible all -i hosts -m ping`{{execute}} - this should display SUCCESS! NOTE! There is no problem if *The authenticity of the host can not be established*, just write `yes` followed by `enter`.
