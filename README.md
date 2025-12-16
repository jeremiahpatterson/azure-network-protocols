<p align="center">
<img src="https://i.imgur.com/BcrjvCp.jpeg" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as configure a Network Security Group. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command Line Tools
- Various Network Protocols (SSH,RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

Observe ICMP Traffic
- Step 1 - Within the Windows VM, download and open Wireshark.
- Step 2 - Start package capture and filter for SSH traffic only.
- Step 3 - Attempt to ping the private IP address of the Ubuntu VM. Observe Request and Replies within Wireshark.

Configure a Firewall NSG
- Step 1 - Within the Resource Group, click on the Ubuntu VM and open the Network Security Group and disable incoming (inbound) ICMP traffic.
- Step 2 - On the Windows VM, ping the Ubuntu VM and observe the ICMP traffic activity.
- Step 3 - Re-enable ICMP traffic for the Network Security Group in your Ubuntu VM.
- Step 4 - On the Windows VM, ping the Ubuntu VM and observe the ICMP traffic activity.

Observe SSH Traffic
- Step 1 - Start packet capture in Wireshark.
- Step 2 - Filter for SSH traffic only.
- Step 3 - From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine via its private IP address.
- Step 4 - Type commands (username, pwd, etc) into the Linux SSH connection and observe SSH traffic spam in Wireshark.
- Step 5 - Exit the SSH connection by typing ‘exit' then pressing Enter.

Observe DNS Traffic
- Step 1 - In Wireshark, filter for DNS traffic only.
- Step 2 - From your Windows 10 VM within a command line, use nslookup to see what Google.com and Disney.com’s IP addresses are.
- Step 3 - Observe the DNS traffic being shown in Wireshark.

Observe RDP Traffic
- Step 1 - In Wireshark, filter for RDP traffic only.
- Step 2 - Observe the immediate non-stop spam of traffic.
- Step 3 - The End.

<h2>Actions and Observations</h2>

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

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
