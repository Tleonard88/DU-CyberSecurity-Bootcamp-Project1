# DU CYBERSECURITY PROJECT 1 THOMAS LEONARD

DU cybersecurity project 1 for bootcamp

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![VIRTUAL NETWORK DIAGRAM](Diagrams/Virtual_Network_Diagram_with_Kibana_VM_included.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible yml files may be used to install only certain pieces of it, such as Filebeat.

  ![install-elk.yml](Ansible/install-elk.yml)
  ![filebeat-playbook.yml](Ansible/filebeat-playbook.yml)
  ![metricbeat-playbook.yml](Ansible/metricbeat-playbook.yml)

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
- Load balancers significantly help reduce the risk of a Denial of Service or Dedicated Denial of Service attack. This allows for the load balancer to distrubute traffic evenly among the three available web servers, making sure one server is not overloaded by high traffic, and can forward traffic to the least used server at the point a user accesses the web server. The advantage of using a jumpbox within the network is that it allows for easy setup of multiple servers using an ansible container to run a playbook on all available virtual machines, saving signficant time and resources by setting up the servers simultaneously. The jumpbox also creates an additional level of security before traffic reaches the servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the event logs and system metrics.
- Filebeat will watch for log files or directories and create an easy way to foward and centralize them.
- Metricbeat collects metrics and statistics from the system and any services that are being run on your server, to help monitor for potential attacks or unusual activity on the web servers.

The configuration details of each machine may be found below.

| Name    | Function          | IP Address | Operating System |
|---------|-------------------|------------|------------------|
| Jumpbox | Gateway           | 10.0.0.4   | Linux            |
| Web1    | Web Server        | 10.0.0.5   | Linux            |
| Web2    | Web Server        | 10.0.0.8   | Linux            |
| Web3    | Web Server        | 10.0.0.9   | Linux            |
| Elk-VM  | Monitoring System | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Admin's Personal IP address

Machines within the network can only be accessed by the Jumpbox.
- Only the Jumpbox can access the Elk-VM, it's IP address is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name               | Publicly Acessable | Allowed IP Addresses                                                                      |
|--------------------|--------------------|-------------------------------------------------------------------------------------------|
| Jumpbox            | Yes                | Admin's Personal Public IP Address                                                        |
| Load Balancer (LB) | Yes                | Admin's Personal Public IP Address (Can be updated to all traffic in practical situation) |
| Web1               | No                 | 10.0.0.4 (Also Via LB Public IP)                                                          |
| Web2               | No                 | 10.0.0.4 (Also Via LB Public IP)                                                          |
| Web3               | No                 | 10.0.0.4 (Also Via LB Public IP)                                                          |
| Elk-VM             | Yes                | Admin's Personal Public IP Address                                                        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible will allow for the creation of a playbook through a yml scripting process. This allows for all servers to be configured simultaneously and also ensures all servers will be configured the same. In addition to being a more efficient and time saving method, it is also more accurate.

The playbook implements the following tasks:
- Installs Docker
- Installs Python-pip
- Installs Docker Python Module
- Increases virtual memory
- Downloads and launches a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker PS screenshot](Elk Screenshot.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

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

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
