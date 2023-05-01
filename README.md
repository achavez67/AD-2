<p align="center">
<img src="https://i.imgur.com/TpTvrlK.png" alt="osTicket logo"/>
</p>

<h1>Installing Active Directory and Creating Admin and User Accounts</h1>




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Command Prompt

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)


<h2>Installing Active Directory Steps</h2>

<p>
<img src="https://i.imgur.com/duNekfV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To install active directory, we will go to DC-1's machine->Server Manager->Add Roles and Configurations->Click "Next" until you get to "Server Roles"->Click on "Active Directory Domain Services"->Add Features->"Next" until you have the ability to "install"
</p>
<br />

<p>
<img src="https://i.imgur.com/YG73wrc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After installing Active Directory Domain Services, our machine is not quite yet a domain controller, so we will need to set it up. We go to the top right corner in Server Manager and we will see a flag with an exclamation mark. We'll click it->click on "Promote this server to a domain controller"->add a new forest->create a domain name that ends in ".com". (I will call it "mydomain.com" in this lab).->create a password
</p>
<br />

<p>
<img src="https://i.imgur.com/B5skk2O.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We will then set DC-1's NIC's private IP address to be static. We can do this by going to our DC-1 virtual machine in Azure->Networking->Click on the Network Interface->IP Configurations->Click on the line where it has the Private IP address(dynamic)->switch assignment from "dynamic" to "static".
</p>
<br />

<p>
<img src="https://i.imgur.com/QKGv7oZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we will remote connect to both DC-1 and Client-1 virtual machines. We are going to ensure connectivity between the two machines using the "ping" command in the command line. We will get DC-1's private IP address from Azure, and type "ping -t [DC-1's private IP address] on Client-1's command line. We should get a perpetual response "requeset timed out". We will go to DC-1's machine and enable ICMPv4 on the local Widnows firewall. We can do this by going to Windows Defender Firewall with Advanced Security->Inbound Rules->*Enable* both rules that are named "Core Networking Diagnostics - ICMP Echo Request (ICMPv4-in)". We will go back to Client-1's machine to check the connectivity in the command line, and it should look like the image above.
</p>
<br />
