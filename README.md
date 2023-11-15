<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


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

- Create a resource group in azure.

<p>

![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/d6bd5aaf-ab65-4711-bf18-5dfed02cf5f0)

  
</p>
<p>

- Create a virtual machine in azure running Windows 10, make sure that this virtual machine is placed in your resource group. Make sure that your vm is also in the same region as your resource group.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/def07035-9af8-4e25-a575-3e669aaaa20e)

  
</p>
<p>

- Create a virtual machine in azure running Linux (Ubuntu), make sure that this virtual machine is placed in your resource group. Make sure that your vm is also in the same region as your resource group.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/847936a2-2e2a-48e9-b428-5463f42d1922)



<h2>Actions and Observations</h2>

<p>

- Log into each virtual machine by going to the remote desktop app on your computer and enter the information for your VM.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/c976c653-05b4-4b86-b8fe-a270208e0534)

  
</p>
<p>
  
- In your windows 10 vm download [WIRE SHARK](https://www.wireshark.org/download.html).
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/33e6c7a0-2bd5-431b-bc62-8b7b2b3942dc)

  
</p>
<p>
  
 - Install Wire Shark onto the vm. You can skip through all of the options, we will install Wire Shark by the default settings.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/5b80c7ea-110c-4327-9262-add4d22eefd7)

  
</p>
<p>
  
- Go to the start menu and open Wire Shark on the vm. Click the Ethernet adapter and the blue icon in the left corner of the window so that we can capture packets.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/23e9001b-1a17-41ad-a1d3-7522261c5897)

  
</p>
<p>
  
- Filter for icmp traffic. 
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/f45b0a3d-3a22-4a29-89e2-af9f8625e1a9)

  
</p>
<p>
  
- Open powershell on vm1 and ping vm2's private ip address.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/f9e7dab8-28d8-4a45-a65f-11776fab7b74)

  
</p>
<p>
  
- Observe ping and reply sequence.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/f4957aec-63b2-4a00-b53d-4da0ea3660b8)

  
</p>
<p>
  
- Ping a website like www.google.com and observe the ping and reply sequence.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/68a34565-9c42-4c71-99a9-1ee9e32fe997)

  
</p>
<p>
  
- Send out a continuous ping ( -t) from vm1 to vm2.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/39d10eba-83d6-4a85-affe-32dd823aefc3)

  
</p>
<p>
  
- Go back to the portal, go to vm2s network security group. Inside of the security group we are going to go to inbound rules and create a rule that denies icmp traffic.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/d4c586c9-802e-42c7-aec3-ff364381865d)

  
</p>
<p>
  
- Observe reaction.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/dc9699c4-c71b-45c2-b07b-3f710d593a14)

  
</p>
<p>
  
- Go to the portal and allow icmp traffic again.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/4bee24e0-ed1a-4854-b618-5624415afdeb)

  
</p>
<p>
  
- In Wire Shark filter for ssh traffic. Use ssh to log in to vm2 using vm1.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/568b1026-4da8-43fc-8fb4-3c7a13729363)

  
</p>
<p>
  
- In powershell type ssh, use your username and password for vm2 to log in. you can check that you have logged in correctly by typing "id" into powershell.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/37bb3966-f48c-4382-aacf-4daa41e3e4a7)

  
</p>
<p>
  
- Filter for dhcp traffic.
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/6c150e00-304a-442a-a22c-1d299778e4e8)

  
</p>
<p>
  
- In powershell type in "ipconfig /renew. Observe the dhcp traffic. 
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/6799e2af-0215-4fe9-a27a-ea4f32f2e337)

  
</p>
<p>
  
- Filter for dns traffic. 
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/5832c9b8-dde7-47b5-911f-94eb99bcf5b0)

  
</p>
<p>
  
- In powershell type "nslookup" along with a website for example www.google.com. Press enter and observe the traffic. 
  
</p>
<br />

<p>
  
![image](https://github.com/Janelle888/azure-network-protocols/assets/142438143/05d00d2f-75a3-4d60-a17d-2a822fe6eeee)

  
</p>
<p>
  
- Make sure to clean up your resources. 🗑️


</p>
<br />
  
</p>
<p>
  
Congratulations you are done.🎉
