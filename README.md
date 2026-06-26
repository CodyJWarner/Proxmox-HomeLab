# Proxmox-HomeLab
![Proxmox](https://img.shields.io/badge/Proxmox-VE-orange)
![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04_LTS-blue)
![Docker](https://img.shields.io/badge/Docker-Containers-2496ED)
![SSH](https://img.shields.io/badge/Remote%20Access-SSH-black)
![Portainer](https://img.shields.io/badge/Portainer-CE-13BEF9)
![Pi-hole](https://img.shields.io/badge/Pi--hole-DNS%20Filtering-red)

This repository documents the development of my personal homelab environment built on a repurposed gaming desktop. The project focuses on learning and gaining hands-on experience with virtualization, Linux server administration, remote management, containerization, and infrastructure troubleshooting. Each deployment, configuration change, and service installation is documented step-by-step to demonstrate both implementation and problem-solving skills.
This documents my experience and lessons learned from building and expanding a homelab environment. Each deployment, configuration, and troubleshooting step is recorded to track my progress and what I've learned.
<br>

## Skills Demonstrated
- Bare-metal hypervisor installation and configuration (Proxmox VE)
- Linux server deployment and administration (Ubuntu Server)
- Remote system administration via SSH
- Containerization and container lifecycle management (Docker)
- Container orchestration via GUI tooling (Portainer)
- Hardware and network troubleshooting (RAM, CMOS, DHCP, SSH host keys)

## Table of Contents
- [Proxmox Setup](#proxmox-setup)
- [Ubuntu Server VM](#ubuntu-server-vm)
- [SSH Configuration](#ssh-configuration)
- [Docker Installation](#docker-installation)
- [Portainer Deployment](#portainer-deployment)
- [Pi-hole Deployment](#pi-hole-deployment)
- [Troubleshooting](#troubleshooting)
- [Future Plans](#future-plans)

---
## Proxmox Setup
Installed Proxmox VE on a repurposed gaming desktop to serve as the virtualization platform for the lab. Configured storage and networking during install and confirmed web interface access.

<br>
<img width="500" height="255.86" alt="Prox Setup" src="https://github.com/user-attachments/assets/0d84e968-2807-4390-9daa-7efcf792261a" />

### Purpose
Proxmox VE was installed as the virtualization platform for the homelab, allowing virtual machines and future services to be managed from a single physical system.

---

## Ubuntu Server VM
Deployed Ubuntu Server 24.04 LTS as the primary VM, allocating CPU, memory, and storage, and configuring networking. This VM hosts all containerized services in the lab.

<br>
<img width="500" height="410.38" alt="Ubuntu-Server install" src="https://github.com/user-attachments/assets/5b4e5862-722c-4467-a292-d99d20aa08a2" />

*Initial Installation done inside Proxmox console*

<br>
<img width="500" height="311.95" alt="ubuntu-vm-summary" src="https://github.com/user-attachments/assets/3acec851-f761-46d3-b4db-ffbc9dcd6149" />

*Ubuntu Server virtual machine running in Proxmox with active resource monitoring.*

### Purpose
Ubuntu Server was deployed as the primary virtual machine for the homelab. It provides a stable Linux environment for system administration practice, Docker containers, and future service deployments.

---

## SSH Configuration
Installed and configured OpenSSH Server to enable remote administration from a separate workstation, confirming connectivity and access.

<br>
<img width="500" alt="OpenSSH" src="https://github.com/user-attachments/assets/5077ce9f-7e38-4f71-be59-58860e6d3f8e" />

*SSH connection established from my main PC to the Ubuntu Server VM, including host key verification.*

<br>
<img width="500" alt="ip a output -- server has networking" src="https://github.com/user-attachments/assets/504eb9e8-da12-4ee9-a667-b87f474c3b3f" />

*Confirms network configuration (ip a) on the Ubuntu Server VM after SSH login.*

### Purpose
SSH was configured to allow remote administration of the Ubuntu Server VM from a separate workstation (my main computer) without requiring direct access through the Proxmox console.

---

## Docker Installation
Installed Docker on the Ubuntu Server VM and verified the install with the hello-world container before deploying anything else.

<br>
<img width="500" height="295.77" alt="docker-hello-world" src="https://github.com/user-attachments/assets/343f7962-6531-4b7d-9597-e4941c7f7df3" />

*Docker installation verified by running a test container with hello-world, confirming funtionality on the Ubuntu Server VM.*

<br>
<img width="500" alt="Docker installed and no containers currently running" src="https://github.com/user-attachments/assets/e486f20a-7137-4ba9-a06f-86f22047882b" />

*Confirming Docker is installed and running with no containers active yet.*

### Purpose
Docker was installed to support containerized applications and services within the homelab. This allows additional tools and services to be deployed without requiring separate virtual machines.

---

## Portainer Deployment
Deployed Portainer as a Docker container with persistent storage, exposing a web-based management interface on port 9443.

<br>
<img width="499" height="39" alt="Persistent storage volume created for Portainer data" src="https://github.com/user-attachments/assets/0fdfc1a1-4e1e-4b76-9f23-71733eacbdaf" />

*Creates a persistent Docker volume to retain Portainer's configuration data.*

<br>
<img width="500" alt="Downloads and Runs Portainer  Showing portainer running" src="https://github.com/user-attachments/assets/e98e4375-d2ff-4f34-9d34-dd2e736d4e5f" />

*Deployment commands. Pulling the Portainer image and confirming the container is up and running.*

<br>
<img width="1677" height="838" alt="Portainer dashboard connected to the local Docker environment, displaying container, image, volume, and network management capabilities" src="https://github.com/user-attachments/assets/02110df0-3094-48a7-a4ba-ecc4dcf8e845" />

*Portainer dashboard connected to the local Docker environment, showing container, image, volume, and network management.*

### Purpose
Portainer was deployed to provide a graphical management interface for Docker containers running on the Ubuntu Server VM.

---

## Pi-hole Deployment
Deployed Pi-hole as a Docker container to provide DNS filtering capabilities within the homelab. During deployment, a networking conflict was encountered because Ubuntu's "systemd-resolved" service was already using DNS port 53. To continue testing without disrupting the host operating system, Pi-hole was temporarily configured to use an alternate host port.

<br>
<img width="468" height="41" alt="Created folders to save pihole configuration settings" src="https://github.com/user-attachments/assets/51603506-3dd0-4ffe-a058-6c59a72b70f8" />

*Created persistent directories to store Pi-hole configuration files and DNS settings outside of the Docker container. This ensures configuration data is retained if the container is recreated.*

<br>
<img width="604" height="250" alt="created pihole container" src="https://github.com/user-attachments/assets/d0cee1d2-72d6-405b-b4ba-2d57b6564150" />

*Downloaded the official Pi-hole image from Docker Hub and deployed the container with persistent storage, Docker restart policies, and web interface access.*

<br>
<img width="2166" height="130" alt="Verified Pihole is running" src="https://github.com/user-attachments/assets/03550ee0-5ea1-4d63-a89b-2af5e18dc955" />

*Verified that the Pi-hole container was running successfully alongside the existing Portainer container. The container was temporarily mapped to host port 5353 because the default DNS port was unavailable.*

<br>
<img width="1241" height="1300" alt="Pi hole running on web interface" src="https://github.com/user-attachments/assets/05e68adc-0bfb-45ae-9df7-32def290d969" />

*Successfully accessed the Pi-hole administrative dashboard, confirming the container deployment. The dashboard displays available blocklists, DNS statistics, and monitoring features.*

### Purpose

Pi-hole was deployed to learn and test DNS filtering within my homelab while expanding my understanding of Docker networking, Linux administration, and containerized network services. My next goal is to configure Pi-hole as the primary DNS server for client devices and observe DNS traffic in a real-world environment.

---

## Troubleshooting

| Issue | Resolution |
|---|---|
| System initially failed to boot and display video output | Reseated RAM modules and CMOS battery during hardware troubleshooting |
| Unable to recreate installation media | Replaced a write-protected USB drive |
| Docker install failed | Corrected Docker repository configuration and package sources |
| Ubuntu VM received a new IP address after reboot | Configured a static IP address to prevent future DHCP reassignment |
| Pi-hole failed to start because DNS port 53 was already in use | Identified "systemd-resolved" as the conflicting service and temporarily mapped Pi-hole to host port 5353 for testing while planning full DNS integration |

---

## Future Plans

- Complete Pi-hole integration for DNS filtering
- Learn Docker Compose for multi-container deployments
- Deploy Uptime Kuma for service monitoring
- Deploy additional self-hosted services
- Create additional virtual machines for network segmentation
- Configure automated backups for Docker volumes and virtual machines
