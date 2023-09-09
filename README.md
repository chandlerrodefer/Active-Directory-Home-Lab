<h1>Active-Directory-Home-Lab</h1>
<h2>Description</h2>
In this lab, I basically set up a mini corporate network as I set up an Active Directory (using Oracle Virtual Box) and used a PowerShell code to simulate 1000 users. I created two VMs (A server acting as my gateway) and a computer (acting as a client computer.)


<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Oracle VirtualBox</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> 
- <b>Windows Server 2019</b>

<h2>Lab walk-through</h2>

<p align="center">
Downloaded "Virtual box": <br/>
<img src="https://i.imgur.com/AADbvBQ.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Downloaded "Windows 10 ISO":  <br/>
<img src="https://i.imgur.com/nfjeGMp.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Downloaded "Windows Server 19 ISO": <br/>
<img src="https://i.imgur.com/ZiQjdOp.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Created the server first, selected 2048 MB of RAM, selected 3 cores, default discs, went to "Settings" and clicked "Bi-directional" in clipboard and "Drag and Drop", went to "Network" and added an adapter, then selected "Internal Network":  <br/>
<img src="https://i.imgur.com/HQ3rald.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Double-clicked the VM to run it, then selected the 2019 server iso download file, clicked "Install", then selected the "Standard Desktop Experience" version, then clicked "Custom Settings" (Which took a while but didn't touch anything.) Logged in (Click "Input"/click "Keyboard"/select "ctrl+alt+delete"):  <br/>
<img src="https://i.imgur.com/VxZaxWt.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Selected devices, inserted "Guest Additions CD image", went to folders and clicked the "CD Drive Guest Additions", selected "VboxWindowsAdditions64", selected "Reboot Later", then I shut down the VM via the power button in the "Start" menu, finally restarting the VM!:  <br/>
<img src="https://i.imgur.com/P9VKMBR.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Logged in, selected "Network" in the bottom right, used the "Change Adapter" option, clicked "Details" on both adapters (identified which was connected to the internet by IP and which was internal also by IP) [Forgot to change the IP, but will later]:  <br/>
<img src="https://i.imgur.com/CJ5rdg5.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Changed the name of the pc, and restarted again:  <br/>
<img src="https://i.imgur.com/mdWAUQ0.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Changed the internal IP address: <br/>
<img src="https://i.imgur.com/Ha8LxWD.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Went to "Server Manager" (Since the NICs were set up) selected option 2 "Add Roles and Features", clicked "Next", clicked "Next", chose the server (the only one), clicked "Next", added "Active Directory Domain Services", clicked "Next", clicked "Next", clicked "Next", chose "Install", and once installed I closed it:  <br/>
<img src="https://i.imgur.com/VXnMzof.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Next, I hit the flag with the notification at the top of the screen and clicked "Choose to Promote":  <br/>
<img src="https://i.imgur.com/bqiTX3x.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Chose "Add A New Forest" and entered a domain name "mydomain.com" for the sake of the lab, clicked "Next", added a password, then kept clicking "Next" until I could install, once installed the computer automatically restarted itself:  <br/>
<img src="https://i.imgur.com/wB0yddn.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Logged in again, went to "Start", went to "Windows administrative tools", and selected "Active Directory Users And Computers":  <br/>
<img src="https://i.imgur.com/LffP77A.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Right clicked "mydomain.com", selected "New", selected "Organizational Unit", named it "admins", then selected the "admins" folder, clicked "New", added a "New User", input my name and a username, selected "Next", added a password and unchecked "User must check in at next login" and selected "Password never expires" for the sake of the lab, clicked "Next" and selected "Finish":  <br/>
<img src="https://i.imgur.com/CG1MD2s.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Saw my user, clicked it, then went to "Properties", selected "Member Of", chose "Add", entered "Domain Admins", then selected "Apply", went to the "Start Menu", and signed out: <br/>
<img src="https://i.imgur.com/RvzEWRP.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Selected "Other User", now used the admin account I just created, went to the "Server Manager", clicked option 2 "Add Roles And Features" again, clicked "Next" until getting to "Server Roles", selected "Remote Access", clicked "Next" until reaching "Role Services", I chose "Routing" and added the feature, then continued pressing "Next" until I could choose "Install", and then selected "Close" once installed:  <br/>
<img src="https://i.imgur.com/NNts6PE.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
In the top right of the screen I selected "Tools", then chose "Routing And Remote Access": <br/>
<img src="https://i.imgur.com/BkkW4M5.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
I right-clicked "Domain Controller" and selected "Configure and Enable Routing and Remote Access":  <br/>
<img src="https://i.imgur.com/KptaU9L.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Selected "Next", selected "NAT", clicked on "Next", chose "Use Public Interfaces", clicked on the one labeled "Internet", clicked "Next", and then selected "Finish":  <br/>
<img src="https://i.imgur.com/2lonASb.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Back at the "Server Manager", clicked option 2 "Add Roles and Features", clicked "Next" until reaching "Server Roles", I then selected "DHCP Server", chose "Add feature", clicked "Next" until I could choose "Install" and then selected "Close":  <br/>
<img src="https://i.imgur.com/gHDQcCz.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Went to "Tools" in the top right of the screen and selected "DHCP":  <br/>
<img src="https://i.imgur.com/QDlBz9j.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Clicked "Domain Controller", right-clicked "IPv4", and then selected "New Scope":  <br/>
<img src="https://i.imgur.com/z67oWIS.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Clicked "Next", named it "172.16.0.100-200" (after the IP range for the lab), clicked "Next", added the "Start" and End" IP, changed the "Length" to "24", clicked "Next" until I could see the option to select "Yes" for configuring the DHCP options now, selected "Next" again: <br/>
<img src="https://i.imgur.com/GuobZ0a.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Added the IP address range (made sure to click "Add"), clicked "Next", kept that domain name, clicked "Next", clicked "Next" again, selected "Yes" to activating the scope now, selected "Next", clicked "Finish":  <br/>
<img src="https://i.imgur.com/ewn5vKU.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Right-clicked the "Domain Controller", selected "Authorize", right-clicked again, and selected "Refresh":  <br/>
<img src="https://i.imgur.com/lh3er5g.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Went back to the "Server Manager", selected option 1 "Configure This Local Server", clicked the "Internet Enhanced Security Configuration On" and then selected "Off", selected "Off", and then pressed "Ok":  <br/>
<img src="https://i.imgur.com/bs0yxRy.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Using the PowerShell script link, I added it to the desktop, opened the file inside named "Names", then added my own name, and then saved it:  <br/>
<img src="https://i.imgur.com/eVRb6sk.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Clicked the "Start Menu", right-clicked "PowerShell ISE", and chose "Run as administrator", then clicked "Yes":  <br/>
<img src="https://i.imgur.com/oTBVish.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
I clicked the folder icon, clicked the script folder, clicked "Create Users" which opened the script:  <br/>
<img src="https://i.imgur.com/qIqICgS.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
I set the execution policy to unrestricted, clicked yes to all, changed the directory (using admin account created), typed "ls" and pressed the enter key, and then chose "Run Script":  <br/>
<img src="https://i.imgur.com/TveaHSb.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Went back to "Active Directory Users and Computers", confirmed the "New Users" folder with all of the new users created, right-clicked the domain and selected "Find", and searched for myself:  <br/>
<img src="https://i.imgur.com/WJ7rGw1.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
I minimized the "Domain Controller", went back to "Virtual Box", created a new VM, selected "Windows 10", and went through the same settings:  <br/>
<img src="https://i.imgur.com/glJSSRI.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
I right-clicked the virtual machine once it was created, opened "Settings", added "Bi-Directional" again, went to "Network", selected "Internal Network" in "Adapter 1", selected "OK", double-clicked to enable, added the "Windows 10 ISO", clicked through, chose "Install", selected "I don't have a product key", selected "Windows 10 Pro", chose "Accept", then chose "Custom",  waited for the installation, selected my region, skipped the "Additional Keyboard", selected "I have no internet", selected "For Home Use",  and kept skipping through while setting up default settings (just to get through for the lab):  <br/>
<img src="https://i.imgur.com/4JDATm0.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Pulled up the VM and "Windows 10" VM simultaneously, used the "Command Prompt" in "Windows 10", used the command "ipconfig", used the "ping" command to ping a website to ensure that I was able to connect to the internet, and also pinged my domain to make sure it was up as well:  <br/>
<img src="https://i.imgur.com/ezhAD6X.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Went to "Rename this pc (Advanced)" in the "About" section of "Settings", selected "Change", I  renamed the computer based on the account that was just created, joined the created domain by typing it in, logged in with my created "User" domain name, and restarted the VM:  <br/>
<img src="https://i.imgur.com/xuqgnR1.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Went back to the "Domain Controller", logged in, went back to "Tools", then selected "DHCP", under "IPv4" I clicked "Scope", I then selected "Address Leases" where I could see the "Lease" for the "Client" account I had just created:  <br/>
<img src="https://i.imgur.com/Gsn0vtA.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Went back to "Start", selected "Active Directory Users and Computers", and under "Computers" I could now see the "Client" computer I just added as well:  <br/>
<img src="https://i.imgur.com/mRhng9F.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Went back to the "Client" computer and I tested a random login from one of the randomly generated users from earlier:  <br/>
<img src="https://i.imgur.com/EuxfH91.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
Went to "Command Prompt" after logging in, just to make sure all was successful and this concluded the lab!:  <br/>
<img src="https://i.imgur.com/GRiXSW8.png" height="80%" width="80%" alt="Active-Directory-Home-Lab"/>
<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
