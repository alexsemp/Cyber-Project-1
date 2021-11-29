## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project Network Diagram](/Diagrams/network diagram (project).PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the 'ansible files' file may be used to install only certain pieces of it, such as Filebeat.

  - [Ansible Files](https://github.com/alexsemp/Cyber-Project-1/tree/main/ansible%20files)

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
- Load balancers protect Network security, specifically the availability portion of the CIA triad. A specific example would be from a DDOS attack, which attempts to flood a system and overload it until it crashes. Load balancers help against these types of attacks. The advantage of having a jump box is it increases security and adds an additional layer of defense. It allows for tighter access for administrators and anyone working witihn them because it only allows for a single access point, which can then open up into a plethora of other servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- Filebeat is used for forwarding and centralizing log data. It will monitor the admin log files or locations that you specify and it also collects log events and forwards them either to Elasticsearch or Logstash for indexing
- Metricbeat is similar in a way, but instead, it is a lightweight shipper for metrics. It takes metrics and other statistics and forwards or ships them to where you design them to go. It is a great tool for monitoring servers and see how other services are running within these servers.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.1   | Linux            |
| Web-1    | VM/server | 10.0.0.7   | Linux            |
| Web-2    | VM/server | 10.0.0.8   | Linux            |
| Web-3    | VM/server | 10.0.0.9   | Linux            |
| Elk-VM   | VM/server | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box-provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 137.117.88.237

Machines within the network can only be accessed by Jump-Box-Provisioner.
- Tehcnically the jump-box-provisioner is the machine that can access Elk, but docker has to be running and you access it through the container. The Elk-VM ip address is: 10.1.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 10.0.0.4             |
| Web-1    | No                  | 10.0.0.7             |
| Web-2    | No                  | 10.0.0.8             |
| Web-3    | No                  | 10.0.0.9             |
| Elk-VM   | No                  | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Using Ansible to automate routine or daily tasks allows the administrator(s) to spend less time on repetitive daily tasks and allows for them to spend more time on projects that need more attention and time. In more technical terms, it helps  with the representation of Infrastructure as Code (IAC).

The playbook implements the following tasks:
- Install Docker
- Install python3-pip
- Install Docker module
- Increase virtual memory
- Use more memory
- Download and launch a Docker Elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![Docker PS Screenshot](/screenshots/761 SS.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.0.0.7), Web-2 (10.0.0.8), Web-3 (10.0.0.9)

We have installed the following Beats on these machines:
- Metricbeat & Filebeat

These Beats allow us to collect the following information from each machine:
- They allow us to monitor the logs and locations specified by the user. They also allow us to keep record metrics from the services running on each server and how they are performing. You may find logstash  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- Navigate to: http://20.114.128.48:5601/app/kibana to see if the Elk server is running.

### These are potential commands you may want to use:
- Use ansible-playbook <playbook-filename.yml> to run playbooks
- Nano to update files
- Ctrl O to save then Ctrl X to exit file config
- ssh user@ip to enter certain servers
