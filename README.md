# Active Directory Lab

## Description
This project involves setting up a small-scale network consisting of two virtual machines. The first virtual machine will function as a domain controller with Active Directory Domain Services, while the second will serve as a client computer. Upon establishing the network, we will add users to the domain using PowerShell. Finally, we will implement group policies objects.
<br />


## Languages and Utilities Used

- <b>VirtualBox</b>
- <b>Microsoft Server 2019<b/>
- <b>Active Directory<b/>
- <b>PowerShell</b> 


## Creating The Virtual Machines:

### Creating the domain controller: <br/> 
Here we use the Windows Server 2019 ISO which can be installed [here](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019). <br/>
<br/>
<img src="https://i.imgur.com/7xzAg4J.png" height="80%" width="80%" />

### Allocating resources:
As we will not be performing demanding tasks with our virtual machine, we will dedicate minimal resources. <br/>
<br/>
<img src="https://imgur.com/WLfn0fo.png" height="80%" width="80%" />

### Allocating disk space: <br/>
A 50 GB virtual disk will be more than enough space. <br/>
<br/>
<img src="https://imgur.com/lsclwXz.png" height="80%" width="80%" />

### Adding network adapters: <br/>
Our domain controller will serve as the gateway for the client virtual machine, allowing it to access the internet. Therefore we will need to add another internal network adapter.  <br/>
<br/>
<img src = "https://imgur.com/NUCwGYp.png" height="80%" width="80%" />
 
<img src = "https://imgur.com/Te8mRGo.png" height="80%" width="80%" />


### Windows Server Setup: <br/>
Our virtual machine is now ready to boot and we can begin setting up Windows Server.

<img src = "https://imgur.com/Xp16mbX.png" height="80%" width="80%" />
<img src = "https://imgur.com/qH3PLDG.png" height="80%" width="80%" />


### Selecting Windows Server Edition: <br/>
We have decided to use this Windows Server 2019 Standard Edition because it includes a graphical user interface (GUI), making it more user-friendly. The main difference between the Standard and Datacenter editions is their support for virtual machines. The Standard Edition allows for up to two virtual machines, while the Datacenter Edition supports an unlimited number. Since we do not plan to run any virtual machines on our Windows Server, the Standard Edition is sufficient for our needs. <br/>
<br/>
<img src = "https://imgur.com/ybu42JW.png" height="80%" width="80%" />

### Type of Installation: <br/>
We are installing Windows Server from scratch so we'll select the custom installation option. <br/>
<br/>
<img src = "https://imgur.com/mHinV9K.png" height="80%" width="80%" />


### Selecting the drive: <br/>
This is our only drive and is where Windows Server will be installed. <br/>
<br/>
<img src = "https://imgur.com/UsEpYjg.png" height="80%" width="80%" />

### Creating the default admin account: <br/>
After a restart Windows Server has been installed and we can create our default admin account. <br/>
<br/>
<img src = "https://imgur.com/ghxkfVH.png" height="80%" width="80%" />

### Windows Server is Installed: <br/>
<br/>
<img src = "https://imgur.com/yJ1FYTh.png" height="80%" width="80%" />

