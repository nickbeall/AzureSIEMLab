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

<hr>

<h4 align="center">Configure Microsoft Defender:</h4> 
<p align="center">
Navigate to Microsoft Defender for Cloud. <br/>
<img src="https://i.imgur.com/bgwDo8F.png" alt="Defender Config Pt1"/>
 Click "Environment Settings" in the left menu.  <br/>
 <img src="https://i.imgur.com/W1Ltio1.png" alt="Defender Config Pt2"/>
 Expand your Azure Subscription to find the Log Analytics Workspace we created and open it.  <br/>
 <img src="https://i.imgur.com/9IMgjI4.png" alt="Defender Config Pt3"/>
 Turn servers on and leave SQL servers off. Click save in the top left. Select "Data Collection" in the left menu and set to "All Events". Click Save in the top left.  <br/>
 <img src="https://i.imgur.com/8vxnYT2.png" alt="Defender Config Pt4"/>
 <img src="https://i.imgur.com/ZVubHVU.png" alt="Defender Config Pt5"/>
</p>

<hr>

<h4 align="center">Connect Log Analytics Workspace to the Virtual Machine:</h4> 
<p align="center">
Navigate back to the Log Analytics Workspaces page. Click our Log Analytic Workspace. Click "Virtual Machines (deprecated)" in the left menu. Click "Connect" in the top left. <br/>
 <img src="https://i.imgur.com/VfHudgx.png" alt="Connect LAW to VM Pt1"/>
 <img src="https://i.imgur.com/0WKRbrl.png" alt="Connect LAW to VM Pt2"/>
</p>

<hr>

<h4 align="center">Set Up Sentinel:</h4> 
<p align="center">
In a new tab, visit portal.azure.com. Navigate to the Microsoft Sentinel page. Click "Create".<br/>
 <img src="https://i.imgur.com/CTd4JYP.png" alt="Sentinel Pt1"/>
 Select our Log Analytics Workspace and Click "ADD" in the bottom left. <br/>
 <img src="https://i.imgur.com/kNILkS8.png" alt="Sentinel Pt2"/>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
