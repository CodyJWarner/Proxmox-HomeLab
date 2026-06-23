# Proxmox-HomeLab
![Proxmox](https://img.shields.io/badge/Proxmox-VE-orange)
![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04_LTS-blue)
![Docker](https://img.shields.io/badge/Docker-Containers-2496ED)
![SSH](https://img.shields.io/badge/Remote%20Access-SSH-black)
![Portainer](https://img.shields.io/badge/Portainer-CE-13BEF9)

This repository documents the development of my personal homelab environment built on a repurposed gaming desktop. The project focuses on learning and gaining hands-on experience with virtualization, Linux server administration, remote management, containerization, and infrastructure troubleshooting. Each deployment, configuration change, and service installation is documented step-by-step to demonstrate both implementation and problem-solving skills.
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
SSH was configured to allow remote administration of the Ubuntu Server VM from a separate workstation without requiring direct access through the Proxmox console.

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

## Troubleshooting

| Issue | Resolution |
|---|---|
| System initially failed to boot and display video output | Reseated RAM modules and CMOS battery during hardware troubleshooting |
| Unable to recreate installation media | Replaced a write-protected USB drive |
| Docker install failed | Corrected Docker repository configuration and package sources |
| Ubuntu VM received a new IP address after reboot | Configured a static IP address to prevent future DHCP reassignment |

---

## Future Plans

- Configure a static IP for the Ubuntu Server VM
- Deploy Pi-hole for DNS filtering
- Deploy Uptime Kuma for service monitoring
- Implement centralized logging
- Add additional VMs for segmented services
