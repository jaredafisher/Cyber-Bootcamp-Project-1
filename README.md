# Cyber-Bootcamp-Project-1
Cybersecurity Bootcamp ELK Stack Project 1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram](Images/Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

![ELK Playbook](/Playbooks/ELK-Playbook.md)
![Filebeat Playbook](Playbooks/filebeat-playbook.yml)
![Metricbeat Playbook](Playbooks/metricbeat-playbook.yml)

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
Both security load balancers share the work to process the incoming traffic. The advantage of the jump box allows me to close off the entire network. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems of the VMs on the network and system metrics.
Filebeat is for log data. 
Metricbeat collects metrics. 

The configuration details of each machine may be found below.
_

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| ELK VM   | Monitoring | 10.1.0.4   | Linux            |
| Web 1    | Web Server | 10.0.0.5   | Linux            |
| Web 2    | Web Server | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Machine machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 67.189.48.255
- 

Machines within the network can only be accessed by each other. The Web 1 and Web 2 machines send traffic to the ELK server. 
- 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 20.24.217.86         |
| Web 1    | No                  | 10.0.0.1-254         |
| Web 2    | No                  | 10.0.0.1-254         |
| ELK      | No                  | 10.0.0.1-254         |

### Elk Server Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the reusable Ansible playbook does this for me. 

The playbook implements the following tasks:
Enables and configures the docker module
Installs Metricbeat and Filebeat

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![DockerPS](/Images/DockerPS.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 10.0.0.5
Web-2 10.0.0.6

We have installed the following Beats on these machines:
Filebeat
Metricbeat 

These Beats allow us to collect the following information from each machine:
Filebeat collects log data and log events. Metricbeat collects any changes in the system metrics such as login information. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible control node.
- Update the host file to include groups and IP's. 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.
