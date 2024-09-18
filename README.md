# Active Directory Lab

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-this-project">About this project</a>
    <ul>
      <li><a href="#languages-and-utilities"> Languages and Utilities</a></li>
    </ul>
    <li><a href="#creating-the-domain-controller-system">Creating the Domain Controller System</a>
        <ul>
         <li><a href="#creating-the-dc-virtual-machine"> Creating the Virtual Machine</a></li>
          <li><a href="#adding-network-adapters"> Adding Network Adapters</a></li>
         <li><a href="#windows-server-installation"> Windows Server Installation</a></li>
        </ul>
    <li><a href="#configuring-the-domain-controller-system">Configuring the Domain Controller System</a>
        <ul>
         <li><a href="#changing-the-hostname">Changing the Hostname</a></li>
         <li><a href="#configuring-network-adapters"> Configuring Network Adapters</a></li>
        </ul>
         <li><a href="#active-directory-installation-and-domain-creation">Active Directory Installation and Domain Creation</a>
        <ul>
         <li><a href="#installing-active-directory-domain-services"> Installing Active Directory Domain Services</a></li>
          <li><a href="#domain-creation"> Domain Creation</a></li>
            </ul>
    <li><a href="#creating-an-admin-account">Creating an Admin account</a>
    <li><a href="#adding-networking-roles-and-features">Adding Networking Roles and Features</a>
    <ul>
         <li><a href="#installing-rasnat"> Installing RAS/NAT</a></li>
         <li><a href="#installing-and-configuring-dhcp"> Installing and configuring DHCP</a></li>
        </ul>
   <li><a href="#creating-ous-and-users">Creating OUs and Users </a>
   <li><a href="#creating-ous-and-users">Creating the Client System </a>
     <ul>
         <li><a href="#creating-the-client-virtual-machine"> Creating the Client Virtual Machine</a></li>
         <li><a href="#windows-10-installation"> Windows 10 Installation</a></li>
       </ul>
         <li><a href="#hostname-change-domain-integration-and-network-verification"> Hostname Change, Domain Integration, and Network Verification</a></li>
    <ul>
         <li><a href="#windows-10-installation"> Signing into the Domain Using a User Account</a></li>
        <li><a href="#windows-10-installation"> Verifying Network Connectivity and Functionality</a></li>
        
          
   
    
</details>


## About this project
This self-study project involves setting up a small-scale network consisting of two virtual machines. The first virtual machine will function as a domain controller with Active Directory Domain Services, while the second will serve as a client computer. After establishing the network, I will carry out standard administrative tasks in Active Directory, including password resets, applying Group Policies, and deploying applications, while also experimenting as a learning tool for myself.
<br />


## Languages and Utilities 

- <b>VirtualBox</b>
- <b>Microsoft Server 2019<b/>
- <b>Active Directory<b/>


## Creating the Domain Controller System

This section covers the initial setup of the DC virtual machine, including the allocation of resources, configuration of network adapters, and installation of Windows Server 2019.

### Creating the DC Virtual Machine

Here we use the Windows Server 2019 ISO which can be installed [here](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019). <br/>
<br/>
<img src="https://i.imgur.com/7xzAg4J.png" height="80%" width="80%" />

### Allocating resources
As we will not be performing demanding tasks with our virtual machine, we will dedicate minimal resources. <br/>
<br/>
<img src="https://imgur.com/WLfn0fo.png" height="80%" width="80%" />

### Allocating disk space <br/>
A 50 GB virtual disk will be more than enough space. <br/>
<br/>
<img src="https://imgur.com/lsclwXz.png" height="80%" width="80%" />

### Adding network adapters 
Our domain controller will serve as the gateway for the client virtual machine, allowing it to access the internet. Therefore we will need to add another internal network adapter.  <br/>
<br/>
<img src = "https://imgur.com/NUCwGYp.png" height="80%" width="80%" />
 
<img src = "https://imgur.com/Te8mRGo.png" height="80%" width="80%" />


### Windows Server Installation
Our virtual machine is now ready to boot and we can begin installing Windows Server.

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

## Configuring the Domain Controller System
Our domain controller virtual machine now has the correct operating system installed, next steps involve renaming the system, configuring the network adapters and installing Active Directory. <br/>
<br/>
<img src = "https://imgur.com/yJ1FYTh.png" height="80%" width="80%" />

