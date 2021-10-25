## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(C:\Users\fagak\OneDrive\Documents\ELK-STACK-PROJECT\Images)(C:\Users\fagak\OneDrive\Documents\ELK-STACK-PROJECT\Scripts)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _/etc/ansible/install-elkplaybook.yml_

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _available____, in addition to restricting attacks_____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
Load balancers provide asurance that applications will be available to customers, as well as provide extra security and provide restrictions to attacks to the application. Load balancers also provide reduncy, with the help of the Health Check tools within the load balancers. 
The JumpBox acts as an extra or added security to the network as its the only way to access the network through SSH.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __logs___ and system _traffic____.
- _TODO: What does Filebeat watch for?_
Filebeat monitor logs files and or locations that you specify, collect log events, and forward them to either Elasticsearch or Logstash for indexing.
- _TODO: What does Metricbeat record?_
Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       	| Function   	| IP Address     	| Operating System 	|   	
|------------	|------------	|----------------	        |------------------	|
| Jump Box   	| Gateway    	| JumpBoxProvisioner-ip  	| Linux            	|   	
| Web-1      	| Server     	| 20.106.166.102 	        | Linux            	|   	
| Web-2      	| Server     	| 20.106.166.102 	        | Linux            	|   	
| Web-3      	| Server     	| 20.106.166.102 	        | Linux            	|   	
| Elk Server 	| Monitoring 	| 13.87.190.124  	        | Linux            	|   		

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by __SSH___.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
The Jumpbox, it has the JumpBoxProvisioner-ip

A summary of the access policies in place can be found in the table below.

| Name       	| Publicly Accessible 	| Allowed IP Addresses  	|
|------------	|---------------------	|-----------------------	|
| Jump Box   	|         Yes         	| JumpBoxProvisioner-ip 	|
| Web-1      	|          No         	| 10.0.0.5              	|
| Web-2      	|          No         	| 10.0.0.5              	|
| We-3       	|          No         	| 10.0.0.10             	|
| Elk Server 	|          No         	| 10.1.0.4              	|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
With a singlr playbook, you can deploy multiple servers

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ... Install dependencies; java, nginx, 
- ... Install Elastic Repository
- ... Install Elasticsearch, configure Elasticsearch, start Elasticsearch, Test Elasticsearch
- ... Install Kibana, configure kibana, start and enable kibana, allow traffic on port 5601, Test kibana
- ... Install Logstash, start and enable logstash, configure logstash
- ... Install Filebeat, configure Filebeat, start and enable filebeat, verify Elasticsearch reception of data
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](C:\Users\fagak\OneDrive\Documents\ELK-STACK-PROJECT\Images\docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
10.0.0.6, 10.0.0.6, 10.0.0.10
We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat: Monitors and collects audit logs, depreciation logs, gc logs, server logs and slow logs. gc logs can provide key insights into the behavior and performance of programking languages
Metricbeat: It collects metrics about the system which can be used to detech the behaviou or functionality of the operating system

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
The .yml file, you copy to the Ansible Directory
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
You update the Host file to include the web server and the Elk server with their IP Addresses
- _Which URL do you navigate to in order to check that the ELK server is running?
http://[your.VM.IP]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
