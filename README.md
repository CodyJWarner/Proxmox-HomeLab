# Proxmox-HomeLab

<h2>Project Overview</h2>
This project is a homelab environment built on a old gaming desktop computer using Proxmox. The goal is to create a working virtualization setup where I can deploy and manage servers, practice Linux administration, and build real world skills.
<br>



<h2>Software Used</h2>
<ul>
  <li>Proxmox VE</li>
  <li>Ubuntu Server 24.04 LTS</li>
  <li>OpenSSH</li>
  <li>Docker</li>
</ul>



<h2>Implemented Features</h2>
<strong>Virtualization</strong>
<ul>
  <li>Created and configured Ubuntu Server VM in Proxmox</li>
  <li>Allocated CPU, memory, and storage resources</li>
  <li>Verified VM operation and system performance</li>
</ul>

<strong>Remote Access</strong>
<ul>
  <li>Configured SSH access to the VM from a separate machine</li>
</ul>

<strong>Containerization</strong>
<ul>
  <li>Installed Docker</li>
  <li>Verified with hello-world</li>
</ul>

<h2>Screenshots</h2>
<img width="500" height="311.95" alt="ubuntu-vm-summary" src="https://github.com/user-attachments/assets/3acec851-f761-46d3-b4db-ffbc9dcd6149" />
<br>Ubuntu Server virtual machine running in Proxmox with active resource monitoring.<br><br>

<br>

<img width="500" height="261.90" alt="OpenSSH" src="https://github.com/user-attachments/assets/3a89144c-cdab-4548-90d5-faf3d0fe6868" />
<br>SSH connection establised from main PC to Ubuntu Server VM, confirming successful remote access and system configuration.<br><br>

<br>

<img width="500" height="295.77" alt="docker-hello-world" src="https://github.com/user-attachments/assets/343f7962-6531-4b7d-9597-e4941c7f7df3" />
<br>Docker installation verified by running a test container with hello-world, confirming funtionality on the Ubuntu Server VM.<br><br>




















<h2>Troubleshooting</h2>
<ul>
  <li>Initial boot issues caused by RAM seating and CMOS reset</li>
  <li>Bootable USB problems due to write-protected drive</li>
  <li>Docker installation issues due to repository and GPG key conflicts</li>
</ul>
