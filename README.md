## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Cloud-Elk-Stack-Project/Diagrams/Elk Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availabe for the clients, in addition to restricting the attacks to the network.

The aspects of security load balancers protects and the advantage of a jump box is:
A load balancercan add additional layers of security to the websites without any changes to the applications. It plays an important role as computing moves to the cloud. Jump box prevents all Azure VM's to expose to the public. it uses the higher security authentication such as multi factor aunthetication.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

Filebeat watches for:
Filebeat is often used to collect log files from very specific files, such as logs generated by Apache, Microsoft Azure tools, the Nginx web server, or MySQL databases. plays the role of logging agent.

Metricbeat records:
Metricbeat collects metrics from your systems and services, and ships them to the output that you specify such as Elasticsearch. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function   | IP Address       | Operating System |
|------------|------------|------------------|------------------|
| Jump Box   | Gateway    | Private 10.0.0.4 | Linux            |
| Web 1      | Server     | 10.0.0.5         | Linux            |
| Web 2      | Server     | 10.0.0.6         | Linux            |
| ELK Server | Monitoring | 10.1.0.4         | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
 
:5601 Kibana

Machines within the network can only be accessed by Jump Box.
The machine we allowed to access our ELK VM and its IP addresses:

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.4             |
| web 1    | No                  | 10.0.0.4             |
| web 2    | No                  | 10.0.0.4             |
|ELK Server| No                  | 10.0.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

The main advantage of automating configuration with Ansible is:
It is rapidly rising to the top in the world of automation tools. It frees up the time and increases efficiency. It is agentless, easy to set up and use.

The playbook implements the following tasks:

In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- install docker.io
- install python3-pip
- download image
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Cloud-Elk-Stack-Project/Images/docker ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring
| Web 1 | 10.0.0.4 |   |   |   |
|-------|----------|---|---|---|
| Web 2 | 10.0.0.5 |   |   |   |

We have installed the following Beats on these machines:

Beats successfully installed
Filebeats
Metricbeats

These Beats allow us to collect the following information from each machine:

Data each beat collects, and an example of what we expect to see.
Filebeat watches the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for clueing.
matricbeats collects metrics and statistics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible.
- Update the host file to include ELK and webservers.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it?
cd/etc/ansible ansible-playbook filebeat-config.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
ansible-playbook filebeat-playbook.yml
- _Which URL do you navigate to in order to check that the ELK server is running?
http://[your.VM.IP]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/files/filebeat-config.yml