### Changing the Hostname 
This is done by the following steps. <br/>
<br/>
Navigating to the start menu and selecting the settings option. <br/>
<br/>
<img src = "https://imgur.com/hSshFsj.png" height="80%" width="80%" />

Then selecting "System". <br/>
<br/>
<img src = "https://imgur.com/GqHmjS1.png" height="80%" width="80%" /> 

Scrolling to the bottom of the list and selecting "About". <br/>
<br/>
<img src = "https://imgur.com/SzVTKLz.png" height="80%" width="80%" />

Scrolling down again and selecting "Rename this PC". <br/>
<br/>
<img src = "https://imgur.com/nAPpeUA.png" height = "80%" width = "80%" />

As this is our domain controller we will name it "DC" for simplicity. <br/>
<br/>
<img src = "https://imgur.com/eksqARG.png" height = "80%" width = "80%" />

After selecting "Next" this page will be displayed. We will choose to restart later as we also need to configure the network adapters.<br/>
<br/>
<img src = "https://imgur.com/gbk6R8u.png" height = "80%" width = "80%" />

### Configuring Network Adapters
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

## Active Directory Installation and Domain Creation
In this section, we will cover the process of installing Active Directory Domain Services on the Windows Server and creating a new domain. This includes adding the Active Directory Domain Services role to the server, promoting the server to a domain controller, and configuring the necessary settings for domain creation. By the end of this section, we will have a fully functional domain environment.

### Installing Active Directory Domain Services

To install Active Directory we select the "Add roles and features" option on the server manager window. <br/>
<br/>
<img src = "https://imgur.com/Go4cbeW.png" height="80%" width = "80%" /> 

A prompt will appear explaining that a few tasks need to have been completed. As we have done this we can continue by selecting "Next". <br/>
<br/>
<img src = "https://imgur.com/wTLz08g.png" height="80%" width = "80%" /> 

We will not be using role services for Virtual Desktop Infrastructure so we will select the first option. <br/>
<br/>
<img src = "https://imgur.com/cSPdFxI.png" height="80%" width = "80%" /> 

We will be asked to choose a destination for the installation. We only have 1 server so there is not much of a choice. We can continue. <br/>
<br/>
<img src = "https://imgur.com/R5VmML6.png" height="80%" width = "80%" /> 

Here we are able to see all the roles we can potentially add to our server. For now we will only select Active Directory Domain Services. <br/>
<br/>
<img src = "https://imgur.com/5C6YegD.png" height="80%" width = "80%" /> 

Here are all the features we can potentially add. The installer has automatically selected two options which we will install as they are required for Active Directory Domain Services. <br/>
<br/>
<img src = "https://imgur.com/nK9hqcY.png" height="80%" width = "80%" /> 

<img src = "https://imgur.com/MG0B8wv.png" height="80%" width = "80%" /> 

Here we select "Install" to begin installing Active Directory Domain Services. <br/>
<br/>

<img src = "https://imgur.com/zzXL4LJ.png" height="80%" width = "80%" /> 

When the installation is complete this will be displayed and we can close the installation wizard. <br/>
<br/>

<img src = "https://imgur.com/nTo5CiY.png" height="80%" width = "80%" /> 

### Domain Creation

We now must configure our server as a domain controller in order to use Active Directory Domain Services. <br/>
<br/>
<img src = "https://imgur.com/5bKETeP.png" height="80%" width = "80%" /> 

We will select "Add a new forest" since we dont have an existing domain or forest to add to. I'll be naming my domain "Mango.com". <br/>
<br/>
<img src = "https://imgur.com/Y5w02xd.png" height="80%" width = "80%" /> 

As I mentioned earlier here we are installing DNS server.<br/>
<br/>
<img src = "https://imgur.com/m35WSig.png" height="80%" width = "80%" /> 

We dont have the option to add a DNS delegation so we can continue. <br/>
<br/>
<img src = "https://imgur.com/JdbQaxv.png" height="80%" width = "80%" /> 

<img src = "https://imgur.com/OWIOtLr.png" height="80%" width = "80%" /> 

We will leave this as their default paths. <br/>
<br/>
<img src = "https://imgur.com/2On6Cwv.png" height="80%" width = "80%" /> 

