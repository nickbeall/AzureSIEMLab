<h1>Azure Honey Pot With Sentinel Map Tracking</h1>

<!-- ### [YouTube Demonstration](https://youtu.be/7eJexJVCqJo)-->

<h2>Description</h2>
In this lab I set up Azure Sentinel (SIEM) and connect it to a virtual machine that has been configured to be a honey pot. Live attacks are observered (RDP Brute Force) from around the world. Using a custom PowerShell script, the attackers geolocation information is gathered and plot on the Azure Sentinel map. 
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Microsoft Azure</b>
- <b>Microsoft Sentinel</b>

<h2>Environments Used </h2>

- <b>Windows 10</b>

<h2>Lab Walk-Through:</h2>


<h4 align="center">Create a Virtual Machine:</h4> 
<p align="center">
 Search "Virtual Machine" in the search bar to visit the Virtual Machine page. Click "Create" in the top left and select "Azure Virtual Machine".
<img src="https://i.imgur.com/Zi6VTdQ.png" height="80%" width="80%" alt="Creating Virtual Machine"/>
<br />
<br />
</p>

<hr>

<h4 align="center">Configure the Virtual Machine:</h4> 
<p align="center">
 Once in the VM settings, create a new Resource group named "HoneypotLab". Name the VM "honeypot". Set the region to "West US 3". Set the Image to "Windows 10 Pro". <br/>
<img src="https://i.imgur.com/AwE05eP.png" height="80%" width="80%" alt="VM Configuration Pt1"/><br/>
 Set a username and password. We will need these in a moment to access our VM. Set inbound ports to "RDP (3389)".<br/>
 <img src="https://i.imgur.com/9KM0Z9c.png" height="80%" width="80%" alt="VM Configuration Pt2"/><br/>
 Click next until you reach the Network page. Set NIC network security group to "Advanced". Click "Create new" under "Configure network security group".<br/>
 <img src="https://i.imgur.com/SWdJGzy.png" height="80%" width="80%" alt="VM Configuration Pt3"/><br/>
 Delete the inbound rule and create and new one with the below settings. <br/>
 <img src="https://i.imgur.com/ja39a3Z.png" alt="VM Configuration Pt4"/><br/>
 Click "Review+Create" and "Create" on the page following that. This will begin the process of deploying your Virtual Machine. <br />
 <img src="https://i.imgur.com/npijgic.png" alt="VM Configuration Pt5"/><br/>
<br />
<br />
</p>

<hr>

<h4 align="center">Set Up Log Analytics Workspace:</h4> 
<p align="center">
Navigate to the Log Analytics Workspaces page. Click "Create" in the top left. <br/>
<img src="https://i.imgur.com/amVBUHV.png" alt="LAW Creation Pt1"/>
 Set resource group to "HoneypotLab". Name the new Log Analytics Workspace "law-honeypot1". Set region to "West US 3". Click "Review+Create". <br/>
 <img src="https://i.imgur.com/wFGAw3Z.png" alt="LAW Creation Pt2"/>
</p>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
