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
**Reconnaissance with Nmap**
After launching the containers, the first step was to get a terminal inside the Kali container and perform a network scan to identify open ports and services on the target.
1. **Enter the Kali container**:
```
docker exec -it kali bash
```
2. **Find the target's IP**: From inside the Kali terminal, I used `ping` to find the IP address of the `metasploitable` container.
```
ping metasploitable
```
The IP address that comes back is `172.18.0.3`

3. **Run the Nmap scan**:
```
nmap -sV -sC 172.18.0.3
```
`-sV` means Service Version Detection and tells Nmap to attempt to determine the **service name and version number** of whats running on each port. `-sC` is a shortcut for `--script=default` and tells Nmap to run a set of default scripts against the target which include **vulnerability checks**, **enumeration** and **misconfiguration audits**.

**Findings**
The Nmap scan revealed several services with outdated and vulnerable versions.
* **FTP**: `vsftpd 2.3.4` running on port `21/tcp`.
* **SSH**: `OpenSSH 4.7p1` running on port `22/tcp`.
* **Samba**: `Samba smbd 3.0.20-Debian` running on ports `139/tcp` and `445/tcp`.
* **IRC**: `UnrealIRCd` running on port `6667/tcp`.
The `vsftpd 2.3.4` version was targeted due to a well-known backdoor vulnerability.
***