Final review before we complete the setup. <br/>
<br/>
<img src = "https://imgur.com/abvYd6V.png" height="80%" width = "80%" /> 

We have met the prerequisite check and can install.
After the installation is complete, the server will automatically reboot. <br/>
<br/>
<img src = "https://imgur.com/4XDqH7l.png" height="80%" width = "80%" /> 

### Creating an Admin account 

While managing the domain controller from a local admin account is possible, most organisations require individual admin accounts for added security, permission control, and auditing. Therefore we will create an admin account.

To do this first we must access Active Directory Users and Computers. <br/>
<br/>

<img src = "https://imgur.com/v1EfujV.png" height="80%" width = "80%" /> <br/>

Next we will create an organisational unit (OU) for our admin accounts. <br/>
<br/>

<img src = "https://imgur.com/xiFba17.png" height="80%" width = "80%" /> 

<img src = "https://imgur.com/RV0kwNH.png" height="80%" width = "80%" /> <br/>

Now we can create an admin account within this OU. <br/>
<br/>

<img src = "https://imgur.com/6QqwhzL.png" height="80%" width = "80%" /> 

<img src = "https://imgur.com/e18ubjB.png" height="80%" width = "80%" /> <br/>


Since this is our own account in a lab environment, we won’t require the user to change the password at their next logon, and we will set the password to never expire. However, in an organisation, it is common practice to enable these options as they are usually part of password policy to enhance security. <br/>
<br/>

<img src = "https://imgur.com/wIOFQw9.png" height="80%" width = "80%" /> <br/>

We have now created an account, but it is not yet recognised as an admin account and does not have administrative permissions. To grant the necessary permissions, we will proceed with the following steps <br/>
<br/>

<img src = "https://imgur.com/FvyvxOu.png" height="80%" width = "80%" /> 


<img src = "https://imgur.com/eimlgxH.png" height="80%" width = "80%" /> 

<img src = "https://imgur.com/UsCp9Db.png" height="80%" width = "80%" /> <br/>

Our account now has admin permissions which we will sign into and use moving forward. <br/>
<br/>

<img src = "https://imgur.com/v0ytjwM.png" height="80%" width = "80%" /> 

## Adding Networking Roles and Features

In this section, I will add key networking roles and features to the Windows Server. This includes installing and configuring Routing and Remote Access Service (RRAS) with Network Address Translation (NAT) as well as setting up DHCP scopes and leases to automatically manage IP address assignment within the network.

### Installing RAS/NAT

To enable our domain controller to function as the gateway for the client virtual machine and provide internet access, we will install the Routing feature.<br/>
<br/>
Routing is a service within the Remote Access role.

<img src = "https://imgur.com/lus04jZ.png" height="80%" width = "80%" /> 

Selecting Routing here will also automatically select RAS.

<img src = "https://imgur.com/8vjrnHN.png" height="80%" width = "80%" /> 

We will keep these default selections without making any changes.

<img src = "https://imgur.com/YGENifY.png" height="80%" width = "80%" /> 


<img src = "https://imgur.com/IsU8oL3.png" height="80%" width = "80%" /> 


After installation, we will proceed to configure it.

<img src = "https://imgur.com/X9q3Fqd.png" height="80%" width = "80%" /> 

<img src = "https://imgur.com/PYDbrcR.png" height="80%" width = "80%" /> 

Here we will select NAT.

<img src = "https://imgur.com/7O7mpMj.png" height="80%" width = "80%" /> 

Selecting our external adapter. 


<img src = "https://imgur.com/cRJANQs.png" height="80%" width = "80%" /> 

<img src = "https://imgur.com/8EsNjsV.png" height="80%" width = "80%" /> 

### Installing and configuring DHCP

Next, we will install and configure DHCP. This will enable automatic IP addressing for the client computer, similar to how it would function in an organisation.


First we navigate to the add role wizard and select DHCP.

<img src = "https://imgur.com/4fBjTk4.png" height="80%" width = "80%" /> 

The wizard has automatically selected this feature as a requirement; we will not add any additional features.

<img src = "https://imgur.com/7ITi5xT.png" height="80%" width = "80%" /> 

Confirming the installation.

<img src = "https://imgur.com/BowqYbk.png" height="80%" width = "80%" /> 

Now that DHCP has been installed we can configure by selecting DHCP from the tools list.

