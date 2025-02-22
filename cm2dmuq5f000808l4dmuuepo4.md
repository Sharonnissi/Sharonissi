---
title: "Creating Linux VM on Azure, Hosting a Site, and Running Network Scans"
datePublished: Thu Oct 17 2024 18:27:00 GMT+0000 (Coordinated Universal Time)
cuid: cm2dmuq5f000808l4dmuuepo4
slug: creating-a-linux-vm-hosting-a-site-and-running-network-scans
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729190525155/f263aa87-ac27-4c1c-b056-fe2f4173ee10.png
tags: virtual-machine, linux, azure

---

In this blog post, I’ll walk you through how I created a Linux Virtual Machine (VM) on Azure, set up a desktop environment, installed essential tools like Git and Chrome, hosted my portfolio website using Nginx, and secured my VM by closing open ports.

### *Step 1: Creating a Linux Virtual Machine on Azure*

1. **Starting the VM Setup**:  
    I logged into the Azure portal, went to the dashboard, and clicked *Create a resource*. From there, I selected *Virtual Machine*. For this, I created a new resource group called "Test Resource Group" and named the virtual machine "Linux VM".
    
2. **Choosing Region and Image**:  
    I picked my desired region and selected *Ubuntu Server* as my image. I chose the size based on cost considerations.
    
3. **User Credentials and Access**:  
    To securely connect to the VM, I entered a username and used an SSH public key. This ensures that I could SSH into the VM later.
    
4. **Network Settings and Ports**:  
    I configured the inbound ports I wanted to allow for connection, such as SSH, and kept the disk settings as default, choosing a standard SSD to reduce costs.
    
