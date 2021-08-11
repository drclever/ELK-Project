## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)
![Elk Project Diagram](https://github.com/drclever/ELK-Project/blob/master/Images/Elk-Project-Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- The load balancer can detect and drop distributed denial-of-service (DDoS) traffic before it gets to your website.
- Jump boxes allow for more easy administration of multiple systems and provide an additional layer between the outside and internal assets.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- Filebeat watches for log files/locations and collects events related to those files and locations.
- Metricbeat records metrics and statistical data from the operating system and services that are running on the server.

The configuration details of each machine may be found below.

| Name                 | Function   | IP Address                             | Operating System   |
|----------------------|------------|----------------------------------------|--------------------|
| Jump-Box-Provisioner | Gateway    | Public 13.64.49.65, Private 10.1.0.4   | Ubuntu 18.04.5 LTS |
| Web-1                | Web Server | Private 10.1.0.5                       | Ubuntu 18.04.5 LTS |
| Web-2                | Web Server | Private 10.1.0.6                       | Ubuntu 18.04.5 LTS |
| Elk-VM               | Monitoring | Public 52.173.38.178, Private 10.2.0.4 | Ubuntu 18.04.5 LTS |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 92.119.18.28

Machines within the network can only be accessed by Jump-Box-Provisioner.
- Only Jump-Box-Provisioner is allowed to access Elk-VM using SSH. The Jump-Box-Provisioner private IP 10.1.0.4 and the Elk-VM private IP address is 10.2.0.4.

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses   |
|----------------------|---------------------|------------------------|
| Jump-Box-Provisioner | Yes                 | 92.119.18.28 (Port 22) |
| Web-1                | No                  | 10.1.0.4 (Port 22)     |
| Web-2                | No                  | 10.1.0.4 (Port 22)     |
| Elk-VM               | No                  | 10.1.0.4 (Port 22)     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible is an open-source tool.  It is simple to setup and use.  No special coding skills are necessary to use Ansible playbooks.  Ansible is not only powerful (letting you model complex IT workflows), it is flexible.

The playbook implements the following tasks:
- Install docker.io
- Install pip3
- Install Docker python module
- Increase Virtual Memory
- Download and launch a docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 - 10.1.0.5
- Web-2 - 10.1.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects system log files, which we can use to see all events that have happened and are currently happening on a specified server or servers.  These can be analyzed to see system issues, events as well as find unknown files that appear on the system.  An example can be monitoring DB logs.

- Metricbeat collects host metrics used for monitoring performance, which we can use to track things such as memory usage and CPU.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the /etc/ansible/hosts file to include the IP Addresses of Web-1, Web-2, and ELK server as well as assign python3 as the interpreter.
- Run the playbook, and navigate to http://[your.Elk-VM-.Public.IP]:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
