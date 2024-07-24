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
We are installing Windows Server from scratch so we will select the custom installation option. <br/>
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
Our domain controller virtual machine now has the correct operating system installed, next steps involve renaming the system, configuring the network adapters and installing Active Directory. <br/>
<br/>
<img src = "https://imgur.com/yJ1FYTh.png" height="80%" width="80%" />

### Renaming this system: <br/>
This is done by the following steps. <br/>
<br/>
Navigating to the start menu and selecting the settings option. <br/>
<br/>
<img src = "https://imgur.com/hSshFsj.png" height="80%" width="80%" />

Then selecting "System". <br/>
<br/>
<img src = "https://imgur.com/GqHmjS1.png" height="80%" width="80%" /> 

Scrolling to the bottom of the list and selecting the "About" setting. <br/>
<br/>
<img src = "https://imgur.com/SzVTKLz.png" height="80%" width="80%" />

Scrolling down again and selecting the "Rename this PC" button. <br/>
<br/>
<img src = "https://imgur.com/nAPpeUA.png" height = "80%" width = "80%" />

As this is our domain controller we will name it "DC" for simplicity. <br/>
<br/>
<img src = "https://imgur.com/eksqARG.png" height = "80%" width = "80%" />

After selecting "Next" this page will be displayed. We will choose to restart later as we also need to configure the network adapters.<br/>
<br/>
<img src = "https://imgur.com/gbk6R8u.png" height = "80%" width = "80%" />

### Configuring Network Adapters: <br/>
Here we're going to be renaming our network adapters and configuring the internal adapter. <br/>
<br/>
First we will head to the settings page and select the "Network & Internet" option. <br/>
<br/>
<img src = "https://imgur.com/oSOwUxt.png" height="80%" width = "80%" /> 

Next we will select "Change adapter options". <br/>
<br/>
<img src = "https://imgur.com/Dvsku6d.png" height="80%" width = "80%" /> 

Here we can see our 2 network adapters. First we must identify which of these is the internal adapter. <br/>
<br/>
<img src = "https://imgur.com/vkn1FXF.png" height="80%" width = "80%" /> 

To find the internal adapter, we should check the IP configuration for each one. To do this we will right click the first adapter and select "Status". <br/>
<br/>
<img src = "https://imgur.com/l6xyEtX.png" height="80%" width = "80%" /> 

Then selecting "Details". <br/>
<br/>
<img src = "https://imgur.com/LJjo1qb.png" height="80%" width = "80%" /> 

The network adapter has a default gateway, meaning it can connect to external networks. Using NAT this adapter connects our internal network to the internet. The other adapter is dedicated to our internal network. However, we can confirm this by reviewing its IP configuration. <br/>
<br/>
<img src = "https://imgur.com/oXaPu44.png" height="80%" width = "80%" /> 

The network adapter does not have a default gateway and has an APIPA-assigned IP address, indicating there is no DHCP server available.Also there isn't a DNS server configured. This all indicates that this adapter is for our internal network. <br/>
<br/>
<img src = "https://imgur.com/VUwkLUj.png" height="80%" width = "80%" /> 

Now that we have identified the adapters we can rename and configure them. <br/>
<br/>
<img src = "https://imgur.com/LTNBPwF.png" height="80%" width = "80%" /> 

<img src = "https://imgur.com/8YNyQ4s.png" height="80%" width = "80%" /> 

Our adapters are now renamed and can be differentiated. Next we will configure our internal adapter. By right clicking it and selecting properties. <br/>
<br/>
<img src = "https://imgur.com/HTB2nc4.png" height="80%" width = "80%" /> 

Then selecting IPv4 and going into properties.<br/>
<br/>
<img src = "https://imgur.com/O9qnfAw.png" height="80%" width = "80%" /> 

We will assign an IP address and subnet mask.The domain controller will function as its own DNS server, as we plan to install DNS server at a later stage, so we will use the loopback address for the DNS server address. <br/>
<br/>
<img src = "https://imgur.com/h2HfKSc.png" height="80%" width = "80%" /> 

