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

- Create Virtual Machines
- Create a Windows 10 VM:
- Create a Linux (Ubuntu) VM
- Observe ICMP Traffic
- Configure Firewall (Network Security Group)
- Observe SSH Traffic
- Observe DHCP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/IQgvMzj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a Resource Group:

Go to Azure Portal.

Create a new Resource Group.

In the Azure Portal, create a new Windows 10 Virtual Machine (VM).

Select the previously created Resource Group.

Allow it to create a new Virtual Network (Vnet) and Subnet.

Create a new Linux (Ubuntu) VM.

Select the same Resource Group and Virtual Network as the Windows 10 VM.

Use Username/Password for authentication.

Ensure both VMs are in the same Virtual Network/Subnet.
</p>
<br />

<p>
Within the Windows 10 VM, install Wireshark.

Open Wireshark and start packet capture.

Filter for ICMP traffic only.

Retrieve the private IP address of the Ubuntu VM.

Attempt to ping the Ubuntu VM from the Windows 10 VM.

Observe ping requests and replies in Wireshark.

Ping a public website (e.g., www.google.com) and observe the traffic in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/tukDuku.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Initiate Perpetual Ping:

From the Windows 10 VM, initiate a non-stop ping to the Ubuntu VM.

Disable Incoming ICMP Traffic:

Open the Network Security Group for the Ubuntu VM.

Disable incoming (inbound) ICMP traffic.


<p>
<img src="https://i.imgur.com/As6Dk2G.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>



Observe the ICMP traffic in Wireshark and the command line Ping activity.

Re-enable ICMP Traffic:

Re-enable ICMP traffic for the Network Security Group.

Observe the ICMP traffic in Wireshark and the command line Ping activity (should start working).

Stop the ping activity.

Start Packet Capture for SSH Traffic:

Log back into the Windows 10 VM.

Start a packet capture in Wireshark and filter for SSH traffic only.

SSH into Ubuntu VM:

From the Windows 10 VM, SSH into the Ubuntu VM using its private IP address.

Open PowerShell and type: ssh labuser@<private IP address>.

Type commands (username, password, etc.) into the Linux SSH connection and observe SSH traffic in Wireshark.

Exit the SSH connection by typing exit and pressing Enter.

Start Packet Capture for DHCP Traffic:

Filter for DHCP traffic only in Wireshark.


<p>
<img src="https://i.imgur.com/5AElwFY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p

Renew IP Address:

From the Windows 10 VM, open PowerShell as admin and run: ipconfig /renew.

Observe the DHCP traffic appearing in Wireshark.

Start Packet Capture for DNS Traffic:

Filter for DNS traffic only in Wireshark.

Use nslookup:

From the Windows 10 VM, use nslookup to see the IP addresses of google.comand disney.com.

Observe the DNS traffic in Wireshark.

Start Packet Capture for RDP Traffic:

Filter for RDP traffic only (tcp.port == 3389) in Wireshark.

Observe the non-stop spam of traffic due to the constant live stream from one computer to another.
</p>
<br />
