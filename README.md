
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

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting _public access__ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_the jumpbox adds a layer od defense to the servers and it prevents the outside from direct access to your virtual machines, in the event of a breach. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the ____logs_ and system ___traffic __.
- _TODO: What does Filebeat watch for?_Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to kibana 
- _TODO: What does Metricbeat record?_Metricbeat takes the metrics and statistics that it collects and diplays the info in kibana 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
|  Web1      Gateway     10.0.0.7    Linux    |                  |
| Web2     | Gateway     10.0.0.8     Linux  |                  |
| Web3   |   Gateway    | 10.0.0.9    Linux                |                                                                                                                       
  Elk Server MOnitoring   10.2.0.4    Linux 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ____jumpbox_ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _5601 kibana port 


Machines within the network can only be accessed by _jumpbox provisioner____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_My IP address 99.249.20.174

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|   Web1     | No                  10.0.0.7                     |                      |
|   Web2       No                 |10.0.0.8                    |
    Web3       No                  10.0.0.9
    Elk-Server No                  10.2.0.4

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_=
Ansible is an open-source tool and it is free
Very simple to set up and use: No special coding skills are necessary to use Ansible’s playbooks (more on playbooks later).
Powerful: Ansible lets you model even highly complex IT workflows.
Flexible: You can orchestrate the entire application environment no matter where it’s deployed. You can also customize it based on your needs.
Agentless: You don’t need to install any other software or firewall ports on the client systems you want to automate. You also don’t have to set up a separate management structure.
Efficient: Because you don’t need to install any extra software, there’s more room for application resources on your server.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install pip3
  Install memory
  Launch and attach docker container 
  Install Docker container 
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
10.0.0.7
10.0.0.8
10.0.0.9

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
Filebeats and Metricbeats (bonus) 

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat - collects data about the file system and logs 
Metricbeat - collects machine metrics, such as uptime 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ___playbook__ file to __Ansible node___.
- Update the ___host _ file to include webserver IP and ELK IP
- Run the playbook, and navigate to http://http://13.87.190.207:5601/app/kibana#/home to check that the installation worked as expected, run 
 ansible-playbook elk.yml 
 ansible-playbook filebeat-playbook.yml
 ansible-playbook metricbeat-playbook.yml 

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
ansible-playbook elk.yml 
 ansible-playbook filebeat-playbook.yml
 ansible-playbook metricbeat-playbook.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? Host file 
How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
[webservers]
10.0.0.7
10.0.0.8
10.0.0.0
[elk]
10.2.0.4
- _Which URL do you navigate to in order to check that the ELK server is running? http://http://13.87.190.207:5601/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
