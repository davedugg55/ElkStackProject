# ElkStackProject
ElkStackProject
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: ElkStackProject/Diagrams/Elk Server.drawio

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible Playbook (YAML file) may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: ElkStackProject/Ansible/Install Elk Playbook.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_The offloading capability of a load balancer defends organizations against DDoS attacks by shifting traffic from a corporate server to a public cloud provider (avinetworks.com). By using a Jump Box you can restrict IP Addresses to communicate and block Public Ips to help improve security.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Jump Box Provisioner and system network.
- _TODO: What does Filebeat watch for?_In Filebeat you can specify one or more inputs to look for log data.  Filebeat then locates logs, reads them and then sends them to Elasticsearch (or similar)for indexing. 
- _TODO: What does Metricbeat record?_Metricbeat records metrics from the OS and from other services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| JumpBoxProvisioner | Gateway  | 10.0.0.4   | Linux     |
| Web-1   |   Web Server       |   10.0.0.7    |  Linux  |
| Web-2     |Web Server    | 10.0.0.6   |  Linux     |
| elk    |  Monitor  |  10.1.0.4  |       Linux     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 66.41.229.183

Machines within the network can only be accessed by SSH 22 to Jumo Box Provisioner and gaining entry to Web1, Web2
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_My personal computer with IP 66.41.229.183

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | yes	                | 66.41.229.183        |
|    Web-1 |    no                 | 10.0.0.4 / 10.1.0.4|
|   Web -2 |      no               | 10.0.0.4 / 10.1.0.4 |
| elk      | no                  | 66.41.229.183/10.1.0.4|


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_Ansible playbooks install applications on multiple servers at one time which are specified by the user rather than having to go in and install the application individually on each server.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. Elk is configured with the Docker.  Docker.io is installed, python3-pip is installed, Docker module is installed, system memory is increased, more memory is used, a docker download and launch of and elk container and the service is started upon booting.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[TODO: ElkStackProject/Diagrams/elk container

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: Web-1: 10.0.0.7, Web-2: 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: elk VM had metricbeat and filebeat installed.

These Beats allow us to collect the following information from each machine: Metricbeat records metrics from the OS and from other services running on the server such as monitoring container performance. Filebeat you can specify one or more inputs to look for log data.  Filebeat then locates logs, reads them and then sends them to Elasticsearch (or similar)for indexing


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Ansible playbook file (Pentest Playbook,txt) and put it withing the ansible folder.
- Update the host file to include the webservers and elk IP addresses and at the end of each IP, “ansible_python_interpreter=/usr/bin/python3” should be included. Ex: 10.0.0.6 ansible_python_interpreter=/usr/bin/python3
-Open the ansible.cfg file and replace root with the usernames for the VMs.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_Playbooks for metricbeats, filebeat, elk, and setting up the dockers are located within ElksStackProject/Ansible.
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_You must update the host file to indicate which machine(s) you want files installed on. Since the playbook draws this information from the host file it is imperative that this is updated prior to running the playbook.
- _Which URL do you navigate to in order to check that the ELK server is running? http://ELKEXTERNALIPADDRESS>5601/app/kibana
