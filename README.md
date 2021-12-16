# ELK-STACK-Project
ELK stack project
# ELK STACK Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ___filebeat-playbook.yml__ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._. filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available for customers, in addition to restricting attacks to the network. If a server goes down, or needs to be updated, services will still continue. -The advantage of using a jump box is that only the jump box can access the Virutal network via ssh.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

Filebeat monitors the log files or locations specified, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
Metricbeat is an extremely easy-to-use, efficient and reliable metric shipper for monitoring your system and the processes running on it. The configuration details of each machine may be found below

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

|Name	             |Function	  |IP address 	                                 |Operating System
|JumpBox-Provisioner |Gateway	  |Public IP:20.120.96.134 Private IP:10.0.0.4    |Linux
|Web-1	             |Server	  |10.0.0.5	                                     |Linux
|Web-2	             |Server	  |10.0.0.6	                                     |Linux
|Web-3	             |Server	  |10.0.0.7	                                     |Linux
|ELK-VM1	         |Server	  |10.1.0.4	                                     |Linux


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the __JumpBox-Provisioner__ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 5061:Kibana Port

Machines within the network can only be accessed by __JumpBox-Provisioner___.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 |  20.120.96.134       |
|   Web-1  |     No              |      10.0.0.5        |
|   Web-2  |      No             |      10.0.0.6        |
|   Web-3  |       No            |      10.0.0.7        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? It was easy to do and prevented any easily overloook vulnerablities.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
-Install docker.io
-Install python3-pip
-Install docker via pip
-Increase vitual memory
-Use more memory
-Download and launch a docker elk container - starts docker and establishes the ports being used.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO:
| Machine | IP address|
| ------ | ------ |
| Web-1 | 10.0.0.5|
| Web-2 | 10.0.0.6|
| Web-3 | 10.0.0.7|

We have installed the following Beats on these machines:
- Filebeat
_ Metricbeat

These Beats allow us to collect the following information from each machine:
- filebeat collects log data and shows them in the monitoring clusters. 
- metricbeat collects metrics and statistics and shows them in the output specified, for example Elasticsearch or Logstash.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
SSH into the control node and follow the steps below:
- Copy the Playbook file to Ansible directory.
- Update the host file to include all the Webserver and ELK Server IP..
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?Path /etc/ansible/roles contains both the playbook file for filebeat and metricbeat. Other playbook file is on ansible directory itself.
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ 
- _Which URL do you navigate to in order to check that the ELK server is running? http://20.109.191.27:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

ansible-playbook filebeat-playbook.yml
ansible-playbook metricbeat-playbook.yml


