## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below:
Images/completenetwork.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

 Ansible/CompletePlaybook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting access to the network.
Load balancers provide protection against overloading of resources, protecting from attack. additionally, using a jumpbox to connect to the established network using ssh keys prevents any brute-force hacking attempts from occuring.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system logs. Many different types of data can be collected using various ELK tools called Beats.

The configuration details of each machine may be found below.


| Name               | Function           | IP Address     | Operating System |
|--------------------|--------------------|----------------|------------------|
| JumpBoxProvisioner | Gateway            | 23.98.148.235  | Linux            |  
| WebOne             |  Webserver         | 10.0.0.7       | Linux            |
| WebTwo             |  Webserver         | 10.0.0.8       |  Linux           |
| ELKServer          | Kibana Interaction | 52.188.119.191 | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the load balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
load balancer front-end ip: 20.97.31.94

Machines within the network can only be accessed by the docker container within the jumpbox.
container ip: 23.98.148.235
A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 10.0.0.7 10.0.0.8    |
|  WebOne  | No                  | 23.98.148.235        |
|  WebTwo  | No                  | 23.98.148.235        |
| ELKServer| 

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because there will be no individual errors during installation and any flaws in the system can be easily fixed in all associated machines.

The playbook implements the following tasks:
- Installs Docker and configures it to work properly with the system
- Installs Python3-pip
- enables and launches a Docker ELK container.


### Target Machines & Beats
This ELK server is configured to monitor the following machines: 10.0.0.7, 10.0.0.8


We have installed the following Beats on these machines:
- Filebeat

Filebeat allows us to collect the log data from a computer or virtual machine, centralize it, and send it to the ELK stack where we can interact with this information through Kibana.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to the roles directory
- Update the Ansible playbook file to include Docker, Python-pip3, a Docker-Python module, and a docker web container running DVWA.
- Run the playbook, and navigate to one of the VMs included in the webserver hosts group to check that the installation worked as expected.

In order to run the Ansible playbooks, it is necessary to have both the hosts and ansible.cfg files correctly updated with ip and user information. To distinguish between machines that are using Filebeat and the ELK server, seperate groups can be established in the hosts file.
- Kibana/ELK webserver site: http://52.188.119.191:5601/app/kibana

