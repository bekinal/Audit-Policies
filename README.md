# Audit-Policies<h1>Handling Local Security Policies</h1>

<h2>Description</h2>
Project consists of using Active Directory Group Policy Management to configure password policies for users in the domain.
<br />


<h2>Utilities Used</h2>

- <b>VirtualBox</b> 
- <b>Group Policy Management</b>

<h2>Environments Used </h2>

- <b>Windows Server 2016</b>
- <b>Windows 10</b>

<h2>Create and Apply Password Group Policy:</h2>
Open Group Policy Management in the domain controller. Naviagate to Default Domain Policy, right-click and select Edit: <br/>
<img src="https://imagizer.imageshack.com/img922/5481/XwwY7o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to Password Policy and double click Minimum Password Length: <br/>
<img src="https://imagizer.imageshack.com/img922/2571/MQsCRw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select Define this policy setting and set the number of characters to 10: <br/>
<img src="https://imagizer.imageshack.com/img923/2154/tiNUes.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Go to Password must meet complexity requirements and verify that the policy is enabled. If not, select Define this policy setting, select Enabled, click Apply, and click OK: <br/>
<img src="https://imagizer.imageshack.com/img924/7524/IvjLZP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Double-click the Maximum password age, select Define this policy setting and set it to 30 days. Click apply and OK: <br/>
<img src="https://imagizer.imageshack.com/img924/5853/x0DNzD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In the next window, click ok: <br/>
<img src="https://imagizer.imageshack.com/img922/4223/Tuauqo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
In order to test this, we need to set the Minimum password age to zero. Double click minimum password age and select Define this policy setting. Set the value to 0 days: <br/>
<img src="https://imagizer.imageshack.com/img922/2846/b2Zbk9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Double click Enforce Password history, select Define this policy setting. Change to 3.: <br/>
<img src="https://imagizer.imageshack.com/img923/4091/CjLWDU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to Account lockout threshold: <br/>
<img src="https://imagizer.imageshack.com/img924/3237/feD4GR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure the account lockout policy with an account lockout threshold of five invalid logon attempts: <br/>
<img src="https://imagizer.imageshack.com/img924/1227/EPAJcm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click OK: <br/>
<img src="https://imagizer.imageshack.com/img924/6843/Z4JLZy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Double click Account lockout duration and change the value to 5 minutes. Click apply and OK: <br/>
<img src="https://imagizer.imageshack.com/img924/4724/Zsqlcm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Note the rule and click OK: <br/>
<img src="https://imagizer.imageshack.com/img922/6889/etmMMf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />




<h2>Rename Administrator:</h2>
Logging into the Windows 10 machine with administrator@cyber.local: <br/>
<img src="https://imagizer.imageshack.com/img922/253/AGQL30.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Search query for Edit local users and groups: <br/>
<img src="https://imagizer.imageshack.com/img922/4189/O3fumz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Opening users to find the Administrator account: <br/>
<img src="https://imagizer.imageshack.com/img924/9849/zF5Nio.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Back to the domain controller on Windows Server. New GPO named Rename Admin: <br/>
<img src="https://imagizer.imageshack.com/img924/8013/owcOap.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
GPO is edited by navigating the following path: <br/>
<img src="https://imagizer.imageshack.com/img923/7154/5mSwEF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Accounts: Rename administrator account is selected: <br/>
<img src="https://imagizer.imageshack.com/img922/6762/rRvOXm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Generic User is defined within the policy setting: <br/>
<img src="https://imagizer.imageshack.com/img922/9392/8Q8plv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Generic User verified within the Policy Setting: <br/>
<img src="https://imagizer.imageshack.com/img923/2214/vxrfQM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Rename Admin GPO is linked to Local Security Policies: <br/>
<img src="https://imagizer.imageshack.com/img922/8071/kfRM28.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Policy is updated on the Windows 10 machine by running gpupdate /force on an administrator account: <br/>
<img src="https://imagizer.imageshack.com/img924/849/52i9UL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Edit local users and groups is reopened to verify that the administrator account is changed in name to Generic User: <br/>
<img src="https://imagizer.imageshack.com/img924/7586/Hguc3V.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />


<h2>Disable Account Display:</h2>
Logging off of the current user will display the last user that was logged in. This can be prevented: <br/>
<img src="https://imagizer.imageshack.com/img922/6300/TfhoC9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Note that "Salesperson1" will appear in the immediate log history: <br/>
<img src="https://imagizer.imageshack.com/img923/9601/1Qbjiw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
On the domain controller, a new GPO is created named Disable Last Login Display in the Gorup Policy Objects Folder: <br/>
<img src="https://imagizer.imageshack.com/img923/2619/tUWpsf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
GPO is edited and Security Options is selected: <br/>
<img src="https://imagizer.imageshack.com/img922/6591/7fPkaJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Interactive logon: Do not display last user name is selected: <br/>
<img src="https://imagizer.imageshack.com/img922/4807/aRfRHG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
GPO is enabled: <br/>
<img src="https://imagizer.imageshack.com/img923/8439/wLYxfQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
New GPO is linked to Local Security Policies: <br/>
<img src="https://imagizer.imageshack.com/img924/6701/6wOjMw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Disable Last Login Display is selected: <br/>
<img src="https://imagizer.imageshack.com/img924/5191/r6t1Fu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Windows 10 is updated via gpupdate /force: <br/>
<img src="https://imagizer.imageshack.com/img924/3213/d1Wkz9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Logging out can verify that the previous user feature is removed: <br/>
<img src="https://imagizer.imageshack.com/img923/5161/kPmIx6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
