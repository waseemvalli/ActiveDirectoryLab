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
Here we use the Windows Server 2019 ISO which can be installed [here](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2019) <br/>
<img src="https://i.imgur.com/7xzAg4J.png" height="80%" width="80%" />

As we will not be performing demanding tasks with our virtual machine, we will allocate minimal resources. <br/>
<img src="https://imgur.com/WLfn0fo.png" height="80%" width="80%" />

Allocating disk space <br/>
<img src="https://imgur.com/lsclwXz.png" height="80%" width="80%" />
 
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
