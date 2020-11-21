## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![https://drive.google.com/file/d/1YP89vBetsGs8z-_evA5M7fib3ljgUiDQ/view?usp=sharing](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the elk-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting access to the network.
Load balancing helps to protect the cloud. When a jump box is used, its hidden benefit is that any tools in place for the SAN system are maintained on that single system.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log data and system metrics.


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump-Box | Gateway  | 10.0.0.16  | Linux            |
| Web-1    |    VM    | 10.0.0.4   | Linux            |
| Web2     |    VM    | 10.0.0.14  | Linux            |
| ELKVM1   |    ELK   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 72.208.73.30

Machines within the network can only be accessed by Jump-Box-Provisioner 104.40.29.159.

A summary of the access policies in place can be found in the table below.

| Name            |Publicly Accessible| Allowed IP Addresses |
|-----------------|-------------------|----------------------|
| Port80_PublicVM | Yes               | 72.208.73.30         |
| Jump_Box_Access | Yes               |  10.0.0.16           | 
|  SSH            | Yes               | 72.208.73.30         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because this frees IT administrators to focus on efforts that help deliver more value to the business by spending time on more important tasks.

The playbook implements the following tasks:
- Install docker.io
- Install python3-pip3
- Install Docker Module
- Increase virutal memory
- Use more memory
- Download and launch a docker web container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

~/Desktop/School/Docker_PS_Output
https://drive.google.com/file/d/1IrfmKz6DNWIrUNwWlULZdMLdCVaNdVEp/view?usp=sharing

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.14
- 10.0.0.4

We have installed the following Beats on these machines:
- 10.1.0.4

These Beats allow us to collect the following information from each machine:
- Beats are a collection of lightweight and open source log shippers that act as agents installed on the different servers in your infrastructure for collecting logs or metrics.
These can be log files (Filebeat), network data (Packetbeat), server metrics (Metricbeat), or any other type of data that can be collected by the growing number of Beats being developed by both Elastic and the community. Once collected, the data is sent either directly into Elasticsearch or to Logstash for additional processing.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yml file to /etc/ansible/elk-playbook.yml.
- Update the yml file to include docker.io, python3-pip3, docker module, and docker web container
- Run the playbook, and navigate to Kibana website to check that the installation worked as expected. http://40.117.102.46:5601/app/kibana#/home

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_ elk-playbook.yml /etc/ansible/elk-playbook.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ /etc/ansible/hosts here you can specify between your webservers and elkservers.
- _Which URL do you navigate to in order to check that the ELK server is running?
http://40.117.102.46:5601/app/kibana
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- /etc/ansible directory will contain elk-playbook.yml
- /etc/ansible/hosts will allow you to specify your servers
- /etc/ansible/roles directory contains both filebeat and metricbeat playbook.ymls
