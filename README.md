## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](https://user-images.githubusercontent.com/86163817/122656874-612f3680-d113-11eb-84c5-4c31fdf69d1c.PNG)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

![Filebeat](https://user-images.githubusercontent.com/86163817/122657082-1c0c0400-d115-11eb-95df-1158e505f95f.PNG)


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Load balancing ensures that the application will be highly stable, in addition to restricting access to the network. The load balancer protects against DDoS attacks by 
redirecting traffic flowing to the server to muplite machines in the cloud preventing the attack from successing. 

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system metrics and system logs.
- Filebeat watches for event data in log files, in this case its monitor system logs for changes and is reporting the findings to elasticsearch then its rewritten and formatted by kibana 

- Metricbeat watches system metrics and running services, it montiors a lot of different services, like for example Apache or MySQL

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux            |
| Web-1    | Container | 10.0.0.10  | Linux            |
| Web-2    | Container | 10.0.0.11  | Linux            |
| Web-3    | Container | 10.0.0.7   | Linux            |
| Elk VM   | Kibana    | 10.1.0.6   | Linux            |

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from my personal ip address- 162.199.190.176    

Machines within the network can only be accessed by the Jump Box machine via ssh with the correct ssh key.
The Elk Vm could only be accessable via sshing from the container within the jump box, the ip address for that is: 13.66.223.181| 10.0.0.4

A summary of the access policies in place can be found in the table below.
| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |       Yes           |   162.199.190.176    |
| Web-1    |       No            |   10.0.0.4           |
| Web-2    |       No            |   10.0.0.4           |
| Web-3    |       No            |   10.0.0.4           |
| Elk-VM   |       No            |   10.0.0.4           | 

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible is a way to automate repetetive tasks needed to be on an network
- Ansible is very user friendly with a lot of doucmention, so people dont need to have a lot of background knowledge to use it 
- Ansible does not require a lot of other tools to run, it only needs a single 3rd party tool called "docker" which makes it very easily accessiable  
- Ansible is also a very powerful free and open source program 

The playbook implements the following tasks:
- change the sysctl confg to allow the correct amount of memory required to run the Elk-VM
- Install docker.io and pyhton3-pip using apt module
- Install docker using pip module 
- Install the container for the Elk-VM (sebp/elk:761) along with a restart policy and published ports (5601:5061,9200:9200,5044:5044) using docker_container module
- Using systemd to restart docker when VM restarts 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker ps](https://user-images.githubusercontent.com/86163817/122655446-1b6c7100-d107-11eb-9fd9-ad3bf585eb75.PNG)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Name  | Ip Addresses  |
|-------|---------------|
| Web-1 | 10.0.0.10     |
| Web-2 | 10.0.0.11     |
| Web-3 | 10.0.0.7      |

We have installed the following Beats on these machines:
- FileBeat 
- MetricBeat
These Beats allow us to collect the following information from each machine:
-Filebeat collects data about system logs and changes made to those logs abd reports them to elasticsearch.for example,Filebeat montiors everything in /var/log/ directroy inside the VM, if something changed in those logs Filebeat would forward that data to elasticsearch.
-Metricbeat collects metric data about the computer itself like for example the operating system or cpu usage

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?
