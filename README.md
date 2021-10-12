## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/diagram-screenshot.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the elk.yaml file may be used to install only certain pieces of it, such as Filebeat.

  - elk.yaml

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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system applications. 
- Filebeat will forward the logs into a centralized location on the network which is assigned to the ELK server. 
- Metricbeat will collect information regarding the services running on the web servers. 

The configuration details of each machine may be found below.


| Name        | Function      | IP Address | Operating System |
|-------------|---------------|------------|------------------|
| Jump Box    | Gateway       | 10.0.0.1   | Linux            |
| ELK Server  | Logging       | 10.1.0.1   | Linux            |
| Web Server 1|Web Application| 10.0.0.4   | Linux            |
| Web Server 2|Web Application| 10.0.0.5   | Linux            |
| Web Server 3|Web Application| 10.0.0.7   | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 70.171.220.196

Machines within the network can only be accessed by JumpBox Ansible Container.
- 10.0.0.6

A summary of the access policies in place can be found in the table below.

| Name        | Publicly Accessible | Allowed IP Addresses |
|-------------|---------------------|----------------------|
| Jump Box    | Yes                 | 70.171.220.196       |
| ELK Server  | No                  | 10.1.0.1             |
| Web Server 1| No                  | 10.0.0.4             |
| Web Server 2| No                  | 10.0.0.5             |
| Web Server 3| No                  | 10.0.0.7             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the computers will automatically start running the programs off of the yaml scripts ensuring that there is no program that is not installed or not running. 

The playbook implements the following tasks:
- ensure the alloted memory for the system is correct
- confirming if docker is installed, if not. Then it will install it. 
- ensure python3 is installed and running. 
- run the python3 docker module
- download and install the docker web container


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.4
- 10.0.0.5
- 10.0.0.7

We have installed the following Beats on these machines:
- filebeat
- metricbeat

These Beats allow us to collect the following information from each machine:
- filebeat will monitor the systems and collect logs to convert to a readible format. 
- metricbeat will monitor the web machines and all services that are running on the system. It will forward the logs to the ELK server to allow Kibana to convert it to a readible format. 


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat.yaml file to /etc/filebeat
- Update the filebeat.yaml file to include the web server(s) IP. 
- Run the playbook, and navigate to the web servers to check that the installation worked as expected.