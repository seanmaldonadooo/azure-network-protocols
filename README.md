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

- Create Resources within Azure
- Observe ICMP traffic with Wire Shark
- Observe SSH traffic
- Observe DHCP traffic
- Observe DNS traffic
- Observe RDP traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/seanmaldonadooo/azure-network-protocols/assets/149026184/7a5b153f-610d-4e3b-af98-60d9339a4bc4" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a Resource Group
Create a Windows 10 Virtual Machine (VM)
Create a Linux (Ubuntu) VM.
While creating the VM, select the previously created Resource Group and Vnet.
</p>
<br />

<p>
<img src="https://github.com/seanmaldonadooo/azure-network-protocols/assets/149026184/e60b9a18-b0b1-417e-8004-9c5ef0cc66f0" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Use Remote Desktop to connect to your Windows 10 Virtual Machine.
Within your Windows 10 Virtual Machine, Install Wireshark.
Open Wireshark and filter for ICMP traffic only.
Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM.
From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark.
</p>
<br />

<p>
<img src="https://github.com/seanmaldonadooo/azure-network-protocols/assets/149026184/6b482bd8-3ee3-4605-bfdc-1ca4f9d3bbfb" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, filter for SSH traffic only.
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address).
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark.
Exit the SSH connection by typing ‘exit’ and pressing [Enter].
</p>
<br />

<p>
<img src="https://github.com/seanmaldonadooo/azure-network-protocols/assets/149026184/e23112ea-c764-4ea0-8525-84f17549f126" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, filter for DHCP traffic only.
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew).
Observe the DHCP traffic appearing in WireShark.
</p>
<br />

<p>
<img src="https://github.com/seanmaldonadooo/azure-network-protocols/assets/149026184/1d93951b-7117-4eb1-af2a-84df16cbb1e5" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, filter for DNS traffic only.
From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are.
Observe the DNS traffic being show in WireShark.
</p>
<br />

<p>
<img src="https://github.com/seanmaldonadooo/azure-network-protocols/assets/149026184/4c2405d5-92db-4023-9ebe-a89468e5b544" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, filter for RDP traffic only (tcp.port == 3389).
Observe the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?
Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefore traffic is always being transmitted.
</p>
<br />
