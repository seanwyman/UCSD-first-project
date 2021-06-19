## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting access to the network. 
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump Box | Gateway   | 10.0.0.1   | Linux            |
| Web-1    | Container |            | Linux            |
| Web-2    | Container |            | Linux            |
| Elk VM   | Kibana    |            | Linux            |

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

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible is a way to automate repetetive tasks needed to be on an network
- Ansible is very user friendly with a lot of doucmention, so people dont need to have a lot of background knowledge to use it 
- Ansible does not require a lot of other tools to run, it only needs a single 3rd party tool called "docker" which makes it very easily accessiable  
- Ansible is also a very powerful free and open source program 

The playbook implements the following tasks:
- change the sysctl confg to allow the correct amount of memory required to run the Elk-VM
- Install docker.io using apt module
- Install pyhton3-pip using apt module 
- Install docker using pip module 
- Install the container for the Elk-VM (sebp/elk:761} using docker_container module
- Using systemd to restart docker when VM restarts 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Name  | Ip Addresses  |
|-------|---------------|
| Web-1 | 10.0.0.10     |
| Web-2 | 10.0.0.11     |
| Web-3 | 10.0.0.7      |

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

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
