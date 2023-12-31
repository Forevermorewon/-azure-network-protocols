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



**Network Traffic**




First we will Verify our two virtual machines are set up on the same network.  VM1 will run Linux Ubuntu 2022 and VM2 will run Windows 10. As highlighted the two machines are on the same Vnet. 
Wireshark will be downloaded from https://www.wireshark.org/ and used to inspect packet traffic between the two machines.  Each machine will have its own network security group (Fireawall resource) and we will 
be working with each of these with command line tools.


![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/18eea789-2509-4abb-bac4-268e97da84de)












        Once Wire shark is actived we can ping VM1 from powershell using the ping command and the private IP address of VM1.
        We will filter WireShark for Ethernet traffic using ICMP protocol.  


![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/a8d596c3-5dd9-4bdd-a817-7a27c22436a7)






        We can observe the random packet data sent in the ping.


![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/bdb338d9-4589-42db-9854-7b29b077f287)







**Firewall and ICMP Protocol**

        
        Next we will use the powershell command ping -t to establish a continuous ping with VM1, while we disable firewall 
        traffic from ICMP protocol.


![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/e3b1c00b-80ee-4115-a569-603d85d55802)












        Create a new rule to Deny ICMP protocol traffic, by navigating to Azure.  Select the Network security group
        for machine 2.  Go to inbound security rules.  Choose +add and create new rule. 
        Note that the Priority number will determin the order in which actions are taken.


![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/3e1b0d5a-646c-469c-8cd6-76bb54624b0e)











![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/4b14b78e-a29c-4d0b-918d-409b8d4759e8)











![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/0f2abdf4-3b31-477e-9ccd-611305292ff9)











        The ping begains to time out

![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/c2d74d2e-34ff-4a6e-b68e-62a5275fa76b)









        Next we will allow ICMP traffic

![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/f207082e-ce6e-408f-85d4-347da67d2b71)








        You will notice the trafiic begain on the command line of powershell

![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/10972279-c722-43b5-9530-8ebb796558e4)









        WireShark also confirms the pings and traffic

![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/6fafe071-a728-406f-af47-b6104bf8ea79)









          Stop the ping with ctrl + c

![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/8b569221-175d-4118-bd6d-700f04c86304)









**SSH Network Traffic**

          Filter WireShark for SSH traffic

![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/3e33d73d-c2b3-4526-ad98-267a25357f2f)












            Remote login to VM1 from VM2 via Power Shell using command ssh "username"@(Private IP address)
            Now we are logged into VM2 through remote log in and Using Linux OS


![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/de2a41f1-9c64-4114-a0aa-775527a195bc)









            Wireshark begins caturing SSH packets
          
![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/6220b635-fb04-413c-9b54-5a35910d46fd)












            We can now exit and we will be back to VM2 windows OS.

![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/88f1f678-8e87-4fd5-9e25-092d3811fbf8)








            In Wireshark we can filter through the port using command tcp.port==22 because ssh uses the port for secure traffic.
            And once again simply type exit to return to VM2. 





![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/762df169-e71b-4497-8a88-c27e504df2c9)




            

**DHCP and DNS Traffic**

        Now we will ananlyze DHCP traffic by forcing a renewal of our ip address with the command ipconfig /renew.
        DHCP traffic occurs on our filter through WireShark.


![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/94219aba-7777-4445-89cf-e6767fa76316)







        Now we will observe DNS traffic through WireShark.  We will use commmand nslookup and view various website.


![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/70a6ae11-c03a-4341-8e48-bd324a9b8c76)










        As before we will use a port to monitor traffic related to DNS.  udp.port==53



![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/db270819-7efd-4176-93c9-27310f8bfe3f)










        Now we will observe RDP traffic through port  3389 using tcp.port==3389.  Remote desktop uses port 3389 by default.

![image](https://github.com/Forevermorewon/-azure-network-protocols/assets/145600604/a2c6a9d6-233e-4bc0-a559-4f37e3cdb570)





