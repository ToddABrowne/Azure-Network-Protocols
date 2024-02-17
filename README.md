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

- Create Our Resources
- Observe ICMP and SSH Protocol Traffic
- Observe DHCP and DNS Protocol Traffic
- Observe RDP (tcp.port ==3389)

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/tsC1qFZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
</p>
<img src="https://i.imgur.com/h20SJQ5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p>
Virtual Machine 1's system is operating on Windows 10 Pro. Virtual Machine 2's system is operating on Ubuntu (Linux). These 2 VMs are on the same Virtual Network but have different public and private  ip addresses. Wireshark will be the analyzer of choice.

</p>
<br />

<p>
<img src="https://i.imgur.com/ewYbUWS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<img src="https://i.imgur.com/yaeH3rf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p>
The top image displays ICMP raw traffic between VM1 and VM2. The raw traffic consist of ping command and perpetual ping command. Behind the scenes I also created a new rule for VM2 inbound IMCP traffic to be denied which created a time out reply. I then changed the access from deny back to allow, which reconnected communication with VM1 and VM1 through ICMP. The bottom image is observation of SSH command from VM1 to VM2. This allows me to take over VM2 from VM1.
  
</p>
<br />

<p>
<img src="https://i.imgur.com/iPQ7KJi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
</p>
<img src="https://i.imgur.com/T2Fox26.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p>
Requesting a new ip address through the DHCP is the image being displayed on top. There are multiple reasons why this request takes place. A few examples are network changes, troubleshooting, lease expiration, and ip address pool exhaustion. Below that image is the ipconfig command for name server lookup. Better known as DNS. This process communicates domain names into ip addresses.
  
</p>
<img src="https://i.imgur.com/raUIuoY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
What you see above is the consistant raw traffic from the tcp.port == 3389 also known as RDP.

</p>
<br />
