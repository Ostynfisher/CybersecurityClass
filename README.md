## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(Images/Diagram with elk.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml or config file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network. Load Balancers protect Web Traffic, Web Security, and web availability. Advantages of a JumpBox include security, virtualization, and control.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs. Integrating Filebeat allows you to monitor log files specified, as well as collecting log events. Inegrating Metricbeat collects statistics and metrics and outputs them to a specified source, in our case Elasticsearch then to Kibana for monitoring.

The configuration details of each machine may be found below.

| Name     | Function | IP Address          | Operating System |
|----------|----------|---------------------|------------------|
| Jump Box | Gateway  |10.0.0.7/20.55.9.3   | Linux            |
| ELK VM   |ELK Server|10.1.0.6/40.122.37.70| Linux            |
| Web 1    |Web Server|     10.0.0.9        | Linux            |
| Web 2    |Web Server|     10.0.0.6        | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- JumpBox IP 20.55.9.3

Machines within the network can only be accessed by the JumpBox. The only VM within the network that can access the ELK VM is the JumpBox at the IP of 10.0.0.7.  

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Home IP Address      |
| Web 1    | No                  |  10.0.0.7            |
| Web 2    | No                  |  10.0.0.7            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible can automate daily tasks, therefore saving time. Automating these simple yet time consuming tasks can allow those working to pursue more important tasks.

The playbook implements the following tasks:
- Install Docker
- Install python3-pip
- Install Docker module
- Increase virtual memory to 262,144
- Download and launch ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!(Images/docker_ps_-a.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1, 10.0.0.9
- Web 2, 10.0.0.6

We have installed the following Beats on these machines:
- Metricbeat
- Filebeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

### Clone the repository
SSH into the control node and follow the steps below:
- Copy the repository with:
'''
git clone https://github.com/Ostynfisher/CybersecurityClass.git
'''
- Move cloned items from /CybersecurityClass/ansible to /etc/ansible
'''
 mv ./CybersecurityClass/ansible/* /etc/ansible/
'''
**WARNING: This replaces entire ansible folder. Executing this code will remove all previous code in this folder.**

- Update the hosts file to include...
Change directories into the ansible directory that you just moved files into.
'''
cd /etc/ansible
'''

You then must open the hosts file within the ansible directory.
'''
nano hosts
'''
Now you uncomment the [webservers] line by removing the #'s, and add the following under the webservers...
'''
10.0.0.5 ansible_python_interpreter=/usr/bin/python3
10.0.0.7 ansible_python_interpreter=/usr/bin/python3
10.0.0.9 ansible_python_interpreter=/usr/bin/python3

[elk]
10.1.0.4 ansible_python_interpreter=/usr/bin/python3
'''

- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

