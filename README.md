<p align="center">
<img src="https://i.imgur.com/BcrjvCp.jpeg" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as configure a Network Security Group. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command Line Tools
- Various Network Protocols (SSH,RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 Enterprise, version 22H2 - x64 Gen2
- Ubuntu Server 22.04 LTS - x64 Gen2

<h2>High-Level Steps</h2>

Observe ICMP Traffic
- Step 1 - Within the Windows VM, download and install Wireshark.
- Step 2 - Open Wireshark and Start packet capture and filter for SSH traffic only.
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
- Step 3 - Task Complete

<h2>Actions and Observations</h2>

<p>
<img width="1603" height="381" alt="nt1" src="https://github.com/user-attachments/assets/60dbc4b3-9cd8-4dc6-96e1-6270abde9cef" />
<img width="751" height="775" alt="nt2" src="https://github.com/user-attachments/assets/8b5e9b6b-a9d2-465a-8a7c-edded76cb817" />
<img width="757" height="689" alt="nt3" src="https://github.com/user-attachments/assets/91dd1694-591e-4ea2-b685-9f2128e7518d" />
</p>
<p>
Let's start by logging into the Windows VM via the Remote Desktop Protocol (RDP). In the VM section of the Azure portal, copy the Windows VM public IP address. Open RDP, click the "+" to add a PC, paste the IP into the PC name box, and click save. Click the new PC to connect and enter the credentials that were created in Azure.
</p>
<br />

<p>
<img width="2680" height="1513" alt="nt4" src="https://github.com/user-attachments/assets/895752d7-3fb7-4f82-aa11-255a3f3e3ed0" />
</p>
<p>
Within the Windows VM via RDP, open a browser and navigate to wireshark.org/download to download Wireshark. Then, install it.
</p>
<br />

<p>
<img width="2134" height="1160" alt="nt5" src="https://github.com/user-attachments/assets/34649f3a-4d4c-443c-84f4-c1ec7f3c01b1" />
<img width="2134" height="1156" alt="nt6" src="https://github.com/user-attachments/assets/a5bfa080-af04-4a8f-9c49-ede0ea5720cd" />
</p>
<p>
Open Wireshark, select Ethernet, then click the shark fin to start packet capture. Type ICMP, then enter to filter only for ICMP traffic.
</p>
<br />

<p>
<img width="1315" height="813" alt="nt7" src="https://github.com/user-attachments/assets/ca504505-4e54-485b-be9b-4ab351f91c52" />
<img width="2192" height="1701" alt="nt8" src="https://github.com/user-attachments/assets/a81785df-d79f-4c24-a5e4-9ba56aff00c9" />
</p>
<p>
Let ping the Ubuntu VM to test connectivity. Go to the Ubuntu VM within Azure and copy the Private IP Address. Return to the Windows VM via RDP and open PowerShell. In the command line, type: ping (Ubuntu Private Ip). In this example, I entered: ping 10.0.0.5, then pressed Enter. You can view the replies in PowerShell, as well as the requests and Replies in Wireshark. The ping was successful.
</p>
<br />

<p>
<img width="1300" height="899" alt="nt10" src="https://github.com/user-attachments/assets/90ed3793-3512-40f0-9c97-f1f857c5747e" />
<img width="1673" height="943" alt="nt11" src="https://github.com/user-attachments/assets/fb681678-4f9a-4e97-81c8-b8311f335e59" />
</p>
<p>
Now, let's set up a firewall on the Ubuntu VM to block ping requests. With the Ubuntu VM in Azure, select Network Settings, then Network Security Group. Select Settings > Inbound Security Rules > Add > ICMPv4 > Deny > Add.
</p>
<br />

<p>
<img width="2180" height="1224" alt="nt12" src="https://github.com/user-attachments/assets/75b53ae8-d1af-4383-b143-7fe93030dc67" />
<img width="1615" height="386" alt="nt13" src="https://github.com/user-attachments/assets/86726a28-2164-450c-a24a-cfb7886f0046" />
</p>
<p>
Now, in the Windows VM via RDP, try to ping the Ubuntu VM. You will see the Request timed out in PowerShell, and no response found in Wireshark. Now return to the Ubuntu VM in Azure, and click on the trash can to delete the firewall.
</p>
<br />

<p>
<img width="2804" height="1288" alt="nt14" src="https://github.com/user-attachments/assets/1674bf59-7967-4f03-a3bc-997522ab6068" />
</p>
<p>
Let's check SSH traffic. Still in the Windows VM via RDP, type ssh into the Wireshark search bar and press Enter. In the PowerShell command line, enter ssh (Ubuntu username@Ubuntu private IP address). In this example, I entered ssh labuser@10.0.0.5 and then pressed Enter. I then entered the Ubuntu VM password and pressed the Enter key. At the bottom of the PowerShell text, you can see labuser@ubuntu-vm in green. That means we are now connected to the Ubuntu VM. If you examine Wireshark, you can see that we are now receiving SSH traffic.
</p>
<br />

<p>
<img width="2684" height="1004" alt="nt15" src="https://github.com/user-attachments/assets/4b0a71c4-90e4-4d2e-b8e7-bea9f99ef5d1" />
</p>
<p>
Now, let's filter for DNS traffic. Still in the Windows VM via RDP, type dns into the Wireshark search bar and press Enter. In the PowerShell command line, enter nslookup google.com. Now you can see the IP addresses that are assigned to google.com, and in Wireshark, the DNS traffic can be observed. 
</p>
<br />

<p>
<img width="1968" height="1018" alt="nt16" src="https://github.com/user-attachments/assets/64423507-5189-4f34-b397-5ec5ab7d9744" />
</p>
<p>
Finally, let's observe RDP traffic. Still in the Windows VM via RDP, type: tcp.port == 3389 into the Wireshark search bar and press Enter. and observe the constant traffic. There is constant traffic, so the RDP user can see it in real-time.
</p>
<br />


