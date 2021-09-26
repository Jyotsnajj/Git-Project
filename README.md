# Git-Project
Cloud Security Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
![Diagram.draw.io]( file:///C:/Users/jyots/OneDrive/Desktop/Git%20Project/Images/Project%20Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible playbook file may be used to install only certain pieces of it, such as Filebeat.

   install-playbook.yml
![install-playbook.yml](file:///C:/Users/jyots/Documents/Git-Project/Screenshot%202021-09-26%20060942.png)   

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.

What aspect of security do load balancers protect? What is the advantage of a jump box?_

Load Balancer protects network security from attacks by efficiently distributing the network traffic among other servers in the backend pool and thus maintains the efficiency and flow of data.  The advantage of jumpbox is that it acts as pinhole into the environment that enables to access other servers/VM’s on the network, through its public IP address. Hence it secures the internal web servers from untrusted sources of network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the JumpBoxProvisioner and system network.

 What does Filebeat watch for?: It watches for any changes or state of file and transfers its state to disk in the file registry.
 
 What does Metricbeat record?_It records metrics such as CPU, memory and load from the system and services running on the server.

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux |  
| Web-1    | Webserver | 10.0.0.5   | Linux |                  
| Web-2    | Webserver | 10.0.0.6   | Linux | 
| Web-3    | Webserver | 10.0.0.7   | Linux |
| Elk-Server| Monitoring log and metric collection | 10.2.0.4 | Linux |                          

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- Public IP address 

Machines within the network can only be accessed by JumpBoxProvisioner

Which machine did you allow to access your ELK VM? 
JumpBoxprovisioner’s Public IP address

What was its IP address? _
52.170.222.238

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              |    10.0.0.4          |
| Web-1    |   No                |    10.0.0.5          |
| Web-2    |   No                |    10.0.0.6          |
| Web-3    |   No	             |    10.0.0.7          |
|Elk-Server| Yes                 |    10.2.0.4          |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible? _

Ansible is an open-source automation tool and is free of cost. It is easy to deploy and configure the infrastructure with ansible as it uses the simple English language called yaml. It can work without software or agents on the server and can be connected using SSH or python. It is 
Fast, efficient, and fairly consistent with very little latency. The ansible playbook is a better platform for writing programs and modules which are further used by the IT. Therefore, making job more manageable.


The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
* Install docker .io
* Install pip3
* Install Docker python module
* Use more memory
* Download and launch a docker elk container


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

![Docker.ps]( file:///C:/Users/jyots/OneDrive/Desktop/Git%20Project/Images/docker%20ps%20-Screenshot%202021-09-22%20111710.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring_

Machines		   Private IP Addresses
Web-1			   10.0.0.5
Web-2			   10.0.0.6
Web-3 		       10.0.0.7

We have installed the following Beats on these machines:
* Filebeat: It is an agent installed on the server that is responsible for monitoring specific log files or directories and transfers them to elasticsearch or logstash for the purpose of indexing. 
o Filebeat sends information from logs such as audit, server, gc, slow and deprication. For eg: Auditd that collects audit events or some type of activities to facilitate incident investigation.
* Metricbeat: Metricbeat is a lightweight shipper that collects OS’s data and from services running on the server such as memory, network, process, load and CPU. Eg: apache.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

 Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_

Install-elk.yml copied to /etc/ansible/files

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_

install-elk.yml on Elk machine
filebeat-playbook.yml  on Elk / Webservers 1, 2 & 3
metricbeat-playbook.yml on Elk / Webservers 1, 2 & 3


- _Which URL do you navigate to in order to check that the ELK server is running?
 
Elk’s Public IP address:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

-ssh RedAdmin@52.170.222.238
-sudo docker container list -a
-sudo docker start vigorous_burnell
-sudo docker attach vigorous_burnell
-cd /etc/ansible
-create folders: files, roles
-Download the config files into file folder
-Create and update playbook and save in Roles folder
-Run playbook using: ansible-playbook filename.yml




