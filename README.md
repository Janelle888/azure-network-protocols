<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Resource and VMs
- Install WireShark to observe traffic
- Observe different kinds of traffic

<h2>Set up</h2>


  
</p>
<br />

Create a resource group in azure.

<p>
Image
  
</p>
<p>

Create a virtual machine in azure running Windows 10, make sure that this virtual machine is placed in your resource group. Make sure that your vm is also in the same region as your resource group.
  
</p>
<br />

<p>
Image
  
</p>
<p>

Create a virtual machine in azure running Linux (Ubuntu), make sure that this virtual machine is placed in your resource group. Make sure that your vm is also in the same region as your resource group.
  
</p>
<br />

<p>
Image
  
</p>
<p>
Line
  
</p>
<br />



<h2>Actions and Observations</h2>

<p>
Image
  
</p>
<p>
Log into each virtual machine by going to the remote desktop app on your computer and enter the information for your VM.
  
</p>
<br />

<p>
Image
  
</p>
<p>
  
In your windows 10 vm download [WIRE SHARK](https://www.wireshark.org/download.html).
  
</p>
<br />

<p>
Image
  
</p>
<p>
 Install Wire Shark onto the vm. You can skip through all of the options, we will install Wire Shark by the default settings.
  
</p>
<br />

<p>
Image
  
</p>
<p>
Go to the start menu and open Wire Shark on the vm. Click the Ethernet adapter and the blue icon in the left corner of the window so that we can capture packets.
  
</p>
<br />

<p>
Image
  
</p>
<p>
Filter for icmp traffic. 
  
</p>
<br />

<p>
Image
  
</p>
<p>
Open powershell on vm1 and ping vm2's private ip address.
  
</p>
<br />

<p>
Image
  
</p>
<p>
Observe ping and reply sequence.
  
</p>
<br />

<p>
Image
  
</p>
<p>
  
Ping a website like www.google.com and observe the ping and reply sequence.
  
</p>
<br />

<p>
Image
  
</p>
<p>
  
Send out a continuous ping ( -t) from vm1 to vm2.
  
</p>
<br />

<p>
Image
  
</p>
<p>
Go back to the portal, go to vm2s network security group. Inside of the security group we are going to go to inbound rules and create a rule that denies icmp traffic.
  
</p>
<br />

<p>
Image
  
</p>
<p>
Observe reaction.
  
</p>
<br />

<p>
Image
  
</p>
<p>
Go to the portal and allow icmp traffic again.
  
</p>
<br />

<p>
Image
  
</p>
<p>
In Wire Shark filter for ssh traffic. Use ssh to log in to vm2 using vm1.
  
</p>
<br />

<p>
Image
  
</p>
<p>
In powershell type ssh, use your username and password for vm2 to log in. you can check that you have logged in correctly by typing "id" into powershell.
  
</p>
<br />

<p>
Image
  
</p>
<p>
Filter for dhcp traffic.
  
</p>
<br />

<p>
Image
  
</p>
<p>
In powershell type in "ipconfig /renew. Observe the dhcp traffic. 
  
</p>
<br />

<p>
Image
  
</p>
<p>
Filter for dns traffic. 
  
</p>
<br />

<p>
Image
  
</p>
<p>
In powershell type "nslookup" along with a website for example www.google.com. Press enter and observe the traffic. 
  
</p>
<br />

<p>
Image
  
</p>
<p>
Filter for rdp traffic. 
  
</p>
<br />

<p>
Image
  
</p>
<p>
Line
  
</p>
<br />

<p>
Image
  
</p>
<p>
Line
  
</p>
<br />

<p>
Image
  
</p>
<p>
Line
  
</p>
<br />

<p>
Image
  
</p>
<p>
Line
  
</p>
<br />

<p>
Image
  
</p>
<p>
Line
  
</p>
<br />

<p>
Image
  
</p>
<p>
Line
  
</p>
<br />

<p>
Image
  
</p>
<p>
Line
  
</p>
<br />

<p>
Image
  
</p>
<p>
Line
  
</p>
<br />

<p>
Image
  
</p>
<p>
Line
  
</p>
<br />
