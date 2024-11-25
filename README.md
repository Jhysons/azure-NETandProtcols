# azure-NETandProtcols<p align="center">
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

- Observe ICMP Traffic
- Configure Firewall (Network Security Group)
- Observe SSH Traffic
- Observe DHCP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/tukDuku.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create Resource Group: Set up a new resource group in the Azure Portal.
Create Windows 10 VM: Create a Windows 10 virtual machine within the resource group.
Create Virtual Network: Allow the VM creation process to set up a new virtual network and subnet.
Create Linux VM: Create a Linux (Ubuntu) VM in the same resource group and virtual network.
</p>
<br />

<p>
<img src="https://i.imgur.com/As6Dk2G.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Connect to Windows VM: Use Remote Desktop to connect to the Windows 10 VM.
Install Wireshark: Install Wireshark on the Windows 10 VM.
Capture ICMP Traffic: Start packet capture in Wireshark and filter for ICMP traffic.
Ping Ubuntu VM: Retrieve the private IP of the Ubuntu VM and ping it from the Windows 10 VM.
Ping Public Website: Ping a public website (e.g., google.com) from the Windows 10 VM and observe the traffic in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/5AElwFY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Initiate Ping: Start a continuous ping from the Windows 10 VM to the Ubuntu VM.
Disable ICMP Traffic: Disable incoming ICMP traffic in the Network Security Group of the Ubuntu VM.
Observe Traffic: Observe the changes in ICMP traffic in Wireshark.
Re-enable ICMP Traffic: Re-enable ICMP traffic and observe the traffic again.
tart Packet Capture: Start a packet capture in Wireshark and filter for SSH traffic.
SSH into Ubuntu VM: Use SSH to connect to the Ubuntu VM from the Windows 10 VM.
Observe SSH Traffic: Type commands in the SSH session and observe the traffic in Wireshark.
Exit SSH: Exit the SSH session.  
Filter for DHCP Traffic: Filter for DHCP traffic in Wireshark.
Renew IP Address: Run ipconfig /renew in the Windows 10 VM and observe the DHCP traffic.  
</p>
<br />
