# Metasploitable2 Docker Lab
## Overview
This repository documents a cybersecurity lab that demonstrates the process of **reconnaissance and exploitation**. The lab environment was created using **Docker** to set up a secure, isolated network with a **Kali Linux** container as the attacking machine and a **Metasploitable2** container as the vulnerable target.

The primary objective was to identify and exploit common, well-known vulnerabilities to gain a comman shell on the target system.
***
## Lab Environment Setup
The lab was built using **Docker** and **Docker Compose** on a Windows host machine. The `docker-compose.yml` file defines the two containers and a private network to allow them to communicate. 

**Prerequisites**
* **Docker Desktop**: Running on the host machine.
* **Git**: Installed on the host machine for cloning and version control.

**Setup Instructions**
1. **Clone the Repository**: Clone this repository to your local machine.
```
git clone https://github.com/MSearleProjects/cybersecurity-lab-1-metasploitable.git
cd cybersecurity-lab-1-metasploitable
```
2. **Launch the Containers**: Run the `docker-compose up` command from the root of this directory. This command reads the `docker-compose.yml` file and starts both containers.
```
docker-compose up -d
```
***
## Lab Walkthrough
