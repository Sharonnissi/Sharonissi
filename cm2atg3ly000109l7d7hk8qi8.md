---
title: "My Experience Creating Virtual Machines on Azure"
datePublished: Tue Oct 15 2024 19:08:16 GMT+0000 (Coordinated Universal Time)
cuid: cm2atg3ly000109l7d7hk8qi8
slug: my-experience-creating-virtual-machines-on-azure
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729019210612/0ba7d5c9-763e-4cac-a000-211d6f7790d1.png
tags: virtual-machine, linux, azure, cloud-computing, windows

---

In this article, I will share my experience creating two virtual machines on Azure, one running Windows and the other Linux.

**<mark>Windows/Linux VM Setup</mark>**  
You can search for virtual machines in the Azure portal search bar, which will take you to the virtual machine landing page. From there, you can create and configure your VM according to your needs. This includes selecting the operating system image, choosing the size and architecture of the VM, as well as specifying the region and availability zones. Additionally, you can attach disks, configure the network interface, and set up load balancing. There are management options for automatic backups and recovery, along with monitoring configurations. Azure also provides advanced configuration settings, such as adding custom extensions or applications and reserving capacity for the virtual machines.

**<mark>Windows vs. Linux VM Experience</mark>**  
The main difference I observed between Windows and Linux VMs is the user interface. While Windows VMs come with a graphical user interface (GUI), Linux VMs do not provide a GUI when connecting via SSH. With Windows VMs, you can connect using Remote Desktop Protocol (RDP), Bastion, or VPN, and the GUI is readily accessible. However, with Linux VMs, the default connection method is SSH, which does not offer a GUI. To use Remote Desktop with a Linux VM (Ubuntu in my case), I had to install and configure **xrdp**.

**<mark>Challenges with Configuring xrdp on Linux VM</mark>**  
After installing the Linux VM, I successfully connected via SSH, but setting up the GUI using **xrdp** was challenging. Despite following Azure's documentation, I encountered an error when attempting to connect using RDP. The error indicated that my virtual machine was not turned on, even though it was running. After some troubleshooting, I realized the issue was due to the absence of a network inbound rule allowing traffic on **<mark>port 3389</mark>**—the default port for RDP. Once I configured the network to allow port 3389, I was able to connect to the Linux VM's GUI.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729052768799/e2d193dc-783d-4886-a014-3c7810cbd827.png align="center")

**<mark>What is Port 3389?</mark>**  
Port 3389 is the default port for the Remote Desktop Protocol (RDP). It is primarily used to connect to the GUI of Windows VMs. However, once installed, RDP can also be used to connect to a Linux VM's GUI, as I did after configuring **xrdp**.

**<mark>Installing Applications on the VM</mark>**  
For web-based applications, I learned that the first step is to install a web server, which is necessary because client requests are processed by the web server to fetch content for users. Once the web server is set up, you can clone your application from Git and copy it to the VM. You can then access the application using the VM’s public IP address.  
Other methods for deploying applications include using FTP servers, CI/CD pipelines, automation tools, cloud storage services like Azure Blob Storage, or manually connecting to the VM via RDP or SSH for installation.

For local desktop applications on a Windows VM, you can use the default Microsoft Edge browser to install other applications. On a Linux VM, you can use commands like <mark>sudo apt update</mark> ; <mark>sudo apt install git </mark> to ensure packages are updated before installing applications.

**<mark>Additional Features</mark>**  
Azure also offers the option to install applications directly from its platform. You can choose from available apps, and they will be installed on the VM automatically.