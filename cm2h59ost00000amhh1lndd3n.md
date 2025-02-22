---
title: "What I Learned About Virtualization & Hypervisors"
datePublished: Sun Oct 20 2024 05:25:49 GMT+0000 (Coordinated Universal Time)
cuid: cm2h59ost00000amhh1lndd3n
slug: what-i-learned-about-virtualization-hypervisors
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729401751398/91e3cf59-affe-4d15-a138-7ba610016cac.png
tags: server, cloud-computing, vmware, virtualization, linkedin-learning, hypervisor, baremetal, vmware-esxi

---

Virtualization means instead of using multiple physical servers to run different services like for emails one server, for database another server when we use one single physical server with different operating systems on it to run different services is called virtualization.  
This virtualization is done by using a software called *<mark>hypervisor</mark>*. This will allow one server to run multiple virtual machines and allocate and share the system resources like storage space, RAM, and CPUs.  
*<mark>Types of Hypervisors</mark>*  
Hypervisors are of two types: Type 1 and Type 2.

*<mark>Type 1 Hypervisors:</mark>* Installed on bare metal (devices without existing software or operating systems). Examples include VMware ESXi, Citrix XenServer, and Microsoft Hyper-V.

*<mark>Type 2 Hypervisors:</mark>* Installed on systems with an existing operating system. Examples include Oracle VM VirtualBox, Microsoft Virtual PC, and VMware Workstation.

For Type 1 hypervisors, you need to install the hardware first (motherboard, RAM, CPUs, and storage drives) before installing the hypervisor directly on the bare metal server. No operating system is installed on this server. Once the hypervisor is in place, we create virtual machines (VMs), allocating hardware resources and loading operating systems onto these VMs. These virtual machines are replicas of physical computers, allowing us to deploy applications later. Type 1 hypervisors are primarily used at the enterprise level and act as an operating system themselves.

Type 2 hypervisors are commonly used on personal computers, allowing users to test different operating systems or projects. For example, I can install Oracle VirtualBox on my Windows laptop and run a Linux operating system alongside it.

*<mark>The Role of Hypervisors</mark>*  
When running a hypervisor, we have a host, the actual physical server running the hypervisor software. This host runs different virtual machines, which exist only in the memory of the hypervisor. In cloud computing, providers run hypervisor software on physical servers, granting companies access to build their virtual machines. Companies won’t know which data center or machine hosts their VMs.

*<mark>Features of Hypervisors</mark>*  
A notable feature is live migration. If there's an issue with the host server, we can move virtual machines to another host without turning them off. The migration time depends on bandwidth and VM size, and this process is managed by an administrator.

Another useful feature is *<mark>snapshots or checkpoints</mark>*, allowing us to capture the VM's current state before making changes. If new changes aren't suitable, we can revert to the previous state using these snapshots. However, they consume more storage than the VM itself, and if the VM's drive is damaged, the snapshots are lost. Traditional backups are more reliable than snapshots.

*<mark>Benefits of Virtualization</mark>*  
Virtualization is cost-effective, enabling portable VMs that can be transferred between servers, maximizing computing resource use. It also provides backup and recovery options, routing traffic to backup servers if one goes down. Hypervisors automatically adjust resources for VMs.

*<mark>Virtualization of the Desktop</mark>*  
This utilizes Virtual Desktop Infrastructure (VDI). When a user logs in, the server sends a copy of the VM to the user’s machine. The user’s laptop acts as a terminal. Since the desktop environment runs on a remote server, files should be saved on a network drive, as they won’t be saved upon logging off.

*<mark>Key Virtualization Concepts</mark>*  
*<mark>Virtual CPU: </mark>* Part of the physical CPU allocated to run VMs.  
*<mark>Virtual Network:</mark>* It is a similar copy of the physical network but is software-designed. It lets the virtual machines communicate with each other. In this, there can be two types of communication: Two virtual machines hosted on one machine communicating with each other. One of the virtual machines trying to communicate with the outside world (the internet). In the second scenario, VM1 will place the traffic on the physical network and then communicate with the internet. In the first scenario, where two virtual machines hosted on the same machine need to talk, older hypervisors used to send traffic through the physical network, with the adapter sending it to the switch, which then sent it to the other virtual machine. This long process has been improved in newer hypervisors by installing a virtual switch that exists only in the memory of the computer. Now, instead of the traffic going through the physical network, VM1’s traffic will be sent to the virtual switch, which will route it to VM2.  
*<mark>Virtual Storage:</mark>* Combines all physical storage units (SSD, hard drives) into a single unit.  
*<mark>Virtual Graphics:</mark>* Virtualization of the physical GUI, allowing multiple VMs to share a single physical GUI.  
*<mark>Virtual Memory:</mark>* A memory management technique that moves less frequently accessed files to a separate storage space (like page files), enabling large applications to run without exhausting memory.  
**<mark>Common Issues in Virtualization and Troubleshooting</mark>**  
*<mark>Access Denied Errors:</mark>* These may occur when connecting to VMs if the hypervisor lacks the proper permissions for the VM files and folders.  
*<mark>Time Accuracy Issues: </mark>* Ensuring the VM clock is accurate is crucial.  
*<mark>Antivirus Impact: </mark>* Antivirus scanning large VM files can slow performance, so optimizing settings is essential.  
*<mark>Graphics and Resource Configuration: </mark>* Proper GPU settings and ensuring adequate CPU and memory for VMs are important.  
*<mark>Unique Identifiers:</mark>* Each VM must have a unique name, IP address, and MAC address.  
*<mark>Firewall Settings:</mark>* Proper software firewalls on both host and guest machines can prevent network performance issues.