<img src = "https://imgur.com/eE5kYnt.png" height="80%" width = "80%" /> 

First, we will create an IP scope. This defines the pool of IP addresses available for our client machines.

<img src = "https://imgur.com/7cLRJqo.png" height="80%" width = "80%" /> 

Here, we are naming the scope. For simplicity, I have used our DHCP range as the scope's name.

<img src = "https://imgur.com/yZ7b6Jl.png" height="80%" width = "80%" /> 

We are defining the scope range, which will provide us with 100 IP addresses available for potential client computers.

<img src = "https://imgur.com/yQc4iYT.png" height="80%" width = "80%" /> 

There are no IP addresses we need to exclude from the range, so we will not make any changes in this section.

<img src = "https://imgur.com/FHVFW3y.png" height="80%" width = "80%" /> 

Lease duration: This is the period for which an IP address is assigned to a client before it must be renewed. I have selected 9 hours here, but it is not of high importance in our environment, as we only have one client machine and do not face the risk of running out of IP addresses. In contrast, in a coffee shop, the lease duration would likely be set to 1 or 2 hours to prevent depleting available IP addresses due to the high turnover of customers.


<img src = "https://imgur.com/mgHtrvP.png" height="80%" width = "80%" /> 

We also need to configure our default gateway, so we will select the 'Configure Now' option.

<img src = "https://imgur.com/uKepfJv.png" height="80%" width = "80%" /> 


Our domain controller will act as the default gateway so we will use its IP address.

<img src = "https://imgur.com/69FGFWd.png" height="80%" width = "80%" /> 

Our domain controller will also resolve DNS requests so we will select it as our parent domain.


<img src = "https://imgur.com/K2Wy3VS.png" height="80%" width = "80%" /> 

We are not using WINS, so no changes will be made here.

<img src = "https://imgur.com/Ugka6ps.png" height="80%" width = "80%" /> 


<img src = "https://imgur.com/TXzbwD6.png" height="80%" width = "80%" /> 

<img src = "https://imgur.com/zVOArid.png" height="80%" width = "80%" /> 

Our scope has been created but is not yet activated. To activate it, we need to authorise our Domain Controller.

<img src = "https://imgur.com/iib0ywX.png" height="80%" width = "80%" /> 

Now that it has been activated, we have a functioning IP scope.

<img src = "https://imgur.com/MSiDukp.png" height="80%" width = "80%" /> 

The Domain Controller is now completely configured and has all the requirements it needs to function. We can now create our first regular user in Active Directory.

## Creating OUs and Users 


Creating a new organisational unit (OU) named 'Mango', which will serve as the parent OU for all subsequent OUs.


<img src = "https://i.imgur.com/XS68x8W.png" height="80%" width = "80%" /> 
<img src = "https://i.imgur.com/MsBpFXR.png" height="80%" width = "80%" /> 

Creating two new organisational units (OUs) named 'Domain Users' and 'Domain Computers' within the 'Mango' OU.

<img src = "https://i.imgur.com/K8SdEur.png" height="80%" width = "80%" /> 
<img src = "https://i.imgur.com/VeVSmOR.png" height="80%" width = "80%" /> 

Creating the first regular user within the Domain Users organisational unit.

<img src = "https://i.imgur.com/tej3tpL.png" height="80%" width = "80%" /> 
<img src = "https://i.imgur.com/zAOjhgV.png" height="80%" width = "80%" /> 


Setting the password. In a professional environment, the 'User must change password at next logon' option is typically selected to ensure IT staff does not have access to user accounts, maintaining security and privacy.

<img src = "https://i.imgur.com/xJh46iK.png" height="80%" width = "80%" /> 
<img src = "https://i.imgur.com/svkXMnG.png" height="80%" width = "80%" /> 

Our user account is now created. We can create our second virtual machine that will act as the client computer.

## Creating the Client System

### Creating the Client Virtual Machine

