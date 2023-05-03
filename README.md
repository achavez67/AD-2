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
<img src="https://i.imgur.com/ck9Iqsb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After installing, we will need to logout of our DC-1 machine, and log back in as user "mydomain.com\[username]". We will go to "Active Directory Users and Computers", right click on "mydomain.com" and create two Organizatinal Units. One named "_EMPLOYEES" and the other named "_ADMINS"(putting an "_" before the name and making it all caps makes it easier to distinguish organizational units that were created by the user)
</p>
<br />

<p>
<img src="https://i.imgur.com/JdHNbkA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We are going to create an admin account by going to "_ADMINS"->right click->new user. For the purposes of this project, we are going to use the name "Jane Doe"and we will create a username and password. Under the "_ADMINS" folder, we will right click in "Jane Doe"->properties->member of->add->*type* "domain admins"->apply->ok
</p>
<br />

<p>
<img src="https://i.imgur.com/35oYUlC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We will logoff DC-1 VM, and connect back in using the username created for Jane Doe.
</p>
<br />

<p>
<img src="https://i.imgur.com/be6Of4Q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we are going to join Client-1 to DC-1's domain. We will go to Azure and find DC-1's private IP address->go to Cllient-1->Networking->*click* network interface->DNS Servers->Custom->*paste* DC-1's private IP address->save.
</p>
<br />

<p>
<img src="https://i.imgur.com/pJwkEdR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
From Azure, we are going to restart Client-1 and log back in. Go to settings->system->about->rename this PC(advance)->change->*click* domain and write "mydomain.com" enter Jane Doe's username and password for permission to join domain. Then, the machine will need to restart.
</p>
<br />

<p>
<img src="https://i.imgur.com/JtZGV73.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We will login to Client-1 as mydomain.com\jane_admin. We will allow "domain users" access to remote desktop. We can achieve this by going to settings->system->remote desktop->select users that can remotely access this PC->add "domain users".->ok
</p>
<br />
