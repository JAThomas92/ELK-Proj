### ELK-Proj ###

The files in this repository were used to configure the network depicted below.

Diagrams/diagram.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

Ansible/filebeat=playbook.yml

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
- Load balancers are used to remove risk of denial of service attacks and spreads traffic across the server, while also protecting the workstation from the public.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- Log files are monitored by Filebeat
- Metric and statistacl data is collected by Metricbeat and outputs to applications such as Elasticsearch or Logstash

The configuration details of each machine may be found below.

|   Name   | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| DVWA 1   | VM       | 10.0.1.7   | Linux            |
| DVWA 2   | VM       | 10.0.1.8   | Linux            |
| ELK      | ElkStack | 10.0.1.12  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 192.168.56.1

Machines within the network can only be accessed by port 22.
- Jumpbox | 10.0.0.1

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 192.168.56.1         |
| DVWA-VMs | No                  | 10.0.0.1             |
| ELK      | No                  | 10.0.0.1             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible runs from the command line to see that scripts are run identically

The playbook implements the following tasks:
- Change memory on the ELK VM
- Install docker.io
- Install python-pip
- Install docker python module
-  Download and launch docker ELK Stack

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Linux/docker_ps.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.1.7
- 10.0.1.8

We have installed the following Beats on these machines:
- filebeat-7.6.1-amd64.deb

These Beats allow us to collect the following information from each machine:
- Filebeat monitors and collects logs from specified servers and sends this log data to Kibana.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-configuration.yml file to ELK machine.
- Update the hosts file to include servers 10.0.1.7 and 10.0.1.8
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- Which file is the playbook?
filebeat-playbook.yml

- Where do you copy it?
https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.6.1-amd64.deb

- Which file do you update to make Ansible run the playbook on a specific machine?
my-playbook.yml