Creating the 2nd VM using the .ISO file using the windows media creation tool which can be installed [here](https://www.microsoft.com/en-gb/software-download/windows10)

<img src = "https://i.imgur.com/bTVlAy8.png" height="80%" width = "80%" /> 

Allocating resources for the virtual machine. 

<img src = "https://i.imgur.com/8CqbwkG.png" height="80%" width = "80%" /> 
<img src = "https://i.imgur.com/q0h4oCm.png" height="80%" width = "80%" /> 
<img src = "https://i.imgur.com/7RPdjHQ.png" height="80%" width = "80%" /> 

Configuring the network adapter to use the internal network.

<img src = "https://i.imgur.com/g7xnICN.png" height="80%" width = "80%" /> 

### Windows 10 Installation

After creating the virtual machine we can being the Windows 10 installation process.

<img src = "https://i.imgur.com/QVd43SV.png" height="80%" width = "80%" /> 
<img src = "https://i.imgur.com/lWqGyHu.png" height="80%" width = "80%" /> 

Selecting "I don't have a Product Key".

<img src = "https://i.imgur.com/7FrBFql.png" height="80%" width = "80%" /> 

We will use the 'Pro' edition of Windows 10 because the Home edition is limited to joining only Workgroups, whereas the Pro version allows the system to join a domain.

<img src = "https://i.imgur.com/Oz9Qd5Q.png" height="80%" width = "80%" /> 

Since this is a fresh installation and not an upgrade, we will select the custom installation option.

<img src = "https://i.imgur.com/qxtaFvB.png" height="80%" width = "80%" /> 

<img src = "https://i.imgur.com/PcbdCq1.png" height="80%" width = "80%" /> 

After a few restarts, Windows presents us with a few preference-based settings.


<img src = "https://i.imgur.com/Vjd2Exz.png" height="80%" width = "80%" /> 
<img src = "https://i.imgur.com/ZFs429E.png" height="80%" width = "80%" /> 

To avoid signing in with an online Microsoft account, we will select the 'Set up for personal use' option.

<img src = "https://i.imgur.com/jkHzV7a.png" height="80%" width = "80%" /> 

Here, we are selecting the offline account option to avoid using an online Microsoft account.

<img src = "https://i.imgur.com/KiQ6Qjm.png" height="80%" width = "80%" /> 

Selecting 'Limited experience' to again avoid using an online Microsoft account.

<img src = "https://i.imgur.com/fJybgQy.png" height="80%" width = "80%" /> 

Here we are creating the default local account.

<img src = "https://i.imgur.com/MyVXx1Z.png" height="80%" width = "80%" /> 

## Hostname Change, Domain Integration, and Network Verification

Windows has been installed on the client virtual machine. This section will cover the process of changing the hostname, joining the domain and verifying the functionality of the network.

### Changing the hostname and connecting to the domain

<img src = "https://imgur.com/MNyOMXM.png" height="80%" width = "80%" /> 
<img src = "https://imgur.com/rl45KP5.png" height="80%" width = "80%" /> 
<img src = "https://imgur.com/wWRUdRR.png" height="80%" width = "80%" /> 
<img src = "https://imgur.com/gwBlhEt.png" height="80%" width = "80%" /> 

Logging into the domain using the designated user account

<img src = "https://imgur.com/CIgJAZT.png" height="80%" width = "80%" /> 
<img src = "https://imgur.com/dNpG8xq.png" height="80%" width = "80%" /> 

Client1 is now connected to the domain. Next, we will move it to the Domain Computers OU, as the current folder is merely a container and does not support linking Group Policy Objects.

<img src = "https://imgur.com/VkBotBd.png" height="80%" width = "80%" /> 
<img src = "https://imgur.com/9Ff0Ser.png" height="80%" width = "80%" /> 
<img src = "https://imgur.com/iHgmpvP.png" height="80%" width = "80%" /> 
<img src = "https://imgur.com/xQa1v1H.png" height="80%" width = "80%" /> 

### Verifying Network Connectivity and Functionality

Using the ipconfig command, we can verify that the machine has been assigned a valid IP address, along with a configured default gateway and subnet mask, confirming correct network configuration. Additionally, using the ping command to ping google.com demonstrates successful DNS resolution, therefore we can conclude that the machine has internet connectivity.

<img src = "https://imgur.com/0Bx9poM.png" height="80%" width = "80%" /> 

## Conclusion of setup 

The network has been successfully established, with the domain controller managing key networking services such as DHCP, DNS, and routing to enable the client machine's Internet access. The remainder of this repository will focus on standard administrative tasks in Active Directory, while also exploring and experimenting with it as a learning tool to further my understanding of its features and functionality.
