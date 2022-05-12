# cyberXsecurity
Cybersecurity Bootcamp 
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

-DarkHelmet1234567/cyberXsecurity/Diagrams/unit 12 hw.drawio

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  -DarkHelmet1234567/cyberXsecurity/Ansible/ansible-playbook filebeat & metricbeat.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly effecient, in addition to restricting unauthorized access to the network.

- What aspect of security do load balancers protect? 
	The off-loading function of a load balancer defends an organization against distributed denial-of-service (DDoS) attacks.   

- What is the advantage of a jump box? 
	A jump box prevents unauthorized access to the web servers by restricting IP addresses that communicate with the web servers 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the DATA and system LOGS.
- What does Filebeat watch for?
	Filebeat is a lightweight shipper for forwarding and centralizing log data. Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- What does Metricbeat record?
	Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server.

The configuration details of each machine may be found below.

| Name      | Function | IP Address |    Public IP   | Operating System |
|-----------|----------|------------|----------------|------------------|
| Jump Box  | Gateway  | 10.0.0.4   | 52.234.132.247 | Linux            |
| Web One   | Server   | 10.0.0.5   |                | Linux            |
| Web Two   | Server   | 10.0.0.6   |                | Linux            |
| Elk-server| Kibana   | 10.1.0.4   |                | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 23.240.62.42

Machines within the network can only be accessed by SSH.
- Which machine did you allow to access your Elk-Server? What was its IP address?
	Only the Jump Box could access the Elk-Server from ip 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| Jump Box   | Yes                 |  23.240.62.42        |
| Web One    | No                  |                      |
| Web Two    | No                  |                      |
| Elk-Server | No                  |                      |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
	Multiple servers can be deployed rapidly using a single playbook

The playbook implements the following tasks:
- Install docker.io
- Install Python-pip
- Install dockert container
- Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

cyberXsecurity/Diagrams/elk server sudo docker ps.jpg

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web One (10.0.0.5); Web Two (10.0.0.6) 

We have installed the following Beats on these machines:
- Filebeat and Metricbeat 

These Beats allow us to collect the following information from each machine:
- Filebeat monitors log files or locations you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat collects metrics from the operating system and from services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the configuration file to include the webservers and Elk-Server private ip address
- Run the playbook, and navigate to the Elk-Server to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- Which file is the playbook? Where do you copy it? 
	/etc/ansible/file/ansible-playbook filebeat & metricbeat.yml
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the Elk-Server on versus which to install Filebeat on?
	edit the /etc/ansible/hosts file to add webserver/Elk-Server ip address
- Which URL do you navigate to in order to check that the ELK server is running?
	http://10.1.0.4:5601/app/kibana

