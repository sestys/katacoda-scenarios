# Configure Ansible with Kubernetes

Automation is one of the core principles in DevOps. In one of the two parts that form DevOps, operations, continuous deployment (CD) is the core principle. In this part of the DevOps process, it is the deployment that is automated. A CD pipeline introduces a series of steps performed to deploy a new version of the software.

This tutorial introduces two open-source tools used for automating routine tasks and container orchestration.

__Ansible__ is an IT automation tool. It can configure systems, deploy software, and orchestrate more advanced IT tasks such as continuous deployments or zero downtime rolling updates. Its goal is ease-of-use and all configuration is done with simple YAML files.

__Kubernetes__ is an container orchestration engine for automating deployment, scaling, and management of containerized applications. Today, it is the de facto standard for container orchestration in the cloud.

This tutorial will show how to set up these together to automate a part of the deployment process.
