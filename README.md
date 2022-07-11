# Project1 - Week13
Week 13 ELK Stack Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](https://github.com/fenixarev/Project1Week13/blob/main/Network%20Diagram/Network%20Diagram%20-%20Project1.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the [Install ELK File](https://github.com/fenixarev/Project1Week13/blob/main/Ansible/install-elk.yml) file may be used to install only certain pieces of it, such as [Filebeat](https://github.com/fenixarev/Project1Week13/blob/main/Ansible/filebeat-playbook.yml).

  

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Efficient in addition to restricting bad actors access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metricts and stats.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function | Private IP Address | Public IP Address | Operating System |
|-----------|----------|--------------------|-------------------|------------------|
| Jump Box  | Gateway  |     10.0.0.4       |  20.70.185.59     |  Linux - Ubuntu  |
| Web-1     |App-Site  |     10.0.0.5       |  20.213.85.27     |  Linux - Ubuntu  |
| Web-2     |App-Site  |     10.0.0.6       |  20.213.85.59     |  Linux - Ubuntu  |
| ELK-Server|ELK-Stack |     10.1.0.4       |  20.42.243.135    |  Linux - Ubuntu  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JUMPBOX PROVISIONER machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Public IP= 76.111.55.63
- Private (LAN) = 10.0.0.4

Machines within the network can only be accessed by SSH.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible          | Allowed IP Addresses |
|-----------|------------------------------|----------------------|
| Jump Box  | Yes-From Whitelisted IP      |   76.111.55.63       |
| Web-1     | Yes, Traffic passtrough LB   |   20.213.85.27       |
| Web-2     | Yes, Traffic passtrough LB   |   20.213.85.27       |                      
| ELK-Server| Yes                          |   76.111.55.63       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantage of Insfraestructure automation deployments.

The playbook implements the following tasks:
- Install Docker
- Install Python
- Install Docker and Python module
- Increase memory

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](https://github.com/fenixarev/Project1Week13/blob/main/Network%20Diagram/Sudo-Docker.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1: 10.0.0.5
- Web-2: 10.0.0.6

We have installed the following Beats on these machines:
- ELK Stack at ELK Server

These Beats allow us to collect the following information from each machine:
- Monitor the logs
- Centralize Data to be analized


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file: /etc/ansible at JumpBox. cp install-elk.yml /etc/ansible
- Update the hosts file to include IP address
- Run the playbook, and navigate to the web site http://20.42.243.135:5601/ to check that the installation worked as expected.


