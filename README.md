## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


![Elk-Stack-Diagram](https://user-images.githubusercontent.com/74278185/110698005-55de7d80-81aa-11eb-9e49-7b1100e63b20.PNG)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.


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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Web App  | 10.0.0.5   | Linux            |
| Web-2    | Web App  | 10.0.0.7   | Linux            |
| Web-3    | Web App  | 10.0.0.8   | Linux            |
| Elk Stack|Monitoring| 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from one public IP address.

Machines within the network can only be accessed by the jump box using the public IP obtained from the jump box upon boot up of the VM.


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses/Port|
|----------|---------------------|--------------------------|
| Jump Box |       Yes           | Client Public IP/SSH     |
| Web-*    |       No            |     10.0.0.4/SSH         |
| Elk Stack|       No            |     10.0.0.4/SSH         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows IT administrators to automate away the drudery from daily taks. It also allows for the creation of many machines with the same configurations using a properly built playbook.

**The playbook implements the following tasks**:
- Install Docker.
- Install pip3 and get the packages needed for python3.
- Install Docker python module.
- Increase the virtual memory.
- Download and lauch Elk Container "sebp/elk:761" with the published ports (5601:5601, 9200:9200, 5044:5044).
- Configure Docker service to run on boot-up.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Elk Stack Info](https://user-images.githubusercontent.com/74278185/110694848-655bc780-81a6-11eb-85ca-6b9093d5c9a4.PNG)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.5
- Web-2 10.0.0.7
- Web-3 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- **Filebeat** monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- **Metricbeat** takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to etc/ansible.
- Update the host file to include the IP addresses of the VM's you want to run the playbook for.
- Run the playbook, and navigate to http://<ELK.VM.External.IP>:5601/app/kibana to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
