# Network-Security-Groups

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

- Step 1. Create Resource Group, VPN, two VM's with windows 10 and Linux
          Connect VM1 to remote desktop.
  
- Step 2. Download, install Wireshark (to monitor traffic)
          Put Powershell on (to type commands) ping Vm2 ipaddress, www.google.com, Vm2 -t(ping Vm2 non-stop)
  
- Step 3. VMm2 NSG create a rule to stop ICMP traffic coming in, change the rule back to accept the rule
          Explore SSH traffic log in to linux type following commands pwd, id, uname -a, ls -lasth, exit linux

- Step 4. Filter SSH traffic type TCP port command ipconfig \renew, nslookup www.google.com 

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step. 1 Azure create the following: RG, VPN, Vm1 (windows 10), Vm2 (linux) once those are set up
copy Vm1 public ipaddress paste to remote desktop, to connect Vm1 desktop 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 2. Download Wireshark analyzer, install Wireshark 64bit software, (type) ICMP to stop traffic flow, start, Powershell, have both windows side by side, ping Vm2 to see both Vm's communicate with each other see the traffic on Wireshark and command from Powershell 
ping www.google.com, ping Vm2 private ip -t should be pinging non-stop 
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 3A. Azure go to Vm2 NSG (network security group), inbound security rules, + (create rule), protocol ICMP, action deny, priority 200 first rule to obey, name blockincomingICMPtraffic. 
3B//Vm1 desktop ping should be timed out, go to Azure Vm2 NSG menu to change the rule allow ICMP traffic coming thru go to Vm1 desktop 
ICMP traffic will start coming in again to stop constant ping control C Wireshark (clear out packet info).
3C//Powershell gonna explore SSH traffic (type) ssh username@Vm2privateip, will show SSH protocols wanna continue yes, type password (password will not show type it careful to get it right), when entered correctly lettering will be green.
3D//(username@Vm2) command line linux, type in following command to see the traffic pwd, id, uname -a, ls -lasth to end linux connection (type) exit
</p>
<br />

p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Step 4. Filter SSH traffic on Wireshark on filter column type tcp, udp it will show you traffic for those protocols 
Powershell ipconfig /renew action will assign new ipaddress nslookup www.google.com will show ipaddress google uses 
</p>
<br />
