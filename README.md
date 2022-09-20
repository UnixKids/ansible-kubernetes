# Description
Ansible Repository for bootstrapping Kubernetes Cluster using Kubeadm

# Usage
1. Configure hosts file with servers (master & worker nodes) that Kubernetes will be installed on.
2. Configure "LOCAL_FILE" variable in "variables.yaml" with the location you'd like the token file to be stored at on the Ansible Control Node.
3. Run "install-docker.yaml" first to install Docker on all nodes
4. Run "install-kubernetes.yaml" to install Kubelet, Kubectl, Kubeadm on all nodes.
5. Run "master-node.yaml" to configure Kubernetes Control Plane and generate Kubeadm token on Master Node.
6. Run "worker-node.yaml" to join worker nodes to the Kubernetes Cluster. 
7. **(Optional)** Configure and run "deployments.yaml" to add additional Kubernetes configuration.
8. **(Optional)** Uninstalling can be done via the "uninstall.yaml" file

# Command Example
Run the ansible-playbook command from the project's root directory.

ansible-playbook [kubeadm/file_name]

ansible-playbook kubeadm/worker-node.yaml

# Notes & Limitations
- Remove .exmaple from all example files such as hosts.example and  ansible.cfg.example and configuring them according to your own specifications.
- Currently only functions with one master-node and multiple worker-nodes. Multiple master-nodes currently not supported.
- The IPADDR variable in "variables.yaml" will need to be overridden if there are multiple private IP Addresses on the master-node
- Current configuration will only add allow root user to manage Cluster 