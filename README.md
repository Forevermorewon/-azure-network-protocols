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

<h2>Actions and Observations</h2>


First we will Verify our two virtual machines are set up on the same network.  VM1 will run Linux Ubuntu 2022 and VM2 will run Windows 10. 
As highlighted the two machines are on the same Vnet.  Wireshark will be downloaded from https://www.wireshark.org/ and used to inspect packet traffic between the two machines.  
Each machine will have its own network security group (Fireawall resource) and we will be working with each of these with command line tools.


![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/18eea789-2509-4abb-bac4-268e97da84de)










Once Wire shark is actived we can ping VM1 from powershell using the ping command and the private IP address of VM1.
We will filter WireShark for Ethernet traffic using ICMP protocol.  


![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/a8d596c3-5dd9-4bdd-a817-7a27c22436a7)










</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
