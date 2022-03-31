## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram]("Diagram/Untitled Diagram.drawio.png")

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file.

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
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? It protect the settings of web servers

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Data and system logs.
- _TODO: What does Filebeat watch for? forwarding and centralizing log data
- _TODO: What does Metricbeat record? takes the metrics and statistics that it collects and ships them to the output that you specify, for instance Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.7 104.45.223.161| Linux|
| Web 1    | Website  |10.0.0.5    | Linux            |
| Web  2   |Website Redandancy| 10.0.0.6       | Linux|
| ELK      | monitoring| 10.1.0.4 13.67.166.64 | Linux|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
Add Jumpbox IP addresses

Machines within the network can only be accessed by Jumpbox.
Which machine did you allow to access your ELK VM? Jumpbox and my public IP. What was its IP address?76.103.103.187

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
|Jump Box  |                     | my ip_address        |
|Elk       |    No               | My ip_address        |
|DVWA1     |    No               |10.0.0.7              |
|DVWA2     |    No               |10.0.0.7              |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous becaus servcies running can be limited, system installation and update can be streamlined, and processes become more replicable.
What is the main advantage of automating configuration with Ansible?  Helps considerably with the representation of Infrastructure as Code (IAC).

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
apt Install docker.io
docker pull sepb/elk
docker run into ansible
change the insible hosts to elkserver
Change the ansible remote user to host name
Create a yml script to connection to elk application
Make sure the host connected to 5601,9200 and 5044


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Update the path with the name of your screenshot of docker ps output](ImagesforDaytwo/sudodockerpsJPG)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring 10.0.0.5 and 10.0.0.6

We have installed the following Beats on these machines: Filebeat.yml and Metricbeat.yml
- _TODO: Specify which Beats you successfully installed_ metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events and what they are trying to do once they login to these servers, etc.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ssh-keygen file to ssh public key.
- Update the security file to include ip_address
- Run the playbook, and navigate to terminal to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine?  Update the Hosts(PrivateIpAddress) and ansible.cfg(remote_user:HOSTNAME) How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running? http://<(YourIpAddress)>:5601/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
ssh jump@IP address.
Run docker -ti container/ansible
Change the director. /etc/ansible
ssh-keygen to web services
nano hosts Update IP on webservers "Elkservers"
nano ansible.cfg (Remote_user to the server I want to use it
