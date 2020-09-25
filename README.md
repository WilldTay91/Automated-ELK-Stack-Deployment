## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Red-Team Network Topography](https://github.com/WilldTay91/Automated-ELK-Stack-Deployment/blob/master/ELK-Stack_Screen-Shots/ELK-PROJECT-TOPOGRAPHY.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml and filebeat-playbook.yml files may be used to install only certain pieces of it, such as Filebeat and Metricbeat

https://github.com/WilldTay91/Automated-ELK-Stack-Deployment/blob/master/VM_Config_Files/Install-ELK.yml

https://github.com/WilldTay91/Automated-ELK-Stack-Deployment/blob/master/VM_Config_Files/Filebeat_Metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
Load balancers offer security on the application layer, making it's routing decsions based off highly detailed information gathered from incoming traffic, while also keeping the network redundant.
To add even more security to the network, we ensured the only node that is externally exposed is the Jump-Box, while access to any other node on the network is restricted by SSH key. The Jump-Box is not externally exposed to the internet, but rather specific IPs through a security group configured with strict internal and external rule sets.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log data and system statistics.

The configuration details of each machine may be found below.
| Name        | Function      | IP Address | Operating System  |
|-------------|---------------|------------|-------------------|
| Jump-Box    | Gateway       | 10.0.0.4   | Linux/Ubuntu 18.4 |
| Web1        | DVWA/Docker   | 10.0.0.5   | Linux/Ubuntu 18.4 |
| Web2        | DVWA/Docker   | 10.0.0.6   | Linux/Ubuntu 18.4 |
| Web3        | DVWA/Docker   | 10.0.0.7   | Linux/Ubuntu 18.4 |
| ELK-Machine | ELK Container | 10.0.0.8   | Linux/Ubuntu 18.4 |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP address: 73.220.175.58

Machines within the network can only be accessed by Jump-Box, with the IP address of 

A summary of the access policies in place can be found in the table below.
| Name        | Publicly Accessible | Allowed Ports   | Allowed IP Addresses                                  |
|-------------|---------------------|-----------------|-------------------------------------------------------|
| Jump-Box    | Yes                 | 3389,22,80,5601 | 73.220.175.57, 10.0.0.5, 10.0.0.6, 10.0.0.7, 10.0.0.8 |
| Web1        | No                  | 22              | 10.0.0.4,10.0.0.8                                     |
| Web2        | No                  | 22              | 10.0.0.4,10.0.0.8                                     |
| Web3        | No                  | 22              | 10.0.0.4,10.0.0.8                                     |
| ELK-Machine | Yes                 | 5601,22         | 10.0.0.4,52.175.215.241                               |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows quick deployment of virtual machines and configurations can be stored as playbooks and used again as needed.
The playbook implements the following tasks:
- Install Docker ISO
- Install Docker/python modules
- Increase virtual memory
- Use increased memory
- Download and launch ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
!(https://github.com/WilldTay91/Automated-ELK-Stack-Deployment/blob/master/ELK-Stack_Screen-Shots/docker_ps.png)
