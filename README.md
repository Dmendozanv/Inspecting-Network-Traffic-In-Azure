# Inspecting-Network-Traffic-In-Azure
In this lab, I observe different kinds of traffic going to and from Azure virtual machines with Wireshark as well as experimenting with network security groups.
<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- WireShark (Protocol Analyzer)
- Command Line Protocols
- Network Protocols (ICMP, SSH, DNS, RDP)
   
<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Ubunto Server
<h2> Setup </h2>
First create a Resource Group with two Virtual Machines, a Windows 10 Pro Virtual Machine as well as an Ubunto Server Virtual Machine within Azure. Make sure to put both on the same Virtual Network so they are able to communicate with eachother. They will connect with eachother via Command Line/Powershell. 

<h2>Installation Steps</h2>
<img src="https://imgur.com/ME4s8Ub.png" height="80%" width="80%" alt="Disk Santization Steps"/>
<p>

</p>
<p>
Using Remote Desktop Connection connect to the Windows 10 Pro VM by using its Public Address. Then install Wireshark in order to start inspecting traffic.
</p>
<br />

<p>
<img src="https://imgur.com/htAEzkA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/18OcssD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In Wireshark filter for ICMP (Internet Control Message Protocol) and then open PowerShell to execute a command called PING. PING uses ICMP in order to communicate problems with data transmission. Use PING to be able to communicate to Ubunto VM's Private IPAddress as well as www.google.com, then observe the traffic. Next execute perpetual ping (ping -t) between Windows 10 and Ubuntu VM's. This will create non-stop pinging between the two VM's.
</p>
<br />

<p>
<img src="https://imgur.com/bAccWLK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/zHtgCyP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next go back into the Azure portal to upen up the network security group settings for the Ubuntu VM. And create an inbound security rule to block ICMP traffic. Make sure the rule is before SSH(300) to apply the rule and make it DENY.
</p>
<br />

<p>
<img src="https://imgur.com/e7Dw1vc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Switching back to the Windows 10 Pro VM the pings start to time out because of the new rule blocking the ICMP traffic. Now go back in to the Azure portal and re-enable ICMP traffic by changing the rule previously made to ALLOW. This allows ICMP traffic to begin resume pinging. To stop Perpetually ping use Ctrl+C.
</p>
<br />

<p>
<img src="https://imgur.com/IJWgeTN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now using Wireshark filter for SSH traffic. Open PowerShell and log into the Ubuntu VM through SSH. (username@IPaddress) Note: when using PowerSHell the password wont visibly show up as you type it in, but its there! Then observe the traffic between the two VM's. By typing exit you will leave the Ubuntu VM and jump back into my Windows 10 VM. 
</p>
<br />

<p>
<img src="https://imgur.com/H1awpKJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next filter through DNS and observe traffic. This lets your computer ask the DNS Server what the IP Address of any given host name is. For example I looked up the IP Addresses for www.google.com and www.disney.com with "nslookup" in PowerShell. 
</p>
<br />

<p>
<img src="https://imgur.com/UygQ5dl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lastly observe the traffic for RDP by using the filter for Wireshark "tcp.port==3389". It shows the non-stop traffic from the RDP live stream between one VM to another. 
</p>
<br />

<h2> Conclusion  </h2>

<p>
To finish the lab close Remote Desktop Connection and make sure to close all VM's and Resource Groups in Microsoft Azure. By observing the traffic between the VM's, you can see how different protocols are used in a network between devices. Its a great way to gether information and get an idea of how Command Prompt Line and PowerShell are used.
</p>
<br />