5. **Review and Create**:  
    Once I reviewed all configurations, I clicked *Create*, which prompted me to download the private SSH key. After that, the VM deployment started, and I waited for the deployment to complete.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729184142477/c327755e-d659-4401-972d-45732cb79371.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729184341237/7fa8619e-1030-4bc2-9056-9cd164ae400a.png align="center")
    
    ### *Step 2: Connecting to the VM and Installed Git/Chrome*
    
    Once the VM was deployed, I followed these steps:
    
    1. **SSH into the VM**:  
        Using the SSH private key I downloaded earlier, I connected to my VM using PowerShell.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729184424471/dd2b1580-ff39-4ba8-87b5-8c3ee3fb9547.png align="left")
        
        Since Azure Linux VMs do not come with a graphical user interface (GUI) by default, I had to install a desktop environment to use Remote Desktop Protocol (RDP):
        
        1. I installed a desktop environment Xfce4 on my Linux VM. This allowed me to connect via RDP using a GUI. Xfce4 is a simple desktop environment specifically for Unix operating systems and it gives a simple interface for the users.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729185111785/c4fedeb5-a4cb-45ec-9beb-ce51ea7be709.png align="center")
            
            *<mark>sudo apt -get update</mark>* command I used to updates the list of available packages and their versions
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729185231859/5a72bdc9-8ed6-446f-b529-7b64469b1ca3.png align="center")
            
            The command “*<mark>sudo DEBIAN_FRONTEND=noninteractive apt-get -y install xfce4</mark>*” installs the Xfce4 desktop environment and installs the xfce4 package.  
            This command took a bit of time for it to execute.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729185469499/8e2f7ac8-b31b-436e-8278-df1ee50c26ea.png align="center")
            
            *<mark>sudo apt install xfce4-session</mark>* command will install the xfce4 session manager which is used to handle the log in log out of the desktop sessions, manage the system resources.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729185819762/cbb41e25-68ac-433a-955b-8f89700157c8.png align="center")
            
            *<mark>sudo apt-get -y install xrdp</mark>* command is used to install xrdp which is a remote desktop protocol server and by doing this I’m trying to enable remote desktop access to my Linux machine.
            
            After installing the Linux VM, I successfully connected via SSH, but setting up the GUI using **xrdp** was challenging. I encountered an error when attempting to connect using RDP. The error indicated that my virtual machine was not turned on, even though it was running. After some troubleshooting, I realized the issue was due to the absence of a network inbound rule allowing traffic on **<mark>port 3389</mark>**—the default port for RDP. Once I configured the network to allow port 3389, I was able to connect to the Linux VM's GUI.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729052768799/e2d193dc-783d-4886-a014-3c7810cbd827.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729186229738/42bfbd9d-8150-46ac-9e52-a0e3609fdbfd.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729186268346/8dd1fb36-7f65-449d-9454-448fc9ada838.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729186296927/79c281bb-0fec-4dd4-bcd7-43bd67bee1eb.png align="center")
            
        
        I began by installing Git to manage my code repositories. Here's the command I used: *<mark>sudo apt install git</mark>*
        
        After installing Git, I confirmed the installation by checking the version: *<mark>git --version</mark>*  
        I tried to install Google Chrome on the VM but noticed that it cannot be downloaded like how I downloaded git using the above command, so I need to download it manually for which I had to download the chrome .deb package using command *<mark>wget </mark>* [*<mark>https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb</mark>*](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb%EF%BF%BC%EF%BF%BC) . Then install it using *<mark>sudo apt install ./google-chrome-stable_current_amd64.deb</mark>*
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729186691725/de1e61e7-c066-48ae-89a9-4e6ee28bcfc2.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729186757206/9e09dd3b-ec76-4ca7-b21b-bb4786d496bb.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729186783408/b97047df-ba12-4fe8-9efa-1fc4d79f2f02.png align="center")
        
        ### *Step 3: Hosting My Portfolio Website Using Nginx*
        
        Once connected to the VM, I wanted to host my portfolio website:
        
        I installed Nginx web server, using the following command: *<mark>sudo apt install nginx</mark>*
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729186978687/72063bd6-4c69-463f-b6e7-a6cb5306ad45.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729187107178/7396bd91-0035-4e8f-add4-9d9d40c9edf9.png align="center")
        
        After installing Nginx, I cloned my portfolio website from my GitHub repository using git clone. Then, I replaced the default Nginx webpage by copying my portfolio’s HTML files to Nginx’s web directory which is in *<mark>/var/www/html</mark>* path
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729187237122/460a67b5-80c7-4f44-afe5-78c2b53efa31.png align="center")
        
        I accessed my portfolio site by entering the public IP address of the VM in a browser. Instead of the default Nginx page, my portfolio website was displayed.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729187433192/8289ffa5-643d-4097-8b63-2439da5c0ebb.png align="center")
        
        ### ***Step 4: Running a Network Scan with Nmap***
        
        I installed Nmap which is a network scanning tool, with the following command: *<mark>sudo apt install nmap</mark>*
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729187661475/b5ccbfaa-ffe5-4943-b56e-259a35d31cb6.png align="center")
        
        I scanned my VM to check for open ports and services running on those ports using the command *<mark>sudo nmap -sV </mark>* [*<mark>localhost</mark>*](http://localhost)
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729187790868/21558f7f-e53a-4c8d-9ebd-4aa95ae689a9.png align="center")
        
        I also scanned my home network
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729188289143/a0f115fc-e1b5-46e7-b883-ce12a68ce4ee.png align="center")
        
        If you noticed in this I have used -Pn instead of -sV asking to ignore the ping check and treat the host is online. Also, the output says that the 1000 ports are in ignored state. This is because the router can have firewall settings that will block the network scans or make it invisible for these network scans for security reasons.  
        I used the *<mark>htop</mark>* command to monitor the VM's processes and resource usage in real-time.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729188752352/0d623d4a-6ec1-4af0-a607-4e254935cf18.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729188769207/4dcacac6-24cf-4a97-8070-ed6955b868b4.png align="center")
        
        Using local host scanning, I confirmed which ports were open. Then, I closed the open port.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729188814062/9283de59-fdc2-4ee9-a35c-c9aed41f5762.png align="center")